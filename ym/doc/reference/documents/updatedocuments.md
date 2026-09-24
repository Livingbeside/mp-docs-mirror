---
title: Обновление документов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/updateDocuments.md"
fetched_at: "2026-09-24T02:13:39Z"
content_sha: cc8739107f4ff012
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/documents/updateDocuments.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/updateDocuments.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/documents/updateDocuments.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/updateDocuments.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/documents/updateDocuments.md -->
<div class="openapi">

# Обновление документов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateDocuments.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateDocuments.md -->
  
  Полностью обновляет номер, тип и даты документов на товары. За один запрос можно обновить не более 100 документов.
  
  Для каждого документа передайте его идентификатор и актуальные значения номера, типа и дат.
  Если дата не указана, ранее сохраненная дата будет удалена.
  Ошибка одного документа не мешает обработке остальных.
  
  <!-- source: ru/_auto/method_limits/updateDocuments.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 5 запросов в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 10 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateDocuments.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/offers/documents/update
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор кабинета.
  
  
  Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "documents": [
      {
        "number": "example",
        "type": "CONFORMITY_DECLARATION",
        "activeFromDate": "2025-01-01",
        "activeToDate": "2025-01-01",
        "id": 1
      }
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _documents_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateDocumentDTO](#entity-UpdateDocumentDTO)[]
  
  Документы для обновления. Идентификаторы документов не должны повторяться в одном запросе.
  Если идентификаторы повторяются, запрос не обрабатывается.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "number": "example",
      "type": "CONFORMITY_DECLARATION",
      "activeFromDate": "2025-01-01",
      "activeToDate": "2025-01-01",
      "id": 1
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DocumentNumber {#entity-DocumentNumber}
  
  Номер, указанный в сертификате, декларации или другом документе.
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `100`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^\S(?:.*\S)?$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DocumentType {#entity-DocumentType}
  
  Тип документа:
  
  * `CONFORMITY_DECLARATION` — Декларация о соответствии.
  * `CONFORMITY_CERTIFICATE` — Сертификат соответствия.
  * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация продукции (санэпид требования).
  * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки.
  * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о государственной регистрации БАД.
  * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение медицинского изделия.
  * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация пестицида и агрохимиката.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CONFORMITY_DECLARATION`, `CONFORMITY_CERTIFICATE`, `STATE_REGISTRATION_CERTIFICATE`, `MEDICINAL_PRODUCT_CERTIFICATE`, `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE`, `MEDICAL_DEVICE_CERTIFICATE`, `AGROCHEMICAL_PESTICIDE_CERTIFICATE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DocumentWriteDTO {#entity-DocumentWriteDTO}
  
  Реквизиты документа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _number_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DocumentNumber](#entity-DocumentNumber)
  
  Номер, указанный в сертификате, декларации или другом документе.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `100`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^\S(?:.*\S)?$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DocumentType](#entity-DocumentType)
  
  Тип документа:
  
  * `CONFORMITY_DECLARATION` — Декларация о соответствии.
  * `CONFORMITY_CERTIFICATE` — Сертификат соответствия.
  * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация продукции (санэпид требования).
  * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки.
  * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о государственной регистрации БАД.
  * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение медицинского изделия.
  * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация пестицида и агрохимиката.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CONFORMITY_DECLARATION`, `CONFORMITY_CERTIFICATE`, `STATE_REGISTRATION_CERTIFICATE`, `MEDICINAL_PRODUCT_CERTIFICATE`, `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE`, `MEDICAL_DEVICE_CERTIFICATE`, `AGROCHEMICAL_PESTICIDE_CERTIFICATE`
  {.table-cell}
  ||
  ||
  
  _activeFromDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата начала действия документа.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _activeToDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата окончания действия документа.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "number": "example",
    "type": "CONFORMITY_DECLARATION",
    "activeFromDate": "2025-01-01",
    "activeToDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DocumentId {#entity-DocumentId}
  
  Идентификатор документа.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateDocumentDTO {#entity-UpdateDocumentDTO}
  
  Полная модель документа для обновления.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [DocumentWriteDTO](#entity-DocumentWriteDTO)
  
    Реквизиты документа.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "number": "example",
      "type": "CONFORMITY_DECLARATION",
      "activeFromDate": "2025-01-01",
      "activeToDate": "2025-01-01"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _id_{.json-schema-reset .json-schema-property .json-schema-required}
    {.table-cell}|
    **Type**: [DocumentId](#entity-DocumentId)
  
    Идентификатор документа.
  
    _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
    _Example:_{.json-schema-reset .json-schema-example} `1`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 1
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "number": "example",
    "type": "CONFORMITY_DECLARATION",
    "activeFromDate": "2025-01-01",
    "activeToDate": "2025-01-01",
    "id": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Если все документы обновлены, поле `status` принимает значение `OK`, а поле `result` не возвращается.
  
  Если хотя бы один документ не удалось обновить, поле `status` принимает значение `ERROR`, а поле
  `result` содержит только ошибки. Остальные документы при этом обрабатываются.
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "errors": [
        {
          "id": 1,
          "code": "DOCUMENT_VALIDATION_FAILED",
          "message": "example"
        }
      ]
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
    **Type**: [UpdateDocumentsResultDTO](#entity-UpdateDocumentsResultDTO)
  
    Ошибки документов, которые не удалось обновить.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "errors": [
        {
          "id": 1,
          "code": "DOCUMENT_VALIDATION_FAILED",
          "message": "example"
        }
      ]
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
        "errors": [
          {
            "id": 1,
            "code": "DOCUMENT_VALIDATION_FAILED",
            "message": "example"
          }
        ]
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
  
  ### DocumentErrorCodeType {#entity-DocumentErrorCodeType}
  
  Код ошибки документа:
  
  * `DOCUMENT_VALIDATION_FAILED` — документ не прошел проверку.
  * `DOCUMENT_ALREADY_EXISTS` — документ уже существует.
  * `DOCUMENT_NOT_FOUND` — документ не найден.
  * `DOCUMENT_UPDATE_NOT_ALLOWED` — изменение документа запрещено.
  * `DOCUMENT_CONCURRENT_MODIFICATION` — документ был изменен параллельно.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DOCUMENT_VALIDATION_FAILED`, `DOCUMENT_ALREADY_EXISTS`, `DOCUMENT_NOT_FOUND`, `DOCUMENT_UPDATE_NOT_ALLOWED`, `DOCUMENT_CONCURRENT_MODIFICATION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateDocumentErrorDTO {#entity-UpdateDocumentErrorDTO}
  
  Ошибка обновления документа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DocumentErrorCodeType](#entity-DocumentErrorCodeType)
  
  Код ошибки документа:
  
  * `DOCUMENT_VALIDATION_FAILED` — документ не прошел проверку.
  * `DOCUMENT_ALREADY_EXISTS` — документ уже существует.
  * `DOCUMENT_NOT_FOUND` — документ не найден.
  * `DOCUMENT_UPDATE_NOT_ALLOWED` — изменение документа запрещено.
  * `DOCUMENT_CONCURRENT_MODIFICATION` — документ был изменен параллельно.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DOCUMENT_VALIDATION_FAILED`, `DOCUMENT_ALREADY_EXISTS`, `DOCUMENT_NOT_FOUND`, `DOCUMENT_UPDATE_NOT_ALLOWED`, `DOCUMENT_CONCURRENT_MODIFICATION`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DocumentId](#entity-DocumentId)
  
  Идентификатор документа.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _message_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание ошибки для человека. Для обработки ошибки используйте поле `code`.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "code": "DOCUMENT_VALIDATION_FAILED",
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateDocumentsResultDTO {#entity-UpdateDocumentsResultDTO}
  
  Ошибки документов, которые не удалось обновить.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _errors_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateDocumentErrorDTO](#entity-UpdateDocumentErrorDTO)[]
  
  Ошибки обработки документов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 1,
      "code": "DOCUMENT_VALIDATION_FAILED",
      "message": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "errors": [
      {
        "id": 1,
        "code": "DOCUMENT_VALIDATION_FAILED",
        "message": "example"
      }
    ]
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
  pathParams:
    - description: "Идентификатор кабинета.\n\n{% if audience == \"partner\" %}\n\nЧтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n\n{% endif %}\n"
      name: businessId
      in: path
      required: true
      schema:
        type: integer
        format: int64
        minimum: 1
  searchParams: []
  headers: []
  body: |-
    {
      "documents": [
        {
          "number": "example",
          "type": "CONFORMITY_DECLARATION",
          "activeFromDate": "2025-01-01",
          "activeToDate": "2025-01-01",
          "id": 1
        }
      ]
    }
  schema:
    type: object
    description: Документы для полного обновления.
    required:
      - documents
    properties:
      documents:
        type: array
        minItems: 1
        maxItems: 100
        description: >
          Документы для обновления. Идентификаторы документов не должны
          повторяться в одном запросе.
  
          Если идентификаторы повторяются, запрос не обрабатывается.
        items:
          type: object
          description: Полная модель документа для обновления.
          allOf:
            - type: object
              description: Реквизиты документа.
              required:
                - number
                - type
              properties:
                number:
                  type: string
                  minLength: 1
                  maxLength: 100
                  pattern: ^\S(?:.*\S)?$
                  description: >-
                    Номер, указанный в сертификате, декларации или другом
                    документе.
                type:
                  type: string
                  description: >
                    Тип документа:
  
  
                    * `CONFORMITY_DECLARATION` — Декларация о соответствии.
  
                    * `CONFORMITY_CERTIFICATE` — Сертификат соответствия.
  
                    * `STATE_REGISTRATION_CERTIFICATE` — Государственная
                    регистрация продукции (санэпид требования).
  
                    * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для
                    аптеки.
  
                    * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о
                    государственной регистрации БАД.
  
                    * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение
                    медицинского изделия.
  
                    * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная
                    регистрация пестицида и агрохимиката.
                  enum:
                    - CONFORMITY_DECLARATION
                    - CONFORMITY_CERTIFICATE
                    - STATE_REGISTRATION_CERTIFICATE
                    - MEDICINAL_PRODUCT_CERTIFICATE
                    - BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE
                    - MEDICAL_DEVICE_CERTIFICATE
                    - AGROCHEMICAL_PESTICIDE_CERTIFICATE
                activeFromDate:
                  type: string
                  format: date
                  description: Дата начала действия документа.
                activeToDate:
                  type: string
                  format: date
                  description: Дата окончания действия документа.
            - type: object
              required:
                - id
              properties:
                id:
                  type: integer
                  format: int64
                  minimum: 1
                  description: Идентификатор документа.
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
  path: v1/businesses/{businessId}/offers/documents/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/documents/updateDocuments.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
