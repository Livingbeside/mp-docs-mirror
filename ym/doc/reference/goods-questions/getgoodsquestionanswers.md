---
title: Ответы на вопрос
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md"
fetched_at: "2026-09-11T01:58:56Z"
content_sha: ffd010c0f0e99a1d
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-questions/getGoodsQuestionAnswers.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-questions/getGoodsQuestionAnswers.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-questions/getGoodsQuestionAnswers.md -->
<div class="openapi">

# Получение ответов на вопрос

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getGoodsQuestionAnswers.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getGoodsQuestionAnswers.md -->
  
  Возвращает ответы на вопрос о товаре по указанным фильтрам.
  
  {% note tip "Вы также можете настроить API-уведомления" %}
  
  Маркет отправит вам [запрос](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый ответ или комментарий. А полную информацию о них можно получить с помощью этого метода.
  
  [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)
  
  {% endnote %}
  
  Результаты возвращаются постранично, одна страница содержит не более 50 ответов.
  
  <!-- source: ru/_auto/method_limits/getGoodsQuestionAnswers.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 000 запросов в час<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getGoodsQuestionAnswers.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/goods-questions/answers
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
  
  
  _Default:_{.json-schema-reset .json-schema-value} `25`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `50`
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
    "questionId": 1,
    "answerIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _answerIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [AnswerId](#entity-AnswerId)[] &#124; null
  
  Идентификаторы ответов.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
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
  
  _questionId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [QuestionId](#entity-QuestionId)
  
  Идентификатор вопроса.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionId {#entity-QuestionId}
  
  Идентификатор вопроса.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### AnswerId {#entity-AnswerId}
  
  Идентификатор ответа на вопрос.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список ответов на вопрос.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "answers": [
        {
          "id": 1,
          "text": "example",
          "canModify": true,
          "author": {},
          "status": "PUBLISHED",
          "questionId": 1,
          "createdAt": "2025-01-01T00:00:00Z",
          "votes": {},
          "comments": [
            null
          ]
        }
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
    **Type**: [AnswerListDTO](#entity-AnswerListDTO)
  
    Ответы на вопрос.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "answers": [
        {
          "id": 1,
          "text": "example",
          "canModify": true,
          "author": {
            "type": "USER",
            "name": "example"
          },
          "status": "PUBLISHED",
          "questionId": 1,
          "createdAt": "2025-01-01T00:00:00Z",
          "votes": {
            "likes": 0,
            "dislikes": 0
          },
          "comments": [
            {
              "id": 1,
              "text": null,
              "canModify": true,
              "parentId": null,
              "author": null,
              "status": null,
              "answerId": null,
              "createdAt": "2025-01-01T00:00:00Z",
              "votes": null
            }
          ]
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
        "answers": [
          {
            "id": 1,
            "text": "example",
            "canModify": true,
            "author": {
              "type": "USER",
              "name": "example"
            },
            "status": "PUBLISHED",
            "questionId": 1,
            "createdAt": "2025-01-01T00:00:00Z",
            "votes": {
              "likes": 0,
              "dislikes": 0
            },
            "comments": [
              {}
            ]
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
  
  ### QuestionsTextContent {#entity-QuestionsTextContent}
  
  Текстовое содержимое.
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `5000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionsTextContentAuthorType {#entity-QuestionsTextContentAuthorType}
  
  Тип автора:
  * `USER` — пользователь.
  * `BUSINESS` — кабинет.
  * `VENDOR` — производитель.
  * `BRAND` — бренд.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER`, `BUSINESS`, `VENDOR`, `BRAND`
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionsTextContentAuthorDTO {#entity-QuestionsTextContentAuthorDTO}
  
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
  **Type**: [QuestionsTextContentAuthorType](#entity-QuestionsTextContentAuthorType)
  
  Тип автора:
  * `USER` — пользователь.
  * `BUSINESS` — кабинет.
  * `VENDOR` — производитель.
  * `BRAND` — бренд.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER`, `BUSINESS`, `VENDOR`, `BRAND`
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
  
  ### QuestionsTextContentModerationStatusType {#entity-QuestionsTextContentModerationStatusType}
  
  Статус модерации ответа или комментария:
  * `PUBLISHED` — опубликован.
  * `UNMODERATED` — не проверен.
  * `BANNED` — заблокирован.
  * `DELETED` — удален.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PUBLISHED`, `UNMODERATED`, `BANNED`, `DELETED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### VotesDTO {#entity-VotesDTO}
  
  Количество лайков и дизлайков на вопросе, ответе или комментарии.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dislikes_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество дизлайков.
  {.table-cell}
  ||
  ||
  
  _likes_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество лайков.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "likes": 0,
    "dislikes": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CommentId {#entity-CommentId}
  
  Идентификатор комментария к ответу.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CommentDTO {#entity-CommentDTO}
  
  Комментарий к ответу.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _answerId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [AnswerId](#entity-AnswerId)
  
  Идентификатор ответа на вопрос.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата создания комментария.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CommentId](#entity-CommentId)
  
  Идентификатор комментария к ответу.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionsTextContentModerationStatusType](#entity-QuestionsTextContentModerationStatusType)
  
  Статус модерации ответа или комментария:
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
  **Type**: [QuestionsTextContent](#entity-QuestionsTextContent)
  
  Текстовое содержимое.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `5000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _author_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [QuestionsTextContentAuthorDTO](#entity-QuestionsTextContentAuthorDTO)
  
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
  **Type**: [CommentId](#entity-CommentId)
  
  Идентификатор родительского комментария.
  
  Идентификатор комментария к ответу.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _votes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [VotesDTO](#entity-VotesDTO)
  
  Количество лайков и дизлайков на вопросе, ответе или комментарии.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "likes": 0,
    "dislikes": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "text": "example",
    "canModify": true,
    "parentId": null,
    "author": {
      "type": "USER",
      "name": "example"
    },
    "status": "PUBLISHED",
    "answerId": 1,
    "createdAt": "2025-01-01T00:00:00Z",
    "votes": {
      "likes": 0,
      "dislikes": 0
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### AnswerDTO {#entity-AnswerDTO}
  
  Ответ на вопрос.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _canModify_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Может ли продавец изменять комментарий или удалять его.
  {.table-cell}
  ||
  ||
  
  _createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время создания ответа.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [AnswerId](#entity-AnswerId)
  
  Идентификатор ответа на вопрос.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _questionId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionId](#entity-QuestionId)
  
  Идентификатор вопроса.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionsTextContentModerationStatusType](#entity-QuestionsTextContentModerationStatusType)
  
  Статус модерации ответа или комментария:
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
  **Type**: [QuestionsTextContent](#entity-QuestionsTextContent)
  
  Текстовое содержимое.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `5000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _votes_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [VotesDTO](#entity-VotesDTO)
  
  Количество лайков и дизлайков на вопросе, ответе или комментарии.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "likes": 0,
    "dislikes": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _author_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [QuestionsTextContentAuthorDTO](#entity-QuestionsTextContentAuthorDTO)
  
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
  
  _comments_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CommentDTO](#entity-CommentDTO)[] &#124; null
  
  Список комментариев.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 1,
      "text": "example",
      "canModify": true,
      "parentId": null,
      "author": {
        "type": "USER",
        "name": "example"
      },
      "status": "PUBLISHED",
      "answerId": 1,
      "createdAt": "2025-01-01T00:00:00Z",
      "votes": {
        "likes": 0,
        "dislikes": 0
      }
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
    "id": 1,
    "text": "example",
    "canModify": true,
    "author": {
      "type": "USER",
      "name": "example"
    },
    "status": "PUBLISHED",
    "questionId": 1,
    "createdAt": "2025-01-01T00:00:00Z",
    "votes": {
      "likes": 0,
      "dislikes": 0
    },
    "comments": [
      {
        "id": 1,
        "text": null,
        "canModify": true,
        "parentId": null,
        "author": null,
        "status": null,
        "answerId": null,
        "createdAt": "2025-01-01T00:00:00Z",
        "votes": null
      }
    ]
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
  
  ### AnswerListDTO {#entity-AnswerListDTO}
  
  Ответы на вопрос.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _answers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [AnswerDTO](#entity-AnswerDTO)[]
  
  Список ответов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 1,
      "text": "example",
      "canModify": true,
      "author": {
        "type": "USER",
        "name": "example"
      },
      "status": "PUBLISHED",
      "questionId": 1,
      "createdAt": "2025-01-01T00:00:00Z",
      "votes": {
        "likes": 0,
        "dislikes": 0
      },
      "comments": [
        {
          "id": 1,
          "text": null,
          "canModify": true,
          "parentId": null,
          "author": null,
          "status": null,
          "answerId": null,
          "createdAt": "2025-01-01T00:00:00Z",
          "votes": null
        }
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _paging_{.json-schema-reset .json-schema-property}
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
    "answers": [
      {
        "id": 1,
        "text": "example",
        "canModify": true,
        "author": {
          "type": "USER",
          "name": "example"
        },
        "status": "PUBLISHED",
        "questionId": 1,
        "createdAt": "2025-01-01T00:00:00Z",
        "votes": {
          "likes": 0,
          "dislikes": 0
        },
        "comments": [
          {
            "id": 1,
            "text": null,
            "canModify": true,
            "parentId": null,
            "author": null,
            "status": null,
            "answerId": null,
            "createdAt": "2025-01-01T00:00:00Z",
            "votes": null
          }
        ]
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
        default: 25
        maximum: 50
  headers: []
  body: |-
    {
      "questionId": 1,
      "answerIds": [
        1
      ]
    }
  schema:
    description: |
      Фильтр запроса ответов на вопрос.
    type: object
    properties:
      questionId:
        description: |
          Идентификатор вопроса.
        type: integer
        format: int64
        minimum: 1
      answerIds:
        description: |
          Идентификаторы ответов.
        type: array
        nullable: true
        uniqueItems: true
        minItems: 1
        maxItems: 50
        items:
          description: |
            Идентификатор ответа на вопрос.
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
  path: v1/businesses/{businessId}/goods-questions/answers
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-questions/getGoodsQuestionAnswers.md -->



[*Deprecated]: No longer supported, please use an alternative and newer version.
