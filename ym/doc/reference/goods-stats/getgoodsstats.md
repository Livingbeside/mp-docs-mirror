---
title: Отчет по товарам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md"
fetched_at: "2026-09-16T02:27:57Z"
content_sha: a570b6ccc18193ee
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/goods-stats/getGoodsStats.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/goods-stats/getGoodsStats.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/goods-stats/getGoodsStats.md -->
<div class="openapi">

# Отчет по товарам

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getGoodsStats.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getGoodsStats.md -->
  
  Возвращает подробный отчет по товарам, которые вы разместили на Маркете. С помощью отчета вы можете узнать, например, об остатках на складе, об условиях хранения ваших товаров и т. д.
  
  <!-- source: ru/_auto/method_limits/getGoodsStats.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 2 000 товаров в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 5 000 товаров в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getGoodsStats.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/stats/skus
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
    "shopSkus": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _shopSkus_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)[]
  
  Список ваших идентификаторов SKU.
  
  
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
  
  Отчет по товарам.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "shopSkus": [
        {
          "shopSku": "example",
          "marketSku": 1,
          "name": "example",
          "price": 0.5,
          "categoryId": 0,
          "categoryName": "example",
          "weightDimensions": {},
          "warehouses": [
            null
          ],
          "tariffs": [
            null
          ],
          "pictures": [
            null
          ]
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
    **Type**: [GoodsStatsDTO](#entity-GoodsStatsDTO)
  
    Отчет по товарам.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "shopSkus": [
        {
          "shopSku": "example",
          "marketSku": 1,
          "name": "example",
          "price": 0.5,
          "categoryId": 0,
          "categoryName": "example",
          "weightDimensions": {
            "length": 0.5,
            "width": 0.5,
            "height": 0.5,
            "weight": 0.5
          },
          "warehouses": [
            {
              "id": 0,
              "name": "example",
              "stocks": [
                null
              ]
            }
          ],
          "tariffs": [
            {
              "type": "AGENCY_COMMISSION",
              "percent": 0.5,
              "amount": 0.5,
              "currency": "RUR",
              "parameters": [
                null
              ]
            }
          ],
          "pictures": [
            "example"
          ]
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
        "shopSkus": [
          {
            "shopSku": "example",
            "marketSku": 1,
            "name": "example",
            "price": 0.5,
            "categoryId": 0,
            "categoryName": "example",
            "weightDimensions": {
              "length": 0.5,
              "width": 0.5,
              "height": 0.5,
              "weight": 0.5
            },
            "warehouses": [
              {}
            ],
            "tariffs": [
              {}
            ],
            "pictures": [
              "example"
            ]
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
  
  ### MarketSku {#entity-MarketSku}
  
  Идентификатор карточки товара на Маркете.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsStatsWeightDimensionsDTO {#entity-GoodsStatsWeightDimensionsDTO}
  
  Информация о весе и габаритах товара.
  
  Если товар уже привязан к карточке (`marketSku`), в ответе вернутся габариты из карточки Маркета, а не размеры, которые вы передаете.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _height_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Высота товара в сантиметрах.
  {.table-cell}
  ||
  ||
  
  _length_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Длина товара в сантиметрах.
  {.table-cell}
  ||
  ||
  
  _weight_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Вес товара в килограммах.
  {.table-cell}
  ||
  ||
  
  _width_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Ширина товара в сантиметрах.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "length": 0.5,
    "width": 0.5,
    "height": 0.5,
    "weight": 0.5
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
  
  ### GoodsStatsWarehouseDTO {#entity-GoodsStatsWarehouseDTO}
  
  Информация о складе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _stocks_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseStockDTO](#entity-WarehouseStockDTO)[]
  
  Информация об остатках товаров на складе.
  
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
    "name": "example",
    "stocks": [
      {
        "type": "FIT",
        "count": 0
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TariffType {#entity-TariffType}
  
  Услуга Маркета или дополнительный тариф к услуге размещения:
  
  * `AGENCY_COMMISSION` — прием платежа покупателя.
  
  * `PAYMENT_TRANSFER` — перевод платежа покупателя.
  
  * `STORAGE` — хранение товара на складе Маркета в течение суток.
  
  * `SURPLUS` — хранение излишков на складе Маркета.
  
  * `WITHDRAW` — вывоз товара со склада Маркета.
  
  * `FEE` — размещение товара на Маркете.
  
  * `DELIVERY_TO_CUSTOMER` — доставка покупателю.
  
  * `CROSSREGIONAL_DELIVERY` — доставка в федеральный округ, город или населенный пункт.
  
  * `CROSSREGIONAL_DELIVERY_RETURN` — доставка невыкупов и возвратов.
  
  * `DISPOSAL` — утилизация.
  
  * `SORTING_CENTER_STORAGE` — хранение невыкупов и возвратов.
  
  * `EXPRESS_DELIVERY` — экспресс-доставка покупателю.
  
  * `FF_XDOC_SUPPLY_BOX` — поставка товара через транзитный склад (за короб).
  
  * `FF_XDOC_SUPPLY_PALLET` — поставка товара через транзитный склад (за палету).
  
  * `SORTING` — обработка заказа.
  
  * `MIDDLE_MILE` — средняя миля.
  
  * `RETURN_PROCESSING` — обработка невыкупов и возвратов.
  
  * `EXPRESS_CANCELLED_BY_PARTNER` — отмена заказа с экспресс-доставкой.
  
  * `CROSSBORDER_DELIVERY` — доставка из-за рубежа.
  
  * `INTAKE_SORTING_BULKY_CARGO` — сортировка заказов с крупногабаритными товарами, которые Маркет забрал со склада продавца.
  
  * `INTAKE_SORTING_SMALL_GOODS` — сортировка заказов с малогабаритными товарами, которые Маркет забрал со склада продавца.
  
  * `INTAKE_SORTING_DAILY` — организация забора заказов со склада продавца.
  
  * `FF_STORAGE_BILLING` — хранение товаров на складе.
  
  * `CANCELLED_ORDER_FEE_QI` — отмена заказа по вине продавца.
  
  * `LATE_ORDER_EXECUTION_FEE_QI` — несвоевременная отгрузка или доставка.
  
  * `VOLUME_STORAGE` — стоимость хранения товара на складе — из расчёта за один кубический метр в сутки.
  
  * `GOODS_ACCEPTANCE` — окончательная приемка товара на складе.
  
  * `CARGO_ACCEPTANCE` — первичная приемка товара на складе.
  
  * `ORDER_PROCESSING` — обработка заказа.
  
  * `WITHDRAW_EXTERNAL` — отгрузка на внешний маркетплейс.
  
  * `ITEM_BOOKING` — бронирование товара.
  
  Подробнее об услугах Маркета читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/introduction/rates/index.html).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `AGENCY_COMMISSION`, `PAYMENT_TRANSFER`, `STORAGE`, `WITHDRAW`, `SURPLUS`, `FEE`, `DELIVERY_TO_CUSTOMER`, `CROSSREGIONAL_DELIVERY`, `CROSSREGIONAL_DELIVERY_RETURN`, `DISPOSAL`, `SORTING_CENTER_STORAGE`, `EXPRESS_DELIVERY`, `FF_XDOC_SUPPLY_BOX`, `FF_XDOC_SUPPLY_PALLET`, `SORTING`, `MIDDLE_MILE`, `RETURN_PROCESSING`, `EXPRESS_CANCELLED_BY_PARTNER`, `CROSSBORDER_DELIVERY`, `INTAKE_SORTING_BULKY_CARGO`, `INTAKE_SORTING_SMALL_GOODS`, `INTAKE_SORTING_DAILY`, `FF_STORAGE_BILLING`, `CANCELLED_ORDER_FEE_QI`, `LATE_ORDER_EXECUTION_FEE_QI`, `VOLUME_STORAGE`, `GOODS_ACCEPTANCE`, `CARGO_ACCEPTANCE`, `ORDER_PROCESSING`, `WITHDRAW_EXTERNAL`, `ITEM_BOOKING`
  
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
  
  ### TariffParameterDTO {#entity-TariffParameterDTO}
  
  Детали расчета конкретной услуги Маркета.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  {% cut "Название параметра." %}
  
  Параметр `name` может принимать следующие значения:
  
  **Основные параметры:**
    - `value` — значение тарифа.
    - `billingUnit` — единицы измерения для товара.
    - `valueType` — тип значения тарифа: `absolute` (денежное значение) или `relative` (процент).
    - `priceDependence` — зависимость тарифа от цены товара.
  
  **Параметры диапазонов цен товара:**
  - `priceFrom` — минимальная цена товара, от которой применяется тариф.
  - `priceTo` — максимальная цена товара, до которой применяется тариф.
  
  **Параметры ограничений значения тарифа:**
  - `minValue` — минимальное значение тарифа.
  - `maxValue` — максимальное значение тарифа.
  
  **Параметры диапазонов дней:**
  - `dayFrom` — день, с которого начинает действовать тариф (для хранения).
  - `dayTo` — день, на который тариф прекращает действие (для хранения).
  
  **Параметры маршрута транзитной поставки:**
  - `xdocFrom` — начальная точка маршрута.
  - `xdocTo` — конечная точка маршрута.
  
  **Параметры частоты:**
  - `frequency` — частота выплат.
  - `paymentDelayWeeks` — отсрочка выплат при еженедельном графике — сколько недель назад были доставлены заказы, за которые приходит выплата.
  
  **Параметры складов и логистики:**
  - `transitWarehouseType` — тип места привоза товаров продавцом.
  - `orderCargoType` — тип груза заказа.
  
  **Параметры оборачиваемости:**
  - `turnoverFrom` — нижняя граница диапазона оборачиваемости, начиная с которой применяется тариф.
  - `turnoverTo` — верхняя граница диапазона оборачиваемости, исключая которую применяется тариф.
  
  **Параметры рейтинга:**
  - `ratingLowerBound` — нижняя граница диапазона рейтинга, по которому применяется тариф.
  - `ratingUpperBound` — верхняя граница диапазона рейтинга, по которому применяется тариф.
  
  **Параметры количества заказов:**
  - `fromOrders` — количество заказов, начиная с которого применяется тариф (включительно).
  - `toOrders` — количество заказов, до которого применяется тариф (не включительно).
  
  **Параметры доставки из-за рубежа:**
  - `shippingPrice` — стоимость отправления при доставке из-за рубежа.
  - `totalSurchargeForWeight` — сумма наценки за вес отправления при доставке из-за рубежа.
  
  {% note info "Не все параметры возвращаются для каждого тарифа." %}
  
  Набор параметров зависит от типа услуги и условий применения тарифа.
  
  {% endnote %}
  
  {% endcut %}
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Значение параметра.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "name": "example",
    "value": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TariffDTO {#entity-TariffDTO}
  
  Информация о тарифах, по которым нужно заплатить за услуги Маркета.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Значение тарифа.
  {.table-cell}
  ||
  ||
  
  _currency_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта, в которой указано значение тарифа.
  
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
  
  _parameters_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TariffParameterDTO](#entity-TariffParameterDTO)[]
  
  Параметры расчета тарифа.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "name": "example",
      "value": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TariffType](#entity-TariffType)
  
  Услуга Маркета, за которую начисляется тариф.
  
  Услуга Маркета или дополнительный тариф к услуге размещения:
  
  * `AGENCY_COMMISSION` — прием платежа покупателя.
  
  * `PAYMENT_TRANSFER` — перевод платежа покупателя.
  
  * `STORAGE` — хранение товара на складе Маркета в течение суток.
  
  * `SURPLUS` — хранение излишков на складе Маркета.
  
  * `WITHDRAW` — вывоз товара со склада Маркета.
  
  * `FEE` — размещение товара на Маркете.
  
  * `DELIVERY_TO_CUSTOMER` — доставка покупателю.
  
  * `CROSSREGIONAL_DELIVERY` — доставка в федеральный округ, город или населенный пункт.
  
  * `CROSSREGIONAL_DELIVERY_RETURN` — доставка невыкупов и возвратов.
  
  * `DISPOSAL` — утилизация.
  
  * `SORTING_CENTER_STORAGE` — хранение невыкупов и возвратов.
  
  * `EXPRESS_DELIVERY` — экспресс-доставка покупателю.
  
  * `FF_XDOC_SUPPLY_BOX` — поставка товара через транзитный склад (за короб).
  
  * `FF_XDOC_SUPPLY_PALLET` — поставка товара через транзитный склад (за палету).
  
  * `SORTING` — обработка заказа.
  
  * `MIDDLE_MILE` — средняя миля.
  
  * `RETURN_PROCESSING` — обработка невыкупов и возвратов.
  
  * `EXPRESS_CANCELLED_BY_PARTNER` — отмена заказа с экспресс-доставкой.
  
  * `CROSSBORDER_DELIVERY` — доставка из-за рубежа.
  
  * `INTAKE_SORTING_BULKY_CARGO` — сортировка заказов с крупногабаритными товарами, которые Маркет забрал со склада продавца.
  
  * `INTAKE_SORTING_SMALL_GOODS` — сортировка заказов с малогабаритными товарами, которые Маркет забрал со склада продавца.
  
  * `INTAKE_SORTING_DAILY` — организация забора заказов со склада продавца.
  
  * `FF_STORAGE_BILLING` — хранение товаров на складе.
  
  * `CANCELLED_ORDER_FEE_QI` — отмена заказа по вине продавца.
  
  * `LATE_ORDER_EXECUTION_FEE_QI` — несвоевременная отгрузка или доставка.
  
  * `VOLUME_STORAGE` — стоимость хранения товара на складе — из расчёта за один кубический метр в сутки.
  
  * `GOODS_ACCEPTANCE` — окончательная приемка товара на складе.
  
  * `CARGO_ACCEPTANCE` — первичная приемка товара на складе.
  
  * `ORDER_PROCESSING` — обработка заказа.
  
  * `WITHDRAW_EXTERNAL` — отгрузка на внешний маркетплейс.
  
  * `ITEM_BOOKING` — бронирование товара.
  
  Подробнее об услугах Маркета читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/introduction/rates/index.html).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `AGENCY_COMMISSION`, `PAYMENT_TRANSFER`, `STORAGE`, `WITHDRAW`, `SURPLUS`, `FEE`, `DELIVERY_TO_CUSTOMER`, `CROSSREGIONAL_DELIVERY`, `CROSSREGIONAL_DELIVERY_RETURN`, `DISPOSAL`, `SORTING_CENTER_STORAGE`, `EXPRESS_DELIVERY`, `FF_XDOC_SUPPLY_BOX`, `FF_XDOC_SUPPLY_PALLET`, `SORTING`, `MIDDLE_MILE`, `RETURN_PROCESSING`, `EXPRESS_CANCELLED_BY_PARTNER`, `CROSSBORDER_DELIVERY`, `INTAKE_SORTING_BULKY_CARGO`, `INTAKE_SORTING_SMALL_GOODS`, `INTAKE_SORTING_DAILY`, `FF_STORAGE_BILLING`, `CANCELLED_ORDER_FEE_QI`, `LATE_ORDER_EXECUTION_FEE_QI`, `VOLUME_STORAGE`, `GOODS_ACCEPTANCE`, `CARGO_ACCEPTANCE`, `ORDER_PROCESSING`, `WITHDRAW_EXTERNAL`, `ITEM_BOOKING`
  {.table-cell}
  ||
  ||
  
  _percent_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `amount`.
  
  {% endnote %}
  
  Значение тарифа в процентах.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "AGENCY_COMMISSION",
    "percent": 0.5,
    "amount": 0.5,
    "currency": "RUR",
    "parameters": [
      {
        "name": "example",
        "value": "example"
      }
    ]
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
  
  ### GoodsStatsGoodsDTO {#entity-GoodsStatsGoodsDTO}
  
  Информация о товаре.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор категории товара на Маркете.
  {.table-cell}
  ||
  ||
  
  _categoryName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название категории товара на Маркете.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _marketSku_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MarketSku](#entity-MarketSku)
  
  SKU на Маркете — идентификатор карточки товара на Маркете.
  
  Идентификатор карточки товара на Маркете.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _pictures_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)[] &#124; null
  
  Ссылки (URL) изображений товара в хорошем качестве.
  
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
  
  _price_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Цена товара в валюте, которая установлена [в кабинете продавца на Маркете](https://partner.market.yandex.ru/).
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
  
  _tariffs_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TariffDTO](#entity-TariffDTO)[] &#124; null
  
  Информация о тарифах, по которым нужно заплатить за услуги Маркета.
  
  По некоторым услугам могут возвращаться несколько разных стоимостей. Например, в модели FBS стоимость услуги `SORTING` (обработка заказа) зависит от способа отгрузки
  и количества заказов в отгрузке. Подробнее о тарифах на услуги читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/introduction/rates/models/).
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "AGENCY_COMMISSION",
      "percent": 0.5,
      "amount": 0.5,
      "currency": "RUR",
      "parameters": [
        {
          "name": "example",
          "value": "example"
        }
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warehouses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsStatsWarehouseDTO](#entity-GoodsStatsWarehouseDTO)[] &#124; null
  
  Информация о складах, на которых хранится товар.
  
  Параметр не приходит, если товара нет ни на одном складе.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "name": "example",
      "stocks": [
        {
          "type": "FIT",
          "count": 0
        }
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _weightDimensions_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GoodsStatsWeightDimensionsDTO](#entity-GoodsStatsWeightDimensionsDTO)
  
  Информация о весе и габаритах товара.
  Если товар уже привязан к карточке (`marketSku`), в ответе вернутся габариты из карточки Маркета, а не размеры, которые вы передаете.
  
  
  Информация о весе и габаритах товара.
  
  Если товар уже привязан к карточке (`marketSku`), в ответе вернутся габариты из карточки Маркета, а не размеры, которые вы передаете.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "length": 0.5,
    "width": 0.5,
    "height": 0.5,
    "weight": 0.5
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "shopSku": "example",
    "marketSku": 1,
    "name": "example",
    "price": 0.5,
    "categoryId": 0,
    "categoryName": "example",
    "weightDimensions": {
      "length": 0.5,
      "width": 0.5,
      "height": 0.5,
      "weight": 0.5
    },
    "warehouses": [
      {
        "id": 0,
        "name": "example",
        "stocks": [
          {
            "type": "FIT",
            "count": 0
          }
        ]
      }
    ],
    "tariffs": [
      {
        "type": "AGENCY_COMMISSION",
        "percent": 0.5,
        "amount": 0.5,
        "currency": "RUR",
        "parameters": [
          {
            "name": "example",
            "value": "example"
          }
        ]
      }
    ],
    "pictures": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GoodsStatsDTO {#entity-GoodsStatsDTO}
  
  Отчет по товарам.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _shopSkus_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GoodsStatsGoodsDTO](#entity-GoodsStatsGoodsDTO)[]
  
  Список товаров.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "shopSku": "example",
      "marketSku": 1,
      "name": "example",
      "price": 0.5,
      "categoryId": 0,
      "categoryName": "example",
      "weightDimensions": {
        "length": 0.5,
        "width": 0.5,
        "height": 0.5,
        "weight": 0.5
      },
      "warehouses": [
        {
          "id": 0,
          "name": "example",
          "stocks": [
            {}
          ]
        }
      ],
      "tariffs": [
        {
          "type": "AGENCY_COMMISSION",
          "percent": 0.5,
          "amount": 0.5,
          "currency": "RUR",
          "parameters": [
            {}
          ]
        }
      ],
      "pictures": [
        "example"
      ]
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
    "shopSkus": [
      {
        "shopSku": "example",
        "marketSku": 1,
        "name": "example",
        "price": 0.5,
        "categoryId": 0,
        "categoryName": "example",
        "weightDimensions": {
          "length": 0.5,
          "width": 0.5,
          "height": 0.5,
          "weight": 0.5
        },
        "warehouses": [
          {
            "id": 0,
            "name": "example",
            "stocks": [
              null
            ]
          }
        ],
        "tariffs": [
          {
            "type": "AGENCY_COMMISSION",
            "percent": 0.5,
            "amount": 0.5,
            "currency": "RUR",
            "parameters": [
              null
            ]
          }
        ],
        "pictures": [
          "example"
        ]
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
      "shopSkus": [
        "example"
      ]
    }
  schema:
    description: Запрос отчета по товарам.
    type: object
    required:
      - shopSkus
    properties:
      shopSkus:
        description: |
          Список ваших идентификаторов SKU.
        type: array
        uniqueItems: true
        items:
          description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
          type: string
          pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
          x-transform: trim
          minLength: 1
          maxLength: 255
        minItems: 1
        maxItems: 500
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
  path: v2/campaigns/{campaignId}/stats/skus
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/goods-stats/getGoodsStats.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
