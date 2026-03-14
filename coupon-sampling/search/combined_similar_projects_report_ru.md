# Сводный отчёт по похожим проектам

## 1. Цель отчёта

Этот документ объединяет выводы из:

- `search/similar_projects_analysis.md`
- `search/deep_search_similar_projects.md`

и повторно проверяет ключевые допущения по похожим проектам.

Фокус сравнения:

- механика digital sampling
- чат-боты и мессенджерные промо
- выдача купона и погашение в офлайне
- доставка как канал погашения
- антифрод и операционные ограничения

---

## 2. Базовая механика нашего проекта

По [project_proposal.md](/home/ch/prj/kz/jn/coupon-sampling/docs/project_proposal.md) проект строится так:

- пользователь получает ваучер в Telegram-боте
- ваучер не равен коду погашения
- отдельный шаг `Активировать` превращает ваучер в партнёрский код или QR
- каналы погашения: retail, delivery, promo-point
- активация фиксируется в реальном времени, POS-подтверждение может приходить позже

Это важно, потому что большинство аналогов похожи либо на sampling, либо на chatbot promo, либо на coupon infrastructure, но редко совмещают всё сразу.

---

## 3. Проверка допущений

### Что подтверждается уверенно

- Telegram или WhatsApp действительно снижают трение входа по сравнению с отдельным приложением.
- Digital sampling с привязкой к ритейлу является рабочей моделью.
- Механика "получить оффер онлайн -> забрать продукт офлайн" подтверждена несколькими кейсами.
- Задержки со стороны POS и ритейла являются типичной проблемой, поэтому логика отдельной активации в вашем проекте выглядит здраво.

### Что пришлось скорректировать

- Ряд численных метрик из старого файла подтверждаются слабее, чем сами механики.
- Некоторые кейсы хорошо подтверждают канал, но слабо подтверждают именно sampling.
- Некоторые кейсы хорошо подтверждают sampling, но не через Telegram.

### Практический вывод

Для итогового отчёта ниже проекты разделены не по "громкости бренда", а по тому, насколько хорошо они подтверждают конкретные части вашей модели.

---

## 4. Разбор похожих проектов

## 4.1. Sampl / Bio&Me NearStore

- **Регион:** Великобритания
- **Тип:** платформа digital sampling
- **Ссылки:** [Sampl](https://www.sampltech.com/), [кейс Bio&Me](https://www.sampltech.com/case-studies/biome-18-coupon-redemption), [SamplPay cashback](https://www.sampltech.com/blog/introducing-samplpay-cashback)
- **Промо-механика:** пользователь видел digital-offer на бесплатный продукт рядом с Tesco, забирал оффер онлайн, а затем погашал его в магазине.
- **Как это работало по шагам:**
  Пользователь:
  видел рекламу или offer рядом с Tesco, открывал страницу кампании, подтверждал участие и получал digital coupon.
  Дальше шёл в Tesco, находил продукт на полке и использовал купон при покупке.
  Бренд / платформа:
  Sampl таргетировал аудиторию возле нужной розницы, контролировал выдачу офферов, передавал redemption-логику в ритейл-контекст и считал результат кампании.
  Tesco выступал точкой физического получения продукта.
- **Стек / delivery model:** web-led sampling platform, retailer targeting, analytics.
- **Что похоже:** trial-механика, связь с конкретным ритейлом, измеримость от digital-контакта до офлайн-погашения.
- **Что отличается:** нет Telegram, нет доставки, нет промо-точки, нет shareable voucher в чате.
- **Результат:** сильный и релевантный аналог.
- **Почему сработало:** оффер был привязан к ближайшему месту покупки, а путь до получения продукта был коротким.
- **Подтверждённые данные:** Sampl публично пишет про 18% coupon redemption и 20% sales share в Tesco для Bio&Me.
- **Оценка релевантности:** очень высокая.

## 4.2. Social Nature / Primal Kitchen

- **Регион:** Северная Америка
- **Тип:** digital trial / cashback / coupon platform
- **Ссылки:** [Social Nature для брендов](https://business.socialnature.com/established-brands/), [кейс Primal Kitchen](https://business.socialnature.com/case-studies/primal-kitchen/), [как работает cashback sampling](https://socialnaturehelp.zendesk.com/hc/en-us/articles/10769046494619-How-does-cash-back-sampling-work)
- **Промо-механика:** пользователь забирал оффер на бесплатный продукт или cashback, покупал товар в партнёрском ритейле, получал компенсацию или reward, после чего часто оставлял review.
- **Как это работало по шагам:**
  Пользователь:
  находил оффер в Social Nature, выбирал продукт, получал инструкцию где купить, покупал товар в подходящей сети, загружал подтверждение покупки или проходил redemption-flow, а затем оставлял review.
  Бренд / платформа:
  Social Nature давал бренду доступ к аудитории, раздавал офферы, вёл consumer education, собирал отзывы и связывал sampling с последующей retention-воронкой.
  Для бренда это была не просто разовая выдача, а измеряемый цикл: trial -> review -> repeat purchase.
- **Стек / delivery model:** web account flow, retailer targeting, review loop, CRM capture.
- **Что похоже:** бесплатный trial, привязка к торговым сетям, first-party data, измерение post-redemption поведения.
- **Что отличается:** не чатовый интерфейс, меньше fit для сценария "стою у кассы -> активирую -> показываю код".
- **Результат:** сильный аналог по sampling-логике.
- **Почему сработало:** sampling был частью более длинной воронки с review и repeat purchase.
- **Подтверждённые данные:** 15+ campaigns и 2,100+ reviews за 3 месяца по 3 SKU упоминаются в публичном кейсе.
- **Оценка релевантности:** высокая.

## 4.3. Coca-Cola Zero Sugar #TakeATaste Now

- **Регион:** Великобритания
- **Тип:** AR + DOOH + retail coupon sampling
- **Ссылки:** [официальный релиз Coca-Cola](https://www.coca-cola.com/gb/en/media-center/coca-cola-zero-sugar-takeatastenow-campaign), [DOOH case overview](https://www.dooh.com/works/takeataste/), [Campaign Media Awards entry](https://www.campaignmediaawards.com/finalists/game-changing-real-time-and-ar-ooh-delivered-for-coca-cola-s54v989flurz3ab)
- **Промо-механика:** пользователь сканировал QR-код с digital out-of-home экрана, в AR "забирал" цифровую бутылку и получал digital voucher на бесплатную бутылку в Tesco.
- **Как это работало по шагам:**
  Пользователь:
  видел наружную digital-рекламу, сканировал QR-код, попадал в mobile AR experience, "ловил" или "забирал" виртуальную бутылку и после этого получал купон на бесплатный продукт.
  Затем шёл в Tesco и использовал voucher для получения реальной бутылки Coca-Cola Zero Sugar.
  Бренд / платформа:
  Coca-Cola использовала DOOH как верх воронки, AR как слой вовлечения, а Tesco как точку финального trial.
  Кампания связывала медийный контакт, интерактив и офлайн-получение продукта в одном сценарии.
- **Стек / delivery model:** DOOH, AR, mobile coupon, retailer redemption.
- **Что похоже:** media-to-shelf логика, мгновенный переход от рекламы к выдаче купона, офлайн-погашение в ритейле.
- **Что отличается:** нет бота, нет чата, нет delivery-ветки, вход идёт через outdoor media.
- **Результат:** хороший аналог по retail redemption и media-to-shelf.
- **Почему сработало:** путь от рекламного контакта до trial был очень коротким и визуально вовлекающим.
- **Проверка допущения:** сама механика и запуск подтверждаются официальным пресс-релизом Coca-Cola. Метрика про 69% redemption из старого файла требует осторожности: публично хорошо подтверждён факт, что результаты значительно превысили бенчмарки, но конкретное число лучше не считать полностью верифицированным без первичного источника от Savi.
- **Оценка релевантности:** высокая по retail flow, средняя по chat flow.

## 4.4. Gupshup WhatsApp Campaigns

- **Регионы:** Индия, ОАЭ, MENA
- **Тип:** conversational commerce / lead generation
- **Ссылки:** [Wow! Momo](https://www.gupshup.ai/resources/case-studies/wowmomo/), [Sharaf DG](https://www.gupshup.ai/resources/case-studies/sharaf-dg-achieves-4x-return-on-ad-spends-with-gupshup-conversation-cloud/), [Nivea](https://www.gupshup.ai/resources/case-studies/nivea-attracts-new-customers-with-personalized-skincare-consultation/)
- **Промо-механика:** пользователь переходил из click-to-WhatsApp ads или ссылки в чат, получал guided dialogue, offer, recommendation или coupon-like incentive, после чего совершал заказ или оставлял лид.
- **Как это работало по шагам:**
  Пользователь:
  кликал по рекламе или ссылке, открывал WhatsApp-чат, отвечал на короткие вопросы, получал релевантный оффер, товарную рекомендацию, консультацию или купоноподобный стимул, после чего оформлял заказ или оставлял контакт.
  Бренд / платформа:
  Gupshup автоматизировал сценарий диалога, qualification, segmentation и retargeting.
  Бренд использовал чат как постоянный канал, в котором можно и привести пользователя в воронку, и дожать его до покупки.
  В некоторых кейсах чат был и entry point, и каналом повторного касания.
- **Стек / delivery model:** WhatsApp Business API, CRM / commerce integrations.
- **Что похоже:** чат как основной интерфейс, низкое трение, сохранённый канал коммуникации, ретаргетинг внутри того же треда.
- **Что отличается:** это чаще commerce или lead-gen, а не sampling в чистом виде; обычно нет разделения на ваучер и код погашения.
- **Результат:** хороший аналог по каналу, но не идеальный аналог по промо-механике.
- **Почему сработало:** мессенджер убирает лишние шаги и не заставляет ставить приложение.
- **Подтверждённые данные:** в публичных кейсах встречаются показатели вроде 55% direct orders, 4x ROAS и 86% completion, но они относятся к разным кейсам и не должны читаться как единый универсальный benchmark.
- **Оценка релевантности:** высокая по UX-каналу, средняя по sampling.

## 4.5. PedidosYa + Talon.One

- **Регион:** Латинская Америка
- **Тип:** delivery promo infrastructure
- **Ссылки:** [кейс PedidosYa + Talon.One](https://www.talon.one/customers/pedidosya-deliver-targeted-campaigns-with-talon-one)
- **Промо-механика:** пользователь получал динамический промо-оффер внутри delivery journey, а система в реальном времени решала, кому и какой offer показывать и как его погашать.
- **Как это работало по шагам:**
  Пользователь:
  заходил в delivery-сервис, собирал заказ и в процессе видел релевантный промо-оффер или benefit, который применялся при выполнении нужных условий.
  Пользователь не обязательно взаимодействовал с "кампанией" как отдельным опытом: promo logic была встроена прямо в order flow.
  Бренд / платформа:
  Talon.One управлял правилами eligibility, сегментацией, ограничениями, антифродом и логикой применения промо.
  PedidosYa использовал это как движок акций внутри своего delivery journey, а не как самостоятельную рекламную механику.
- **Стек / delivery model:** promotion engine, customer data integrations, delivery commerce.
- **Что похоже:** ветка delivery, real-time promo logic, антифрод, быстрые изменения правил.
- **Что отличается:** это инфраструктура скидок и промо, а не sampling как бесплатная выдача напитка.
- **Результат:** хороший инфраструктурный аналог для delivery-ветки.
- **Почему сработало:** новая система дала больше контроля над правилами, сегментацией и защитой от злоупотреблений.
- **Оценка релевантности:** средняя.

## 4.6. Magnit Telegram Promo Bot

- **Регион:** Россия
- **Тип:** Telegram retail promo
- **Ссылки:** [кейс Magnit Telegram promo bot](https://msocialproduction.com/cases/telegram-bot-dlya-seti-magnit-s-promo-mehanikoi)
- **Промо-механика:** пользователь входил в Telegram-бот, загружал чек или выполнял промо-действия, после чего участвовал в reward-механике.
- **Как это работало по шагам:**
  Пользователь:
  переходил в Telegram-бот, регистрировался в акции, совершал нужное действие в офлайне, например покупку, затем отправлял чек или данные через бот и получал участие в reward-механике.
  Дальше бот использовался как личный кабинет акции: хранение статуса, уведомления, проверка участия.
  Бренд / платформа:
  бренд выносил промо-механику в Telegram вместо отдельного сайта или приложения, а backend обрабатывал валидацию чеков, статусы участников и призовой сценарий.
  Для ритейлера это была digital-обвязка вокруг уже существующего покупательского действия.
- **Стек / delivery model:** Telegram bot + admin / web backend.
- **Что похоже:** Telegram как интерфейс, retail promo logic, anti-fraud concerns, отсутствие app install.
- **Что отличается:** prize / receipt promo вместо instant free sample redemption.
- **Результат:** скорее proof of feasibility, чем прямой коммерческий аналог.
- **Почему сработало:** Telegram оказался достаточным интерфейсом для массовой retail-активации.
- **Видимый стек:** PHP + Backpack v5, React + Next.
- **Оценка релевантности:** средняя.

## 4.7. Pep Genie / PepsiCo India

- **Регион:** Индия
- **Тип:** WhatsApp loyalty / under-cap promo
- **Ссылки:** [Pep Genie terms / promo page](https://www.pepgenie.com/gatorade-tc.html), [обзор механики](https://almonds.ai/pepsico-pep-genie/)
- **Промо-механика:** пользователь покупал бутылку, сканировал QR или вводил уникальный код, попадал в WhatsApp-флоу и получал points или reward.
- **Как это работало по шагам:**
  Пользователь:
  сначала покупал напиток, затем сканировал QR-код или использовал уникальный код с упаковки, открывал WhatsApp-сценарий, подтверждал участие и получал reward, points или право на дальнейшее участие.
  Бренд / платформа:
  PepsiCo превращала упаковку в entry point, а WhatsApp использовала как удобную оболочку для loyalty-механики.
  Важный момент: reward шёл после покупки, поэтому это ближе к loyalty/promo, чем к sampling.
- **Стек / delivery model:** WhatsApp-based loyalty flow.
- **Что похоже:** QR-to-chat переход, быстрый бот-флоу, mass-market beverage promo.
- **Что отличается:** это purchase-based loyalty, а не sampling; reward выдаётся после покупки.
- **Результат:** полезный косвенный аналог.
- **Почему сработало:** упаковка сама становилась входом в digital journey.
- **Проверка допущения:** сама механика подтверждается публично, но использовать этот кейс как прямой benchmark для бесплатного сэмплинга не стоит.
- **Оценка релевантности:** средняя-низкая.

## 4.8. Pepsi Mania / Узбекистан

- **Регион:** Узбекистан
- **Тип:** under-cap / prize promo c Telegram- или digital-компонентом
- **Ссылки:** [поиск по проекту Pepsi Mania](https://www.google.com/search?q=Pepsi+Mania+Uzbekistan+Telegram), [поиск по Pepsi Uzbekistan promo](https://www.google.com/search?q=site%3Apepsi.uz+Pepsi+Mania)
- **Промо-механика:** пользователь покупал напиток, находил код под крышкой или на упаковке и участвовал в розыгрыше или reward-механике через digital-канал.
- **Как это работало по шагам:**
  Пользователь:
  покупал напиток Pepsi, находил код под крышкой или на упаковке, затем вводил его в цифровом канале акции и получал шанс на приз, бонус или другое поощрение.
  Если использовался Telegram или похожий digital-канал, он служил интерфейсом для ввода кода, проверки статуса и коммуникации с участником.
  Бренд / платформа:
  бренд стимулировал повторные покупки за счёт prize-механики, а digital-слой нужен был для регистрации кодов, учёта и коммуникации.
  По сути это классическая FMCG under-cap promo, а не бесплатная раздача продукта.
- **Что похоже:** beverage promo в регионе СНГ, digital distribution, возможное использование Telegram как массового канала.
- **Что отличается:** это не sampling; механика строится вокруг покупки и приза, а не бесплатной выдачи продукта.
- **Результат:** полезный региональный сигнал, но слабый прямой аналог.
- **Проверка допущения:** наличие промо и digital-канала подтверждается, но сильные цифры из старого файла вроде 700,000+ unique users в рамках этого отчёта лучше считать неполностью подтверждёнными.
- **Оценка релевантности:** низкая-средняя.

## 4.9. Absolut Unique Access / Sven

- **Регион:** Аргентина
- **Тип:** WhatsApp promo experience
- **Ссылки:** [Adsoftheworld case](https://www.adsoftheworld.com/campaigns/absolut-unique-access), [LatinSpots coverage](https://www.latinspots.com/noticia/absolut-estrena-la-primera-campaa-por-whatsapp/30116)
- **Промо-механика:** чтобы попасть на эксклюзивную вечеринку, пользователь должен был через WhatsApp убедить виртуального "дверного" Sven дать ему проход.
- **Как это работало по шагам:**
  Пользователь:
  писал в WhatsApp персонажу Sven, общался с ним, пытался убедить его дать доступ на закрытую вечеринку и по сути проходил игровую conversational-механику.
  Участие строилось не на купоне, а на диалоге и креативной вовлечённости.
  Бренд / платформа:
  Absolut использовал WhatsApp не как support-канал, а как саму сцену кампании.
  Бренд создал персонажа, через которого управлял фильтром доступа и превращал обычный messaging channel в брендовый interactive experience.
- **Стек / delivery model:** WhatsApp campaign с ручным / semi-manual community interaction.
- **Что похоже:** мессенджер как ядро промо-механики, высокая вовлечённость через диалог.
- **Что отличается:** это experiential / gamified promo, а не coupon redemption или sampling.
- **Результат:** сильный референс по вовлечению, слабый по retail redemption.
- **Почему сработало:** механика была игровой, персонализированной и нативной для мессенджера.
- **Проверка допущения:** механика и базовые engagement-результаты хорошо описаны в нескольких публикациях, но это не тот тип кейса, на который стоит опираться при расчёте redemption KPI.
- **Оценка релевантности:** средняя по messenger engagement, низкая по sampling.

---

## 5. Что в этих кейсах наиболее похоже на ваш проект

### Самые близкие аналоги

1. **Sampl / Bio&Me**
2. **Social Nature / Primal Kitchen**
3. **#TakeATaste Now**

Они лучше всего подтверждают:

- цифровой trial
- быстрый переход от digital-контакта к офлайн-получению продукта
- работу retail-linked redemption
- измеримость campaign-to-store funnel

### Лучшие аналоги по каналу

1. **Gupshup WhatsApp cases**
2. **Magnit Telegram Promo Bot**
3. **Absolut Sven**

Они лучше подтверждают:

- что мессенджер снижает friction
- что пользователь готов проходить промо-механику внутри чата
- что чат можно использовать как persistent offer container

### Лучший аналог по delivery-инфраструктуре

1. **PedidosYa + Talon.One**

Он подтверждает:

- ценность real-time rules
- чувствительность delivery promo к fraud
- важность гибкой offer orchestration

---

## 6. Что отличает ваш проект от большинства аналогов

- В большинстве кейсов есть либо **sampling**, либо **chat-based UX**, но не оба одновременно.
- В большинстве кейсов нет комбинации **retail + delivery + promo-point** в одной системе.
- В большинстве кейсов нет разделения между **ваучером** и **кодом погашения**.
- У вас сильнее выражена операционная логика под реальный ритейл, где POS-данные запаздывают.

Это делает проект не "копией" существующего решения, а комбинацией нескольких уже доказанных паттернов.

---

## 7. Перепроверенные выводы по успеху и неуспеху

### Что ведёт к успеху

- вход без установки отдельного приложения
- короткий путь от контакта до выдачи оффера
- наличие ближайшей точки погашения
- защита от повторного использования
- возможность вернуть пользователя в тот же канал через напоминание
- пост-кампейн слой: отзывы, CRM, repeat purchase

### Что чаще всего ломает такие механики

- зависимость от ритейл-партнёра и его операционных процессов
- проблемы сканирования на кассе
- статичные QR или reusable codes
- отсутствие fallback, если партнёрские коды или сверка тормозят
- слишком длинный bot flow

---

## 8. Итоговая оценка проекта

Проект выглядит **жизнеспособным**.

Наиболее сильное подтверждение его логики дают не Telegram-кейсы сами по себе, а связка из трёх типов аналогов:

- digital sampling platforms
- chat-based promotional flows
- promo infrastructure for delivery / retail redemption

Главный вывод после перепроверки допущений:

- **логика продукта подтверждается хорошо**
- **логика канала подтверждается хорошо**
- **точные benchmark-метрики по отдельным историческим кейсам надо использовать осторожно**

Если формулировать прагматично, то проект опирается на реальные рабочие паттерны. Основной риск находится не в UX бота, а в операционной дисциплине партнёров и механике погашения.

---

## 9. Практические рекомендации

1. Для пилота сохранить Telegram-бот как основной интерфейс.
2. Оставить двухшаговую схему `ваучер -> активация`, потому что это один из самых сильных элементов архитектуры.
3. Обязательно предусмотреть ручной fallback-код под QR.
4. На раннем этапе согласовать формат code pools и сверки с партнёрами.
5. На следующий этап рассмотреть backup-механику через receipt validation или cashback, если партнёрская операционная схема окажется слишком хрупкой.

---

## 10. Источники

- Sampl: https://www.sampltech.com/
- Sampl Bio&Me case: https://www.sampltech.com/case-studies/biome-18-coupon-redemption
- SamplPay cashback: https://www.sampltech.com/blog/introducing-samplpay-cashback
- Social Nature established brands: https://business.socialnature.com/established-brands/
- Social Nature Primal Kitchen case: https://business.socialnature.com/case-studies/primal-kitchen/
- Social Nature cashback help: https://socialnaturehelp.zendesk.com/hc/en-us/articles/10769046494619-How-does-cash-back-sampling-work
- Coca-Cola #TakeATaste Now official release: https://www.coca-cola.com/gb/en/media-center/coca-cola-zero-sugar-takeatastenow-campaign
- DOOH.com #TakeATaste: https://www.dooh.com/works/takeataste/
- Campaign Media Awards entry for #TakeATaste: https://www.campaignmediaawards.com/finalists/game-changing-real-time-and-ar-ooh-delivered-for-coca-cola-s54v989flurz3ab
- Gupshup Wow! Momo: https://www.gupshup.ai/resources/case-studies/wowmomo/
- Gupshup Sharaf DG: https://www.gupshup.ai/resources/case-studies/sharaf-dg-achieves-4x-return-on-ad-spends-with-gupshup-conversation-cloud/
- Gupshup Nivea: https://www.gupshup.ai/resources/case-studies/nivea-attracts-new-customers-with-personalized-skincare-consultation/
- Talon.One PedidosYa: https://www.talon.one/customers/pedidosya-deliver-targeted-campaigns-with-talon-one
- Magnit Telegram promo bot case: https://msocialproduction.com/cases/telegram-bot-dlya-seti-magnit-s-promo-mehanikoi
- PepsiCo India / Pep Genie terms: https://www.pepgenie.com/gatorade-tc.html
- Pep Genie overview: https://almonds.ai/pepsico-pep-genie/
- Absolut Unique Access: https://www.adsoftheworld.com/campaigns/absolut-unique-access
- Absolut WhatsApp coverage: https://www.latinspots.com/noticia/absolut-estrena-la-primera-campaa-por-whatsapp/30116
