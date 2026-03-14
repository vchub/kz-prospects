# Анализ проекта Sampl

## Область анализа

Этот документ рассматривает **Sampl** как самостоятельный референсный проект и summarises:

- какую проблему решает Sampl
- как устроен продукт
- как выглядит механика для потребителя и для бренда
- какие успехи публично заявлены
- какие ограничения и вероятные слабые места видны снаружи
- какие интеграции можно увидеть публично
- какой технологический стек можно предположить

Источники:

- продуктовые страницы Sampl
- страницы интеграций
- help-материалы
- кейсы и award-посты

Важная оговорка:

- **метрики успеха** в основном взяты из материалов самого Sampl
- **неудачи** почти не публикуются напрямую, поэтому ограничения и слабые места выводятся из эволюции продукта и из тех проблем, которые Sampl сам формулирует

---

## 1. Что такое Sampl

Sampl позиционирует себя как **платформу измеримого product sampling для FMCG-брендов**.

Её основной тезис:

- бренды раздают образцы
- но не понимают, что произошло после trial
- часто не могут связать sampling с review, CRM-ростом или покупкой

Публичное позиционирование Sampl:

- “reach the right consumers”
- “capture reviews, opt-ins, and purchase signals”
- “prove what sampling delivered”

Источники:

- [Главная страница Sampl](https://www.sampltech.com/)
- [Sampl wins Best Lead Gen Software 2025](https://www.sampltech.com/blog/sampl-named-best-lead-gen-software-uk-business-tech-awards-2025)

---

## 2. Какую проблему Sampl формулирует напрямую

Sampl прямо описывает рыночную проблему как:

- отсутствие data capture
- отсутствие follow-up после trial
- отсутствие измеримого пути от sample к purchase

Это видно в формулировках на сайте:

- бренды отправляют миллионы сэмплов и не знают, что произошло после использования
- не понимают, понравился ли продукт
- не понимают, купил ли пользователь его потом

Sampl заявляет, что решает это через:

- reviews
- opt-ins
- purchase signals

Источник:

- [Главная страница Sampl](https://www.sampltech.com/)

В award-постах эта же логика подаётся уже не только как sampling, но и как **lead generation / customer acquisition**.

Источник:

- [Best Lead Gen Software 2025](https://www.sampltech.com/blog/sampl-named-best-lead-gen-software-uk-business-tech-awards-2025)

---

## 3. Какие продуктовые модули видны публично

По публичным материалам можно выделить несколько именованных частей продукта:

- **SamplSend**: доставка образца домой
- **SamplPay**: cashback / механика с подтверждённой покупкой по чеку
- **SamplMatch**: квалификация, валидация, фильтрация дублей, снижение fraud
- **Sampl Analytics**: отчётность и измерение кампаний
- **SamplStudio**: среда настройки и управления кампаниями
- **NearStore**: логика привязки к ближайшему магазину и in-store conversion

Источники:

- [Главная страница Sampl](https://www.sampltech.com/)
- [NearStore](https://www.sampltech.com/blog/how-nearstore-links-digital-sampling-with-in-store-sales)
- [SamplPay product page](https://www.sampltech.com/products/samplpay)
- [SamplPay launch post](https://www.sampltech.com/blog/introducing-samplpay-cashback)

---

## 4. Как Sampl работает в целом

Публично Sampl описывает брендовый flow в три шага:

1. бренд задаёт аудиторию и цели кампании
2. Sampl берёт на себя targeting, fulfilment и delivery
3. бренд видит, что произошло после trial

Источник:

- [Главная страница Sampl](https://www.sampltech.com/)

Если раскрыть это более подробно, получается следующий operating model.

### Логика со стороны бренда

1. Бренд определяет:
- целевую аудиторию
- объём сэмплов
- цель кампании
- тип механики: in-home sampling или cashback / purchase-led trial

2. Sampl строит digital journey:
- media entry
- qualification
- обработку заявок
- approval logic
- sample fulfillment или cashback-flow

3. Sampl валидирует участников:
- пытается отсечь дубли
- фильтрует “freebie hunters”
- проверяет eligibility

4. Происходит сам trial:
- sample доставляется домой, или
- пользователь покупает товар в ритейле и загружает чек для cashback

5. Sampl собирает post-trial действия:
- reviews
- feedback
- marketing opt-ins
- purchase signals

6. Бренд получает структурированную отчётность:
- CRM-ready профили
- данные по эффективности кампании
- отзывы
- сигналы о покупке или подтверждённые purchase claims

### Логика со стороны потребителя

В типовом in-home flow:

1. пользователь видит рекламу или publisher placement
2. переходит на Sampl campaign page
3. заполняет короткую заявку
4. Sampl проверяет eligibility
5. одобренный пользователь получает sample домой
6. после использования его приглашают оставить review, opt-in или совершить follow-up action
7. в части кампаний пользователя дополнительно ведут к nearby store или покупке

В cashback / SamplPay flow:

1. пользователь видит offer
2. проходит короткий eligibility flow
3. покупает продукт в магазине или онлайн
4. загружает чек или invoice
5. Sampl валидирует claim
6. пользователю выплачивается cashback
7. бренд получает данные с подтверждённой покупкой

Источники:

- [Главная страница Sampl](https://www.sampltech.com/)
- [SamplPay launch post](https://www.sampltech.com/blog/introducing-samplpay-cashback)
- [SamplPay help page](https://help.sampltech.com/sampl-pay)

---

## 5. Основные механики для потребителя

У Sampl как минимум три видимые consumer-механики.

## 5.1. Запрос образца с доставкой домой

Пользователь:

- видит таргетированную рекламу
- запрашивает sample
- получает approval или rejection
- получает образец домой
- позже получает приглашение оставить review или купить продукт

Это лучше всего подходит для:

- товаров, которые можно отправлять физически
- категорий, где home trial удобен
- кампаний, ориентированных на reviews, awareness, CRM или product education

Примеры:

- [Andrex](https://www.sampltech.com/case-studies/heres-how-we-helped-andrex-r-capture-genuine-reviews)
- [Cadbury](https://www.sampltech.com/case-studies/how-cadbury-harnessed-product-sampling)
- [CocoaVia](https://www.sampltech.com/case-studies/cocoavia-crm-sampling-campaign)

## 5.2. NearStore conversion

Пользователь:

- получает digital sample experience или in-home sample
- затем видит ближайший магазин, где можно купить полный продукт
- может также получить store guidance или coupon

Это лучше всего подходит для:

- product launch
- товаров с ограниченной дистрибуцией
- retail sell-in и поддержки store-level sales

Примеры:

- [NearStore](https://www.sampltech.com/blog/how-nearstore-links-digital-sampling-with-in-store-sales)
- [Bio&Me](https://www.sampltech.com/case-studies/biome-18-coupon-redemption)
- [Manilife](https://www.sampltech.com/case-studies/how-we-helped-manilife-with-their-healthy-eating-campaign)

## 5.3. SamplPay cashback trial

Пользователь:

- видит cashback-offer
- покупает продукт за свои деньги
- загружает подтверждение покупки
- получает reimbursement после проверки

Это лучше всего подходит для:

- hard-to-ship products
- chilled, fragile, heavy, alcohol или regulated products
- случаев, когда retailer approval слишком медленный
- кампаний, где нужна purchase proof, а не просто факт отправки sample

Источники:

- [SamplPay product page](https://www.sampltech.com/products/samplpay)
- [SamplPay launch post](https://www.sampltech.com/blog/introducing-samplpay-cashback)

---

## 6. Основные механики для бренда

Sampl — это не просто consumer-facing flow, а операционная система для brand teams.

### Что бренд может контролировать

Публично Sampl пишет, что бренд может управлять:

- кому доступен оффер
- как устроена reward / sample mechanics
- где запускается кампания
- какие данные собираются
- какие permissions запрашиваются

Источник:

- [SamplPay product page](https://www.sampltech.com/products/samplpay)

### Что бренд получает на выходе

По сайту Sampl повторяются следующие output types:

- reviews
- feedback
- marketing opt-ins
- CRM-ready profiles
- media performance data
- purchase signals
- verified claims в purchase-led механиках

Источники:

- [Главная страница Sampl](https://www.sampltech.com/)
- [Integrations page](https://www.sampltech.com/integrations)

### Зачем это покупает бренд

Sampl продаёт ценность сразу нескольким внутренним заказчикам:

- **media teams**: нужна измеримость и оптимизация
- **CRM teams**: нужны opt-ins и first-party data
- **brand / launch teams**: нужен trial у нужной аудитории
- **trade / sales teams**: нужен сигнал, что sampling сдвинул retail sales

Источник:

- [Главная страница Sampl](https://www.sampltech.com/)

---

## 7. Публично заявленные успехи

## 7.1. Платформенные метрики

Sampl заявляет, что в 2024 году:

- провёл **1.7 million samples**
- в **35 countries**
- сгенерировал **278,000 reviews**
- сгенерировал **1.7 million marketing opt-ins**
- дал **3x–4x average conversion uplifts** у крупных retail partners

Источник:

- [Best Lead Generation Campaign 2025](https://www.sampltech.com/blog/sampl-best-lead-generation-campaign-global-performance-marketing-awards-2025)

## 7.2. Кейсы

### Bio&Me

- **18% coupon redemption**
- sampling дал **20% of Tesco sales during the period**

Источник:

- [Bio&Me case](https://www.sampltech.com/case-studies/biome-18-coupon-redemption)

### Manilife

- **92% enjoyed their sample**
- **40% uplift in rate of sale**
- **20% purchased within 2 weeks**

Источник:

- [Manilife case](https://www.sampltech.com/case-studies/how-we-helped-manilife-with-their-healthy-eating-campaign)

### Andrex

- **1,664 reviews**
- **93% satisfaction**
- over **35,000 requests** in under 24 hours
- **20,000 requests filtered out**

Источник:

- [Andrex case](https://www.sampltech.com/case-studies/heres-how-we-helped-andrex-r-capture-genuine-reviews)

### CocoaVia

- **11,909 high-intent leads**
- **$0.84 CPL**
- **1,106 reviews**
- **4.52 average rating**

Источник:

- [CocoaVia case](https://www.sampltech.com/case-studies/cocoavia-crm-sampling-campaign)

### Cadbury Nuttier

- **7,000+ reviews**
- **19,000 marketing opt-ins**
- **86% purchase intent**

Источник:

- [Cadbury case](https://www.sampltech.com/case-studies/how-cadbury-harnessed-product-sampling)

### Royal Canin

- **65% CRM opt-in rate**
- **88% purchase intent**
- **22% review response rate**
- **€2.09 CPL**
- **40% faster campaign delivery**

Источник:

- [Best Lead Generation Campaign 2025](https://www.sampltech.com/blog/sampl-best-lead-generation-campaign-global-performance-marketing-awards-2025)

### NIVEA

- **150,000+ marketing opt-ins**
- **8% purchase rate**

Источник:

- [SamplPay product page](https://www.sampltech.com/products/samplpay)

---

## 8. Неудачи, ограничения и слабые места

Sampl не публикует “failed case studies” в явном виде.

Поэтому полезнее разбирать ограничения так:

- смотреть, какие проблемы продукту пришлось решать по мере развития
- выводить слабые места из новых модулей и формулировок
- разделять прямые факты и аналитические выводы

## 8.1. Исходная слабость традиционного sampling

Это главная “неудача старого подхода”, вокруг которой строится Sampl:

- samples раздаются
- структурированные данные не возвращаются
- бренд не понимает связь с review и purchase

Источник:

- [Главная страница Sampl](https://www.sampltech.com/)

## 8.2. Низкокачественный спрос и “freebie hunters”

Sampl много говорит про filtering и validation.

Это сильный сигнал, что типовая проблема sampling такова:

- приходит слишком много low-intent users
- есть дубли и слабые заявки
- бюджет на fulfillment тратится впустую

Факты:

- в кейсе Andrex из **35,000+ requests** было отфильтровано **20,000**
- SamplMatch постоянно описывается как validation layer

Источники:

- [Andrex case](https://www.sampltech.com/case-studies/heres-how-we-helped-andrex-r-capture-genuine-reviews)
- [Best Lead Gen Software 2025](https://www.sampltech.com/blog/sampl-named-best-lead-gen-software-uk-business-tech-awards-2025)

## 8.3. Доставка sample домой подходит не всем категориям

Появление **SamplPay** само по себе показывает ограничение чистого in-home sampling.

Sampl прямо пишет, что cashback особенно нужен для категорий:

- chilled
- heavy
- fragile
- alcohol
- regulated

Источник:

- [SamplPay launch post](https://www.sampltech.com/blog/introducing-samplpay-cashback)

Это один из самых важных structural signals про слабость pure shipping model.

## 8.4. Retailer approval и интеграции тормозят механику

SamplPay отдельно продаётся как решение, которое работает:

- без retailer approval
- без сложных интеграций

Из этого следует типовая слабость рынка:

- бренд хочет purchase proof
- но retailer programs и integrations слишком медленные или сложные

Источники:

- [SamplPay product page](https://www.sampltech.com/products/samplpay)
- [SamplPay launch post](https://www.sampltech.com/blog/introducing-samplpay-cashback)

## 8.5. Purchase proof различается по силе в зависимости от механики

Sampl часто использует формулировку **purchase signals**, а не всегда “hard sales proof”.

Это важный нюанс.

Это значит, что:

- в части кампаний покупка выводится через косвенные сигналы, redemption, store-level indicators или follow-up
- только некоторые механики, например receipt-verified cashback, дают очень сильное подтверждение покупки

Источник:

- [Главная страница Sampl](https://www.sampltech.com/)

### Итог по ограничениям

Публично не видно крупных “провалов”, но хорошо видно, что Sampl пришлось эволюционировать дальше simple in-home sampling, чтобы решить три реальные проблемы:

1. низкокачественный спрос
2. hard-to-ship categories
3. слабое доказательство retail purchase без retailer integration

---

## 9. Другие важные детали продукта

## 9.1. Экосистема интеграций

Sampl публично показывает интеграции с:

- **CRM / email**: HubSpot, Salesforce, Mailchimp, Klaviyo, Braze, ActiveCampaign, Bloomreach, Ometria
- **reviews / UGC**: Bazaarvoice, PowerReviews, Reviews.io, Yotpo
- **media**: Meta, Google, TikTok, Pinterest, Hearst
- **automation / APIs**: Zapier, API integration
- **retail / publisher partners**: Superdrug, The Hut Group и др.

Источник:

- [Integrations page](https://www.sampltech.com/integrations)

Это важно, потому что показывает: Sampl — это не просто лендинг под раздачу sample, а платформа, встроенная в CRM, reviews и media stack бренда.

## 9.2. Use cases кампаний

Публично видны такие сценарии:

- product launch
- CRM growth
- review generation
- media performance measurement
- company-wide reporting

Источник:

- [Главная страница Sampl](https://www.sampltech.com/)

## 9.3. Consumer support и claims operations

Help page по SamplPay показывает реальные operational details:

- один image per receipt
- один claim на человека на offer
- чек должен содержать retailer, item, date/time
- cashback выплачивается через PayPal или Venmo
- есть логика reject / recheck claim

Источник:

- [SamplPay help page](https://help.sampltech.com/sampl-pay)

Это подтверждает, что у Sampl есть настоящий claims-processing workflow, а не просто маркетинговая надстройка.

---

## 10. Возможный tech stack

Точный application stack публично **не раскрыт**.

Поэтому корректный формат здесь — **осторожное предположение**, а не утверждение.

## 10.1. Что можно предположить с умеренной уверенностью

У Sampl, вероятно, есть:

- web marketing site
- отдельная authenticated app environment
- campaign-management tooling
- analytics / reporting layer
- integrations middleware
- receipt / claim validation workflows
- CRM и review sync

Основания:

- упоминается `app.sampltech.com`
- есть named modules: SamplStudio, Sampl Analytics, SamplSend, SamplPay
- большое количество интеграций почти наверняка означает API-led архитектуру

Источники:

- [Главная страница Sampl](https://www.sampltech.com/)
- [Integrations page](https://www.sampltech.com/integrations)

## 10.2. Какие архитектурные компоненты вероятны

Это inference, а не подтверждённый факт.

Вероятные компоненты:

- **web frontend** для consumer campaign pages и forms
- **brand dashboard / admin app** для setup, reporting и operations
- **rules / qualification engine** для SamplMatch
- **fulfillment orchestration** для sample shipping workflows
- **receipt validation service** для SamplPay
- **review syndication connectors** для Bazaarvoice / Yotpo / PowerReviews
- **CRM connectors** для HubSpot / Salesforce / Braze / Klaviyo
- **media attribution / reporting layer**
- **payments / payout integration** для cashback

## 10.3. Что можно и чего нельзя утверждать

Без более сильных источников безопасно утверждать только следующее:

- Sampl ведёт себя как multi-tenant SaaS workflow platform для campaign operations
- у него почти наверняка есть API, background jobs, dashboard-отчётность и интеграционный слой

Небезопасно утверждать без доказательств:

- точный язык программирования
- точный frontend framework
- точный cloud provider
- точный database choice

---

## 11. Что особенно важно, если рассматривать Sampl как benchmark для нового проекта

Если использовать Sampl как benchmark, то самые важные уроки такие.

### Что они сделали правильно

- сосредоточились на реальной слабости sampling: отсутствие измеримого downstream behavior
- сразу встроили qualification в механику
- связали sampling не только с awareness, но и с CRM и reviews
- не остановились на одной модели, а добавили несколько механик: in-home, NearStore, cashback
- упаковали продукт под несколько внутренних заказчиков бренда, а не только под brand team

### Что им пришлось добавить по мере развития

- receipt-verified purchase mechanics
- более сильный anti-fraud / qualification layer
- store-nearby logic для улучшения retail conversion

### Что это означает стратегически

Sampl, похоже, эволюционировал из модели “отправим samples и соберём reviews” в более широкую платформу для:

- audience qualification
- trial fulfillment
- review generation
- CRM growth
- retail conversion proof

Сама эта эволюция — уже важный стратегический урок.

---

## 12. Общая оценка

Sampl — один из самых сильных примеров productized и measurable sampling.

Его главное достижение не в том, что он просто отправляет samples.
Главное в том, что он превращает sampling в воронку:

`target -> qualify -> trial -> review / opt-in -> purchase signal`

Его наиболее сильные стороны:

- измеримость
- сильная интеграционная история
- работа с low-intent demand
- несколько механик под разные категории

Его наиболее заметные ограничения:

- идеальное purchase attribution доступно не во всех механиках
- shipping-based sampling ограничен типом продукта
- receipt-based flows дают более сильное доказательство покупки, но добавляют friction

Если брать Sampl как benchmark для нового проекта, то он особенно полезен как пример:

- qualification
- post-trial measurement
- modular mechanics
- thinking around CRM / review / retail integration

---

## Источники

- Sampl platform: https://www.sampltech.com/
- Sampl integrations: https://www.sampltech.com/integrations
- Sampl case studies: https://www.sampltech.com/case-studies
- NearStore blog: https://www.sampltech.com/blog/how-nearstore-links-digital-sampling-with-in-store-sales
- SamplPay product page: https://www.sampltech.com/products/samplpay
- SamplPay launch post: https://www.sampltech.com/blog/introducing-samplpay-cashback
- SamplPay help page: https://help.sampltech.com/sampl-pay
- Best Lead Gen Software 2025: https://www.sampltech.com/blog/sampl-named-best-lead-gen-software-uk-business-tech-awards-2025
- Best Lead Generation Campaign 2025: https://www.sampltech.com/blog/sampl-best-lead-generation-campaign-global-performance-marketing-awards-2025
- Andrex case: https://www.sampltech.com/case-studies/heres-how-we-helped-andrex-r-capture-genuine-reviews
- Manilife case: https://www.sampltech.com/case-studies/how-we-helped-manilife-with-their-healthy-eating-campaign
- CocoaVia case: https://www.sampltech.com/case-studies/cocoavia-crm-sampling-campaign
- Cadbury case: https://www.sampltech.com/case-studies/how-cadbury-harnessed-product-sampling
- Bio&Me case: https://www.sampltech.com/case-studies/biome-18-coupon-redemption
