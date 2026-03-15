# Cashback Verification and Coupon Reactivation — Analysis

---

## Cashback / Receipt Verification — Mechanics and Constraints

### The Kazakhstan fiscal receipt system

Kazakhstan's tax authority (КГД) has been rolling out mandatory electronic fiscal receipts since 2019. Every registered POS terminal must issue an electronic fiscal receipt with a QR code. That QR code links to the official КГД portal and contains the transaction record.

This means receipt validation in Kazakhstan is fundamentally different from most markets — you don't need OCR guessing. You read the QR, query the government database, and get a verified record with store, date, time, amount, and line items.

**What this gives you:**

- Proof the receipt is real (can't be photoshopped — the КГД record either exists or doesn't)
- Store name and address
- Date and time
- Total amount
- Line items (SKU-level in modern terminals, category-level in older ones)

**What this doesn't give you:**

- Real-time API access is not publicly documented — you'd need to negotiate with КГД or use a licensed OFD (оператор фискальных данных) that has API access
- Not all small stores/kiosks are on the electronic system. Magnum and CU are — they're required to be.

### The mechanic flow

```
User buys product in Magnum →
Uploads receipt photo in bot →
Bot extracts QR from receipt image →
Bot queries КГД/OFD API with QR data →
System confirms: Magnum, today's date, product in purchase →
Bot issues Kaspi refund (or wallet credit)
```

### Critical constraints

**1. Two-step delay**
User has to buy first, then claim. This inverts the sampling proposition — you're not reducing purchase friction, you're adding a post-purchase step. This is cashback, not sampling. The psychology is different: user has already paid, now they want money back. The behavioral model is different from "free product voucher."

**2. КГД API access**
There is no public API for querying fiscal receipts programmatically. Licensed OFD operators (e.g., Kazakhtelecom) have this data. You'd need either:

- A commercial agreement with an OFD operator
- An unofficial approach (scraping the КГД portal — fragile, TOS-violating)
- Accept receipt photo + OCR as "good enough" validation (loses fraud protection)

**3. Payment rail**
Kaspi Pay is the right answer for Kazakhstan. Near-universal penetration, supports P2P and merchant payments. Practical flow: brand pre-loads a Kaspi Business account, refunds go from there. Requires Kaspi Business API access and a commercial agreement.

**4. Tax treatment**
A cashback payment may be treated differently from "free product" under Kazakhstan tax law. The brand's finance team would need to confirm. This is a complexity the brand may not want in a pilot.

**5. Product-level validation**
"User bought Coca-Cola" requires line items from the receipt. КГД records include item names, but the level of detail depends on the retailer's POS setup. Magnum should have SKU-level data. If they only record "beverages" as a category, validation becomes weaker.

### When cashback makes sense

- As a fallback when retail code pools fail (see ideas_analysis.md, Idea 5)
- As a channel for geographies without partner retailers
- As a recovery mechanic for users whose activation code expired at checkout
- As Stage 2 when OFD API access is established

For the pilot: not worth the setup complexity unless code pools fail entirely.

---

## Coupon Reactivation Problem

### The core issue

When a user activates for Partner A (e.g., Magnum) and receives a QR code:

- Our system knows: QR code was generated at T, expires at T+15min
- We do NOT know: whether Magnum's scanner actually processed it
- POS confirmation comes in batches, with lag (daily, at best)

So if the user says "I didn't use it, let me switch to Glovo" — we cannot verify.

### Three policy options

**Option A: No reactivation. Code issued = voucher consumed.**

Once you select a partner and the code is generated, that voucher is used. No reactivation, ever.

- Pro: zero fraud surface, simplest to implement and explain
- Con: terrible UX for legitimate failures (cashier couldn't scan, app crashed, user changed plans)
- In practice: generates support requests and angry users; not suitable for a consumer-facing pilot

**Option B: One reactivation after TTL expires, with rate limiting.**

After the 15-minute code expires, user can request one reactivation for a different (or same) partner. Rules:

- Minimum 30-minute wait between activations for same voucher
- Maximum 2 activations per voucher total
- System flags accounts that consistently activate → switch → activate (fraud pattern)

- Pro: covers legitimate failures, bounded fraud exposure, detectable abuse pattern
- Con: small fraud surface (user activates for Partner A, waits 15 min, switches to Partner B)
- Fraud cost estimate: 1 extra drink per fraudulent voucher in the worst case. At 400 KZT/drink and a 10% abuse rate on a 10,000-voucher pilot = 400,000 KZT. Brand decides if this is acceptable.

**Option C: Free reactivation, monitor during pilot.**

Allow partner switching freely after TTL expires. Log everything. Analyze fraud signal from pilot data.

- Pro: best UX, generates data to calibrate fraud baseline
- Con: no bound on fraud until pilot data exists; brand may not accept unknown exposure

### Recommended policy for pilot

**Option B**, with these specific parameters:

- 1 free reactivation per voucher, available only after code TTL expires (15 min after issuance)
- 60-minute cooldown between reactivation attempts
- After 2nd code generation, voucher is locked — no further reactivation
- Flag users who burn 2 activations across 2 different partners → manual review list

This gives legitimate users a recovery path, bounds fraud at 2 drinks max per voucher, and generates the pilot data needed to calibrate the policy for Stage 2.

### What POS integration would change

With real-time POS integration, you'd know within seconds whether the code was scanned. The reactivation question becomes a technical one: "was it scanned? no → allow switch. yes → reject." But retail POS integration in Kazakhstan (Magnum, CU) requires negotiation, technical work, and ongoing maintenance. Not realistic for a pilot.

The right framing: Option B for pilot. POS integration as Stage 2 upgrade that eliminates the policy ambiguity entirely.

---

# Анализ доступа к API фискальных чеков в Казахстане (2024–2025)

В данном отчете представлен глубокий технический анализ способов программной проверки фискальных чеков ККМ (контрольно-кассовых машин) для задач маркетинга, лояльности и предотвращения фрода.

---

## 1. Официальный государственный контур (КГД МФ РК)

Комитет государственных доходов (КГД) является первоисточником данных, но прямой доступ к их API для частного бизнеса сильно ограничен.

- **Портал Smart Bridge (isb.kz):**
  - **Сервис:** `Esalyq Business - получение номера чека` (ключ `USC_ESBM_CheckNumService`).
  - **Метод:** SOAP.
  - **Доступ:** Требует официальной заявки через Smart Bridge. Доступен в основном госорганам или стратегическим партнерам. Для малого и среднего бизнеса этот путь практически закрыт из-за бюрократии.
- **Публичная проверка (consumer.kgd.gov.kz):**
  - Позволяет проверить факт существования чека по фискальному признаку (ФП), сумме и дате.
  - **Минус:** Не отдает номенклатуру (список товаров) в машиночитаемом виде без парсинга HTML-страницы.

---

## 2. Коммерческий контур: Операторы фискальных данных (ОФД)

Это наиболее жизнеспособный путь для коммерческих проектов. Каждый чек в РК проходит через одного из лицензированных ОФД.

### А. АО «Казахтелеком» (oofd.kz)

Крупнейший оператор. Предоставляет наиболее развитое API.

- **API E-Kassa:** REST/JSON интерфейс.
- **Возможности:** Получение полной номенклатуры (список товаров), данных по сменам (Z-отчеты) и истории чеков.
- **Условие доступа:** Заключение коммерческого договора и генерация `AuthToken` в личном кабинете. Это платный сервис.
- **Документация:** Доступна по адресу `oofd.kz/integration`.

### Б. АО «Транстелеком» (ofd1.kz)

Второй по величине игрок.

- **Доступ:** Предоставляет API-ключи корпоративным клиентам по запросу в техподдержку.
- **Особенности:** Имеет тестовый стенд для разработчиков, но менее подробную документацию, чем Казахтелеком.

---

## 3. SaaS-решения: Программные ККМ (Webkassa, re:Kassa)

Если проект не может договориться с ОФД напрямую, можно использовать API «программных касс», которые уже интегрированы со всеми ОФД.

- **Webkassa (webkassa.kz):** Предоставляет мощный REST API. Если ваши партнеры-ритейлеры используют Webkassa, вы можете получать данные о продажах напрямую через их токены.
- **re:Kassa:** Аналогичный сервис, популярный у малого бизнеса. Имеет удобные SDK для мобильных приложений.

---

## 4. Сравнение методов интеграции

| Метод                  | Данные (Номенклатура) | Защита от фрода | Сложность доступа       | Рекомендация                                    |
| :--------------------- | :-------------------- | :-------------- | :---------------------- | :---------------------------------------------- |
| **ОФД (Казахтелеком)** | Полные данные         | Максимальная    | Средняя (нужен договор) | **Лучший выбор** для крупных систем лояльности. |
| **Smart Bridge (КГД)** | Официальный статус    | Максимальная    | Высокая (гос. барьеры)  | Только для гос-проектов.                        |
| **API Webkassa**       | Полные данные         | Высокая         | Низкая (SaaS подписка)  | Идеально для малого/среднего бизнеса.           |
| **Парсинг QR-кода**    | Зависит от ОФД        | Низкая          | Низкая (но нестабильно) | Только для MVP или прототипов.                  |
| **OCR + Проверка ФП**  | Только сумма/дата     | Средняя         | Средняя                 | Если не нужен список товаров.                   |

---

## 5. Выводы и рекомендации для проекта

Для реализации **Sampling/Coupon платформы** в Казахстане:

1. **Основной путь:** Интеграция с **API Казахтелеком ОФД**. Это единственный способ гарантированно получать список товаров в чеке, чтобы убедиться, что пользователь купил именно Coca-Cola, а не просто любой товар на сумму 500 тенге.
2. **Запасной путь (OCR):** Использование фото чека + OCR (Google Vision / Mindee) для извлечения параметров (РНМ, ФП, Сумма) и последующая автоматическая проверка через публичный URL ОФД. Это подтвердит, что чек настоящий, но не даст 100% уверенности в составе товаров без парсинга HTML.
3. **Безопасность (Fraud Protection):**
   - **Проблема:** Чек может быть настоящим, но «чужим» (найденным на улице).
   - **Решение:** Ограничение по времени загрузки (не более 1 часа с момента выдачи чека) и проверка уникальности фискального признака (ФП) в вашей базе данных.
4. **Юридический аспект:** Использование данных чеков сторонних организаций через парсинг публичных ссылок находится в «серой» зоне TOS. Для промышленного решения **необходим прямой контракт с ОФД**.
