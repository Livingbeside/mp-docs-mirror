---
title: Получение списка чатов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md"
fetched_at: "2026-08-28T11:53:12Z"
content_sha: 5541de73bfc6e2d0
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/chats/getChats.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/chats/getChats.md
  - href: ru/reference/chats/getChats.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/chats/getChats.md -->
<div class="openapi">

# Получение доступных чатов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getChats.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getChats.md -->
  
  Возвращает чаты с покупателями.
  
  {% note tip "Подключите API-уведомления" %}
  
  Маркет отправит вам запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый чат или сообщение.
  
  [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/getChats.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getChats.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/chats
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
  
  
  _Default:_{.json-schema-reset .json-schema-value} `10`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `20`
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
    "orderIds": [
      0
    ],
    "contexts": [
      {
        "type": "ORDER",
        "id": 1
      }
    ],
    "contextTypes": [
      "ORDER"
    ],
    "types": [
      "CHAT"
    ],
    "statuses": [
      "NEW"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _contexts_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ChatContextDTO](#entity-ChatContextDTO)[] &#124; null
  
  Фильтр по контексту чата.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "ORDER",
      "id": 1
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _contextTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ChatContextType](#entity-ChatContextType)[] &#124; null
  
  Фильтр по типу контекста чата.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "ORDER"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _orderIds_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
  Вместо него используйте `contexts`.
  
  {% endnote %}
  
  Фильтр по идентификаторам заказов на Маркете.
  
  
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
  
  _statuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ChatStatusType](#entity-ChatStatusType)[] &#124; null
  
  Фильтр по статусам чатов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "NEW"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _types_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ChatType](#entity-ChatType)[] &#124; null
  
  Фильтр по типам чатов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "CHAT"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ChatContextIdentifiableType {#entity-ChatContextIdentifiableType}
  
  Тип чата:
  
  * `ORDER` — по заказам.
  * `RETURN` — по возвратам (FBY, FBS и Экспресс).
  
  Подробнее о чатах по заказам и возвратам читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ORDER`, `RETURN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ChatContextDTO {#entity-ChatContextDTO}
  
  Информация о заказе или возврате, по которому начат чат.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа или возврата.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ChatContextIdentifiableType](#entity-ChatContextIdentifiableType)
  
  Тип чата:
  
  * `ORDER` — по заказам.
  * `RETURN` — по возвратам (FBY, FBS и Экспресс).
  
  Подробнее о чатах по заказам и возвратам читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ORDER`, `RETURN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "ORDER",
    "id": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ChatContextType {#entity-ChatContextType}
  
  Тип контекста:
  
  * `ORDER` — чат по заказу. [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders)
  * `RETURN` — чат по возврату (FBY, FBS и Экспресс). [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders)
  * `DIRECT` — чат, который начал покупатель. [Сообщения от покупателей](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ORDER`, `RETURN`, `DIRECT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ChatType {#entity-ChatType}
  
  Тип чата:
  
  * `CHAT` — чат с покупателем.
  * `ARBITRAGE` — спор.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CHAT`, `ARBITRAGE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ChatStatusType {#entity-ChatStatusType}
  
  Статус чата:
  
  * `NEW` — новый чат.
  * `WAITING_FOR_CUSTOMER` — нужен ответ покупателя.
  * `WAITING_FOR_PARTNER` — нужен ответ магазина.
  * `WAITING_FOR_ARBITER` — нужен ответ арбитра.
  * `WAITING_FOR_MARKET` — нужен ответ Маркета.
  * `FINISHED` — чат завершен.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `NEW`, `WAITING_FOR_CUSTOMER`, `WAITING_FOR_PARTNER`, `WAITING_FOR_ARBITER`, `WAITING_FOR_MARKET`, `FINISHED`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список чатов.
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "chats": [
        {
          "chatId": 1,
          "orderId": 1,
          "context": {},
          "type": "CHAT",
          "status": "NEW",
          "createdAt": "2017-11-21T00:00:00+03:00",
          "updatedAt": "2017-11-21T00:00:00+03:00"
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
    **Type**: [GetChatsInfoDTO](#entity-GetChatsInfoDTO)
  
    Список чатов.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "chats": [
        {
          "chatId": 1,
          "orderId": 1,
          "context": {
            "type": "ORDER",
            "customer": {
              "name": "example",
              "publicId": "example"
            },
            "campaignId": 1,
            "orderId": 1,
            "returnId": 1
          },
          "type": "CHAT",
          "status": "NEW",
          "createdAt": "2017-11-21T00:00:00+03:00",
          "updatedAt": "2017-11-21T00:00:00+03:00"
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
        "chats": [
          {
            "chatId": 1,
            "orderId": 1,
            "context": {
              "type": "ORDER",
              "customer": {},
              "campaignId": 1,
              "orderId": 1,
              "returnId": 1
            },
            "type": "CHAT",
            "status": "NEW",
            "createdAt": "2017-11-21T00:00:00+03:00",
            "updatedAt": "2017-11-21T00:00:00+03:00"
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
  
  ### ChatCustomerDTO {#entity-ChatCustomerDTO}
  
  Информация о покупателе в чате.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Публичное имя покупателя в Яндекс Паспорте, которое отображается в сервисах Яндекса.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _publicId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Публичный идентификатор пользователя в Яндекс Паспорте.
  
  {% cut "Примеры, где используется" %}
  
  * Маркет: `https://market.yandex.ru/user/{public-id}/reviews`
  * Дзен: `https://zen.yandex.ru/user/{public-id}`
  * Отзывы: `https://yandex.ru/user/{public-id}`
  
  {% endcut %}
  
  Подробнее о публичных данных читайте в [документации Яндекс ID](https://yandex.ru/support/id/ru/data/public-data).
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "name": "example",
    "publicId": "example"
  }
  ```
  
  {% endcut %}
  
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
  
  ### ChatFullContextDTO {#entity-ChatFullContextDTO}
  
  Информация о заказе или возврате, по которому начат чат.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ChatContextType](#entity-ChatContextType)
  
  Тип контекста:
  
  * `ORDER` — чат по заказу. [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders)
  * `RETURN` — чат по возврату (FBY, FBS и Экспресс). [Чаты о заказах и возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders)
  * `DIRECT` — чат, который начал покупатель. [Сообщения от покупателей](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ORDER`, `RETURN`, `DIRECT`
  {.table-cell}
  ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)
  
  Возвращается для заказов и возвратов.
  
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
  
  _customer_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ChatCustomerDTO](#entity-ChatCustomerDTO)
  
  Информация о покупателе.
  
  Информация о покупателе в чате.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "name": "example",
    "publicId": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _orderId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  
  Возвращается для заказов и возвратов.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _returnId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор возврата.
  
  Возвращается только для возвратов.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "ORDER",
    "customer": {
      "name": "example",
      "publicId": "example"
    },
    "campaignId": 1,
    "orderId": 1,
    "returnId": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetChatInfoDTO {#entity-GetChatInfoDTO}
  
  Информация о чате.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _chatId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор чата.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _context_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ChatFullContextDTO](#entity-ChatFullContextDTO)
  
  Информация о заказе или возврате, по которому начат чат.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "ORDER",
    "customer": {
      "name": "example",
      "publicId": "example"
    },
    "campaignId": 1,
    "orderId": 1,
    "returnId": 1
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _createdAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время создания чата.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2017-11-21T00:00:00+03:00`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ChatStatusType](#entity-ChatStatusType)
  
  Статус чата:
  
  * `NEW` — новый чат.
  * `WAITING_FOR_CUSTOMER` — нужен ответ покупателя.
  * `WAITING_FOR_PARTNER` — нужен ответ магазина.
  * `WAITING_FOR_ARBITER` — нужен ответ арбитра.
  * `WAITING_FOR_MARKET` — нужен ответ Маркета.
  * `FINISHED` — чат завершен.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `NEW`, `WAITING_FOR_CUSTOMER`, `WAITING_FOR_PARTNER`, `WAITING_FOR_ARBITER`, `WAITING_FOR_MARKET`, `FINISHED`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ChatType](#entity-ChatType)
  
  Тип чата:
  
  * `CHAT` — чат с покупателем.
  * `ARBITRAGE` — спор.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CHAT`, `ARBITRAGE`
  {.table-cell}
  ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время последнего сообщения в чате.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2017-11-21T00:00:00+03:00`
  {.table-cell}
  ||
  ||
  
  _orderId_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
  Вместо него используйте `context`.
  
  {% endnote %}
  
  Идентификатор заказа.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "chatId": 1,
    "orderId": 1,
    "context": {
      "type": "ORDER",
      "customer": {
        "name": "example",
        "publicId": "example"
      },
      "campaignId": 1,
      "orderId": 1,
      "returnId": 1
    },
    "type": "CHAT",
    "status": "NEW",
    "createdAt": "2017-11-21T00:00:00+03:00",
    "updatedAt": "2017-11-21T00:00:00+03:00"
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
  
  ### GetChatsInfoDTO {#entity-GetChatsInfoDTO}
  
  Список чатов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _chats_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetChatInfoDTO](#entity-GetChatInfoDTO)[]
  
  Информация о чатах.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "chatId": 1,
      "orderId": 1,
      "context": {
        "type": "ORDER",
        "customer": {
          "name": "example",
          "publicId": "example"
        },
        "campaignId": 1,
        "orderId": 1,
        "returnId": 1
      },
      "type": "CHAT",
      "status": "NEW",
      "createdAt": "2017-11-21T00:00:00+03:00",
      "updatedAt": "2017-11-21T00:00:00+03:00"
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
  
  Информация о страницах с результатами.
  
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
    "chats": [
      {
        "chatId": 1,
        "orderId": 1,
        "context": {
          "type": "ORDER",
          "customer": {
            "name": "example",
            "publicId": "example"
          },
          "campaignId": 1,
          "orderId": 1,
          "returnId": 1
        },
        "type": "CHAT",
        "status": "NEW",
        "createdAt": "2017-11-21T00:00:00+03:00",
        "updatedAt": "2017-11-21T00:00:00+03:00"
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
        default: 10
        maximum: 20
  headers: []
  body: |-
    {
      "orderIds": [
        0
      ],
      "contexts": [
        {
          "type": "ORDER",
          "id": 1
        }
      ],
      "contextTypes": [
        "ORDER"
      ],
      "types": [
        "CHAT"
      ],
      "statuses": [
        "NEW"
      ]
    }
  schema:
    description: |
      Фильтры по чатам, которые нужно вернуть.
    type: object
    properties:
      orderIds:
        description: |
          {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
          Вместо него используйте `contexts`.
  
          {% endnote %}
  
          Фильтр по идентификаторам заказов на Маркете.
        type: array
        nullable: true
        uniqueItems: true
        items:
          type: integer
          format: int64
        minItems: 1
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-19'
          replacement-field: contexts
      contexts:
        description: Фильтр по контексту чата.
        type: array
        nullable: true
        uniqueItems: true
        items:
          description: Информация о заказе или возврате, по которому начат чат.
          type: object
          required:
            - type
            - id
          properties:
            type:
              description: >
                Тип чата:
  
  
                * `ORDER` — по заказам.
  
                * `RETURN` — по возвратам (FBY, FBS и Экспресс).
  
  
                Подробнее о чатах по заказам и возвратам читайте в [Справке
                Маркета для
                продавцов](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders).
              type: string
              enum:
                - ORDER
                - RETURN
            id:
              description: Идентификатор заказа или возврата.
              type: integer
              format: int64
              minimum: 1
        minItems: 1
      contextTypes:
        description: Фильтр по типу контекста чата.
        type: array
        nullable: true
        uniqueItems: true
        items:
          description: >
            Тип контекста:
  
  
            * `ORDER` — чат по заказу. [Чаты о заказах и
            возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders)
  
            * `RETURN` — чат по возврату (FBY, FBS и Экспресс). [Чаты о заказах и
            возвратах](https://yandex.ru/support/marketplace/ru/orders/communication/about-orders)
  
            * `DIRECT` — чат, который начал покупатель. [Сообщения от
            покупателей](https://yandex.ru/support/marketplace/ru/orders/communication/with-users)
          type: string
          enum:
            - ORDER
            - RETURN
            - DIRECT
        minItems: 1
      types:
        description: Фильтр по типам чатов.
        type: array
        nullable: true
        uniqueItems: true
        items:
          description: |
            Тип чата:
  
            * `CHAT` — чат с покупателем.
            * `ARBITRAGE` — спор.
          type: string
          enum:
            - CHAT
            - ARBITRAGE
        minItems: 1
      statuses:
        description: Фильтр по статусам чатов.
        type: array
        nullable: true
        uniqueItems: true
        items:
          description: |
            Статус чата:
  
            * `NEW` — новый чат.
            * `WAITING_FOR_CUSTOMER` — нужен ответ покупателя.
            * `WAITING_FOR_PARTNER` — нужен ответ магазина.
            * `WAITING_FOR_ARBITER` — нужен ответ арбитра.
            * `WAITING_FOR_MARKET` — нужен ответ Маркета.
            * `FINISHED` — чат завершен.
          type: string
          enum:
            - NEW
            - WAITING_FOR_CUSTOMER
            - WAITING_FOR_PARTNER
            - WAITING_FOR_ARBITER
            - WAITING_FOR_MARKET
            - FINISHED
        minItems: 1
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
  path: v2/businesses/{businessId}/chats
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/chats/getChats.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
