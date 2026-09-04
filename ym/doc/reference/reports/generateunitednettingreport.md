---
title: Отчет по платежам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md"
fetched_at: "2026-09-04T01:59:12Z"
content_sha: 68350c0083c6ee64
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateUnitedNettingReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateUnitedNettingReport.md
  - href: ru/reference/reports/generateUnitedNettingReport.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateUnitedNettingReport.md -->
<div class="openapi">

# Отчет по платежам

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateUnitedNettingReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateUnitedNettingReport.md -->
  
  Запускает генерацию отчета по платежам за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/accounting/transactions#all-pay)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  Тип отчета зависит от того, какие поля заполнены в запросе:
  
  #|
  || **Тип отчета** | **Какие поля нужны** | **Комментарий** ||
  || О платежах за период | `dateFrom` и `dateTo` |
    В отчет попадают все платежи, которые были выплачены и начислены в выбранный период.
  
    Пример: если перевод выполнен 31 августа и зачислен 1 сентября, он попадет в отчет за оба месяца.
  ||
  || О платежном поручении | `bankOrderId` и `bankOrderDateTime` |—||
  || [О баллах Маркета](*баллы_маркета) | `monthOfYear` |—||
  |#
  
  Заказать отчеты нескольких типов одним запросом нельзя.
  
  <!-- source: ru/_auto/reports/united/netting/generator/united_netting.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Отчёт о платежах** (файл **transaction_date**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
  || TRANSACTION_ID | transactionId | Информация о платежах/ID транзакции | string ||
  || ORDER_ID | orderId | Информация о платежах/Номер заказа или отгрузки | integer ||
  || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
  || ORDER_CREATION_DATE | orderCreationDate | Информация о платежах/Дата создания заказа | string ||
  || ORDER_DELIVERY_DATE | orderDeliveryDate | Информация о платежах/Дата доставки заказа | string ||
  || CLAIM_NUMBER | claimNumber | Информация о платежах/Номер и дата претензии | string ||
  || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
  || SHOP_SKU | shopSku | Информация о платежах/Ваш SKU | string ||
  || ACT_ID | actId | Информация о платежах/Номер акта об оказанных услугах | integer ||
  || ACT_DATE | actDate | Информация о платежах/Дата акта об оказанных услугах | string ||
  ||
  OFFER_OR_SERVICE_NAME
  |
  offerOrServiceName
  |
  Информация о платежах/Название товара (к начислению) или услуги (к удержанию)

  |
  string
  ||
  || COUNT | count | Информация о платежах/Количество | integer ||
  || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
  || VAT_RATE | vatRate | Информация о платежах/Ставка НДС | string ||
  || VAT_SUM | vatSum | Информация о платежах/Сумма НДС | number ||
  || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
  || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
  || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
  ||
  BONUS_ACCOUNT_YEAR_MONTH
  |
  bonusAccountYearMonth
  |
  Информация о платежах/Расчётный период премии за участие в совместных акциях
  |
  string
  ||
  || BANK_ORDER_DATE | bankOrderDate | Информация о платежах/Дата платежного поручения | string ||
  || BANK_ORDER_ID | bankOrderId | Информация о платежах/Номер платежного поручения | integer ||
  ||
  BANK_SUM
  |
  bankSum
  |
  Информация о платежах/Сумма платежного поручения или удерживаемая за услуги сумма
  |
  number
  ||
  || COMMENTS | comments | Информация о платежах/Комментарии | string ||
  |#

  {% endcut %}

  {% cut "Лист **Отчёт о платежном поручении** (файл **netting_report_accruals**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о начислениях/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE | orderCreationDate | Информация о начислениях/Дата создания заказа | string ||
  || ORDER_DELIVERY_DATE | orderDeliveryDate | Информация о начислениях/Дата доставки заказа | string ||
  || CLAIM_NUMBER | claimNumber | Информация о начислениях/Номер и дата претензии | string ||
  || ORDER_TYPE | orderType | Информация о начислениях/Тип заказа | string ||
  || SHOP_SKU | shopSku | Информация о начислениях/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о начислениях/Название товара | string ||
  || COUNT | count | Информация о начислениях/Количество | integer ||
  || TRANSACTION_SUM | transactionSum | Информация о начислениях/Сумма транзакции | number ||
  || TRANSACTION_SOURCE | transactionSource | Информация о начислениях/Источник транзакции | string ||
  || ACT_ID | actId | Информация о начислениях/Номер акта об оказанных услугах | integer ||
  || ACT_DATE | actDate | Информация о начислениях/Дата акта об оказанных услугах | string ||
  || TRANSACTION_DATE | transactionDate | Информация о начислениях/Дата транзакции | string ||
  || TRANSACTION_ID | transactionId | Информация о начислениях/ID транзакции | string ||
  |#

  {% endcut %}

  {% cut "Лист **Отчёт о платежном поручении** (файл **netting_report_returns_and_compensations**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о возвратах и компенсациях покупателям/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE
  |
  orderCreationDate
  |
  Информация о возвратах и компенсациях покупателям/Дата оформления
  |
  string
  ||
  ||
  ORDER_DELIVERY_DATE
  |
  orderDeliveryDate
  |
  Информация о возвратах и компенсациях покупателям/Дата доставки заказа
  |
  string
  ||
  || ORDER_TYPE | orderType | Информация о возвратах и компенсациях покупателям/Тип заказа | string ||
  || SHOP_SKU | shopSku | Информация о возвратах и компенсациях покупателям/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о возвратах и компенсациях покупателям/Название товара | string ||
  || COUNT | count | Информация о возвратах и компенсациях покупателям/Количество | integer ||
  ||
  TRANSACTION_SUM
  |
  transactionSum
  |
  Информация о возвратах и компенсациях покупателям/Сумма транзакции
  |
  number
  ||
  ||
  TRANSACTION_SOURCE
  |
  transactionSource
  |
  Информация о возвратах и компенсациях покупателям/Источник транзакции
  |
  string
  ||
  ||
  TRANSACTION_DATE
  |
  transactionDate
  |
  Информация о возвратах и компенсациях покупателям/Дата транзакции
  |
  string
  ||
  || TRANSACTION_ID | transactionId | Информация о возвратах и компенсациях покупателям/ID транзакции | string ||
  |#

  {% endcut %}

  {% cut "Лист **Отчёт о платежном поручении** (файл **netting_report_retentions**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ACT_ID | actId | Информация об удержаниях/Номер акта об оказанных услугах | integer ||
  || ACT_DATE | actDate | Информация об удержаниях/Дата акта об оказанных услугах | string ||
  || SERVICE_NAME | serviceName | Информация об удержаниях/Название услуги к удержанию | string ||
  || TRANSACTION_SUM | transactionSum | Информация об удержаниях/Сумма транзакции | number ||
  || TRANSACTION_SOURCE | transactionSource | Информация об удержаниях/Источник транзакции | string ||
  || TRANSACTION_DATE | transactionDate | Информация об удержаниях/Дата транзакции | string ||
  || TRANSACTION_ID | transactionId | Информация об удержаниях/ID транзакции | string ||
  |#

  {% endcut %}

  {% cut "Лист **Отчёт по баллам** (файл **netting_bonuses**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || TRANSACTION_DATE | transactionDate | Информация о платежах/Дата транзакции | string ||
  || ORDER_ID | orderId | Информация о платежах/Номер заказа или отгрузки | integer ||
  || SHOP_ORDER_ID | shopOrderId | Информация о платежах/Ваш номер заказа | string ||
  || ORDER_CREATION_DATE | orderCreationDate | Информация о платежах/Дата создания заказа | string ||
  || ORDER_DELIVERY_DATE | orderDeliveryDate | Информация о платежах/Дата доставки заказа | string ||
  || ORDER_TYPE | orderType | Информация о платежах/Тип заказа | string ||
  || SHOP_SKU | shopSku | Информация о платежах/Ваш SKU | string ||
  ||
  OFFER_OR_SERVICE_NAME
  |
  offerOrServiceName
  |
  Информация о платежах/Название товара (к начислению) или услуги (к удержанию)

  |
  string
  ||
  || COUNT | count | Информация о платежах/Количество | integer ||
  || TRANSACTION_SUM | transactionSum | Информация о платежах/Сумма транзакции | number ||
  || TRANSACTION_TYPE | transactionType | Информация о платежах/Тип транзакции | string ||
  || TRANSACTION_SOURCE | transactionSource | Информация о платежах/Источник транзакции | string ||
  || PAYMENT_STATUS | paymentStatus | Информация о платежах/Статус | string ||
  || COMMENTS | comments | Информация о платежах/Комментарии | string ||
  ||
  BONUS_ACCOUNT_YEAR_MONTH
  |
  bonusAccountYearMonth
  |
  Информация о платежах/Месяц формирования премии за участие в совместных акциях
  |
  string
  ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/united/netting/generator/united_netting.md -->
  
  <!-- source: ru/_auto/method_limits/generateUnitedNettingReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateUnitedNettingReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/united-netting/generate
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _format_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReportFormatType](#entity-ReportFormatType)
  
  Формат отчета или документа.
  
  Формат отчета:
  
  * `FILE` — файл с электронной таблицей (XLSX).
  * `CSV` — ZIP-архив с CSV-файлами на каждый лист отчета.
  * `JSON` — ZIP-архив с JSON-файлами на каждый лист отчета.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `FILE`
  
  _Enum:_{.json-schema-reset .json-schema-value} `FILE`, `CSV`, `JSON`
  {.table-cell}
  ||
  ||
  
  _language_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReportLanguageType](#entity-ReportLanguageType)
  
  Язык отчета или документа.
  
  Язык отчета:
  
  * `RU` — русский язык.
  * `EN` — английский язык.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `EN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### ReportFormatType {#entity-ReportFormatType}
  
  Формат отчета:
  
  * `FILE` — файл с электронной таблицей (XLSX).
  * `CSV` — ZIP-архив с CSV-файлами на каждый лист отчета.
  * `JSON` — ZIP-архив с JSON-файлами на каждый лист отчета.
  
  
  **Type**: string
  
  _Default:_{.json-schema-reset .json-schema-value} `FILE`
  
  _Enum:_{.json-schema-reset .json-schema-value} `FILE`, `CSV`, `JSON`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReportLanguageType {#entity-ReportLanguageType}
  
  Язык отчета:
  
  * `RU` — русский язык.
  * `EN` — английский язык.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `EN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "businessId": 1,
    "dateTimeFrom": "2025-01-01T00:00:00Z",
    "dateTimeTo": "2025-01-01T00:00:00Z",
    "dateFrom": "2025-08-22",
    "dateTo": "2025-01-01",
    "bankOrderId": 0,
    "bankOrderDateTime": "2025-01-01T00:00:00Z",
    "monthOfYear": {
      "year": 2025,
      "month": 12
    },
    "placementPrograms": [
      "FBS"
    ],
    "inns": [
      "example"
    ],
    "campaignIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessId](#entity-BusinessId)
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _bankOrderDateTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата платежного поручения.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _bankOrderId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Номер платежного поручения.
  {.table-cell}
  ||
  ||
  
  _campaignIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)[] &#124; null
  
  Список идентификаторов кампании тех магазинов, которые нужны в отчете.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    1
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _dateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PeriodDateFrom](#entity-PeriodDateFrom)
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  {.table-cell}
  ||
  ||
  
  _dateTimeFrom_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `dateFrom`.
  
  {% endnote %}
  
  Начало периода, включительно.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _dateTimeTo_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `dateTo`.
  
  {% endnote %}
  
  Конец периода, включительно. Максимальный период — 3 месяца.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конец периода, включительно. Максимальный период — 3 месяца.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _inns_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Список ИНН, которые нужны в отчете.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "example"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _monthOfYear_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MonthOfYearDTO](#entity-MonthOfYearDTO)
  
  Месяц, за который нужен отчет о баллах Маркета.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "year": 2025,
    "month": 12
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _placementPrograms_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PlacementType](#entity-PlacementType)[] &#124; null
  
  Список моделей, которые нужны в отчете.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "FBS"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessId {#entity-BusinessId}
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PeriodDateFrom {#entity-PeriodDateFrom}
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  **Type**: string&lt;date&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Year {#entity-Year}
  
  Год.
  
  **Type**: integer
  
  </div>
  
  <div class="openapi-entity">
  
  ### Month {#entity-Month}
  
  Номер месяца.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  </div>
  
  <div class="openapi-entity">
  
  ### MonthOfYearDTO {#entity-MonthOfYearDTO}
  
  Месяц, за который нужен отчет о баллах Маркета.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _month_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Month](#entity-Month)
  
  Номер месяца.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  _Example:_{.json-schema-reset .json-schema-example} `12`
  {.table-cell}
  ||
  ||
  
  _year_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Year](#entity-Year)
  
  Год.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "year": 2025,
    "month": 12
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PlacementType {#entity-PlacementType}
  
  Модель, по которой работает магазин:
  
  * `FBS` — FBS или Экспресс.
  * `FBY` — FBY.
  * `DBS` — DBS.
  * `LAAS` — LaaS.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBS`, `FBY`, `DBS`, `LAAS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignId {#entity-CampaignId}
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  В ответ приходит идентификатор, который позволяет узнавать статус генерации и скачать готовый отчет.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "reportId": "example",
      "estimatedGenerationTime": 0
    }
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _result_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GenerateReportDTO](#entity-GenerateReportDTO)
  
    Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "reportId": "example",
      "estimatedGenerationTime": 0
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "result": {
        "reportId": "example",
        "estimatedGenerationTime": 0
      }
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiResponseStatusType {#entity-ApiResponseStatusType}
  
  Тип ответа.
  Возможные значения:
  * `OK` — ошибок нет.
  * `ERROR` — при обработке запроса произошла ошибка.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiResponse {#entity-ApiResponse}
  
  Стандартная обертка для ответов сервера.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ApiResponseStatusType](#entity-ApiResponseStatusType)
  
  Тип ответа.
  Возможные значения:
  * `OK` — ошибок нет.
  * `ERROR` — при обработке запроса произошла ошибка.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "OK"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GenerateReportDTO {#entity-GenerateReportDTO}
  
  Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _estimatedGenerationTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Ожидаемая продолжительность генерации в миллисекундах.
  {.table-cell}
  ||
  ||
  
  _reportId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "reportId": "example",
    "estimatedGenerationTime": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#400)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiErrorDTO {#entity-ApiErrorDTO}
  
  Общий формат ошибки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Код ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _message_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "code": "example",
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiErrorResponse {#entity-ApiErrorResponse}
  
  Стандартная обертка для ошибок сервера.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _errors_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [ApiErrorDTO](#entity-ApiErrorDTO)[] &#124; null
  
    Список ошибок.
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "code": "example",
        "message": "example"
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__401">
  
  ## 401 Unauthorized
  
  В запросе не указаны данные для авторизации. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#401)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__403">
  
  ## 403 Forbidden
  
  Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#403)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__404">
  
  ## 404 Not Found
  
  Запрашиваемый ресурс не найден. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#404)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__420">
  
  ## 420 Method Failure
  
  Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#420)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__500">
  
  ## 500 Internal Server Error
  
  Внутренняя ошибка Маркета. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#500)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
        

- Console

  ```openapi-sandbox translate=no
  pathParams: []
  searchParams:
    - description: Формат отчета или документа.
      name: format
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/dy0i/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
    - description: Язык отчета или документа.
      name: language
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/dy0i/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportLanguageType
  headers: []
  body: |-
    {
      "businessId": 1,
      "dateTimeFrom": "2025-01-01T00:00:00Z",
      "dateTimeTo": "2025-01-01T00:00:00Z",
      "dateFrom": "2025-08-22",
      "dateTo": "2025-01-01",
      "bankOrderId": 0,
      "bankOrderDateTime": "2025-01-01T00:00:00Z",
      "monthOfYear": {
        "year": 2025,
        "month": 12
      },
      "placementPrograms": [
        "FBS"
      ],
      "inns": [
        "example"
      ],
      "campaignIds": [
        1
      ]
    }
  schema:
    description: >
      Данные, необходимые для генерации отчета: идентификатор кампании, период, за
      который нужен отчет, а также фильтры.
    type: object
    required:
      - businessId
    properties:
      businessId:
        description: "Идентификатор кабинета. {% if audience == \"partner\" %}Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n{% endif %}\n"
        type: integer
        format: int64
        minimum: 1
      dateTimeFrom:
        description: |
          {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
          Вместо него используйте `dateFrom`.
  
          {% endnote %}
  
          Начало периода, включительно.
        format: date-time
        type: string
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-12'
          replacement-field: dateFrom
      dateTimeTo:
        description: |
          {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
          Вместо него используйте `dateTo`.
  
          {% endnote %}
  
          Конец периода, включительно. Максимальный период — 3 месяца.
        format: date-time
        type: string
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-12'
          replacement-field: dateTo
      dateFrom:
        type: string
        format: date
        description: |
          Начало периода, включительно.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        example: '2025-08-22'
      dateTo:
        description: |
          Конец периода, включительно. Максимальный период — 3 месяца.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        format: date
        type: string
      bankOrderId:
        description: Номер платежного поручения.
        format: int64
        type: integer
      bankOrderDateTime:
        description: Дата платежного поручения.
        format: date-time
        type: string
      monthOfYear:
        description: Месяц, за который нужен отчет о баллах Маркета.
        type: object
        required:
          - year
          - month
        properties:
          year:
            description: Год.
            type: integer
            format: int32
            example: 2025
          month:
            description: Номер месяца.
            type: integer
            format: int32
            minimum: 1
            maximum: 12
            example: 12
      placementPrograms:
        description: |
          Список моделей, которые нужны в отчете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: |
            Модель, по которой работает магазин:
  
            * `FBS` — FBS или Экспресс.
            * `FBY` — FBY.
            * `DBS` — DBS.
            * `LAAS` — LaaS.
          type: string
          enum:
            - FBS
            - FBY
            - DBS
            - LAAS
      inns:
        description: Список ИНН, которые нужны в отчете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          type: string
      campaignIds:
        description: |
          Список идентификаторов кампании тех магазинов, которые нужны в отчете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
          type: integer
          format: int64
          minimum: 1
  bodyType: application/json
  method: post
  security:
    - type: apiKey
      name: Api-Key
      in: header
    - type: oauth2
      x-inline: true
      flows:
        implicit:
          authorizationUrl: https://oauth.yandex.ru/authorize
          scopes:
            market:partner-api: API Яндекс.Маркета / Поиска по товарам для партнеров
  path: v2/reports/united-netting/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateUnitedNettingReport.md -->

[*баллы_маркета]: О том, что это такое, читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/accounting/market-points).

[*Deprecated]: No longer supported, please use an alternative and newer version.
