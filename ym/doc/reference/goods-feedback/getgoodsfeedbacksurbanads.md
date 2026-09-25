---
title: Отзывы на товары бренда
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacksUrbanads.md"
fetched_at: "2026-09-25T02:18:00Z"
content_sha: 67756e43c7dc6a8a
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-feedback/getGoodsFeedbacksUrbanads.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacksUrbanads.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-feedback/getGoodsFeedbacksUrbanads.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacksUrbanads.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-feedback/getGoodsFeedbacksUrbanads.md -->
<div class="openapi">

# Получение отзывов о товарах для рекламодателей

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getGoodsFeedbacksUrbanads.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getGoodsFeedbacksUrbanads.md -->
  
  Возвращает отзывы о товарах бренда по указанным фильтрам. **Исключение:** отзывы, которые удалили покупатели или Маркет.
  
  Результаты возвращаются постранично.
  
  Отзывы расположены в порядке публикации, поэтому вы можете передавать определенный идентификатор страницы в `pageToken`, если вы получали его ранее.
  
  <!-- source: ru/_auto/method_limits/getGoodsFeedbacksUrbanads.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getGoodsFeedbacksUrbanads.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/goods-feedback-advertiser
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
    "feedbackIds": [
      0
    ],
    "dateTimeFrom": "2020-02-02T14:30:30+03:00",
    "dateTimeTo": "2020-02-02T14:30:30+03:00",
    "reactionStatus": "ALL",
    "ratingValues": [
      0
    ],
    "paid": true
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dateTimeFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Начало периода. Не включительно.
  
  Если параметр не указан, возвращается информация за 6 месяцев до указанной в `dateTimeTo` даты.
  
  Максимальный интервал 6 месяцев.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  ||
  
  _dateTimeTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Конец периода. Не включительно.
  
  Если параметр не указан, используется текущая дата.
  
  Максимальный интервал 6 месяцев.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  ||
  
  _feedbackIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsFeedbackId](#entity-GoodsFeedbackId)[] &#124; null
  
  Идентификаторы отзывов.
  
  ⚠️ Не используйте это поле одновременно с другими фильтрами. Если вы хотите воспользоваться ими, оставьте поле пустым.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
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
  
  _paid_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Фильтр отзывов за баллы Плюса.
  {.table-cell}
  ||
  ||
  
  _ratingValues_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Оценка товара.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `5`
  
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
  
  _reactionStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [FeedbackReactionStatusType](#entity-FeedbackReactionStatusType)
  
  Нужно ли вернуть только непрочитанные отзывы. Для этого передайте значение `NEED_REACTION`.
  
  По умолчанию возвращаются все отзывы.
  
  
  Статус реакции на отзыв:
  
  * `ALL` — все отзывы.
  
  * `NEED_REACTION` — отзывы, на которые нужно ответить.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ALL`, `NEED_REACTION`
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
  
  ### FeedbackReactionStatusType {#entity-FeedbackReactionStatusType}
  
  Статус реакции на отзыв:
  
  * `ALL` — все отзывы.
  
  * `NEED_REACTION` — отзывы, на которые нужно ответить.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ALL`, `NEED_REACTION`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список отзывов.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "feedbacks": [
        {
          "feedbackId": 0,
          "createdAt": "2025-01-01T00:00:00Z",
          "needReaction": true,
          "context": {},
          "author": "example",
          "description": {},
          "media": {},
          "statistics": {}
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
    **Type**: [GoodsFeedbackUrbanadsListDTO](#entity-GoodsFeedbackUrbanadsListDTO)
  
    Список отзывов о товарах.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "feedbacks": [
        {
          "feedbackId": 0,
          "createdAt": "2025-01-01T00:00:00Z",
          "needReaction": true,
          "context": {
            "offerName": "example",
            "pictureUrl": "example",
            "businessId": 1,
            "businessName": "example",
            "brandId": "example",
            "brandName": "example"
          },
          "author": "example",
          "description": {
            "advantages": "example",
            "disadvantages": "example",
            "comment": "example"
          },
          "media": {
            "photos": [
              "example"
            ],
            "videos": [
              "example"
            ]
          },
          "statistics": {
            "rating": 1,
            "commentsCount": 0,
            "recommended": true,
            "paidAmount": 0
          }
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
        "feedbacks": [
          {
            "feedbackId": 0,
            "createdAt": "2025-01-01T00:00:00Z",
            "needReaction": true,
            "context": {
              "offerName": "example",
              "pictureUrl": "example",
              "businessId": 1,
              "businessName": "example",
              "brandId": "example",
              "brandName": "example"
            },
            "author": "example",
            "description": {
              "advantages": "example",
              "disadvantages": "example",
              "comment": "example"
            },
            "media": {
              "photos": [
                null
              ],
              "videos": [
                null
              ]
            },
            "statistics": {
              "rating": 1,
              "commentsCount": 0,
              "recommended": true,
              "paidAmount": 0
            }
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
  
  ### Url {#entity-Url}
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessId {#entity-BusinessId}
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackContextUrbanadsDTO {#entity-GoodsFeedbackContextUrbanadsDTO}
  
  Информация о товаре, бизнесе и бренде, которые связаны с отзывом.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _brandId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор бренда товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _brandName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название бренда товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessId](#entity-BusinessId)
  
  Идентификатор бизнеса, под товаром которого оставлен отзыв.
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _businessName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название бизнеса, под товаром которого оставлен отзыв.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _offerName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название товара, под которым оставлен отзыв.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _pictureUrl_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)
  
  Ссылка на фотографию товара.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerName": "example",
    "pictureUrl": "example",
    "businessId": 1,
    "businessName": "example",
    "brandId": "example",
    "brandName": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackDescriptionDTO {#entity-GoodsFeedbackDescriptionDTO}
  
  Текстовая часть отзыва.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _advantages_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание плюсов товара в отзыве.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий в отзыве.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _disadvantages_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание минусов товара в отзыве.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "advantages": "example",
    "disadvantages": "example",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackMediaDTO {#entity-GoodsFeedbackMediaDTO}
  
  Фотографии и видео.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _photos_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Ссылки на фотографии.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  _videos_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Ссылки на видео.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "photos": [
      "example"
    ],
    "videos": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackStatisticsDTO {#entity-GoodsFeedbackStatisticsDTO}
  
  Статистическая информация по отзыву.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _commentsCount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество комментариев к отзыву.
  
  Учитываются только ответы на отзывы, а не дочерние комментарии.
  
  {.table-cell}
  ||
  ||
  
  _rating_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Оценка товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `5`
  {.table-cell}
  ||
  ||
  
  _paidAmount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество баллов Плюса, которое автор получил за отзыв.
  {.table-cell}
  ||
  ||
  
  _recommended_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Рекомендуют ли этот товар.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "rating": 1,
    "commentsCount": 0,
    "recommended": true,
    "paidAmount": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsFeedbackUrbanadsDTO {#entity-GoodsFeedbackUrbanadsDTO}
  
  Отзыв о товаре.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _context_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackContextUrbanadsDTO](#entity-GoodsFeedbackContextUrbanadsDTO)
  
  Информация о товаре, бизнесе и бренде, которые связаны с отзывом.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerName": "example",
    "pictureUrl": "example",
    "businessId": 1,
    "businessName": "example",
    "brandId": "example",
    "brandName": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время создания отзыва.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
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
  ||
  
  _needReaction_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Прочитан ли отзыв.
  
  Принимает значение `false`, если рекламодатель:
  
  * Прочитал отзыв в кабинете UrbanAds.
  * Пропустил реакцию на отзыв — метод [POST v2/businesses/{businessId}/goods-feedback/skip-reaction](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/skipGoodsFeedbacksReaction.md).
  * Оставил комментарий к отзыву — метод [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md).
  
  {.table-cell}
  ||
  ||
  
  _statistics_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackStatisticsDTO](#entity-GoodsFeedbackStatisticsDTO)
  
  Статистическая информация по отзыву.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "rating": 1,
    "commentsCount": 0,
    "recommended": true,
    "paidAmount": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _author_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Имя автора отзыва.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _description_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsFeedbackDescriptionDTO](#entity-GoodsFeedbackDescriptionDTO)
  
  Текстовая часть отзыва.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "advantages": "example",
    "disadvantages": "example",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _media_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsFeedbackMediaDTO](#entity-GoodsFeedbackMediaDTO)
  
  Фотографии и видео.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "photos": [
      "example"
    ],
    "videos": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "feedbackId": 0,
    "createdAt": "2025-01-01T00:00:00Z",
    "needReaction": true,
    "context": {
      "offerName": "example",
      "pictureUrl": "example",
      "businessId": 1,
      "businessName": "example",
      "brandId": "example",
      "brandName": "example"
    },
    "author": "example",
    "description": {
      "advantages": "example",
      "disadvantages": "example",
      "comment": "example"
    },
    "media": {
      "photos": [
        "example"
      ],
      "videos": [
        "example"
      ]
    },
    "statistics": {
      "rating": 1,
      "commentsCount": 0,
      "recommended": true,
      "paidAmount": 0
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
  
  ### GoodsFeedbackUrbanadsListDTO {#entity-GoodsFeedbackUrbanadsListDTO}
  
  Список отзывов о товарах.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _feedbacks_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackUrbanadsDTO](#entity-GoodsFeedbackUrbanadsDTO)[]
  
  Список отзывов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "feedbackId": 0,
      "createdAt": "2025-01-01T00:00:00Z",
      "needReaction": true,
      "context": {
        "offerName": "example",
        "pictureUrl": "example",
        "businessId": 1,
        "businessName": "example",
        "brandId": "example",
        "brandName": "example"
      },
      "author": "example",
      "description": {
        "advantages": "example",
        "disadvantages": "example",
        "comment": "example"
      },
      "media": {
        "photos": [
          "example"
        ],
        "videos": [
          "example"
        ]
      },
      "statistics": {
        "rating": 1,
        "commentsCount": 0,
        "recommended": true,
        "paidAmount": 0
      }
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
    "feedbacks": [
      {
        "feedbackId": 0,
        "createdAt": "2025-01-01T00:00:00Z",
        "needReaction": true,
        "context": {
          "offerName": "example",
          "pictureUrl": "example",
          "businessId": 1,
          "businessName": "example",
          "brandId": "example",
          "brandName": "example"
        },
        "author": "example",
        "description": {
          "advantages": "example",
          "disadvantages": "example",
          "comment": "example"
        },
        "media": {
          "photos": [
            "example"
          ],
          "videos": [
            "example"
          ]
        },
        "statistics": {
          "rating": 1,
          "commentsCount": 0,
          "recommended": true,
          "paidAmount": 0
        }
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
    - name: sourceType
      in: query
      required: false
      description: "Признак типа кабинета, от имени которого вызывается метод:\n{% if audience == \"partner\" %}\n\n- `SELLER` — продавец.\n\n{% endif %}\n\n- `ADVERTISER` — рекламодатель.\n\n{% if audience == \"advertiser\" %}\n\n{% note info \"Обязательно указывайте sourceType=ADVERTISER в каждом запросе.\" %}\n\n\_\n\n{% endnote %}\n\n{% endif %}\n"
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/fti6/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/SourceType
        default: SELLER
  headers: []
  body: |-
    {
      "feedbackIds": [
        0
      ],
      "dateTimeFrom": "2020-02-02T14:30:30+03:00",
      "dateTimeTo": "2020-02-02T14:30:30+03:00",
      "reactionStatus": "ALL",
      "ratingValues": [
        0
      ],
      "paid": true
    }
  schema:
    description: |
      Фильтр запроса отзывов в кабинете.
    type: object
    properties:
      feedbackIds:
        description: >
          Идентификаторы отзывов.
  
  
          ⚠️ Не используйте это поле одновременно с другими фильтрами. Если вы
          хотите воспользоваться ими, оставьте поле пустым.
        type: array
        nullable: true
        uniqueItems: true
        minItems: 1
        maxItems: 50
        items:
          description: |
            Идентификатор отзыва.
          type: integer
          format: int64
      dateTimeFrom:
        description: >
          Начало периода. Не включительно.
  
  
          Если параметр не указан, возвращается информация за 6 месяцев до
          указанной в `dateTimeTo` даты.
  
  
          Максимальный интервал 6 месяцев.
        type: string
        format: date-time
        example: '2020-02-02T14:30:30+03:00'
      dateTimeTo:
        description: |
          Конец периода. Не включительно.
  
          Если параметр не указан, используется текущая дата.
  
          Максимальный интервал 6 месяцев.
        type: string
        format: date-time
        example: '2020-02-02T14:30:30+03:00'
      reactionStatus:
        description: >
          Нужно ли вернуть только непрочитанные отзывы. Для этого передайте
          значение `NEED_REACTION`.
  
  
          По умолчанию возвращаются все отзывы.
        $ref: '#/$defs/FeedbackReactionStatusType'
      ratingValues:
        description: Оценка товара.
        type: array
        uniqueItems: true
        maxItems: 5
        nullable: true
        minItems: 1
        items:
          type: integer
          format: int32
      paid:
        description: Фильтр отзывов за баллы Плюса.
        type: boolean
    $defs:
      /home/sandbox/.ya/build/build_root/fti6/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/goods-feedback/schemas.yaml#/FeedbackReactionStatusType:
        description: |
          Статус реакции на отзыв:
  
          * `ALL` — все отзывы.
  
          * `NEED_REACTION` — отзывы, на которые нужно ответить.
        type: string
        enum:
          - ALL
          - NEED_REACTION
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
  path: v1/businesses/{businessId}/goods-feedback-advertiser
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-feedback/getGoodsFeedbacksUrbanads.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
