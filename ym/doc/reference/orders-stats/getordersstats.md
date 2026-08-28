---
title: Детальная информация по заказам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md"
fetched_at: "2026-08-28T11:52:49Z"
content_sha: 431af2c3e28e5ffd
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders-stats/getOrdersStats.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders-stats/getOrdersStats.md
  - href: ru/reference/orders-stats/getOrdersStats.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders-stats/getOrdersStats.md -->
<div class="openapi">

# Детальная информация по заказам

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOrdersStats.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOrdersStats.md -->
  
  Возвращает информацию по заказам на Маркете, в которых есть ваши товары.
  
  С помощью нее вы можете собрать статистику по вашим заказам и узнать, например, какие из товаров чаще всего возвращаются покупателями, какие, наоборот, пользуются большим спросом и т. п.
  
  {% note tip "Информация по созданным или обновленным заказам может появиться с задержкой до 40 минут" %}
  
  Чтобы получить данные без задержки, используйте метод [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md).
  
  {% endnote %}
  
  В одном запросе можно получить информацию не более чем по 200 заказам.
  
  <!-- source: ru/_auto/method_limits/getOrdersStats.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOrdersStats.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/stats/orders
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
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _limit_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество значений на одной странице.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `100`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `200`
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
    "dateFrom": "2025-01-01",
    "dateTo": "2025-01-01",
    "updateFrom": "2025-01-01",
    "updateTo": "2025-01-01",
    "orders": [
      0
    ],
    "statuses": [
      "CANCELLED_BEFORE_PROCESSING"
    ],
    "hasCis": true
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начальная дата, когда заказ был сформирован.
  
  Формат даты: `ГГГГ‑ММ‑ДД`.
  
  Нельзя использовать вместе с параметрами `updateFrom` и `updateTo`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конечная дата, когда заказ был сформирован.
  
  Формат даты: `ГГГГ‑ММ‑ДД`.
  
  Нельзя использовать вместе с параметрами `updateFrom` и `updateTo`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _hasCis_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Фильтр для получения заказов, в которых есть хотя бы один товар с кодом идентификации в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go):
  
  * `true` — да.
  * `false` — нет.
  Такие коды присваиваются товарам, которые подлежат маркировке и относятся к определенным категориям.
  
  {.table-cell}
  ||
  ||
  
  _orders_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Список идентификаторов заказов.
  
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
  **Type**: [OrderStatsStatusType](#entity-OrderStatsStatusType)[] &#124; null
  
  Список статусов заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "CANCELLED_BEFORE_PROCESSING"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _updateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начальная дата периода, за который были изменения в заказе (например, статуса или информации о платежах).
  
  Формат даты: `ГГГГ‑ММ‑ДД`.
  
  Нельзя использовать вместе с параметрами `dateFrom` и `dateTo`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _updateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конечная дата периода, за который были изменения в заказе (например, статуса или информации о платежах).
  
  Формат даты: `ГГГГ‑ММ‑ДД`.
  
  Нельзя использовать вместе с параметрами `dateFrom` и `dateTo`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderStatsStatusType {#entity-OrderStatsStatusType}
  
  Текущий статус заказа:
  
  * `CANCELLED_BEFORE_PROCESSING` — заказ отменен до начала его обработки.
  
  * `CANCELLED_IN_DELIVERY` — заказ отменен во время его доставки.
  
  * `CANCELLED_IN_PROCESSING` — заказ отменен во время его обработки.
  
  * `DELIVERY` — заказ передан службе доставки.
  
  * `DELIVERED` — заказ доставлен.
  
  * `PARTIALLY_DELIVERED` — заказ частично доставлен.
  
      {% note warning "Статус заказа может перейти в `PARTIALLY_DELIVERED` не сразу" %}
  
      Если в доставленном заказе был невыкуп, статус изменится только после получения заказа на складе Маркета.
  
      {% endnote %}
  
  * `PARTIALLY_RETURNED` — заказ частично возвращен покупателем.
  
  * `PENDING` — заказ ожидает подтверждения.
  
  * `PICKUP` — заказ доставлен в пункт выдачи.
  
  * `PROCESSING` — заказ в обработке.
  
  * `RESERVED` — товар зарезервирован на складе.
  
  * `RETURNED` — заказ полностью возвращен покупателем.
  
  * `UNKNOWN` — неизвестный статус заказа.
  
  * `UNPAID` — заказ от юридического лица ожидает оплаты.
  
  * `LOST` — заказ утерян.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CANCELLED_BEFORE_PROCESSING`, `CANCELLED_IN_DELIVERY`, `CANCELLED_IN_PROCESSING`, `DELIVERY`, `DELIVERED`, `PARTIALLY_DELIVERED`, `PARTIALLY_RETURNED`, `PENDING`, `PICKUP`, `PROCESSING`, `RESERVED`, `RETURNED`, `UNKNOWN`, `UNPAID`, `LOST`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация по заказам.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "orders": [
        {
          "id": 0,
          "creationDate": "2025-01-01",
          "statusUpdateDate": "2025-01-01T00:00:00Z",
          "status": "CANCELLED_BEFORE_PROCESSING",
          "partnerOrderId": "example",
          "paymentType": "POSTPAID",
          "fake": true,
          "deliveryRegion": {},
          "items": [
            null
          ],
          "initialItems": [
            null
          ],
          "payments": [
            null
          ],
          "commissions": [
            null
          ],
          "subsidies": [
            null
          ],
          "currency": "RUR"
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
    **Type**: [OrdersStatsDTO](#entity-OrdersStatsDTO)
  
    Информация по заказам.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "orders": [
        {
          "id": 0,
          "creationDate": "2025-01-01",
          "statusUpdateDate": "2025-01-01T00:00:00Z",
          "status": "CANCELLED_BEFORE_PROCESSING",
          "partnerOrderId": "example",
          "paymentType": "POSTPAID",
          "fake": true,
          "deliveryRegion": {
            "id": 0,
            "name": "example"
          },
          "items": [
            {
              "offerName": "example",
              "marketSku": 1,
              "shopSku": "example",
              "count": 0,
              "prices": [
                null
              ],
              "warehouse": {},
              "details": [
                null
              ],
              "cisList": [
                null
              ],
              "initialCount": 0,
              "bidFee": 570,
              "cofinanceThreshold": 0.5,
              "cofinanceValue": 0.5
            }
          ],
          "initialItems": [
            null
          ],
          "payments": [
            {
              "id": "example",
              "date": "2025-01-01",
              "type": "PAYMENT",
              "source": "BUYER",
              "total": 0.5,
              "paymentOrder": {}
            }
          ],
          "commissions": [
            {
              "type": "FEE",
              "actual": 0.5
            }
          ],
          "subsidies": [
            {
              "operationType": "ACCRUAL",
              "type": "YANDEX_CASHBACK",
              "amount": 0.5
            }
          ],
          "currency": "RUR"
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
        "orders": [
          {
            "id": 0,
            "creationDate": "2025-01-01",
            "statusUpdateDate": "2025-01-01T00:00:00Z",
            "status": "CANCELLED_BEFORE_PROCESSING",
            "partnerOrderId": "example",
            "paymentType": "POSTPAID",
            "fake": true,
            "deliveryRegion": {
              "id": 0,
              "name": "example"
            },
            "items": [
              {}
            ],
            "initialItems": [
              null
            ],
            "payments": [
              {}
            ],
            "commissions": [
              {}
            ],
            "subsidies": [
              {}
            ],
            "currency": "RUR"
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
  
  ### OrdersStatsOrderPaymentType {#entity-OrdersStatsOrderPaymentType}
  
  Тип оплаты заказа:
  - `POSTPAID` — заказ оплачен после того, как был получен.
  - `PREPAID` — заказ оплачен до того, как был получен.
  - `UNKNOWN` — неизвестный тип оплаты. Скорее всего покупатель отменил или вернул заказ или не было его оплаты.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `POSTPAID`, `PREPAID`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsDeliveryRegionDTO {#entity-OrdersStatsDeliveryRegionDTO}
  
  Информация о регионе доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона доставки.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название региона доставки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### MarketSku {#entity-MarketSku}
  
  Идентификатор карточки товара на Маркете.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  ### OrdersStatsPriceType {#entity-OrdersStatsPriceType}
  
  Тип скидки или цена товара:
  - `BUYER` — цена товара с учетом скидок, в том числе купонов.
  - `CASHBACK` — баллы Плюса.
  - `MARKETPLACE` — купоны.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `BUYER`, `CASHBACK`, `MARKETPLACE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsPriceDTO {#entity-OrdersStatsPriceDTO}
  
  Цена или скидки на товар.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _costPerItem_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Цена или скидка на единицу товара в заказе.
  
  Точность — два знака после запятой.
  
  Включает НДС.
  
  {.table-cell}
  ||
  ||
  
  _total_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Суммарная цена или скидка на все единицы товара в заказе.
  
  Точность — два знака после запятой.
  
  Включает НДС.
  
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsPriceType](#entity-OrdersStatsPriceType)
  
  Тип скидки или цена товара.
  
  Тип скидки или цена товара:
  - `BUYER` — цена товара с учетом скидок, в том числе купонов.
  - `CASHBACK` — баллы Плюса.
  - `MARKETPLACE` — купоны.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `BUYER`, `CASHBACK`, `MARKETPLACE`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "BUYER",
    "costPerItem": 0.5,
    "total": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsWarehouseDTO {#entity-OrdersStatsWarehouseDTO}
  
  Информация о складе, на котором хранится товар.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название склада.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsItemStatusType {#entity-OrdersStatsItemStatusType}
  
  Статус товара:
  
  * `REJECTED` — товар был добавлен в созданный заказ, но не был оплачен.
  * `RETURNED` — товар вернули.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `REJECTED`, `RETURNED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsStockType {#entity-OrdersStatsStockType}
  
  Тип товара:
  
  * `FIT` — товар надлежащего качества.
  
  * `DEFECT` — товар бракованный.
  
  * `EXPIRED` — товар с истекшим сроком годности.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `DEFECT`, `EXPIRED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsDetailsDTO {#entity-OrdersStatsDetailsDTO}
  
  Информация об удалении товара из заказа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _itemCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товара со статусом, указанном в параметре `itemStatus`.
  {.table-cell}
  ||
  ||
  
  _itemStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsItemStatusType](#entity-OrdersStatsItemStatusType)
  
  Статус товара.
  
  Статус товара:
  
  * `REJECTED` — товар был добавлен в созданный заказ, но не был оплачен.
  * `RETURNED` — товар вернули.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `REJECTED`, `RETURNED`
  {.table-cell}
  ||
  ||
  
  _stockType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsStockType](#entity-OrdersStatsStockType)
  
  **Только для модели FBY**
  
  Тип товара.
  
  Возвращается только после обработки возврата на складе Маркета.
  
  
  Тип товара:
  
  * `FIT` — товар надлежащего качества.
  
  * `DEFECT` — товар бракованный.
  
  * `EXPIRED` — товар с истекшим сроком годности.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `DEFECT`, `EXPIRED`
  {.table-cell}
  ||
  ||
  
  _updateDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  **Только для модели FBY**
  
  Дата, когда возврат был обработан на складе Маркета.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "itemStatus": "REJECTED",
    "itemCount": 0,
    "updateDate": "2025-01-01",
    "stockType": "FIT"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsItemDTO {#entity-OrdersStatsItemDTO}
  
  Список товаров в заказе после возможных изменений.
  
  В ходе обработки заказа Маркет может удалить из него единицы товаров — при проблемах на складе или по инициативе пользователя.
  
  * Если из заказа удалены все единицы товара, его не будет в списке `items` — только в списке `initialItems`.
  
  * Если в заказе осталась хотя бы одна единица товара, он будет и в списке `items` (с уменьшенным количеством единиц `count`), и в списке `initialItems` (с первоначальным количеством единиц `initialCount`).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _bidFee_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Списанная ставка ближайшего конкурента.
  
  Указывается в процентах от стоимости товара и умножается на 100. Например, ставка 5% обозначается как 500.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `10000`
  {.table-cell}
  ||
  ||
  
  _cisList_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Список кодов идентификации товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
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
  
  _cofinanceThreshold_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Порог для скидок с Маркетом на момент оформления заказа. [Что это такое?](https://yandex.ru/support/marketplace/marketing/smart-pricing.html#sponsored-discounts)
  
  Точность — два знака после запятой.
  
  {.table-cell}
  ||
  ||
  
  _cofinanceValue_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Скидка с Маркетом. [Что это такое?](https://yandex.ru/support/marketplace/marketing/smart-pricing.html#sponsored-discounts)
  
  Точность — два знака после запятой.
  
  {.table-cell}
  ||
  ||
  
  _count_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара с учетом удаленных единиц.
  
  Если из заказа удалены все единицы товара, он попадет только в список `initialItems`.
  
  {.table-cell}
  ||
  ||
  
  _details_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsDetailsDTO](#entity-OrdersStatsDetailsDTO)[] &#124; null
  
  Информация об удалении товара из заказа.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "itemStatus": "REJECTED",
      "itemCount": 0,
      "updateDate": "2025-01-01",
      "stockType": "FIT"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _initialCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Первоначальное количество единиц товара.
  {.table-cell}
  ||
  ||
  
  _marketSku_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MarketSku](#entity-MarketSku)
  
  Идентификатор карточки товара на Маркете.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _offerName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _prices_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsPriceDTO](#entity-OrdersStatsPriceDTO)[] &#124; null
  
  Цена или скидки на товар.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "BUYER",
      "costPerItem": 0.5,
      "total": 0.5
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _shopSku_{.json-schema-reset .json-schema-property}
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
  
  _warehouse_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsWarehouseDTO](#entity-OrdersStatsWarehouseDTO)
  
  Информация о складе, на котором хранится товар.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerName": "example",
    "marketSku": 1,
    "shopSku": "example",
    "count": 0,
    "prices": [
      {
        "type": "BUYER",
        "costPerItem": 0.5,
        "total": 0.5
      }
    ],
    "warehouse": {
      "id": 0,
      "name": "example"
    },
    "details": [
      {
        "itemStatus": "REJECTED",
        "itemCount": 0,
        "updateDate": "2025-01-01",
        "stockType": "FIT"
      }
    ],
    "cisList": [
      "example"
    ],
    "initialCount": 0,
    "bidFee": 570,
    "cofinanceThreshold": 0.5,
    "cofinanceValue": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsPaymentType {#entity-OrdersStatsPaymentType}
  
  Тип денежного перевода:
  - `PAYMENT` — оплата.
  - `REFUND` — возврат.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PAYMENT`, `REFUND`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsPaymentSourceType {#entity-OrdersStatsPaymentSourceType}
  
  Способ денежного перевода:
  - `BUYER` — оплата или возврат деньгами.
  - `MARKET_CESSION` — уступка задолженности покупателя.
  
  Устаревшие способы:
  - `CASHBACK`.
  - `MARKETPLACE`.
  - `SPLIT`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `BUYER`, `CASHBACK`, `MARKETPLACE`, `MARKET_CESSION`, `SPLIT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsPaymentOrderDTO {#entity-OrdersStatsPaymentOrderDTO}
  
  Информация о платежном поручении.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _date_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата платежного поручения.
  
  Формат даты: `ГГГГ‑ММ‑ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер платежного поручения.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "date": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsPaymentDTO {#entity-OrdersStatsPaymentDTO}
  
  Информация о денежных переводах по заказу.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _date_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата денежного перевода.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор денежного перевода.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _paymentOrder_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsPaymentOrderDTO](#entity-OrdersStatsPaymentOrderDTO)
  
  Информация о платежном поручении.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "date": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _source_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsPaymentSourceType](#entity-OrdersStatsPaymentSourceType)
  
  Способ денежного перевода.
  
  Способ денежного перевода:
  - `BUYER` — оплата или возврат деньгами.
  - `MARKET_CESSION` — уступка задолженности покупателя.
  
  Устаревшие способы:
  - `CASHBACK`.
  - `MARKETPLACE`.
  - `SPLIT`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `BUYER`, `CASHBACK`, `MARKETPLACE`, `MARKET_CESSION`, `SPLIT`
  {.table-cell}
  ||
  ||
  
  _total_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Сумма денежного перевода.
  
  Точность — два знака после запятой.
  
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsPaymentType](#entity-OrdersStatsPaymentType)
  
  Тип денежного перевода.
  
  Тип денежного перевода:
  - `PAYMENT` — оплата.
  - `REFUND` — возврат.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PAYMENT`, `REFUND`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "date": "2025-01-01",
    "type": "PAYMENT",
    "source": "BUYER",
    "total": 0.5,
    "paymentOrder": {
      "id": "example",
      "date": "2025-01-01"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsCommissionType {#entity-OrdersStatsCommissionType}
  
  Услуга:
  
  * `FEE` — размещение товара на Маркете.
  * `FULFILLMENT` — складская обработка. Не возвращается с 1 января 2024 года.
  * `LOYALTY_PARTICIPATION_FEE` — участие в программе лояльности и отзывы за баллы.
  * `AUCTION_PROMOTION` — буст продаж с оплатой за продажи.
  * `INSTALLMENT` — рассрочка. Не возвращается с 24 февраля 2022 года.
  * `DELIVERY_TO_CUSTOMER` — доставка покупателю (FBY, FBS). Для DBS и Экспресс — если заказ возвращается через логистику Маркета.
  * `EXPRESS_DELIVERY_TO_CUSTOMER` — экспресс-доставка покупателю (Экспресс).
  * `AGENCY` — прием платежа покупателя.
  * `PAYMENT_TRANSFER` — перевод платежа покупателя.
  * `RETURNED_ORDERS_STORAGE` — хранение невыкупов и возвратов (FBS). Для DBS и Экспресс — если заказ возвращается через логистику Маркета.
  * `SORTING` — обработка заказа (FBS).
  * `INTAKE_SORTING` — организация забора заказов со склада продавца (FBS).
  * `RETURN_PROCESSING` — обработка заказов на складе (FBS). Для DBS и Экспресс — если заказ возвращается через логистику Маркета.
  * `ILLIQUID_GOODS_SALE` — вознаграждение за продажу невывезенных товаров.
  * `CROSSREGIONAL_DELIVERY` - доставка средней мили.
  * `FULFILLMENT_WITHDRAW` - вывоз со склада.
  * `ITEM_BOOKING` - бронирование товара (только для продавцов Market Yandex Go).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FEE`, `FULFILLMENT`, `LOYALTY_PARTICIPATION_FEE`, `AUCTION_PROMOTION`, `INSTALLMENT`, `DELIVERY_TO_CUSTOMER`, `EXPRESS_DELIVERY_TO_CUSTOMER`, `AGENCY`, `PAYMENT_TRANSFER`, `RETURNED_ORDERS_STORAGE`, `SORTING`, `INTAKE_SORTING`, `RETURN_PROCESSING`, `ILLIQUID_GOODS_SALE`, `CROSSREGIONAL_DELIVERY`, `FULFILLMENT_WITHDRAW`, `ITEM_BOOKING`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsCommissionDTO {#entity-OrdersStatsCommissionDTO}
  
  Информация о стоимости услуг.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _actual_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Сумма, которая была выставлена в момент создания заказа и которую нужно оплатить.
  Точность — два знака после запятой.
  
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsCommissionType](#entity-OrdersStatsCommissionType)
  
  Услуга.
  
  Услуга:
  
  * `FEE` — размещение товара на Маркете.
  * `FULFILLMENT` — складская обработка. Не возвращается с 1 января 2024 года.
  * `LOYALTY_PARTICIPATION_FEE` — участие в программе лояльности и отзывы за баллы.
  * `AUCTION_PROMOTION` — буст продаж с оплатой за продажи.
  * `INSTALLMENT` — рассрочка. Не возвращается с 24 февраля 2022 года.
  * `DELIVERY_TO_CUSTOMER` — доставка покупателю (FBY, FBS). Для DBS и Экспресс — если заказ возвращается через логистику Маркета.
  * `EXPRESS_DELIVERY_TO_CUSTOMER` — экспресс-доставка покупателю (Экспресс).
  * `AGENCY` — прием платежа покупателя.
  * `PAYMENT_TRANSFER` — перевод платежа покупателя.
  * `RETURNED_ORDERS_STORAGE` — хранение невыкупов и возвратов (FBS). Для DBS и Экспресс — если заказ возвращается через логистику Маркета.
  * `SORTING` — обработка заказа (FBS).
  * `INTAKE_SORTING` — организация забора заказов со склада продавца (FBS).
  * `RETURN_PROCESSING` — обработка заказов на складе (FBS). Для DBS и Экспресс — если заказ возвращается через логистику Маркета.
  * `ILLIQUID_GOODS_SALE` — вознаграждение за продажу невывезенных товаров.
  * `CROSSREGIONAL_DELIVERY` - доставка средней мили.
  * `FULFILLMENT_WITHDRAW` - вывоз со склада.
  * `ITEM_BOOKING` - бронирование товара (только для продавцов Market Yandex Go).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FEE`, `FULFILLMENT`, `LOYALTY_PARTICIPATION_FEE`, `AUCTION_PROMOTION`, `INSTALLMENT`, `DELIVERY_TO_CUSTOMER`, `EXPRESS_DELIVERY_TO_CUSTOMER`, `AGENCY`, `PAYMENT_TRANSFER`, `RETURNED_ORDERS_STORAGE`, `SORTING`, `INTAKE_SORTING`, `RETURN_PROCESSING`, `ILLIQUID_GOODS_SALE`, `CROSSREGIONAL_DELIVERY`, `FULFILLMENT_WITHDRAW`, `ITEM_BOOKING`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "FEE",
    "actual": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsSubsidyOperationType {#entity-OrdersStatsSubsidyOperationType}
  
  Тип операции с баллами, которые используются для уменьшения стоимости размещения:
  
  * `ACCRUAL` — начисление баллов.
  * `DEDUCTION` — списание баллов.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ACCRUAL`, `DEDUCTION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsSubsidyType {#entity-OrdersStatsSubsidyType}
  
  Источник баллов, которые используются для уменьшения стоимости размещения:
  
  * `YANDEX_CASHBACK` — скидка по подписке Яндекс Плюс.
  
  * `SUBSIDY` — скидка Маркета (по акциям, промокодам, купонам и т. д.)
  
  * `DELIVERY` — скидка за доставку (DBS).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `YANDEX_CASHBACK`, `SUBSIDY`, `DELIVERY`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsSubsidyDTO {#entity-OrdersStatsSubsidyDTO}
  
  Информация о начислении баллов, которые используются для уменьшения стоимости размещения, и их списании в случае невыкупа или возврата.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Количество баллов, которые используются для уменьшения стоимости размещения, с точностью до двух знаков после запятой.
  
  {.table-cell}
  ||
  ||
  
  _operationType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrdersStatsSubsidyOperationType](#entity-OrdersStatsSubsidyOperationType)
  
  Тип операции c баллами, которые используются для уменьшения стоимости размещения.
  
  Тип операции с баллами, которые используются для уменьшения стоимости размещения:
  
  * `ACCRUAL` — начисление баллов.
  * `DEDUCTION` — списание баллов.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ACCRUAL`, `DEDUCTION`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrdersStatsSubsidyType](#entity-OrdersStatsSubsidyType)
  
  Источник баллов, которые используются для уменьшения стоимости размещения.
  
  Источник баллов, которые используются для уменьшения стоимости размещения:
  
  * `YANDEX_CASHBACK` — скидка по подписке Яндекс Плюс.
  
  * `SUBSIDY` — скидка Маркета (по акциям, промокодам, купонам и т. д.)
  
  * `DELIVERY` — скидка за доставку (DBS).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `YANDEX_CASHBACK`, `SUBSIDY`, `DELIVERY`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "operationType": "ACCRUAL",
    "type": "YANDEX_CASHBACK",
    "amount": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBuyerType {#entity-OrderBuyerType}
  
  Тип покупателя:
  
  * `PERSON` — физическое лицо.
  
  * `BUSINESS` — организация.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERSON`, `BUSINESS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CurrencyType {#entity-CurrencyType}
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrdersStatsOrderDTO {#entity-OrdersStatsOrderDTO}
  
  Информация о заказе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _commissions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrdersStatsCommissionDTO](#entity-OrdersStatsCommissionDTO)[]
  
  Информация о стоимости услуг.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "FEE",
      "actual": 0.5
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _currency_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта, в которой указаны цены в заказе.
  
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrdersStatsItemDTO](#entity-OrdersStatsItemDTO)[]
  
  Список товаров в заказе после возможных изменений.
  
  Информация о доставке заказа добавляется отдельным элементом в массиве `items`— параметр `offerName` со значением `Доставка`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerName": "example",
      "marketSku": 1,
      "shopSku": "example",
      "count": 0,
      "prices": [
        {
          "type": "BUYER",
          "costPerItem": 0.5,
          "total": 0.5
        }
      ],
      "warehouse": {
        "id": 0,
        "name": "example"
      },
      "details": [
        {
          "itemStatus": "REJECTED",
          "itemCount": 0,
          "updateDate": "2025-01-01",
          "stockType": "FIT"
        }
      ],
      "cisList": [
        "example"
      ],
      "initialCount": 0,
      "bidFee": 570,
      "cofinanceThreshold": 0.5,
      "cofinanceValue": 0.5
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _payments_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrdersStatsPaymentDTO](#entity-OrdersStatsPaymentDTO)[]
  
  Информация о расчетах по заказу.
  
  Возвращается пустым, если заказ:
    * только начали обрабатывать (даже если он оплачен);
    * отменили до момента передачи в доставку.
  
  Окончательная информация о расчетах по заказу вернется после его финальной обработки (например, после перехода в статус `DELIVERED`).
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": "example",
      "date": "2025-01-01",
      "type": "PAYMENT",
      "source": "BUYER",
      "total": 0.5,
      "paymentOrder": {
        "id": "example",
        "date": "2025-01-01"
      }
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _creationDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата создания заказа.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _deliveryRegion_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsDeliveryRegionDTO](#entity-OrdersStatsDeliveryRegionDTO)
  
  Информация о регионе доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _fake_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Тип заказа:
  
  * `false` — настоящий заказ покупателя.
  
  * `true` — [тестовый заказ](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md) Маркета.
  
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  ||
  
  _initialItems_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsItemDTO](#entity-OrdersStatsItemDTO)[] &#124; null
  
  Список товаров в заказе.
  
  Возвращается, только если было изменение количества товаров.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerName": "example",
      "marketSku": 1,
      "shopSku": "example",
      "count": 0,
      "prices": [
        {
          "type": "BUYER",
          "costPerItem": 0.5,
          "total": 0.5
        }
      ],
      "warehouse": {
        "id": 0,
        "name": "example"
      },
      "details": [
        {
          "itemStatus": "REJECTED",
          "itemCount": 0,
          "updateDate": "2025-01-01",
          "stockType": "FIT"
        }
      ],
      "cisList": [
        "example"
      ],
      "initialCount": 0,
      "bidFee": 570,
      "cofinanceThreshold": 0.5,
      "cofinanceValue": 0.5
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _partnerOrderId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор заказа в информационной системе магазина.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _paymentType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsOrderPaymentType](#entity-OrdersStatsOrderPaymentType)
  
  Тип оплаты заказа.
  
  Тип оплаты заказа:
  - `POSTPAID` — заказ оплачен после того, как был получен.
  - `PREPAID` — заказ оплачен до того, как был получен.
  - `UNKNOWN` — неизвестный тип оплаты. Скорее всего покупатель отменил или вернул заказ или не было его оплаты.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `POSTPAID`, `PREPAID`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderStatsStatusType](#entity-OrderStatsStatusType)
  
  Текущий статус заказа:
  
  * `CANCELLED_BEFORE_PROCESSING` — заказ отменен до начала его обработки.
  
  * `CANCELLED_IN_DELIVERY` — заказ отменен во время его доставки.
  
  * `CANCELLED_IN_PROCESSING` — заказ отменен во время его обработки.
  
  * `DELIVERY` — заказ передан службе доставки.
  
  * `DELIVERED` — заказ доставлен.
  
  * `PARTIALLY_DELIVERED` — заказ частично доставлен.
  
      {% note warning "Статус заказа может перейти в `PARTIALLY_DELIVERED` не сразу" %}
  
      Если в доставленном заказе был невыкуп, статус изменится только после получения заказа на складе Маркета.
  
      {% endnote %}
  
  * `PARTIALLY_RETURNED` — заказ частично возвращен покупателем.
  
  * `PENDING` — заказ ожидает подтверждения.
  
  * `PICKUP` — заказ доставлен в пункт выдачи.
  
  * `PROCESSING` — заказ в обработке.
  
  * `RESERVED` — товар зарезервирован на складе.
  
  * `RETURNED` — заказ полностью возвращен покупателем.
  
  * `UNKNOWN` — неизвестный статус заказа.
  
  * `UNPAID` — заказ от юридического лица ожидает оплаты.
  
  * `LOST` — заказ утерян.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CANCELLED_BEFORE_PROCESSING`, `CANCELLED_IN_DELIVERY`, `CANCELLED_IN_PROCESSING`, `DELIVERY`, `DELIVERED`, `PARTIALLY_DELIVERED`, `PARTIALLY_RETURNED`, `PENDING`, `PICKUP`, `PROCESSING`, `RESERVED`, `RETURNED`, `UNKNOWN`, `UNPAID`, `LOST`
  {.table-cell}
  ||
  ||
  
  _statusUpdateDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время, когда статус заказа был изменен в последний раз.
  
  Формат даты и времени: ISO 8601. Например, `2017-11-21T00:00:00`. Часовой пояс — UTC+03:00 (Москва).
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _subsidies_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrdersStatsSubsidyDTO](#entity-OrdersStatsSubsidyDTO)[] &#124; null
  
  Начисление баллов, которые используются для уменьшения стоимости размещения, и их списание в случае невыкупа или возврата.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "operationType": "ACCRUAL",
      "type": "YANDEX_CASHBACK",
      "amount": 0.5
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
    "id": 0,
    "creationDate": "2025-01-01",
    "statusUpdateDate": "2025-01-01T00:00:00Z",
    "status": "CANCELLED_BEFORE_PROCESSING",
    "partnerOrderId": "example",
    "paymentType": "POSTPAID",
    "fake": true,
    "deliveryRegion": {
      "id": 0,
      "name": "example"
    },
    "items": [
      {
        "offerName": "example",
        "marketSku": 1,
        "shopSku": "example",
        "count": 0,
        "prices": [
          {
            "type": "BUYER",
            "costPerItem": 0.5,
            "total": 0.5
          }
        ],
        "warehouse": {
          "id": 0,
          "name": "example"
        },
        "details": [
          {
            "itemStatus": "REJECTED",
            "itemCount": 0,
            "updateDate": "2025-01-01",
            "stockType": "FIT"
          }
        ],
        "cisList": [
          "example"
        ],
        "initialCount": 0,
        "bidFee": 570,
        "cofinanceThreshold": 0.5,
        "cofinanceValue": 0.5
      }
    ],
    "initialItems": [
      null
    ],
    "payments": [
      {
        "id": "example",
        "date": "2025-01-01",
        "type": "PAYMENT",
        "source": "BUYER",
        "total": 0.5,
        "paymentOrder": {
          "id": "example",
          "date": "2025-01-01"
        }
      }
    ],
    "commissions": [
      {
        "type": "FEE",
        "actual": 0.5
      }
    ],
    "subsidies": [
      {
        "operationType": "ACCRUAL",
        "type": "YANDEX_CASHBACK",
        "amount": 0.5
      }
    ],
    "currency": "RUR"
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
  
  ### OrdersStatsDTO {#entity-OrdersStatsDTO}
  
  Информация по заказам.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _orders_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrdersStatsOrderDTO](#entity-OrdersStatsOrderDTO)[]
  
  Список заказов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "creationDate": "2025-01-01",
      "statusUpdateDate": "2025-01-01T00:00:00Z",
      "status": "CANCELLED_BEFORE_PROCESSING",
      "partnerOrderId": "example",
      "paymentType": "POSTPAID",
      "fake": true,
      "deliveryRegion": {
        "id": 0,
        "name": "example"
      },
      "items": [
        {
          "offerName": "example",
          "marketSku": 1,
          "shopSku": "example",
          "count": 0,
          "prices": [
            {}
          ],
          "warehouse": {
            "id": 0,
            "name": "example"
          },
          "details": [
            {}
          ],
          "cisList": [
            "example"
          ],
          "initialCount": 0,
          "bidFee": 570,
          "cofinanceThreshold": 0.5,
          "cofinanceValue": 0.5
        }
      ],
      "initialItems": [
        null
      ],
      "payments": [
        {
          "id": "example",
          "date": "2025-01-01",
          "type": "PAYMENT",
          "source": "BUYER",
          "total": 0.5,
          "paymentOrder": {
            "id": "example",
            "date": "2025-01-01"
          }
        }
      ],
      "commissions": [
        {
          "type": "FEE",
          "actual": 0.5
        }
      ],
      "subsidies": [
        {
          "operationType": "ACCRUAL",
          "type": "YANDEX_CASHBACK",
          "amount": 0.5
        }
      ],
      "currency": "RUR"
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
    "orders": [
      {
        "id": 0,
        "creationDate": "2025-01-01",
        "statusUpdateDate": "2025-01-01T00:00:00Z",
        "status": "CANCELLED_BEFORE_PROCESSING",
        "partnerOrderId": "example",
        "paymentType": "POSTPAID",
        "fake": true,
        "deliveryRegion": {
          "id": 0,
          "name": "example"
        },
        "items": [
          {
            "offerName": "example",
            "marketSku": 1,
            "shopSku": "example",
            "count": 0,
            "prices": [
              null
            ],
            "warehouse": {},
            "details": [
              null
            ],
            "cisList": [
              null
            ],
            "initialCount": 0,
            "bidFee": 570,
            "cofinanceThreshold": 0.5,
            "cofinanceValue": 0.5
          }
        ],
        "initialItems": [
          null
        ],
        "payments": [
          {
            "id": "example",
            "date": "2025-01-01",
            "type": "PAYMENT",
            "source": "BUYER",
            "total": 0.5,
            "paymentOrder": {}
          }
        ],
        "commissions": [
          {
            "type": "FEE",
            "actual": 0.5
          }
        ],
        "subsidies": [
          {
            "operationType": "ACCRUAL",
            "type": "YANDEX_CASHBACK",
            "amount": 0.5
          }
        ],
        "currency": "RUR"
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибках в отчетах и документах](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#reports)
  
  
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
        default: 100
        maximum: 200
  headers: []
  body: |-
    {
      "dateFrom": "2025-01-01",
      "dateTo": "2025-01-01",
      "updateFrom": "2025-01-01",
      "updateTo": "2025-01-01",
      "orders": [
        0
      ],
      "statuses": [
        "CANCELLED_BEFORE_PROCESSING"
      ],
      "hasCis": true
    }
  schema:
    description: Запрос информации по заказам.
    type: object
    properties:
      dateFrom:
        description: |
          Начальная дата, когда заказ был сформирован.
  
          Формат даты: `ГГГГ‑ММ‑ДД`.
  
          Нельзя использовать вместе с параметрами `updateFrom` и `updateTo`.
        type: string
        format: date
      dateTo:
        description: |
          Конечная дата, когда заказ был сформирован.
  
          Формат даты: `ГГГГ‑ММ‑ДД`.
  
          Нельзя использовать вместе с параметрами `updateFrom` и `updateTo`.
        type: string
        format: date
      updateFrom:
        description: >
          Начальная дата периода, за который были изменения в заказе (например,
          статуса или информации о платежах).
  
  
          Формат даты: `ГГГГ‑ММ‑ДД`.
  
  
          Нельзя использовать вместе с параметрами `dateFrom` и `dateTo`.
        type: string
        format: date
      updateTo:
        description: >
          Конечная дата периода, за который были изменения в заказе (например,
          статуса или информации о платежах).
  
  
          Формат даты: `ГГГГ‑ММ‑ДД`.
  
  
          Нельзя использовать вместе с параметрами `dateFrom` и `dateTo`.
        type: string
        format: date
      orders:
        description: Список идентификаторов заказов.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: >
            Список товаров в заказе после возможных изменений.
  
  
            В ходе обработки заказа Маркет может удалить из него единицы товаров —
            при проблемах на складе или по инициативе пользователя.
  
  
            * Если из заказа удалены все единицы товара, его не будет в списке
            `items` — только в списке `initialItems`.
  
  
            * Если в заказе осталась хотя бы одна единица товара, он будет и в
            списке `items` (с уменьшенным количеством единиц `count`), и в списке
            `initialItems` (с первоначальным количеством единиц `initialCount`).
          type: integer
          format: int64
      statuses:
        description: Список статусов заказов.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: >
            Текущий статус заказа:
  
  
            * `CANCELLED_BEFORE_PROCESSING` — заказ отменен до начала его
            обработки.
  
  
            * `CANCELLED_IN_DELIVERY` — заказ отменен во время его доставки.
  
  
            * `CANCELLED_IN_PROCESSING` — заказ отменен во время его обработки.
  
  
            * `DELIVERY` — заказ передан службе доставки.
  
  
            * `DELIVERED` — заказ доставлен.
  
  
            * `PARTIALLY_DELIVERED` — заказ частично доставлен.
  
                {% note warning "Статус заказа может перейти в `PARTIALLY_DELIVERED` не сразу" %}
  
                Если в доставленном заказе был невыкуп, статус изменится только после получения заказа на складе Маркета.
  
                {% endnote %}
  
            * `PARTIALLY_RETURNED` — заказ частично возвращен покупателем.
  
  
            * `PENDING` — заказ ожидает подтверждения.
  
  
            * `PICKUP` — заказ доставлен в пункт выдачи.
  
  
            * `PROCESSING` — заказ в обработке.
  
  
            * `RESERVED` — товар зарезервирован на складе.
  
  
            * `RETURNED` — заказ полностью возвращен покупателем.
  
  
            * `UNKNOWN` — неизвестный статус заказа.
  
  
            * `UNPAID` — заказ от юридического лица ожидает оплаты.
  
  
            * `LOST` — заказ утерян.
          type: string
          enum:
            - CANCELLED_BEFORE_PROCESSING
            - CANCELLED_IN_DELIVERY
            - CANCELLED_IN_PROCESSING
            - DELIVERY
            - DELIVERED
            - PARTIALLY_DELIVERED
            - PARTIALLY_RETURNED
            - PENDING
            - PICKUP
            - PROCESSING
            - RESERVED
            - RETURNED
            - UNKNOWN
            - UNPAID
            - LOST
      hasCis:
        description: >
          Фильтр для получения заказов, в которых есть хотя бы один товар с кодом
          идентификации в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или
          [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов
          Market Yandex Go):
  
  
          * `true` — да.
  
          * `false` — нет.
  
          Такие коды присваиваются товарам, которые подлежат маркировке и
          относятся к определенным категориям.
        type: boolean
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
  path: v2/campaigns/{campaignId}/stats/orders
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders-stats/getOrdersStats.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
