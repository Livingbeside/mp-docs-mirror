---
title: Отчет по бусту показов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md"
fetched_at: "2026-09-16T02:28:04Z"
content_sha: 1c4d2edc7c390e28
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateShowsBoostReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateShowsBoostReport.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateShowsBoostReport.md -->
<div class="openapi">

# Отчет по бусту показов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateShowsBoostReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * promotion:read-only — [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateShowsBoostReport.md -->
  
  Запускает генерацию сводного отчета по бусту показов за заданный период. [Что такое буст показов](https://yandex.ru/support/marketplace/ru/marketing/boost-shows)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/cpm_boost/business_cpm_boost_consolidated.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Отчёт по кампаниям** (файл **business_shows_boost_consolidated_campaigns**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || DATE | date | Дата | string ||
  || SALE_CAMPAIGN_ID | saleCampaignId | ID кампании | integer ||
  || SALE_CAMPAIGN_NAME | saleCampaignName | Название кампании | string ||
  || SHOWS | shows | Показы, шт. | integer ||
  || COVERAGE | coverage | Охват, чел. | integer ||
  || CLICKS | clicks | Клики, шт. | integer ||
  || CTR | ctr | CTR, % | number ||
  || SHOWS_FREQUENCY | showsFrequency | Частота показа | number ||
  || CART_ADDITION | cartAddition | Добавления в корзину, шт. | integer ||
  || ORDERED_COUNT | orderedCount | Заказанные товары, шт. | integer ||
  || CONVERSION | conversion | Конверсия в заказы, % | number ||
  || ORDERED_AMOUNT | orderedAmount | Стоимость заказанных товаров, ₽ | number ||
  || CPO | cpo | СРО, ₽ | number ||
  ||
  COST
  |
  cost
  |
  Расчётные
  расходы, ₽
  |
  number
  ||
  || COST_SHARE | costShare | Доля расчетных расходов от выручки с бустом продаж с оплатой за показы | number ||
  || CPM | cpm | CPM, ₽ | number ||
  || REAL_COST | realCost | Фактические расходы, ₽ | number ||
  || DEDUCTED_BONUSES | deductedBonuses | Списано бонусов | number ||
  |#

  {% endcut %}

  {% cut "Лист **Отчёт по товарам** (файл **business_shows_boost_consolidated_offers**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || OFFER_ID | offerId | Ваш SKU | string ||
  || OFFER_NAME | offerName | Название товара | string ||
  || SHOWS | shows | Показы товаров с бустом продаж с оплатой за показы | integer ||
  || CLICKS | clicks | Клики по товарам с бустом продаж с оплатой за показы | integer ||
  || CART_ADDITION | cartAddition | Добавления в корзину с бустом продаж с оплатой за показы | integer ||
  || ORDERED_COUNT | orderedCount | Заказанные товары с бустом продаж с оплатой за показы | integer ||
  || CPM | cpm | CPM | number ||
  || COST | cost | Расчётные расходы на буст продаж с оплатой за показы, ₽ | number ||
  || ORDERED_AMOUNT | orderedAmount | Выручка с бустом продаж с оплатой за показы | number ||
  || SALES_CAMPAIGN_IDS | salesCampaignIds | ID кампаний | string ||
  || SALES_CAMPAIGN_NAMES | salesCampaignNames | Названия кампаний | string ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/cpm_boost/business_cpm_boost_consolidated.md -->
  
  
  <!-- source: ru/_includes/common/report-data-period-400-days.md -->
  {% note warning "Ограничения по тарифному плану" %}

  Период выгрузки данных и количество одновременно генерирующихся отчетов зависят от вашего тарифного плана:
  * **Без подписки или тариф «Лайт»** — доступны данные за последние 90 дней, одновременно может генерироваться 1 отчет
  * **Тариф «Медиум»** — доступны данные за последние 400 дней, одновременно может генерироваться до 10 отчетов

  Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).

  {% endnote %}
  <!-- endsource: ru/_includes/common/report-data-period-400-days.md -->
  
  
  <!-- source: ru/_auto/method_limits/generateShowsBoostReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateShowsBoostReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/shows-boost/generate
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
  
  _sourceType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SourceType](#entity-SourceType)
  
  Признак типа кабинета, от имени которого вызывается метод:
  
  - `SELLER` — продавец.
  
  
  - `ADVERTISER` — рекламодатель.
  
  
  
  Тип кабинета:
  
  * `SELLER` — продавец.
  * `ADVERTISER` — рекламодатель.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `SELLER`
  
  _Enum:_{.json-schema-reset .json-schema-value} `SELLER`, `ADVERTISER`
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
  
  ### SourceType {#entity-SourceType}
  
  Тип кабинета:
  
  * `SELLER` — продавец.
  * `ADVERTISER` — рекламодатель.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SELLER`, `ADVERTISER`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "businessId": 1,
    "dateFrom": "2025-08-22",
    "dateTo": "2025-09-22",
    "attributionType": "CLICKS"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _attributionType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [StatisticsAttributionType](#entity-StatisticsAttributionType)
  
  Тип атрибуции.
  
  Тип атрибуции:
    * `CLICKS` — по кликам.
    * `SHOWS` — по показам.
  <br><br>
  
  О том, какие данные в отчете зависят и не зависят от типа атрибуции, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/shelf#stats).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CLICKS`, `SHOWS`
  {.table-cell}
  ||
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
  
  ### PeriodDateTo {#entity-PeriodDateTo}
  
  Конец периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  **Type**: string&lt;date&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-09-22`
  
  </div>
  
  <div class="openapi-entity">
  
  ### StatisticsAttributionType {#entity-StatisticsAttributionType}
  
  Тип атрибуции:
    * `CLICKS` — по кликам.
    * `SHOWS` — по показам.
  <br><br>
  
  О том, какие данные в отчете зависят и не зависят от типа атрибуции, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/shelf#stats).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CLICKS`, `SHOWS`
  
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
    - name: sourceType
      in: query
      required: false
      description: "Признак типа кабинета, от имени которого вызывается метод:\n{% if audience == \"partner\" %}\n\n- `SELLER` — продавец.\n\n{% endif %}\n\n- `ADVERTISER` — рекламодатель.\n\n{% if audience == \"advertiser\" %}\n\n{% note info \"Обязательно указывайте sourceType=ADVERTISER в каждом запросе.\" %}\n\n\_\n\n{% endnote %}\n\n{% endif %}\n"
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/SourceType
        default: SELLER
  headers: []
  body: |-
    {
      "businessId": 1,
      "dateFrom": "2025-08-22",
      "dateTo": "2025-09-22",
      "attributionType": "CLICKS"
    }
  schema:
    description: |
      Данные, необходимые для генерации отчета.
    type: object
    required:
      - businessId
      - dateFrom
      - dateTo
      - attributionType
    properties:
      businessId:
        description: "Идентификатор кабинета. {% if audience == \"partner\" %}Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n{% endif %}\n"
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
      attributionType:
        description: Тип атрибуции.
        $ref: '#/$defs/StatisticsAttributionType'
    $defs:
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/StatisticsAttributionType:
        type: string
        description: >
          Тип атрибуции:
            * `CLICKS` — по кликам.
            * `SHOWS` — по показам.
          {% if audience == "partner" %}
  
          <br><br>
  
  
          О том, какие данные в отчете зависят и не зависят от типа атрибуции,
          читайте [в Справке Маркета для
          продавцов](https://yandex.ru/support2/marketplace/ru/marketing/shelf#stats).
  
          {% endif %}
        enum:
          - CLICKS
          - SHOWS
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
  path: v2/reports/shows-boost/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateShowsBoostReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
