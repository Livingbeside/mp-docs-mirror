---
title: Закрывающие документы
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsReport.md"
fetched_at: "2026-09-10T01:57:03Z"
content_sha: 97abbef74b171b19
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateClosureDocumentsReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateClosureDocumentsReport.md
  - href: ru/reference/reports/generateClosureDocumentsReport.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/reports/generateClosureDocumentsReport.md -->
<div class="openapi">

# Закрывающие документы

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateClosureDocumentsReport.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateClosureDocumentsReport.md -->
  
  Возвращает ZIP-архив с закрывающими документами в формате PDF за указанный месяц.
  
  {% cut "Состав документов в зависимости от типа договора" %}
  
  * **Договор на размещение**
  
    * [акт об оказанных услугах](*acts-main-act)
    * [счет-фактура](*acts-main-invoice)
    * [сводный отчет по данным статистики](*acts-main-report)
    * [отчет об исполнении поручения и о зачете взаимных требований](*acts-main-agent) (отчет агента)
  
  * **Договор на продвижение** (в России не заключается после 30 сентября 2024 года)
  
    * [акт об оказании услуг](*acts-discounts-act)
    * [счет-фактура](*acts-discounts-invoice), если этого требует схема налогообложения
  
  * **Договор на маркетинг**
  
    * [акт об оказанных услугах](*acts-marketing-act)
    * [счет-фактура](*acts-main-invoice)
    * [счет-фактура на аванс](*acts-marketing-invoice)
    * [выписка по лицевому счету](*acts-marketing-account)
    * [детализация к акту](*acts-marketing-details)
  
  {% endcut %}
  
  Узнать статус генерации и получить ссылку на архив можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/method_limits/generateClosureDocumentsReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateClosureDocumentsReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/closure-documents/generate
  ```
  
  </div>
  
  </div>
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "campaignId": 1,
    "monthOfYear": {
      "year": 2025,
      "month": 12
    },
    "contractTypes": [
      "INCOME"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
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
  ||
  
  _monthOfYear_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ClosureDocumentsMonthOfYearDTO](#entity-ClosureDocumentsMonthOfYearDTO)
  
  Месяц, за который нужны закрывающие документы.
  
  Месяц и год.
  
  
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
  
  _contractTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ClosureDocumentsContractType](#entity-ClosureDocumentsContractType)[] &#124; null
  
  Типы договоров, по которым нужны закрывающие документы.
  
  Если их не указать, вернется архив с документами по всем найденным договорам.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `3`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "INCOME"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  ### Month {#entity-Month}
  
  Номер месяца.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ClosureDocumentsMonthOfYearDTO {#entity-ClosureDocumentsMonthOfYearDTO}
  
  Месяц и год.
  
  
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
  **Type**: integer
  
  Год.
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
  
  ### ClosureDocumentsContractType {#entity-ClosureDocumentsContractType}
  
  Тип договора:
  
  * `INCOME` — договор на размещение.
  
  * `OUTCOME` — договор на продвижение.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `INCOME`, `OUTCOME`, `MARKETING`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  ZIP-архив с закрывающими документами в формате PDF.
  
  
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
  searchParams: []
  headers: []
  body: |-
    {
      "campaignId": 1,
      "monthOfYear": {
        "year": 2025,
        "month": 12
      },
      "contractTypes": [
        "INCOME"
      ]
    }
  schema:
    description: |
      Данные, необходимые для запроса закрывающих документов.
    type: object
    required:
      - campaignId
      - monthOfYear
    properties:
      campaignId:
        description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
        type: integer
        format: int64
        minimum: 1
      monthOfYear:
        description: Месяц, за который нужны закрывающие документы.
        $ref: '#/$defs/ClosureDocumentsMonthOfYearDTO'
      contractTypes:
        description: >
          Типы договоров, по которым нужны закрывающие документы.
  
  
          Если их не указать, вернется архив с документами по всем найденным
          договорам.
        type: array
        uniqueItems: true
        minItems: 1
        maxItems: 3
        nullable: true
        items:
          description: |
            Тип договора:
  
            * `INCOME` — договор на размещение.
  
            * `OUTCOME` — договор на продвижение.
          type: string
          enum:
            - INCOME
            - OUTCOME
            - MARKETING
    $defs:
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ClosureDocumentsMonthOfYearDTO:
        description: |
          Месяц и год.
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
  path: v2/reports/closure-documents/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateClosureDocumentsReport.md -->

[*acts-main-act]:
В нем перечислены все услуги, которые Маркет оказал продавцу за прошедший месяц.<br><br>Подробнее об акте читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/accounting/acts/main/act).

[*acts-marketing-act]:
В нем перечислены все услуги, которые Маркет оказал продавцу за прошедший месяц.

[*acts-main-invoice]:
Это обязательный документ, регламентированный специальным постановлением Правительства.<br><br>В счете-фактуре содержится та же информация, что в акте об оказанных услугах. Для учета и анализа удобнее пользоваться актом.

[*acts-discounts-invoice]:
Это обязательный документ, регламентированный специальным постановлением Правительства.<br><br>В счете-фактуре содержится та же информация, что в акте об оказании услуг. Для учета и анализа удобнее пользоваться актом.

[*acts-main-report]:
Сводный отчет нужен бухгалтеру магазина, чтобы отражать в учете реализацию товаров.<br><br>Отчет составляется для магазинов, работающих по моделям FBY и FBS. В нем указано, сколько товаров и на какую сумму:<ul><li>отправлено покупателям;</li><li>доставлено покупателям;</li><li>покупатели не выкупили;</li><li>покупатели вернули.</li></ul>Отчет находится в том же PDF-файле, что акт об оказанных услугах.<br><br>Подробнее об отчете читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/accounting/acts/main/report).

[*acts-main-agent]:
Отчет показывает, сколько Маркет получил денег от покупателей, сколько уже перевел продавцу и сколько остался должен.<br><br>Подробнее об отчете читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/accounting/acts/main/agent).

[*acts-discounts-act]:
В акте указана:<ul><li>общая сумма всех скидок на товары, которые Маркет предоставил покупателям;</li><li>общая сумма всех скидок на доставку, которые Маркет предоставил покупателям (только для модели DBS);</li><li>общая сумма платежей баллами Плюса.</li></ul>

[*acts-marketing-invoice]:
Показывает сумму на балансе на начало месяца, которую продавец еще не потратили. Документ пригодится для бухгалтера.

[*acts-marketing-account]:
Показывает баланс продавца — расходы и остаток на конец месяца.

[*acts-marketing-details]:
Показывает услуги, оказанные по всем брендам продавца или рекламодателя. Детализация пригодится для учета.

[*Deprecated]: No longer supported, please use an alternative and newer version.
