---
title: Добавление/изменение комментария
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md"
fetched_at: "2026-09-11T01:58:54Z"
content_sha: 410d847471ae876c
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-feedback/updateGoodsFeedbackComment.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-feedback/updateGoodsFeedbackComment.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-feedback/updateGoodsFeedbackComment.md -->
<div class="openapi">

# Добавление нового или изменение созданного комментария

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateGoodsFeedbackComment.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateGoodsFeedbackComment.md -->
  
  Добавляет новый комментарий магазина или изменяет комментарий, который магазин оставлял ранее.
  
  Для создания комментария к отзыву передайте только идентификатор отзыва `feedbackId`.
  
  Чтобы добавить комментарий к другому комментарию, передайте:
  
  * `feedbackId` — идентификатор отзыва;
  * `comment.parentId` — идентификатор родительского комментария.
  
  Чтобы изменить комментарий, передайте:
  
  * `feedbackId`— идентификатор отзыва;
  * `comment.id` — идентификатор комментария, который нужно изменить.
  
  Если передать одновременно `comment.parentId` и `comment.id`, будет изменен существующий комментарий.
  
  <!-- source: ru/_auto/method_limits/updateGoodsFeedbackComment.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateGoodsFeedbackComment.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/goods-feedback/comments/update
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
    "feedbackId": 0,
    "comment": {
      "id": 0,
      "parentId": 0,
      "text": "example"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateGoodsFeedbackCommentDTO](#entity-UpdateGoodsFeedbackCommentDTO)
  
  Параметры комментария.
  
  Комментарий к отзыву или другому комментарию.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "parentId": 0,
    "text": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _feedbackId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackId](#entity-GoodsFeedbackId)
  
  Идентификатор отзыва.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackId {#entity-GoodsFeedbackId}
  
  Идентификатор отзыва.
  
  
  **Type**: integer
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackCommentId {#entity-GoodsFeedbackCommentId}
  
  Идентификатор комментария к отзыву.
  
  
  **Type**: integer
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackCommentText {#entity-GoodsFeedbackCommentText}
  
  Текст комментария.
  
  Не должен содержать контакты магазина и ссылки на сайты, кроме Маркета.
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `4096`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateGoodsFeedbackCommentDTO {#entity-UpdateGoodsFeedbackCommentDTO}
  
  Комментарий к отзыву или другому комментарию.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _text_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentText](#entity-GoodsFeedbackCommentText)
  
  Текст комментария.
  
  Не должен содержать контакты магазина и ссылки на сайты, кроме Маркета.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `4096`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentId](#entity-GoodsFeedbackCommentId)
  
  Идентификатор комментария, который нужно изменить.
  
  Оставьте поле пустым, если хотите добавить новый комментарий.
  
  
  Идентификатор комментария к отзыву.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _parentId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор родительского комментария, на который нужно ответить.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "parentId": 0,
    "text": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о добавленном или измененном комментарии.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "id": 0,
      "text": "example",
      "canModify": true,
      "parentId": 0,
      "author": {
        "type": "USER",
        "name": "example"
      },
      "status": "PUBLISHED",
      "feedbackId": 0
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
    **Type**: [GoodsFeedbackCommentDTO](#entity-GoodsFeedbackCommentDTO)
  
    Комментарий к отзыву.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 0,
      "text": "example",
      "canModify": true,
      "parentId": 0,
      "author": {
        "type": "USER",
        "name": "example"
      },
      "status": "PUBLISHED",
      "feedbackId": 0
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
        "id": 0,
        "text": "example",
        "canModify": true,
        "parentId": 0,
        "author": {
          "type": "USER",
          "name": "example"
        },
        "status": "PUBLISHED",
        "feedbackId": 0
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
  
  ### GoodsFeedbackCommentAuthorType {#entity-GoodsFeedbackCommentAuthorType}
  
  Тип автора:
  
  * `USER` — пользователь.
  * `BUSINESS` — кабинет.
  * `BRAND` — бренд.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER`, `BUSINESS`, `BRAND`
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackCommentAuthorDTO {#entity-GoodsFeedbackCommentAuthorDTO}
  
  Информация об авторе комментария.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Имя автора или название кабинета.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentAuthorType](#entity-GoodsFeedbackCommentAuthorType)
  
  Тип автора:
  
  * `USER` — пользователь.
  * `BUSINESS` — кабинет.
  * `BRAND` — бренд.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER`, `BUSINESS`, `BRAND`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "USER",
    "name": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackCommentStatusType {#entity-GoodsFeedbackCommentStatusType}
  
  Статус комментария:
  
  * `PUBLISHED` — опубликован.
  * `UNMODERATED` — не проверен.
  * `BANNED` — заблокирован.
  * `DELETED` — удален.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PUBLISHED`, `UNMODERATED`, `BANNED`, `DELETED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackCommentDTO {#entity-GoodsFeedbackCommentDTO}
  
  Комментарий к отзыву.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _feedbackId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackId](#entity-GoodsFeedbackId)
  
  Идентификатор отзыва.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentId](#entity-GoodsFeedbackCommentId)
  
  Идентификатор комментария к отзыву.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentStatusType](#entity-GoodsFeedbackCommentStatusType)
  
  Статус комментария:
  
  * `PUBLISHED` — опубликован.
  * `UNMODERATED` — не проверен.
  * `BANNED` — заблокирован.
  * `DELETED` — удален.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PUBLISHED`, `UNMODERATED`, `BANNED`, `DELETED`
  {.table-cell}
  ||
  ||
  
  _text_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentText](#entity-GoodsFeedbackCommentText)
  
  Текст комментария.
  
  Не должен содержать контакты магазина и ссылки на сайты, кроме Маркета.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `4096`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _author_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsFeedbackCommentAuthorDTO](#entity-GoodsFeedbackCommentAuthorDTO)
  
  Информация об авторе комментария.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "USER",
    "name": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _canModify_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Может ли продавец изменять комментарий или удалять его.
  {.table-cell}
  ||
  ||
  
  _parentId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор родительского комментария.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "text": "example",
    "canModify": true,
    "parentId": 0,
    "author": {
      "type": "USER",
      "name": "example"
    },
    "status": "PUBLISHED",
    "feedbackId": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с отзывами о товарах](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#feedback)
  
  
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
  searchParams:
    - name: sourceType
      in: query
      required: false
      description: "Признак типа кабинета, от имени которого вызывается метод:\n{% if audience == \"partner\" %}\n\n- `SELLER` — продавец.\n\n{% endif %}\n\n- `ADVERTISER` — рекламодатель.\n\n{% if audience == \"advertiser\" %}\n\n{% note info \"Обязательно указывайте sourceType=ADVERTISER в каждом запросе.\" %}\n\n\_\n\n{% endnote %}\n\n{% endif %}\n"
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/givs/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/SourceType
        default: SELLER
  headers: []
  body: |-
    {
      "feedbackId": 0,
      "comment": {
        "id": 0,
        "parentId": 0,
        "text": "example"
      }
    }
  schema:
    description: Комментарий к отзыву.
    type: object
    required:
      - feedbackId
      - comment
    properties:
      feedbackId:
        description: |
          Идентификатор отзыва.
        type: integer
        format: int64
      comment:
        description: Параметры комментария.
        $ref: '#/$defs/UpdateGoodsFeedbackCommentDTO'
    $defs:
      /home/sandbox/.ya/build/build_root/givs/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/GoodsFeedbackCommentId:
        description: |
          Идентификатор комментария к отзыву.
        type: integer
        format: int64
      /home/sandbox/.ya/build/build_root/givs/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/goods-feedback/api/updateGoodsFeedbackComment.yaml#/UpdateGoodsFeedbackCommentDTO:
        description: Комментарий к отзыву или другому комментарию.
        type: object
        required:
          - text
        properties:
          id:
            description: |
              Идентификатор комментария, который нужно изменить.
  
              Оставьте поле пустым, если хотите добавить новый комментарий.
            $ref: '#/$defs/GoodsFeedbackCommentId'
          parentId:
            description: Идентификатор родительского комментария, на который нужно ответить.
            type: integer
            format: int64
          text:
            description: >
              Текст комментария.
  
  
              Не должен содержать контакты магазина и ссылки на сайты, кроме
              Маркета.
            type: string
            minLength: 1
            maxLength: 4096
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
  path: v2/businesses/{businessId}/goods-feedback/comments/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-feedback/updateGoodsFeedbackComment.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
