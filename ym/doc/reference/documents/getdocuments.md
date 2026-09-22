---
title: Получение документов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/getDocuments.md"
fetched_at: "2026-09-22T02:26:47Z"
content_sha: fe0f49f50f2f7e03
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/documents/getDocuments.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/getDocuments.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/documents/getDocuments.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/getDocuments.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/documents/getDocuments.md -->
<div class="openapi">

# Получение документов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getDocuments.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getDocuments.md -->
  
  Возвращает страницу документов на товары с учетом переданных фильтров.
  
  <!-- source: ru/_auto/method_limits/getDocuments.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 15 запросов в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 30 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getDocuments.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/offers/documents
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
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _limit_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество значений на одной странице.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `50`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `100`
  {.table-cell}
  ||
  ||
  
  _pageToken_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор страницы c результатами.
  
  Если параметр не указан, возвращается первая страница.
  
  Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе.
  
  
  _Example:_{.json-schema-reset .json-schema-example} ``
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "documentIds": [
      1
    ],
    "documentNumbers": [
      "example"
    ],
    "documentTypes": [
      "CONFORMITY_DECLARATION"
    ],
    "documentStatuses": [
      "ACTIVE"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _documentIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DocumentId](#entity-DocumentId)[] &#124; null
  
  Идентификаторы документов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
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
  
  _documentNumbers_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DocumentNumber](#entity-DocumentNumber)[] &#124; null
  
  Номера документов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
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
  
  _documentStatuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DocumentStatusType](#entity-DocumentStatusType)[] &#124; null
  
  Статусы документов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "ACTIVE"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _documentTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DocumentType](#entity-DocumentType)[] &#124; null
  
  Типы документов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "CONFORMITY_DECLARATION"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DocumentId {#entity-DocumentId}
  
  Идентификатор документа.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  ### DocumentStatusType {#entity-DocumentStatusType}
  
  Статус документа:
  
  * `ACTIVE` — действует.
  * `NOT_FOUND` — не найден в реестре.
  * `VALIDATING` — проверяется.
  * `WAITING_FIXES` — ожидает исправлений.
  * `EXPIRED` — срок действия истек.
  * `REVOKED` — отозван.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ACTIVE`, `NOT_FOUND`, `VALIDATING`, `WAITING_FIXES`, `EXPIRED`, `REVOKED`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Страница документов.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "documents": [
        {}
      ],
      "paging": {
        "nextPageToken": "example"
      }
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
    **Type**: [GetDocumentsResultDTO](#entity-GetDocumentsResultDTO)
  
    Страница документов.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "documents": [
        {
          "number": "example",
          "type": "CONFORMITY_DECLARATION",
          "activeFromDate": "2025-01-01",
          "activeToDate": "2025-01-01",
          "id": 1,
          "status": "ACTIVE"
        }
      ],
      "paging": {
        "nextPageToken": "example"
      }
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
        "documents": [
          {
            "number": "example",
            "type": "CONFORMITY_DECLARATION",
            "activeFromDate": "2025-01-01",
            "activeToDate": "2025-01-01",
            "id": 1,
            "status": "ACTIVE"
          }
        ],
        "paging": {
          "nextPageToken": "example"
        }
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
  
  ### BusinessDocumentDTO {#entity-BusinessDocumentDTO}
  
  Документ бизнеса.
  
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
    ||
  
    _status_{.json-schema-reset .json-schema-property .json-schema-required}
    {.table-cell}|
    **Type**: [DocumentStatusType](#entity-DocumentStatusType)
  
    Статус документа:
  
    * `ACTIVE` — действует.
    * `NOT_FOUND` — не найден в реестре.
    * `VALIDATING` — проверяется.
    * `WAITING_FIXES` — ожидает исправлений.
    * `EXPIRED` — срок действия истек.
    * `REVOKED` — отозван.
  
  
    _Enum:_{.json-schema-reset .json-schema-value} `ACTIVE`, `NOT_FOUND`, `VALIDATING`, `WAITING_FIXES`, `EXPIRED`, `REVOKED`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 1,
      "status": "ACTIVE"
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
    "id": 1,
    "status": "ACTIVE"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PackagingForwardScrollingPagerDTO {#entity-PackagingForwardScrollingPagerDTO}
  
  Идентификатор следующей страницы.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _nextPageToken_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор следующей страницы результатов.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "nextPageToken": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetDocumentsResultDTO {#entity-GetDocumentsResultDTO}
  
  Страница документов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _documents_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessDocumentDTO](#entity-BusinessDocumentDTO)[]
  
  Документы на странице.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "number": "example",
      "type": "CONFORMITY_DECLARATION",
      "activeFromDate": "2025-01-01",
      "activeToDate": "2025-01-01",
      "id": 1,
      "status": "ACTIVE"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _paging_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PackagingForwardScrollingPagerDTO](#entity-PackagingForwardScrollingPagerDTO)
  
  Идентификатор следующей страницы.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "nextPageToken": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "documents": [
      {
        "number": "example",
        "type": "CONFORMITY_DECLARATION",
        "activeFromDate": "2025-01-01",
        "activeToDate": "2025-01-01",
        "id": 1,
        "status": "ACTIVE"
      }
    ],
    "paging": {
      "nextPageToken": "example"
    }
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
  searchParams:
    - name: pageToken
      description: >
        Идентификатор страницы c результатами.
  
  
        Если параметр не указан, возвращается первая страница.
  
  
        Передавайте значение выходного параметра `nextPageToken`, полученное при
        последнем запросе.
      in: query
      required: false
      x-transform: token
      x-aliases:
        - pageToken
        - page_token
      schema:
        type: string
    - name: limit
      description: |
        Количество значений на одной странице.
      in: query
      required: false
      schema:
        type: integer
        format: int32
        minimum: 1
        default: 50
        maximum: 100
  headers: []
  body: |-
    {
      "documentIds": [
        1
      ],
      "documentNumbers": [
        "example"
      ],
      "documentTypes": [
        "CONFORMITY_DECLARATION"
      ],
      "documentStatuses": [
        "ACTIVE"
      ]
    }
  schema:
    type: object
    description: Фильтры для получения документов.
    properties:
      documentIds:
        type: array
        nullable: true
        minItems: 0
        maxItems: 100
        uniqueItems: true
        description: Идентификаторы документов.
        items:
          type: integer
          format: int64
          minimum: 1
          description: Идентификатор документа.
      documentNumbers:
        type: array
        nullable: true
        minItems: 0
        maxItems: 100
        uniqueItems: true
        description: Номера документов.
        items:
          type: string
          minLength: 1
          maxLength: 100
          pattern: ^\S(?:.*\S)?$
          description: Номер, указанный в сертификате, декларации или другом документе.
      documentTypes:
        type: array
        nullable: true
        minItems: 0
        uniqueItems: true
        description: Типы документов.
        items:
          type: string
          description: >
            Тип документа:
  
  
            * `CONFORMITY_DECLARATION` — Декларация о соответствии.
  
            * `CONFORMITY_CERTIFICATE` — Сертификат соответствия.
  
            * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация
            продукции (санэпид требования).
  
            * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки.
  
            * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о
            государственной регистрации БАД.
  
            * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение
            медицинского изделия.
  
            * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация
            пестицида и агрохимиката.
          enum:
            - CONFORMITY_DECLARATION
            - CONFORMITY_CERTIFICATE
            - STATE_REGISTRATION_CERTIFICATE
            - MEDICINAL_PRODUCT_CERTIFICATE
            - BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE
            - MEDICAL_DEVICE_CERTIFICATE
            - AGROCHEMICAL_PESTICIDE_CERTIFICATE
      documentStatuses:
        type: array
        nullable: true
        minItems: 0
        uniqueItems: true
        description: Статусы документов.
        items:
          type: string
          description: |
            Статус документа:
  
            * `ACTIVE` — действует.
            * `NOT_FOUND` — не найден в реестре.
            * `VALIDATING` — проверяется.
            * `WAITING_FIXES` — ожидает исправлений.
            * `EXPIRED` — срок действия истек.
            * `REVOKED` — отозван.
          enum:
            - ACTIVE
            - NOT_FOUND
            - VALIDATING
            - WAITING_FIXES
            - EXPIRED
            - REVOKED
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
  path: v1/businesses/{businessId}/offers/documents
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/documents/getDocuments.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
