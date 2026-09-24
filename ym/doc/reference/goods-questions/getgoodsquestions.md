---
title: Вопросы
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md"
fetched_at: "2026-09-24T02:14:40Z"
content_sha: 5207a294fd001425
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-questions/getGoodsQuestions.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-questions/getGoodsQuestions.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-questions/getGoodsQuestions.md -->
<div class="openapi">

# Получение вопросов о товарах продавца

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getGoodsQuestions.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getGoodsQuestions.md -->
  
  Возвращает вопросы о товарах продавца по указанным фильтрам.
  
  {% note tip "Вы также можете настроить API-уведомления" %}
  
  Маркет отправит вам [запрос](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый вопрос. А полную информацию о нем можно получить с помощью этого метода.
  
  [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)
  
  {% endnote %}
  
  Результаты возвращаются постранично, одна страница содержит не более 50 вопросов.
  
  <!-- source: ru/_auto/method_limits/getGoodsQuestions.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 000 запросов в час<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getGoodsQuestions.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/goods-questions
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
    "categoryIds": [
      0
    ],
    "questionIds": [
      1
    ],
    "dateFrom": "2020-02-02",
    "dateTo": "2020-02-02",
    "needAnswer": false,
    "sort": "CREATED_AT_DESC"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Идентификаторы категорий товаров.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  _dateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата начала периода создания вопроса.
  
  Если параметр не указан, возвращается информация за 1 месяц до указанной в `dateTo` даты.
  
  Максимальный интервал 1 месяц.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата окончания периода создания вопроса.
  
  Если параметр не указан, используется текущая дата.
  
  Максимальный интервал 1 месяц.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02`
  {.table-cell}
  ||
  ||
  
  _needAnswer_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Нужен ли ответ на вопрос.
  
  * `true` — только вопросы, которые ждут ответа.
  * `false` — все вопросы.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `false`
  {.table-cell}
  ||
  ||
  
  _questionIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [QuestionId](#entity-QuestionId)[] &#124; null
  
  Идентификаторы вопросов.
  
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
  
  _sort_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [QuestionSortOrderType](#entity-QuestionSortOrderType)
  
  Порядок сортировки вопросов.
  * `CREATED_AT_DESC` — по дате создания вопроса по убыванию;
  * `CREATED_AT_ASC` — по дате создания вопроса по возрастанию.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED_AT_DESC`, `CREATED_AT_ASC`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  <div class="openapi-entity">
  
  ### QuestionId {#entity-QuestionId}
  
  Идентификатор вопроса.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### QuestionSortOrderType {#entity-QuestionSortOrderType}
  
  Порядок сортировки вопросов.
  * `CREATED_AT_DESC` — по дате создания вопроса по убыванию;
  * `CREATED_AT_ASC` — по дате создания вопроса по возрастанию.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED_AT_DESC`, `CREATED_AT_ASC`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список вопросов.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "questions": [
        {
          "questionIdentifiers": {},
          "businessId": 1,
          "text": "example",
          "createdAt": "2025-01-01T00:00:00Z",
          "votes": {},
          "author": {}
        }
      ],
      "paging": {
        "nextPageToken": "example"
      },
      "totalCount": 0
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
    **Type**: [QuestionListDTO](#entity-QuestionListDTO)
  
    Список вопросов.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "questions": [
        {
          "questionIdentifiers": {
            "id": 1,
            "categoryId": 0,
            "offerId": "example"
          },
          "businessId": 1,
          "text": "example",
          "createdAt": "2025-01-01T00:00:00Z",
          "votes": {
            "likes": 0,
            "dislikes": 0
          },
          "author": {
            "type": "USER",
            "name": "example"
          }
        }
      ],
      "paging": {
        "nextPageToken": "example"
      },
      "totalCount": 0
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
        "questions": [
          {
            "questionIdentifiers": {
              "id": 1,
              "categoryId": 0,
              "offerId": "example"
            },
            "businessId": 1,
            "text": "example",
            "createdAt": "2025-01-01T00:00:00Z",
            "votes": {
              "likes": 0,
              "dislikes": 0
            },
            "author": {
              "type": "USER",
              "name": "example"
            }
          }
        ],
        "paging": {
          "nextPageToken": "example"
        },
        "totalCount": 0
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
  
  ### QuestionIdentifiersDTO {#entity-QuestionIdentifiersDTO}
  
  Идентификаторы вопроса.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionId](#entity-QuestionId)
  
  Идентификатор вопроса.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  Ваш SKU — идентификатор товара в вашей системе.
  
  Правила использования SKU:
  
  * У каждого товара SKU должен быть свой.
  
  * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.
  
  SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).
  
  {% note warning %}
  
  Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.
  
  {% endnote %}
  
  [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _categoryId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор категории.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "categoryId": 0,
    "offerId": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessId {#entity-BusinessId}
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  ### QuestionDTO {#entity-QuestionDTO}
  
  Вопрос.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _author_{.json-schema-reset .json-schema-property .json-schema-required}
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
  
  _createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время создания вопроса.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _questionIdentifiers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionIdentifiersDTO](#entity-QuestionIdentifiersDTO)
  
  Идентификаторы вопроса.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "categoryId": 0,
    "offerId": "example"
  }
  ```
  
  {% endcut %}
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "questionIdentifiers": {
      "id": 1,
      "categoryId": 0,
      "offerId": "example"
    },
    "businessId": 1,
    "text": "example",
    "createdAt": "2025-01-01T00:00:00Z",
    "votes": {
      "likes": 0,
      "dislikes": 0
    },
    "author": {
      "type": "USER",
      "name": "example"
    }
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
  
  ### QuestionListDTO {#entity-QuestionListDTO}
  
  Список вопросов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _questions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [QuestionDTO](#entity-QuestionDTO)[]
  
  Список вопросов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "questionIdentifiers": {
        "id": 1,
        "categoryId": 0,
        "offerId": "example"
      },
      "businessId": 1,
      "text": "example",
      "createdAt": "2025-01-01T00:00:00Z",
      "votes": {
        "likes": 0,
        "dislikes": 0
      },
      "author": {
        "type": "USER",
        "name": "example"
      }
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _totalCount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Общее количество вопросов, которые попадают под фильтр.
  
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
    "questions": [
      {
        "questionIdentifiers": {
          "id": 1,
          "categoryId": 0,
          "offerId": "example"
        },
        "businessId": 1,
        "text": "example",
        "createdAt": "2025-01-01T00:00:00Z",
        "votes": {
          "likes": 0,
          "dislikes": 0
        },
        "author": {
          "type": "USER",
          "name": "example"
        }
      }
    ],
    "paging": {
      "nextPageToken": "example"
    },
    "totalCount": 0
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
      "categoryIds": [
        0
      ],
      "questionIds": [
        1
      ],
      "dateFrom": "2020-02-02",
      "dateTo": "2020-02-02",
      "needAnswer": false,
      "sort": "CREATED_AT_DESC"
    }
  schema:
    type: object
    description: Запрос на получение вопросов о товарах продавца.
    properties:
      offerId:
        x-hidden: true
        $ref: '#/$defs/ShopSku'
      categoryIds:
        type: array
        description: Идентификаторы категорий товаров.
        nullable: true
        uniqueItems: true
        minItems: 1
        items:
          type: integer
          format: int64
          minimum: 0
      questionIds:
        type: array
        description: Идентификаторы вопросов.
        nullable: true
        uniqueItems: true
        minItems: 1
        maxItems: 50
        items:
          description: |
            Идентификатор вопроса.
          type: integer
          format: int64
          minimum: 1
      dateFrom:
        description: >
          Дата начала периода создания вопроса.
  
  
          Если параметр не указан, возвращается информация за 1 месяц до указанной
          в `dateTo` даты.
  
  
          Максимальный интервал 1 месяц.
        type: string
        format: date
        example: '2020-02-02'
      dateTo:
        description: |
          Дата окончания периода создания вопроса.
  
          Если параметр не указан, используется текущая дата.
  
          Максимальный интервал 1 месяц.
        type: string
        format: date
        example: '2020-02-02'
      updatedDateFrom:
        x-hidden: true
        description: |
          Дата и время начала периода обновления вопроса.
  
          Максимальный интервал 1 месяц.
        type: string
        format: date
        example: '2020-02-02'
      updatedDateTo:
        x-hidden: true
        description: >
          Дата и время окончания периода обновления вопроса.
  
  
          Если указан только updatedDateFrom, а updatedDateTo не передан,
          используется текущая дата. Иначе — то что передали.
  
  
          Максимальный интервал 1 месяц.
        type: string
        format: date
        example: '2020-02-02'
      needAnswer:
        description: |
          Нужен ли ответ на вопрос.
  
          * `true` — только вопросы, которые ждут ответа.
          * `false` — все вопросы.
        type: boolean
        default: false
      sort:
        type: string
        description: |
          Порядок сортировки вопросов.
          * `CREATED_AT_DESC` — по дате создания вопроса по убыванию;
          * `CREATED_AT_ASC` — по дате создания вопроса по возрастанию.
        enum:
          - CREATED_AT_DESC
          - CREATED_AT_ASC
    $defs:
      /home/sandbox/.ya/build/build_root/pyur/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/ShopSku:
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
  path: v1/businesses/{businessId}/goods-questions
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-questions/getGoodsQuestions.md -->



[*Deprecated]: No longer supported, please use an alternative and newer version.
