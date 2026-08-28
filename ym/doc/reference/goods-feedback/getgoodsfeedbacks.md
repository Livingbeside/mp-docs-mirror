---
title: Отзывы на товары продавца
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md"
fetched_at: "2026-08-28T11:53:03Z"
content_sha: 225f77c6638bb71b
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-feedback/getGoodsFeedbacks.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-feedback/getGoodsFeedbacks.md
  - href: ru/reference/goods-feedback/getGoodsFeedbacks.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-feedback/getGoodsFeedbacks.md -->
<div class="openapi">

# Получение отзывов о товарах продавца

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getGoodsFeedbacks.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getGoodsFeedbacks.md -->
  
  Возвращает отзывы о товарах продавца по указанным фильтрам. **Исключение:** отзывы, которые удалили покупатели или Маркет.
  
  {% note tip "Вы также можете настроить API-уведомления" %}
  
  Маркет отправит вам [запрос](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый отзыв. А полную информацию о нем можно получить с помощью этого метода.
  
  [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)
  
  {% endnote %}
  
  Результаты возвращаются постранично.
  
  Отзывы расположены в порядке публикации, поэтому вы можете передавать определенный идентификатор страницы в `pageToken`, если вы получали его ранее.
  
  <!-- source: ru/_auto/method_limits/getGoodsFeedbacks.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 5 000 запросов в час<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getGoodsFeedbacks.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/goods-feedback
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
    "feedbackIds": [
      0
    ],
    "dateTimeFrom": "2020-02-02T14:30:30+03:00",
    "dateTimeTo": "2020-02-02T14:30:30+03:00",
    "reactionStatus": "ALL",
    "ratingValues": [
      0
    ],
    "offerIds": [
      "example"
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
  
  _offerIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)[] &#124; null
  
  Фильтр по идентификатору товара.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `20`
  
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
          "identifiers": {},
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
    **Type**: [GoodsFeedbackListDTO](#entity-GoodsFeedbackListDTO)
  
    Список отзывов о товарах.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "feedbacks": [
        {
          "feedbackId": 0,
          "createdAt": "2025-01-01T00:00:00Z",
          "needReaction": true,
          "identifiers": {
            "orderId": 0,
            "offerId": "example"
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
            "identifiers": {
              "orderId": 0,
              "offerId": "example"
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
  
  ### GoodsFeedbackIdentifiersDTO {#entity-GoodsFeedbackIdentifiersDTO}
  
  Идентификаторы, которые связаны с отзывом.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  Идентификатор товара.
  
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
  
  _orderId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа на Маркете.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "orderId": 0,
    "offerId": "example"
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
  
  ### GoodsFeedbackDTO {#entity-GoodsFeedbackDTO}
  
  Отзыв о товаре.
  
  #|
  || **Name** | **Description** ||
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
  
  _identifiers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackIdentifiersDTO](#entity-GoodsFeedbackIdentifiersDTO)
  
  Идентификаторы, которые связаны с отзывом.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "orderId": 0,
    "offerId": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _needReaction_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Прочитан ли отзыв.
  
  Принимает значение `false`, если магазин:
  
  * Прочитал отзыв в кабинете продавца на Маркете.
  * Отметил отзыв прочитанным — метод [POST v2/businesses/{businessId}/goods-feedback/skip-reaction](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/skipGoodsFeedbacksReaction.md).
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
    "identifiers": {
      "orderId": 0,
      "offerId": "example"
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
  
  ### GoodsFeedbackListDTO {#entity-GoodsFeedbackListDTO}
  
  Список отзывов о товарах.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _feedbacks_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsFeedbackDTO](#entity-GoodsFeedbackDTO)[]
  
  Список отзывов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "feedbackId": 0,
      "createdAt": "2025-01-01T00:00:00Z",
      "needReaction": true,
      "identifiers": {
        "orderId": 0,
        "offerId": "example"
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
        "identifiers": {
          "orderId": 0,
          "offerId": "example"
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
      "offerIds": [
        "example"
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
      updatedDateFrom:
        x-hidden: true
        description: |
          Дата и время начала периода обновления вопроса.
  
          Максимальный интервал 1 месяц.
        type: string
        format: date-time
        example: '2020-02-02T14:30:30+03:00'
      updatedDateTo:
        x-hidden: true
        description: >
          Дата и время окончания периода обновления вопроса.
  
  
          Если указан только updatedDateFrom, а updatedDateTo не передан,
          используется текущая дата. Иначе — то что передали.
  
  
          Максимальный интервал 1 месяц.
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
      modelIds:
        description: "{% note warning \"Параметр устарел и будет отключен 19.10.2026.\" %}\n\n\_\n\n{% endnote %}\n\nФильтр по идентификатору модели товара.\n\nПолучить идентификатор модели можно с помощью одного из запросов:\n\n* [POST\_v2/businesses/{businessId}/offer-mappings](../../reference/business-offer-mappings/getOfferMappings.md);\n\n* [POST\_v2/businesses/{businessId}/offer-cards](../../reference/content/getOfferCardsContentStatus.md).\n"
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-19'
        x-hidden: true
        type: array
        uniqueItems: true
        maxItems: 20
        nullable: true
        minItems: 1
        items:
          type: integer
          format: int64
      offerIds:
        description: |
          Фильтр по идентификатору товара.
        type: array
        uniqueItems: true
        maxItems: 20
        nullable: true
        minItems: 1
        items:
          description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
          type: string
          pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
          x-transform: trim
          minLength: 1
          maxLength: 255
      paid:
        description: Фильтр отзывов за баллы Плюса.
        type: boolean
    $defs:
      /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/goods-feedback/schemas.yaml#/FeedbackReactionStatusType:
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
  path: v2/businesses/{businessId}/goods-feedback
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-feedback/getGoodsFeedbacks.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
