---
title: Документы по заявке
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md"
fetched_at: "2026-09-11T01:58:27Z"
content_sha: fd793daa9bbe5b84
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/supply-requests/getSupplyRequestDocuments.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/supply-requests/getSupplyRequestDocuments.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/supply-requests/getSupplyRequestDocuments.md -->
<div class="openapi">

# Получение документов по заявке на поставку, вывоз или утилизацию

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getSupplyRequestDocuments.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md) и [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * supplies-management:read-only — [Получение информации по FBY-заявкам](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getSupplyRequestDocuments.md -->
  
  Возвращает документы по заявке.
  
  <!-- source: ru/_auto/method_limits/getSupplyRequestDocuments.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getSupplyRequestDocuments.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/supply-requests/documents
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "requestId": 1
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _requestId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestId](#entity-SupplyRequestId)
  
  Идентификатор заявки.
  
  {% note warning "Используется только в API" %}
  
  По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`.
  
  {% endnote %}
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestId {#entity-SupplyRequestId}
  
  Идентификатор заявки.
  
  {% note warning "Используется только в API" %}
  
  По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`.
  
  {% endnote %}
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список документов и ссылки на них.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "documents": [
        {
          "type": "SUPPLY",
          "url": "example",
          "createdAt": "2025-01-01T00:00:00Z"
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
    **Type**: [GetSupplyRequestDocumentsDTO](#entity-GetSupplyRequestDocumentsDTO)
  
    Информация о документах по заявке.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "documents": [
        {
          "type": "SUPPLY",
          "url": "example",
          "createdAt": "2025-01-01T00:00:00Z"
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
        "documents": [
          {
            "type": "SUPPLY",
            "url": "example",
            "createdAt": "2025-01-01T00:00:00Z"
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
  
  ### SupplyRequestDocumentType {#entity-SupplyRequestDocumentType}
  
  Тип документа:
  
  * **Документы, которые загружает магазин**
    * `SUPPLY` — список товаров.
    * `ADDITIONAL_SUPPLY` — список товаров в дополнительной поставке.
    * `VIRTUAL_DISTRIBUTION_CENTER_SUPPLY` — список товаров в [мультипоставке](*multisupply).
    * `TRANSFER` — список товаров для утилизации.
    * `WITHDRAW` — список товаров для вывоза.
  
  * **Поставка товаров**
    * `VALIDATION_ERRORS` — ошибки по товарам в поставке.
    * `CARGO_UNITS` — ярлыки для грузомест.
  
  * **Дополнительная поставка и непринятые товары**
    * `ADDITIONAL_SUPPLY_ACCEPTABLE_GOODS` — товары, которые подходят для дополнительной поставки.
    * `ADDITIONAL_SUPPLY_UNACCEPTABLE_GOODS` — вывоз непринятых товаров.
  
  * **Маркировка товаров**
    * `INBOUND_UTD` — входящий УПД.
    * `OUTBOUND_UTD` — исходящий УПД.
    * `IDENTIFIERS` — коды маркировки товаров.
    * `CIS_FACT` — принятые товары с кодами маркировки.
    * `ITEMS_WITH_CISES` — товары, для которых нужна маркировка.
    * `REPORT_OF_WITHDRAW_WITH_CISES` — маркированные товары для вывоза со склада.
    * `SECONDARY_ACCEPTANCE_CISES` — маркированные товары, которые приняты после вторичной приемки.
    * `RNPT_FACT` — принятые товары с регистрационным номером партии товара (РНПТ).
  
  * **Акты**
    * `ACT_OF_WITHDRAW` — акт возврата.
    * `ANOMALY_CONTAINERS_WITHDRAW_ACT` — акт изъятия непринятого товара.
    * `ACT_OF_WITHDRAW_FROM_STORAGE` — акт списания с ответственного хранения.
    * `ACT_OF_RECEPTION_TRANSFER` — акт приема-передачи.
    * `ACT_OF_DISCREPANCY` — акт о расхождениях.
    * `SECONDARY_RECEPTION_ACT` — акт вторичной приемки.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SUPPLY`, `ADDITIONAL_SUPPLY`, `VIRTUAL_DISTRIBUTION_CENTER_SUPPLY`, `TRANSFER`, `INBOUND_UTD`, `OUTBOUND_UTD`, `ADDITIONAL_SUPPLY_ACCEPTABLE_GOODS`, `ADDITIONAL_SUPPLY_UNACCEPTABLE_GOODS`, `VALIDATION_ERRORS`, `WITHDRAW`, `ACT_OF_WITHDRAW`, `ANOMALY_CONTAINERS_WITHDRAW_ACT`, `ACT_OF_WITHDRAW_FROM_STORAGE`, `ACT_OF_RECEPTION_TRANSFER`, `ACT_OF_DISCREPANCY`, `SECONDARY_RECEPTION_ACT`, `CARGO_UNITS`, `IDENTIFIERS`, `CIS_FACT`, `ITEMS_WITH_CISES`, `REPORT_OF_WITHDRAW_WITH_CISES`, `SECONDARY_ACCEPTANCE_CISES`, `RNPT_FACT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Url {#entity-Url}
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestDocumentDTO {#entity-SupplyRequestDocumentDTO}
  
  Документ по заявке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время создания документа.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestDocumentType](#entity-SupplyRequestDocumentType)
  
  Тип документа:
  
  * **Документы, которые загружает магазин**
    * `SUPPLY` — список товаров.
    * `ADDITIONAL_SUPPLY` — список товаров в дополнительной поставке.
    * `VIRTUAL_DISTRIBUTION_CENTER_SUPPLY` — список товаров в [мультипоставке](*multisupply).
    * `TRANSFER` — список товаров для утилизации.
    * `WITHDRAW` — список товаров для вывоза.
  
  * **Поставка товаров**
    * `VALIDATION_ERRORS` — ошибки по товарам в поставке.
    * `CARGO_UNITS` — ярлыки для грузомест.
  
  * **Дополнительная поставка и непринятые товары**
    * `ADDITIONAL_SUPPLY_ACCEPTABLE_GOODS` — товары, которые подходят для дополнительной поставки.
    * `ADDITIONAL_SUPPLY_UNACCEPTABLE_GOODS` — вывоз непринятых товаров.
  
  * **Маркировка товаров**
    * `INBOUND_UTD` — входящий УПД.
    * `OUTBOUND_UTD` — исходящий УПД.
    * `IDENTIFIERS` — коды маркировки товаров.
    * `CIS_FACT` — принятые товары с кодами маркировки.
    * `ITEMS_WITH_CISES` — товары, для которых нужна маркировка.
    * `REPORT_OF_WITHDRAW_WITH_CISES` — маркированные товары для вывоза со склада.
    * `SECONDARY_ACCEPTANCE_CISES` — маркированные товары, которые приняты после вторичной приемки.
    * `RNPT_FACT` — принятые товары с регистрационным номером партии товара (РНПТ).
  
  * **Акты**
    * `ACT_OF_WITHDRAW` — акт возврата.
    * `ANOMALY_CONTAINERS_WITHDRAW_ACT` — акт изъятия непринятого товара.
    * `ACT_OF_WITHDRAW_FROM_STORAGE` — акт списания с ответственного хранения.
    * `ACT_OF_RECEPTION_TRANSFER` — акт приема-передачи.
    * `ACT_OF_DISCREPANCY` — акт о расхождениях.
    * `SECONDARY_RECEPTION_ACT` — акт вторичной приемки.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `SUPPLY`, `ADDITIONAL_SUPPLY`, `VIRTUAL_DISTRIBUTION_CENTER_SUPPLY`, `TRANSFER`, `INBOUND_UTD`, `OUTBOUND_UTD`, `ADDITIONAL_SUPPLY_ACCEPTABLE_GOODS`, `ADDITIONAL_SUPPLY_UNACCEPTABLE_GOODS`, `VALIDATION_ERRORS`, `WITHDRAW`, `ACT_OF_WITHDRAW`, `ANOMALY_CONTAINERS_WITHDRAW_ACT`, `ACT_OF_WITHDRAW_FROM_STORAGE`, `ACT_OF_RECEPTION_TRANSFER`, `ACT_OF_DISCREPANCY`, `SECONDARY_RECEPTION_ACT`, `CARGO_UNITS`, `IDENTIFIERS`, `CIS_FACT`, `ITEMS_WITH_CISES`, `REPORT_OF_WITHDRAW_WITH_CISES`, `SECONDARY_ACCEPTANCE_CISES`, `RNPT_FACT`
  {.table-cell}
  ||
  ||
  
  _url_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Url](#entity-Url)
  
  Ссылка на документ.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "SUPPLY",
    "url": "example",
    "createdAt": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetSupplyRequestDocumentsDTO {#entity-GetSupplyRequestDocumentsDTO}
  
  Информация о документах по заявке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _documents_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestDocumentDTO](#entity-SupplyRequestDocumentDTO)[]
  
  Список документов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "SUPPLY",
      "url": "example",
      "createdAt": "2025-01-01T00:00:00Z"
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
    "documents": [
      {
        "type": "SUPPLY",
        "url": "example",
        "createdAt": "2025-01-01T00:00:00Z"
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
  pathParams:
    - description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
      name: campaignId
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
      "requestId": 1
    }
  schema:
    type: object
    required:
      - requestId
    properties:
      requestId:
        type: integer
        format: int64
        minimum: 1
        description: >
          Идентификатор заявки.
  
  
          {% note warning "Используется только в API" %}
  
  
          По нему не получится найти заявки в кабинете продавца на Маркете. Для
          этого используйте `marketplaceRequestId` или `warehouseRequestId`.
  
  
          {% endnote %}
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
  path: v2/campaigns/{campaignId}/supply-requests/documents
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/supply-requests/getSupplyRequestDocuments.md -->

[*multisupply]:
О том, что это такое, читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/storage/shipment/application#create).

[*Deprecated]: No longer supported, please use an alternative and newer version.
