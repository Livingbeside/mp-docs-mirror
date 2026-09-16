---
title: Отчет «Аналитика продаж»
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md"
fetched_at: "2026-09-16T02:27:53Z"
content_sha: ef43fe18cb904674
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateShowsSalesReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateShowsSalesReport.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateShowsSalesReport.md -->
<div class="openapi">

# Отчет «Аналитика продаж»

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateShowsSalesReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateShowsSalesReport.md -->
  
  Запускает генерацию отчета «Аналитика продаж» за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/analytics/shows-sales.html)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/masterstat/sales_funnel_by_created_at.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Аналитика продаж** (файл **sales_funnel_report**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DAY | day | День | string ||
  || MONTH | month | Месяц | string ||
  || YEAR | year | Год | integer ||
  || CATEGORY_NAME | categoryName | Категория | string ||
  || BRAND_NAME | brandName | Бренд | string ||
  || OFFER_ID | offerId | Ваш SKU | string ||
  || OFFER_NAME | offerName | Название товара | string ||
  || BY_MSKU_SHOWS | byMskuShows | Показы товаров всех продавцов, шт. | integer ||
  || VISIBILITY_INDEX | visibilityIndex | Индекс видимости, % | string ||
  || SHOWS | shows | Показы моих товаров, шт. | integer ||
  || SHOWS_WITH_PROMOTION | showsWithPromotion | Показы моих товаров с акциями, шт. | integer ||
  || SHOWS_SHARE | showsShare | Доля показов с бустом, % | number ||
  || CLICKS | clicks | Клики по товарам, шт. | integer ||
  || CLICKS_WITH_PROMOTION | clicksWithPromotion | Клики по товарам с акциями, шт. | integer ||
  || TO_CART_CONVERSION | toCartConversion | Конверсия из показа в корзину, % | number ||
  || TO_CART | toCart | Добавления в корзину, шт. | integer ||
  || TO_CART_WITH_PROMOTION | toCartWithPromotion | Добавления в корзину по акциям, шт. | integer ||
  || TO_CART_SHARE | toCartShare | Доля добавлений товаров с бустом в корзину, % | number ||
  || ORDER_ITEMS | orderItems | Заказанные товары, шт. | integer ||
  || ORDER_ITEMS_WITH_PROMOTION | orderItemsWithPromotion | Заказанные товары по акциям, шт. | integer ||
  || ORDER_ITEMS_TOTAL_AMOUNT | orderItemsTotalAmount | Заказано товаров на сумму, ₽ | integer ||
  ||
  ORDER_ITEMS_TOTAL_AMOUNT_WITH_PROMOTION
  |
  orderItemsTotalAmountWithPromotion
  |
  Заказано товаров с акциями на сумму, ₽
  |
  integer
  ||
  || TO_ORDER_CONVERSION | toOrderConversion | Конверсия из корзины в заказ, % | number ||
  || ORDER_ITEMS_SHARE | orderItemsShare | Доля заказанных товаров с бустом, % | number ||
  || ORDER_ITEMS_DELIVERED_COUNT | orderItemsDeliveredCount | Доставлено за период, шт. | integer ||
  ||
  ORDER_ITEMS_DELIVERED_COUNT_WITH_PROMOTION
  |
  orderItemsDeliveredCountWithPromotion
  |
  Доставлено за период по акциям, шт.
  |
  string
  ||
  ||
  ORDER_ITEMS_DELIVERED_TOTAL_AMOUNT
  |
  orderItemsDeliveredTotalAmount
  |
  Доставлено за период на сумму, ₽
  |
  integer
  ||
  ||
  ORDER_ITEMS_DELIVERED_TOTAL_AMOUNT_WITH_PROMOTION
  |
  orderItemsDeliveredTotalAmountWithPromotion
  |
  Доставлено за период по акциям на сумму, ₽
  |
  integer
  ||
  ||
  ORDER_ITEMS_DELIVERED_FROM_ORDERED_COUNT
  |
  orderItemsDeliveredFromOrderedCount
  |
  Доставлено из заказанных за период, шт.
  |
  integer
  ||
  ||
  ORDER_ITEMS_DELIVERED_FROM_ORDERED_TOTAL_AMOUNT
  |
  orderItemsDeliveredFromOrderedTotalAmount
  |
  Доставлено из заказанных на сумму за период, ₽
  |
  integer
  ||
  ||
  ORDER_ITEMS_DELIVERED_FROM_ORDERED_TOTAL_AMOUNT_WITH_PROMOTION
  |
  orderItemsDeliveredFromOrderedTotalAmountWithPromotion
  |
  Доставлено из заказанных на сумму за период по акциям, ₽
  |
  integer
  ||
  || ORDER_ITEMS_CANCELED_COUNT | orderItemsCanceledCount | Отмены и невыкупы за период, шт. | integer ||
  ||
  ORDER_ITEMS_CANCELED_BY_CREATED_AT_COUNT
  |
  orderItemsCanceledByCreatedAtCount
  |
  Отмены и невыкупы заказанного за период, шт.
  |
  integer
  ||
  || ORDER_ITEMS_RETURNED_COUNT | orderItemsReturnedCount | Возвращённые товары за период, шт. | integer ||
  ||
  ORDER_ITEMS_RETURNED_BY_CREATED_AT_COUNT
  |
  orderItemsReturnedByCreatedAtCount
  |
  Возвраты заказанного за период, шт.
  |
  integer
  ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/masterstat/sales_funnel_by_created_at.md -->
  
  <!-- source: ru/_includes/common/report-data-period-400-days.md -->
  {% note warning "Ограничения по тарифному плану" %}

  Период выгрузки данных и количество одновременно генерирующихся отчетов зависят от вашего тарифного плана:
  * **Без подписки или тариф «Лайт»** — доступны данные за последние 90 дней, одновременно может генерироваться 1 отчет
  * **Тариф «Медиум»** — доступны данные за последние 400 дней, одновременно может генерироваться до 10 отчетов

  Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).

  {% endnote %}
  <!-- endsource: ru/_includes/common/report-data-period-400-days.md -->
  
  <!-- source: ru/_auto/method_limits/generateShowsSalesReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 10 минут<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в 6 минут</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateShowsSalesReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/shows-sales/generate
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
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "businessId": 1,
    "campaignId": 1,
    "dateFrom": "2025-08-22",
    "dateTo": "2025-09-22",
    "grouping": "CATEGORIES"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dateFrom_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PeriodDateFrom](#entity-PeriodDateFrom)
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PeriodDateTo](#entity-PeriodDateTo)
  
  Конец периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-09-22`
  {.table-cell}
  ||
  ||
  
  _grouping_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShowsSalesGroupingType](#entity-ShowsSalesGroupingType)
  
  Группировка данных отчета.
  
  Группировка данных отчета.
  Возможные значения:
  * `CATEGORIES` — группировка по категориям.
  * `OFFERS` — группировка по товарам.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CATEGORIES`, `OFFERS`
  {.table-cell}
  ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessId](#entity-BusinessId)
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
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
  
  <div class="openapi-entity">
  
  ### PeriodDateFrom {#entity-PeriodDateFrom}
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  **Type**: string&lt;date&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PeriodDateTo {#entity-PeriodDateTo}
  
  Конец периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  **Type**: string&lt;date&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-09-22`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ShowsSalesGroupingType {#entity-ShowsSalesGroupingType}
  
  Группировка данных отчета.
  Возможные значения:
  * `CATEGORIES` — группировка по категориям.
  * `OFFERS` — группировка по товарам.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CATEGORIES`, `OFFERS`
  
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
          /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
  headers: []
  body: |-
    {
      "businessId": 1,
      "campaignId": 1,
      "dateFrom": "2025-08-22",
      "dateTo": "2025-09-22",
      "grouping": "CATEGORIES"
    }
  schema:
    description: >
      Данные, необходимые для генерации отчета.
  
  
      В запросе обязательно должен быть либо `businessId`, либо `campaignId`, но
      не оба сразу.
    type: object
    required:
      - dateFrom
      - dateTo
      - grouping
    properties:
      businessId:
        description: "Идентификатор кабинета. {% if audience == \"partner\" %}Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n{% endif %}\n"
        type: integer
        format: int64
        minimum: 1
      campaignId:
        description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
        type: integer
        format: int64
        minimum: 1
      dateFrom:
        type: string
        format: date
        description: |
          Начало периода, включительно.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        example: '2025-08-22'
      dateTo:
        type: string
        format: date
        description: |
          Конец периода, включительно.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        example: '2025-09-22'
      grouping:
        description: Группировка данных отчета.
        $ref: '#/$defs/ShowsSalesGroupingType'
    $defs:
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/api/generateShowsSalesReport.yaml#/ShowsSalesGroupingType:
        type: string
        description: |
          Группировка данных отчета.
          Возможные значения:
          * `CATEGORIES` — группировка по категориям.
          * `OFFERS` — группировка по товарам.
        enum:
          - CATEGORIES
          - OFFERS
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
  path: v2/reports/shows-sales/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateShowsSalesReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
