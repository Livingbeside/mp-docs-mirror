---
title: Получение доступных вариантов доставки
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md"
fetched_at: "2026-08-28T11:52:21Z"
content_sha: efbd1cdea97c1650
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/delivery-options/getDeliveryOptions.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/delivery-options/getDeliveryOptions.md
  - href: ru/reference/delivery-options/getDeliveryOptions.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/delivery-options/getDeliveryOptions.md -->
<div class="openapi">

# Получение доступных вариантов доставки заказов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getDeliveryOptions.md -->
  **Метод доступен для модели [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * pricing:read-only — [Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getDeliveryOptions.md -->
  
  Возвращает список вариантов для доставки заказов. Выберите подходящий вариант доставки из ответа и передайте его при создании заказа.
  
  Укажите `courierDelivery` для курьерской доставки или `pickupDelivery` для доставки в пункт выдачи. Не передавайте оба параметра одновременно.
  
  <!-- source: ru/_auto/method_limits/getDeliveryOptions.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getDeliveryOptions.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/campaigns/{campaignId}/delivery-options
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
    "items": [
      {
        "offerId": "example",
        "count": 1,
        "warehouseId": 1
      }
    ],
    "pickupDelivery": {
      "logisticPointsIds": [
        1
      ]
    },
    "courierDelivery": {
      "fullAddress": "example"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetDeliveryOptionsItemDTO](#entity-GetDeliveryOptionsItemDTO)[]
  
  Товары на складах, для которых нужно вернуть варианты доставки.
  
  В рамках одного запроса все значения `offerId` должны быть уникальными. Не допускается передача двух объектов с одинаковым `offerId`.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `1000`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "count": 1,
      "warehouseId": 1
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _courierDelivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CourierDeliveryParametersDTO](#entity-CourierDeliveryParametersDTO)
  
  Информация о курьерской доставке.
  
  Не передавайте вместе с `pickupDelivery`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pickupDelivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PickupDeliveryParametersDTO](#entity-PickupDeliveryParametersDTO)
  
  Информация о доставке в пункт выдачи.
  
  Не передавайте вместе с `courierDelivery`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "logisticPointsIds": [
      1
    ]
  }
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
  
  <div class="openapi-entity">
  
  ### BasicOrderItemDTO {#entity-BasicOrderItemDTO}
  
  Товар в заказе или возврате.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `1000`
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "count": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetDeliveryOptionsItemDTO {#entity-GetDeliveryOptionsItemDTO}
  
  Товар, для которого нужно вернуть варианты доставки.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BasicOrderItemDTO](#entity-BasicOrderItemDTO)
  
    Товар в заказе или возврате.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offerId": "example",
      "count": 1
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _warehouseId_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: integer
  
    Идентификатор фулфилмент-склада Маркета.
  
    Передайте этот параметр, чтобы вернулись варианты доставки для указанного склада. Иначе Маркет сам выберет склад.
  
    [Как узнать остатки товаров на складах](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)
  
  
    _Min value:_{.json-schema-reset .json-schema-assertion} `1`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "warehouseId": 1
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "count": 1,
    "warehouseId": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointId {#entity-LogisticPointId}
  
  Идентификатор пункта выдачи.
  
  Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PickupDeliveryParametersDTO {#entity-PickupDeliveryParametersDTO}
  
  Информация о доставке в пункт выдачи.
  
  Не передавайте вместе с `courierDelivery`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _logisticPointsIds_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointId](#entity-LogisticPointId)[]
  
  Идентификаторы пунктов выдачи.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `20`
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "logisticPointsIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CourierDeliveryParametersDTO {#entity-CourierDeliveryParametersDTO}
  
  Информация о курьерской доставке.
  
  Не передавайте вместе с `pickupDelivery`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fullAddress_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Полный адрес с точностью до номера дома.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список доступных вариантов доставки с разных складов.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "warehousesDeliveryOptions": [
        {
          "warehouseId": 1,
          "deliveryOptions": {},
          "items": [
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
    **Type**: [GetDeliveryOptionsDTO](#entity-GetDeliveryOptionsDTO)
  
    Список доступных вариантов для разных складов.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "warehousesDeliveryOptions": [
        {
          "warehouseId": 1,
          "deliveryOptions": {
            "pickupDelivery": {
              "pickupOptions": [
                null
              ]
            },
            "courierDelivery": {
              "courierDeliveryOptions": [
                null
              ]
            }
          },
          "items": [
            {
              "offerId": "example",
              "count": 1
            }
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
        "warehousesDeliveryOptions": [
          {
            "warehouseId": 1,
            "deliveryOptions": {
              "pickupDelivery": {},
              "courierDelivery": {}
            },
            "items": [
              {}
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
  
  ### WarehouseId {#entity-WarehouseId}
  
  Идентификатор фулфилмент-склада Маркета.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryDateIntervalDTO {#entity-DeliveryDateIntervalDTO}
  
  Интервал дат доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начало интервала.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _toDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конец интервала.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
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
  
  ### CurrencyValueDTO {#entity-CurrencyValueDTO}
  
  Валюта и ее значение.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _currencyId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта.
  
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
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Значение.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryOptionPriceDTO {#entity-DeliveryOptionPriceDTO}
  
  Стоимость, которую магазин должен заплатить за доставку с выбранным вариантом.
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
    Валюта и ее значение.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0.5,
      "currencyId": "RUR"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PickupOptionDTO {#entity-PickupOptionDTO}
  
  Временной интервал и стоимость доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryDateInterval_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryDateIntervalDTO](#entity-DeliveryDateIntervalDTO)
  
  Интервал дат доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _price_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryOptionPriceDTO](#entity-DeliveryOptionPriceDTO)
  
  Стоимость, которую магазин должен заплатить за доставку с выбранным вариантом.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "deliveryDateInterval": {
      "fromDate": "2025-01-01",
      "toDate": "2025-01-01"
    },
    "price": {
      "value": 0.5,
      "currencyId": "RUR"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryPaymentType {#entity-DeliveryPaymentType}
  
  Тип оплаты заказа:
  
  * `PREPAID` — оплата при оформлении заказа.
  
  
  **Type**: string
  
  _Const:_{.json-schema-reset .json-schema-value} `PREPAID`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PickupOptionsDTO {#entity-PickupOptionsDTO}
  
  Временной интервал, идентификатор пункта выдачи и способ оплаты.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _logisticPointId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointId](#entity-LogisticPointId)
  
  Идентификатор пункта выдачи.
  
  Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _options_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PickupOptionDTO](#entity-PickupOptionDTO)[]
  
  Варианты доставки в ПВЗ.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "deliveryDateInterval": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01"
      },
      "price": {
        "value": 0.5,
        "currencyId": "RUR"
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
    "logisticPointId": 1,
    "options": [
      {
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "price": {
          "value": 0.5,
          "currencyId": "RUR"
        }
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PickupDeliveryOptionsDTO {#entity-PickupDeliveryOptionsDTO}
  
  Информация о доставке в пункт выдачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _pickupOptions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PickupOptionsDTO](#entity-PickupOptionsDTO)[]
  
  Информация о доставке в пункт выдачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "logisticPointId": 1,
      "options": [
        {
          "deliveryDateInterval": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01"
          },
          "price": {}
        }
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
    "pickupOptions": [
      {
        "logisticPointId": 1,
        "options": [
          {
            "deliveryDateInterval": {},
            "price": {}
          }
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TimeIntervalDTO {#entity-TimeIntervalDTO}
  
  Интервал времени доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Начало интервала.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _toTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Конец интервала.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromTime": "example",
    "toTime": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CourierDeliveryOptionDTO {#entity-CourierDeliveryOptionDTO}
  
  Временные интервалы и способ оплаты.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryDateInterval_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryDateIntervalDTO](#entity-DeliveryDateIntervalDTO)
  
  Интервал дат доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryTimeInterval_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TimeIntervalDTO](#entity-TimeIntervalDTO)
  
  Интервал времени доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromTime": "example",
    "toTime": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _price_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryOptionPriceDTO](#entity-DeliveryOptionPriceDTO)
  
  Стоимость, которую магазин должен заплатить за доставку с выбранным вариантом.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "deliveryDateInterval": {
      "fromDate": "2025-01-01",
      "toDate": "2025-01-01"
    },
    "deliveryTimeInterval": {
      "fromTime": "example",
      "toTime": "example"
    },
    "price": {
      "value": 0.5,
      "currencyId": "RUR"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CourierDeliveryOptionsDTO {#entity-CourierDeliveryOptionsDTO}
  
  Информация о курьерской доставке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _courierDeliveryOptions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CourierDeliveryOptionDTO](#entity-CourierDeliveryOptionDTO)[]
  
  Информация о курьерской доставке.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "deliveryDateInterval": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01"
      },
      "deliveryTimeInterval": {
        "fromTime": "example",
        "toTime": "example"
      },
      "price": {
        "value": 0.5,
        "currencyId": "RUR"
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
    "courierDeliveryOptions": [
      {
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        },
        "price": {
          "value": 0.5,
          "currencyId": "RUR"
        }
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseDeliveryOptionsDTO {#entity-WarehouseDeliveryOptionsDTO}
  
  Варианты доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _courierDelivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CourierDeliveryOptionsDTO](#entity-CourierDeliveryOptionsDTO)
  
  Информация о курьерской доставке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "courierDeliveryOptions": [
      {
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        },
        "price": {
          "value": 0.5,
          "currencyId": "RUR"
        }
      }
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pickupDelivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PickupDeliveryOptionsDTO](#entity-PickupDeliveryOptionsDTO)
  
  Информация о доставке в пункт выдачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "pickupOptions": [
      {
        "logisticPointId": 1,
        "options": [
          {
            "deliveryDateInterval": {},
            "price": {}
          }
        ]
      }
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
    "pickupDelivery": {
      "pickupOptions": [
        {
          "logisticPointId": 1,
          "options": [
            {}
          ]
        }
      ]
    },
    "courierDelivery": {
      "courierDeliveryOptions": [
        {
          "deliveryDateInterval": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01"
          },
          "deliveryTimeInterval": {
            "fromTime": "example",
            "toTime": "example"
          },
          "price": {}
        }
      ]
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehousesDeliveryOptionsDTO {#entity-WarehousesDeliveryOptionsDTO}
  
  Варианты доставки со склада.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryOptions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseDeliveryOptionsDTO](#entity-WarehouseDeliveryOptionsDTO)
  
  Варианты доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "pickupDelivery": {
      "pickupOptions": [
        {
          "logisticPointId": 1,
          "options": [
            {}
          ]
        }
      ]
    },
    "courierDelivery": {
      "courierDeliveryOptions": [
        {
          "deliveryDateInterval": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01"
          },
          "deliveryTimeInterval": {
            "fromTime": "example",
            "toTime": "example"
          },
          "price": {}
        }
      ]
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BasicOrderItemDTO](#entity-BasicOrderItemDTO)[]
  
  Товары в заказе.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "count": 1
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warehouseId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseId](#entity-WarehouseId)
  
  Идентификатор фулфилмент-склада Маркета.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "warehouseId": 1,
    "deliveryOptions": {
      "pickupDelivery": {
        "pickupOptions": [
          {
            "logisticPointId": 1,
            "options": [
              null
            ]
          }
        ]
      },
      "courierDelivery": {
        "courierDeliveryOptions": [
          {
            "deliveryDateInterval": {},
            "deliveryTimeInterval": {},
            "price": {}
          }
        ]
      }
    },
    "items": [
      {
        "offerId": "example",
        "count": 1
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetDeliveryOptionsDTO {#entity-GetDeliveryOptionsDTO}
  
  Список доступных вариантов для разных складов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _warehousesDeliveryOptions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehousesDeliveryOptionsDTO](#entity-WarehousesDeliveryOptionsDTO)[]
  
  Варианты доставки для разных складов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "warehouseId": 1,
      "deliveryOptions": {
        "pickupDelivery": {
          "pickupOptions": [
            {}
          ]
        },
        "courierDelivery": {
          "courierDeliveryOptions": [
            {}
          ]
        }
      },
      "items": [
        {
          "offerId": "example",
          "count": 1
        }
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
    "warehousesDeliveryOptions": [
      {
        "warehouseId": 1,
        "deliveryOptions": {
          "pickupDelivery": {
            "pickupOptions": [
              null
            ]
          },
          "courierDelivery": {
            "courierDeliveryOptions": [
              null
            ]
          }
        },
        "items": [
          {
            "offerId": "example",
            "count": 1
          }
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с заказами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#orders)
  
  
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
      "items": [
        {
          "offerId": "example",
          "count": 1,
          "warehouseId": 1
        }
      ],
      "pickupDelivery": {
        "logisticPointsIds": [
          1
        ]
      },
      "courierDelivery": {
        "fullAddress": "example"
      }
    }
  schema:
    type: object
    description: >
      Запрос для получения вариантов доставки.
  
  
      Используйте `pickupDelivery` для получения вариантов доставки самовывозом и
      `courierDelivery` для получения вариантов доставки курьером.
    required:
      - items
    properties:
      items:
        type: array
        description: >
          Товары на складах, для которых нужно вернуть варианты доставки.
  
  
          В рамках одного запроса все значения `offerId` должны быть уникальными.
          Не допускается передача двух объектов с одинаковым `offerId`.
        minItems: 1
        maxItems: 1000
        items:
          description: Товар, для которого нужно вернуть варианты доставки.
          type: object
          allOf:
            - description: Товар в заказе или возврате.
              type: object
              required:
                - offerId
                - count
              properties:
                offerId:
                  description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
                  type: string
                  pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
                  x-transform: trim
                  minLength: 1
                  maxLength: 255
                count:
                  description: Количество единиц товара.
                  type: integer
                  format: int32
                  minimum: 1
                  maximum: 1000
            - properties:
                warehouseId:
                  description: >
                    Идентификатор фулфилмент-склада Маркета.
  
  
                    Передайте этот параметр, чтобы вернулись варианты доставки для
                    указанного склада. Иначе Маркет сам выберет склад.
  
  
                    [Как узнать остатки товаров на
                    складах](../../reference/stocks/getStocks.md)
                  type: integer
                  format: int64
                  minimum: 1
      pickupDelivery:
        type: object
        description: |
          Информация о доставке в пункт выдачи.
  
          Не передавайте вместе с `courierDelivery`.
        required:
          - logisticPointsIds
        properties:
          logisticPointsIds:
            description: Идентификаторы пунктов выдачи.
            type: array
            minItems: 1
            maxItems: 20
            uniqueItems: true
            items:
              type: integer
              description: "Идентификатор пункта выдачи.\n\nЕго можно узнать с помощью метода [POST\_v1/businesses/{businessId}/logistics-points](../../reference/logistic-points/getLogisticPoints.md).\n"
              format: int64
              minimum: 1
      courierDelivery:
        type: object
        description: |
          Информация о курьерской доставке.
  
          Не передавайте вместе с `pickupDelivery`.
        required:
          - fullAddress
        properties:
          fullAddress:
            type: string
            description: Полный адрес с точностью до номера дома.
            minLength: 1
            maxLength: 512
      fake:
        x-hidden: true
        type: boolean
        description: >
          Скрытый параметр. Если `true`, то гарантированно возвращает опции для
          дефолтного склада, вне зависимости от наличия остатков.
        default: false
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
  path: v1/campaigns/{campaignId}/delivery-options
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/delivery-options/getDeliveryOptions.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
