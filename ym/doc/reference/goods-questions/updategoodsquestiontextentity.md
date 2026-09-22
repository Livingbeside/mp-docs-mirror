---
title: Создание, изменение и удаление ответа или комментария
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md"
fetched_at: "2026-09-22T02:27:49Z"
content_sha: aaf921a5a4224c0a
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-questions/updateGoodsQuestionTextEntity.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-questions/updateGoodsQuestionTextEntity.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-questions/updateGoodsQuestionTextEntity.md -->
<div class="openapi">

# Создание, изменение и удаление ответа или комментария

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateGoodsQuestionTextEntity.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateGoodsQuestionTextEntity.md -->
  
  Создание, изменение и удаление ответа или комментария.
  
  <!-- source: ru/_auto/method_limits/updateGoodsQuestionTextEntity.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 500 запросов в час<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateGoodsQuestionTextEntity.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/goods-questions/update
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
    "entityId": {
      "id": 1,
      "type": "QUESTION"
    },
    "parentEntityId": null,
    "text": "example",
    "operationType": "UPDATE"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _operationType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionsTextEntityOperationType](#entity-QuestionsTextEntityOperationType)
  
  Операция над ответом или комментарием.
  * `UPDATE` — обновление.
  * `CREATE` — создание.
  * `DELETE` — удаление.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UPDATE`, `CREATE`, `DELETE`
  {.table-cell}
  ||
  ||
  
  _entityId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TypedQuestionsTextEntityIdDTO](#entity-TypedQuestionsTextEntityIdDTO)
  
  Идентификатор обновляемого или удаляемого ответа или комментария.
  
  Обязателен для операций `UPDATE` и `DELETE`.
  
  
  Идентификатор вопроса, ответа или комментария.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "type": "QUESTION"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _parentEntityId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TypedQuestionsTextEntityIdDTO](#entity-TypedQuestionsTextEntityIdDTO)
  
  Идентификатор родительского вопроса или ответа.
  
  Обязателен для операции `CREATE`. Используется для создания ответа или комментария:
  * При создании ответа — указывайте идентификатор вопроса.
  * При создании комментария к ответу — указывайте идентификатор ответа.
  
  
  Идентификатор вопроса, ответа или комментария.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "type": "QUESTION"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _text_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [QuestionsTextContent](#entity-QuestionsTextContent)
  
  Текст ответа или комментария.
  
  Обязателен для операций `CREATE` и `UPDATE`. Не требуется для операции `DELETE`.
  
  
  Текстовое содержимое.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `5000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionsTextEntityType {#entity-QuestionsTextEntityType}
  
  Тип сущности:
  
  * `QUESTION` — вопрос о товаре.
  * `ANSWER` — ответ на вопрос.
  * `COMMENT` — комментарий к ответу.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `QUESTION`, `ANSWER`, `COMMENT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### TypedQuestionsTextEntityIdDTO {#entity-TypedQuestionsTextEntityIdDTO}
  
  Идентификатор вопроса, ответа или комментария.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор вопроса, ответа или комментария.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionsTextEntityType](#entity-QuestionsTextEntityType)
  
  Тип сущности (вопрос, ответ или комментарий).
  
  Тип сущности:
  
  * `QUESTION` — вопрос о товаре.
  * `ANSWER` — ответ на вопрос.
  * `COMMENT` — комментарий к ответу.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `QUESTION`, `ANSWER`, `COMMENT`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "type": "QUESTION"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionsTextContent {#entity-QuestionsTextContent}
  
  Текстовое содержимое.
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `5000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionsTextEntityOperationType {#entity-QuestionsTextEntityOperationType}
  
  Операция над ответом или комментарием.
  * `UPDATE` — обновление.
  * `CREATE` — создание.
  * `DELETE` — удаление.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UPDATE`, `CREATE`, `DELETE`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о созданном ответе или комментарии.
  
  Возвращается только при операции создания (`operationType` = `CREATE`). При обновлении и удалении возвращается пустой ответ.
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "entity": {
        "id": 1,
        "type": "QUESTION"
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
    **Type**: [UpdateGoodsQuestionTextEntityDTO](#entity-UpdateGoodsQuestionTextEntityDTO)
  
    Информация о созданном ответе или комментария.
  
    Возвращается только для запроса создания.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "entity": {
        "id": 1,
        "type": "QUESTION"
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
        "entity": {
          "id": 1,
          "type": "QUESTION"
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
  
  ### UpdateGoodsQuestionTextEntityDTO {#entity-UpdateGoodsQuestionTextEntityDTO}
  
  Информация о созданном ответе или комментария.
  
  Возвращается только для запроса создания.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _entity_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TypedQuestionsTextEntityIdDTO](#entity-TypedQuestionsTextEntityIdDTO)
  
  Идентификатор вопроса, ответа или комментария.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "type": "QUESTION"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "entity": {
      "id": 1,
      "type": "QUESTION"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#questions)
  
  
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
      "entityId": {
        "id": 1,
        "type": "QUESTION"
      },
      "parentEntityId": null,
      "text": "example",
      "operationType": "UPDATE"
    }
  schema:
    type: object
    required:
      - operationType
    description: |
      Запрос на создание, обновление или удаление вопроса, ответа или комментария.
  
      **Параметры для разных операций:**
  
      * `CREATE` — создание ответа или комментария:
        * Обязательно: `operationType`, `parentEntityId`, `text`.
        * `parentEntityId` — идентификатор родителя (для ответа — вопроса, для комментария — ответа).
  
      * `UPDATE` — обновление ответа или комментария:
        * Обязательно: `operationType`, `entityId`, `text`.
        * `entityId` — идентификатор ответа или комментария.
  
      * `DELETE` — удаление ответа или комментария:
        * Обязательно: `operationType`, `entityId`.
        * `text` не требуется.
    properties:
      entityId:
        description: |
          Идентификатор обновляемого или удаляемого ответа или комментария.
  
          Обязателен для операций `UPDATE` и `DELETE`.
        $ref: '#/$defs/TypedQuestionsTextEntityIdDTO'
      parentEntityId:
        description: >
          Идентификатор родительского вопроса или ответа.
  
  
          Обязателен для операции `CREATE`. Используется для создания ответа или
          комментария:
  
          * При создании ответа — указывайте идентификатор вопроса.
  
          * При создании комментария к ответу — указывайте идентификатор ответа.
        $ref: '#/$defs/TypedQuestionsTextEntityIdDTO'
      text:
        description: >
          Текст ответа или комментария.
  
  
          Обязателен для операций `CREATE` и `UPDATE`. Не требуется для операции
          `DELETE`.
        $ref: '#/$defs/QuestionsTextContent'
      operationType:
        description: |
          Операция над ответом или комментарием.
          * `UPDATE` — обновление.
          * `CREATE` — создание.
          * `DELETE` — удаление.
        type: string
        enum:
          - UPDATE
          - CREATE
          - DELETE
    $defs:
      /home/sandbox/.ya/build/build_root/jc95/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/goods-questions/api/updateGoodsQuestionTextEntity.yaml#/QuestionsTextEntityType:
        description: |
          Тип сущности:
  
          * `QUESTION` — вопрос о товаре.
          * `ANSWER` — ответ на вопрос.
          * `COMMENT` — комментарий к ответу.
        type: string
        enum:
          - QUESTION
          - ANSWER
          - COMMENT
      /home/sandbox/.ya/build/build_root/jc95/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/goods-questions/api/updateGoodsQuestionTextEntity.yaml#/TypedQuestionsTextEntityIdDTO:
        type: object
        description: |
          Идентификатор вопроса, ответа или комментария.
        required:
          - id
          - type
        properties:
          id:
            description: Идентификатор вопроса, ответа или комментария.
            type: integer
            format: int64
            minimum: 1
          type:
            description: Тип сущности (вопрос, ответ или комментарий).
            $ref: '#/$defs/QuestionsTextEntityType'
      /home/sandbox/.ya/build/build_root/jc95/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/goods-questions/schemas.yaml#/QuestionsTextContent:
        description: |
          Текстовое содержимое.
        type: string
        minLength: 1
        maxLength: 5000
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
  path: v1/businesses/{businessId}/goods-questions/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-questions/updateGoodsQuestionTextEntity.md -->



[*Deprecated]: No longer supported, please use an alternative and newer version.
