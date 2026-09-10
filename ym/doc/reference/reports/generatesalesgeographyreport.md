---
title: Отчет по географии продаж
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateSalesGeographyReport.md"
fetched_at: "2026-09-10T01:56:53Z"
content_sha: c8c012d8624a4f9f
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateSalesGeographyReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateSalesGeographyReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateSalesGeographyReport.md
  - href: ru/reference/reports/generateSalesGeographyReport.md
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

<!-- source: ru/api/reports/generateSalesGeographyReport.md -->
<div class="openapi">

# Отчет по географии продаж

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateSalesGeographyReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateSalesGeographyReport.md -->
  
  Запускает генерацию отчета по географии продаж. [Что это за отчет](https://yandex.ru/support/marketplace/ru/analytics/sales-geography)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/locality/locality_offers_report_v2.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **География продаж** (файл **sales_geography**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || OFFER_ID | offerId | Информация о товарах/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о товарах/Название товара | string ||
  || CATEGORY | category | Информация о товарах/Категория | string ||
  ||
  EXPENSES_ON_DELIVERY_IN_RUSSIA
  |
  expensesOnDeliveryInRussia
  |
  Доля локальных продаж и ваши расходы/Расходы на доставку по России
  |
  number
  ||
  || LOCAL_SALES | localSales | Доля локальных продаж и ваши расходы/Локальных продаж | integer ||
  || DELIVERED_ITEMS | deliveredItems | Доля локальных продаж и ваши расходы/Товаров доставлено | integer ||
  || CLUSTER_MOSCOW | clusterMoscow | Сколько товаров доставлено в конкретные кластеры/Москва | integer ||
  ||
  CLUSTER_ROSTOV_ON_DON
  |
  clusterRostovOnDon
  |
  Сколько товаров доставлено в конкретные кластеры/Ростов-на-Дону
  |
  integer
  ||
  ||
  CLUSTER_EKATERINBURG
  |
  clusterEkaterinburg
  |
  Сколько товаров доставлено в конкретные кластеры/Екатеринбург
  |
  integer
  ||
  ||
  CLUSTER_SAINT_PETERSBURG
  |
  clusterSaintPetersburg
  |
  Сколько товаров доставлено в конкретные кластеры/Санкт-Петербург
  |
  integer
  ||
  || CLUSTER_SAMARA | clusterSamara | Сколько товаров доставлено в конкретные кластеры/Самара | integer ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/locality/locality_offers_report_v2.md -->
  
  <!-- source: ru/_includes/common/report-data-period-400-days.md -->
  {% note warning "Ограничения по тарифному плану" %}

  Период выгрузки данных и количество одновременно генерирующихся отчетов зависят от вашего тарифного плана:
  * **Без подписки или тариф «Лайт»** — доступны данные за последние 90 дней, одновременно может генерироваться 1 отчет
  * **Тариф «Медиум»** — доступны данные за последние 400 дней, одновременно может генерироваться до 10 отчетов

  Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).

  {% endnote %}
  <!-- endsource: ru/_includes/common/report-data-period-400-days.md -->
  
  <!-- source: ru/_auto/method_limits/generateSalesGeographyReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateSalesGeographyReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/sales-geography/generate
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
    "dateFrom": "2025-08-22",
    "dateTo": "2025-09-22",
    "categoryIds": [
      0
    ],
    "offerIds": [
      "example"
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
  
  _categoryIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Идентификаторы категорий.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `1000`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    0
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _offerIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)[] &#124; null
  
  Идентификаторы товаров.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `1000`
  
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
  
  ### ShopSku {#entity-ShopSku}
  
  Ваш SKU — идентификатор товара в вашей системе.
  
  Правила использования SKU:
  
  * У каждого товара SKU должен быть свой.
  
  * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.
  
  SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).
  
  {% note warning %}
  
  Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.
  
  {% endnote %}
  
  [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
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
          /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
  headers: []
  body: |-
    {
      "businessId": 1,
      "dateFrom": "2025-08-22",
      "dateTo": "2025-09-22",
      "categoryIds": [
        0
      ],
      "offerIds": [
        "example"
      ]
    }
  schema:
    description: |
      Данные, необходимые для генерации отчета.
    type: object
    required:
      - businessId
      - dateFrom
      - dateTo
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
      categoryIds:
        description: Идентификаторы категорий.
        type: array
        uniqueItems: true
        minItems: 1
        maxItems: 1000
        nullable: true
        items:
          type: integer
          format: int32
          minimum: 0
          exclusiveMinimum: true
      offerIds:
        description: Идентификаторы товаров.
        type: array
        uniqueItems: true
        minItems: 1
        maxItems: 1000
        nullable: true
        items:
          description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
          type: string
          pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
          x-transform: trim
          minLength: 1
          maxLength: 255
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
  path: v2/reports/sales-geography/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateSalesGeographyReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
