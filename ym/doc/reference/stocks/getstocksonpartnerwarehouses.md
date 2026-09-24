---
title: Информация об остатках на складах партнера
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md"
fetched_at: "2026-09-24T02:13:45Z"
content_sha: 94d8cc14f71e8f83
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/stocks/getStocksOnPartnerWarehouses.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/stocks/getStocksOnPartnerWarehouses.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/stocks/getStocksOnPartnerWarehouses.md -->
<div class="openapi">

# Информация об остатках

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getStocksOnPartnerWarehouses.md -->
  **Метод доступен для моделей: [FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getStocksOnPartnerWarehouses.md -->
  
  Возвращает данные об остатках товаров на складе кабинета.
  
  {% note warning "Метод подходит, только если в кабинете нет групп складов" %}
  
  Если в кабинете есть группы складов, используйте метод [POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md). [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks).
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/getStocksOnPartnerWarehouses.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 500 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getStocksOnPartnerWarehouses.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v3/businesses/{businessId}/offers/stocks
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
  
  Количество значений на одной странице. <br><br> Если значение параметра превышает максимально допустимое, оно будет уменьшено до максимума.
  
  
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
    "partnerWarehouseId": 1,
    "archived": true,
    "offerIds": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _partnerWarehouseId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада.
  
  Чтобы узнать идентификатор склада, воспользуйтесь запросом [POST v3/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _archived_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Фильтр по нахождению в архиве.
  
  Передайте `true`, чтобы получить информацию об остатках товаров, которые находятся в архиве. Если фильтр не заполнен или передано `false`, в ответе возвращается информация о товарах, которые не находятся в архиве.
  
  {.table-cell}
  ||
  ||
  
  _offerIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)[] &#124; null
  
  Фильтр по вашим SKU товаров.
  
  Возвращается информация об остатках всех переданных SKU, включая товары в архиве.
  
  {% note warning "Такой список возвращается только целиком" %}
  
  Если вы запрашиваете информацию по конкретным SKU, не заполняйте:
  
  * `pageToken`
  * `limit`
  * `archived`
  
  {% endnote %}
  
   
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `500`
  
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
  
  Остатки товаров на складе.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "partnerWarehouseId": 1,
      "offers": [
        {
          "offerId": "example",
          "stocks": [
            null
          ],
          "updatedAt": "2025-01-01T00:00:00Z"
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
    **Type**: [GetStocksOnPartnerWarehousesDTO](#entity-GetStocksOnPartnerWarehousesDTO)
  
    Информация об остатках товаров на складе.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "partnerWarehouseId": 1,
      "offers": [
        {
          "offerId": "example",
          "stocks": [
            {
              "type": "FIT",
              "count": 0
            }
          ],
          "updatedAt": "2025-01-01T00:00:00Z"
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
        "partnerWarehouseId": 1,
        "offers": [
          {
            "offerId": "example",
            "stocks": [
              {}
            ],
            "updatedAt": "2025-01-01T00:00:00Z"
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
  
  ### WarehouseStockType {#entity-WarehouseStockType}
  
  Тип остатков товаров на складе:
  
  * `AVAILABLE` (соответствует типу «Доступный к заказу» в отчете «Остатки на складе» в кабинете продавца на Маркете) — товар, доступный для продажи.
  
  * `DEFECT` (соответствует типу «Брак») — товар с браком.
  
  * `EXPIRED` (соответствует типу «Просрочен») — товар с истекшим сроком годности.
  
  * `FIT` (соответствует типу «Годный») — товар, который доступен для продажи или уже зарезервирован.
  
  * `FREEZE` — товар, который зарезервирован для заказов.
  
  * `QUARANTINE` (соответствует типу «Карантин») — товар, временно недоступный для продажи (например, товар перемещают из одного помещения склада в другое).
  
  * `UTILIZATION` — товар, который будет утилизирован.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `FREEZE`, `AVAILABLE`, `QUARANTINE`, `UTILIZATION`, `DEFECT`, `EXPIRED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseStockDTO {#entity-WarehouseStockDTO}
  
  Информация об остатках товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Значение остатков.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseStockType](#entity-WarehouseStockType)
  
  Тип остатков.
  
  Тип остатков товаров на складе:
  
  * `AVAILABLE` (соответствует типу «Доступный к заказу» в отчете «Остатки на складе» в кабинете продавца на Маркете) — товар, доступный для продажи.
  
  * `DEFECT` (соответствует типу «Брак») — товар с браком.
  
  * `EXPIRED` (соответствует типу «Просрочен») — товар с истекшим сроком годности.
  
  * `FIT` (соответствует типу «Годный») — товар, который доступен для продажи или уже зарезервирован.
  
  * `FREEZE` — товар, который зарезервирован для заказов.
  
  * `QUARANTINE` (соответствует типу «Карантин») — товар, временно недоступный для продажи (например, товар перемещают из одного помещения склада в другое).
  
  * `UTILIZATION` — товар, который будет утилизирован.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `FREEZE`, `AVAILABLE`, `QUARANTINE`, `UTILIZATION`, `DEFECT`, `EXPIRED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "FIT",
    "count": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PartnerWarehouseOfferDTO {#entity-PartnerWarehouseOfferDTO}
  
  Информация об остатках товара.
  
  #|
  || **Name** | **Description** ||
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
  
  _stocks_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseStockDTO](#entity-WarehouseStockDTO)[]
  
  Информация об остатках.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "FIT",
      "count": 0
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время последнего обновления информации об остатках.
  
  Формат даты и времени: ISO 8601 со смещением относительно UTC. Например, `2023-11-21T00:42:42+03:00`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "stocks": [
      {
        "type": "FIT",
        "count": 0
      }
    ],
    "updatedAt": "2025-01-01T00:00:00Z"
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
  
  ### GetStocksOnPartnerWarehousesDTO {#entity-GetStocksOnPartnerWarehousesDTO}
  
  Информация об остатках товаров на складе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PartnerWarehouseOfferDTO](#entity-PartnerWarehouseOfferDTO)[]
  
  Страница списка товаров.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "stocks": [
        {
          "type": "FIT",
          "count": 0
        }
      ],
      "updatedAt": "2025-01-01T00:00:00Z"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _partnerWarehouseId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
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
    "partnerWarehouseId": 1,
    "offers": [
      {
        "offerId": "example",
        "stocks": [
          {
            "type": "FIT",
            "count": 0
          }
        ],
        "updatedAt": "2025-01-01T00:00:00Z"
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
        Количество значений на одной странице. <br><br> Если значение параметра превышает максимально допустимое, оно будет уменьшено до максимума.
      in: query
      required: false
      x-transform: truncateLimit
      schema:
        type: integer
        format: int32
        minimum: 1
        default: 50
        maximum: 100
  headers: []
  body: |-
    {
      "partnerWarehouseId": 1,
      "archived": true,
      "offerIds": [
        "example"
      ]
    }
  schema:
    description: |
      Фильтры для запроса остатков.
    type: object
    required:
      - partnerWarehouseId
    properties:
      partnerWarehouseId:
        description: "Идентификатор склада.\n\nЧтобы узнать идентификатор склада, воспользуйтесь запросом [POST\_v3/businesses/{businessId}/warehouses](../../reference/warehouses/getPartnerWarehouses.md).\n"
        type: integer
        format: int64
        minimum: 1
      archived:
        description: >
          Фильтр по нахождению в архиве.
  
  
          Передайте `true`, чтобы получить информацию об остатках товаров, которые
          находятся в архиве. Если фильтр не заполнен или передано `false`, в
          ответе возвращается информация о товарах, которые не находятся в архиве.
        type: boolean
      offerIds:
        description: "Фильтр по вашим SKU товаров.\n\nВозвращается информация об остатках всех переданных SKU, включая товары в архиве.\n\n{% note warning \"Такой список возвращается только целиком\" %}\n\nЕсли вы запрашиваете информацию по конкретным SKU, не заполняйте:\n\n* `pageToken`\n* `limit`\n* `archived`\n\n{% endnote %}\n\n\_\n"
        type: array
        uniqueItems: true
        minItems: 1
        maxItems: 500
        nullable: true
        items:
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
  path: v3/businesses/{businessId}/offers/stocks
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/stocks/getStocksOnPartnerWarehouses.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
