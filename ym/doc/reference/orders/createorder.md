---
title: Создание заказа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md"
fetched_at: "2026-09-16T02:27:34Z"
content_sha: a9428f8e8f639d5b
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/createOrder.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/createOrder.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/createOrder.md -->
<div class="openapi">

# Создание заказа

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/createOrder.md -->
  **Метод доступен для модели [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/createOrder.md -->
  
  Создает новый заказ, если на складе Маркета есть нужное количество товаров.
  
  Укажите `courierDelivery` для курьерской доставки или `pickupDelivery` для доставки в пункт выдачи. Не передавайте оба параметра одновременно.
  
  Значение параметра `draft`:
  
  * `true` — Маркет создаст заказ в статусе `RESERVED` и будет ждать подтверждения от магазина. Когда будете готовы, передайте статус `PROCESSING` с подстатусом `STARTED` в методе [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md). Если не сделать это в течение часа после создания заказа, Маркет отменит его.
  * `false` — Маркет создаст заказ в статусе `PROCESSING` с подстатусом `STARTED`, подтверждение не требуется.
  
  Значение параметра `fake`:
  
  * `true` — тестовый заказ. Позволяет проверить работу магазина и его API на [тестовых заказах](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md). Такой заказ не будет отгружен и не влияет на остатки.
  * `false` — настоящий заказ.
  
  {% note warning "Перед вызовом метода" %}
  
  Получите доступные варианты доставки — [POST v2/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md).
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/createOrder.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/createOrder.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/campaigns/{campaignId}/orders/create
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
    "order": {
      "externalOrderId": "example",
      "itemsDelivery": [
        {
          "warehouseId": 1,
          "items": [
            {}
          ],
          "deliveryDateInterval": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01"
          },
          "deliveryTimeInterval": {
            "fromTime": "example",
            "toTime": "example"
          }
        }
      ],
      "destination": {
        "pickupDelivery": {
          "logisticPointId": 1
        },
        "courierDelivery": {
          "address": {},
          "notes": "example"
        }
      },
      "customer": {
        "firstName": "example",
        "lastName": "example",
        "middleName": "example",
        "phone": "example"
      },
      "packaging": {
        "packageType": "WHITELABEL"
      },
      "paymentType": "PREPAID",
      "draft": false,
      "fake": false
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _order_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateOrderDTO](#entity-CreateOrderDTO)
  
  Информация о заказе.
  
  Передайте выбранный вариант доставки из ответа метода [POST v1/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md).
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "externalOrderId": "example",
    "itemsDelivery": [
      {
        "warehouseId": 1,
        "items": [
          {}
        ],
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        }
      }
    ],
    "destination": {
      "pickupDelivery": {
        "logisticPointId": 1
      },
      "courierDelivery": {
        "address": {
          "fullAddress": "example",
          "entrance": "example",
          "floor": 0,
          "apartment": "example"
        },
        "notes": "example"
      }
    },
    "customer": {
      "firstName": "example",
      "lastName": "example",
      "middleName": "example",
      "phone": "example"
    },
    "packaging": {
      "packageType": "WHITELABEL"
    },
    "paymentType": "PREPAID",
    "draft": false,
    "fake": false
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
  
  ### BasePriceDTO {#entity-BasePriceDTO}
  
  Цена товара.
  
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
  
  Цена товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderVatType {#entity-OrderVatType}
  
  НДС на товар или доставку:
  
  * `NO_VAT` — НДС не облагается, используется только для отдельных видов услуг.
  
  * `VAT_0` — НДС 0%. Например, используется при продаже товаров, вывезенных в таможенной процедуре экспорта, или при оказании услуг по международной перевозке товаров.
  
  * `VAT_10` — НДС 10%. Например, используется при реализации отдельных продовольственных и медицинских товаров.
  
  * `VAT_10_110` — НДС 10/110. НДС 10%, применяется только при предоплате.
  
  * `VAT_20` — НДС 20%. Основной НДС с 2019 года до 1 января 2026 года.
  
  * `VAT_20_120` — НДС 20/120. НДС 20%, применяется только при предоплате.
  
  * `VAT_18` — НДС 18%. Основной НДС до 2019 года.
  
  * `VAT_18_118` — НДС 18/118. НДС использовался до 1 января 2019 года при предоплате.
  
  * `VAT_12` — НДС 12%. Используется только в Узбекистане.
  
  * `VAT_05` — НДС 5%. НДС для упрощенной системы налогообложения (УСН).
  
  * `VAT_07` — НДС 7%. НДС для упрощенной системы налогообложения (УСН).
  
  * `VAT_22` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  * `UNKNOWN_VALUE` — неизвестный тип.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `NO_VAT`, `VAT_0`, `VAT_10`, `VAT_10_110`, `VAT_20`, `VAT_20_120`, `VAT_18`, `VAT_18_118`, `VAT_12`, `VAT_05`, `VAT_07`, `VAT_22`, `UNKNOWN_VALUE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateOrderItemDTO {#entity-CreateOrderItemDTO}
  
  Товар в заказе.
  
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
  
    _price_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [BasePriceDTO](#entity-BasePriceDTO)
  
    Цена товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR"
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
      "price": {
        "value": 0,
        "currencyId": "RUR"
      }
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "count": 1,
    "price": {
      "value": 0,
      "currencyId": "RUR"
    }
  }
  ```
  
  {% endcut %}
  
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
  
  ### CreateOrderWarehouseItemsDTO {#entity-CreateOrderWarehouseItemsDTO}
  
  Список товаров в заказе.
  
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
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateOrderItemDTO](#entity-CreateOrderItemDTO)[]
  
  Список товаров в заказе.
  
  В рамках одного запроса все значения `offerId` должны быть уникальными. Не допускается передача двух объектов с одинаковым `offerId`.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `1000`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "count": 1,
      "price": {
        "value": 0,
        "currencyId": "RUR"
      }
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warehouseId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор фулфилмент-склада Маркета.
  
  Получите его с помощью метода [POST v2/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _deliveryTimeInterval_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimeIntervalDTO](#entity-TimeIntervalDTO)
  
  Интервал времени доставки.
  
  Обязателен для курьерской доставки.
  
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "warehouseId": 1,
    "items": [
      {
        "offerId": "example",
        "count": 1,
        "price": {
          "value": 0,
          "currencyId": "RUR"
        }
      }
    ],
    "deliveryDateInterval": {
      "fromDate": "2025-01-01",
      "toDate": "2025-01-01"
    },
    "deliveryTimeInterval": {
      "fromTime": "example",
      "toTime": "example"
    }
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
  
  ### OrderPickupDeliveryDTO {#entity-OrderPickupDeliveryDTO}
  
  Информация о доставке в пункт выдачи.
  
  Не передавайте вместе с `courierDelivery`.
  
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "logisticPointId": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BasicCourierDeliveryAddressDTO {#entity-BasicCourierDeliveryAddressDTO}
  
  Адрес доставки.
  
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
  
  <div class="openapi-entity">
  
  ### CourierDeliveryAddressDTO {#entity-CourierDeliveryAddressDTO}
  
  Адрес доставки.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BasicCourierDeliveryAddressDTO](#entity-BasicCourierDeliveryAddressDTO)
  
    Адрес доставки.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "fullAddress": "example"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _apartment_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Номер квартиры или офиса.
  
    _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
    _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _entrance_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Номер подъезда.
  
    _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
    _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _floor_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: integer
  
    Этаж.
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "entrance": "example",
      "floor": 0,
      "apartment": "example"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example",
    "entrance": "example",
    "floor": 0,
    "apartment": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderCourierDeliveryDTO {#entity-OrderCourierDeliveryDTO}
  
  Информация о курьерской доставке.
  
  Не передавайте вместе с `pickupDelivery`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CourierDeliveryAddressDTO](#entity-CourierDeliveryAddressDTO)
  
  Адрес доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example",
    "entrance": "example",
    "floor": 0,
    "apartment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _notes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий к заказу.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `3000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "address": {
      "fullAddress": "example",
      "entrance": "example",
      "floor": 0,
      "apartment": "example"
    },
    "notes": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateOrderDeliveryOptionDTO {#entity-CreateOrderDeliveryOptionDTO}
  
  Информация о доставке.
  
  Не передавайте одновременно `courierDelivery` и `pickupDelivery`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _courierDelivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderCourierDeliveryDTO](#entity-OrderCourierDeliveryDTO)
  
  Информация о курьерской доставке.
  
  Не передавайте вместе с `pickupDelivery`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "address": {
      "fullAddress": "example",
      "entrance": "example",
      "floor": 0,
      "apartment": "example"
    },
    "notes": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pickupDelivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderPickupDeliveryDTO](#entity-OrderPickupDeliveryDTO)
  
  Информация о доставке в пункт выдачи.
  
  Не передавайте вместе с `courierDelivery`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "logisticPointId": 1
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
      "logisticPointId": 1
    },
    "courierDelivery": {
      "address": {
        "fullAddress": "example",
        "entrance": "example",
        "floor": 0,
        "apartment": "example"
      },
      "notes": "example"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CustomerDTO {#entity-CustomerDTO}
  
  Данные получателя заказа или отправителя возврата.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _firstName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Имя.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _lastName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Фамилия.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _phone_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Номер телефона.
  
  Формат: `+<код_страны><код_региона><номер_телефона>`.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `5`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^\+[0-9]+$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _middleName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Отчество.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "firstName": "example",
    "lastName": "example",
    "middleName": "example",
    "phone": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateOrderPackageType {#entity-CreateOrderPackageType}
  
  Требования к упаковке:
  
  * `WHITELABEL` — коробка.
  
  * `BRAND` — [брендированная упаковка](*brand-package) магазина.
  
  Если не передать `packageType`, заказ приедет в коробке или без упаковки.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `WHITELABEL`, `BRAND`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateOrderPackagingDTO {#entity-CreateOrderPackagingDTO}
  
  Правила упаковки товаров в заказе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _packageType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CreateOrderPackageType](#entity-CreateOrderPackageType)
  
  Требования к упаковке:
  
  * `WHITELABEL` — коробка.
  
  * `BRAND` — [брендированная упаковка](*brand-package) магазина.
  
  Если не передать `packageType`, заказ приедет в коробке или без упаковки.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `WHITELABEL`, `BRAND`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "packageType": "WHITELABEL"
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
  
  ### ClientServiceType {#entity-ClientServiceType}
  
  Тип услуги, запрашиваемой клиентом для заказа:
  
  * `IDENTIFICATION` — идентификация получателя.
  
  
  **Type**: string
  
  _Const:_{.json-schema-reset .json-schema-value} `IDENTIFICATION`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ClientServiceDTO {#entity-ClientServiceDTO}
  
  Услуга, запрашиваемая клиентом для заказа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _isRequired_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Признак обязательности услуги.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ClientServiceType](#entity-ClientServiceType)
  
  Тип услуги, запрашиваемой клиентом для заказа:
  
  * `IDENTIFICATION` — идентификация получателя.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `IDENTIFICATION`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "IDENTIFICATION",
    "isRequired": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateOrderDTO {#entity-CreateOrderDTO}
  
  Информация о заказе.
  
  Передайте выбранный вариант доставки из ответа метода [POST v1/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _customer_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CustomerDTO](#entity-CustomerDTO)
  
  Данные получателя заказа или отправителя возврата.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "firstName": "example",
    "lastName": "example",
    "middleName": "example",
    "phone": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _destination_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateOrderDeliveryOptionDTO](#entity-CreateOrderDeliveryOptionDTO)
  
  Информация о доставке.
  
  Не передавайте одновременно `courierDelivery` и `pickupDelivery`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "pickupDelivery": {
      "logisticPointId": 1
    },
    "courierDelivery": {
      "address": {
        "fullAddress": "example",
        "entrance": "example",
        "floor": 0,
        "apartment": "example"
      },
      "notes": "example"
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _externalOrderId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Внешний идентификатор заказа в системе магазина.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _itemsDelivery_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateOrderWarehouseItemsDTO](#entity-CreateOrderWarehouseItemsDTO)[]
  
  Список товаров в заказе.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `1000`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "warehouseId": 1,
      "items": [
        {
          "offerId": "example",
          "count": 1,
          "price": {}
        }
      ],
      "deliveryDateInterval": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01"
      },
      "deliveryTimeInterval": {
        "fromTime": "example",
        "toTime": "example"
      }
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _packaging_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateOrderPackagingDTO](#entity-CreateOrderPackagingDTO)
  
  Правила упаковки товаров в заказе.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "packageType": "WHITELABEL"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _paymentType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryPaymentType](#entity-DeliveryPaymentType)
  
  Тип оплаты заказа:
  
  * `PREPAID` — оплата при оформлении заказа.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREPAID`
  {.table-cell}
  ||
  ||
  
  _draft_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Признак создания черновика заказа.
  
  * `true` — Маркет создаст заказ в статусе `RESERVED` и будет ждать подтверждения от магазина.
  * `false` — Маркет создаст заказ в статусе `PROCESSING` с подстатусом `STARTED` и начнёт его обработку, дополнительных подтверждений не требуется.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `false`
  {.table-cell}
  ||
  ||
  
  _fake_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Признак тестового заказа.
  
  * `true` — позволяет проверить работу магазина и его API на [тестовых заказах](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md). Такой заказ не будет отгружен и не влияет на остатки.
  * `false` — настоящий заказ.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `false`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "externalOrderId": "example",
    "itemsDelivery": [
      {
        "warehouseId": 1,
        "items": [
          {}
        ],
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        }
      }
    ],
    "destination": {
      "pickupDelivery": {
        "logisticPointId": 1
      },
      "courierDelivery": {
        "address": {
          "fullAddress": "example",
          "entrance": "example",
          "floor": 0,
          "apartment": "example"
        },
        "notes": "example"
      }
    },
    "customer": {
      "firstName": "example",
      "lastName": "example",
      "middleName": "example",
      "phone": "example"
    },
    "packaging": {
      "packageType": "WHITELABEL"
    },
    "paymentType": "PREPAID",
    "draft": false,
    "fake": false
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о созданных заказах.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "orders": [
        {
          "id": 0
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
    **Type**: [CreatedOrdersDTO](#entity-CreatedOrdersDTO)
  
    Информация о созданных заказах.
  
    По одному заказу для каждого склада.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "orders": [
        {
          "id": 0
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
        "orders": [
          {
            "id": 0
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
  
  ### CreatedOrderDTO {#entity-CreatedOrderDTO}
  
  Информация о созданном заказе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreatedOrdersDTO {#entity-CreatedOrdersDTO}
  
  Информация о созданных заказах.
  
  По одному заказу для каждого склада.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _orders_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreatedOrderDTO](#entity-CreatedOrderDTO)[]
  
  Созданные заказы.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0
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
    "orders": [
      {
        "id": 0
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
      "order": {
        "externalOrderId": "example",
        "itemsDelivery": [
          {
            "warehouseId": 1,
            "items": [
              {}
            ],
            "deliveryDateInterval": {
              "fromDate": "2025-01-01",
              "toDate": "2025-01-01"
            },
            "deliveryTimeInterval": {
              "fromTime": "example",
              "toTime": "example"
            }
          }
        ],
        "destination": {
          "pickupDelivery": {
            "logisticPointId": 1
          },
          "courierDelivery": {
            "address": {},
            "notes": "example"
          }
        },
        "customer": {
          "firstName": "example",
          "lastName": "example",
          "middleName": "example",
          "phone": "example"
        },
        "packaging": {
          "packageType": "WHITELABEL"
        },
        "paymentType": "PREPAID",
        "draft": false,
        "fake": false
      }
    }
  schema:
    type: object
    required:
      - order
    properties:
      order:
        type: object
        description: "Информация о заказе.\n\nПередайте выбранный вариант доставки из ответа метода [POST\_v1/campaigns/{campaignId}/delivery-options](../../reference/delivery-options/getDeliveryOptions.md).\n"
        required:
          - externalOrderId
          - itemsDelivery
          - destination
          - customer
          - packaging
          - paymentType
        properties:
          externalOrderId:
            description: Внешний идентификатор заказа в системе магазина.
            type: string
            minLength: 1
          itemsDelivery:
            description: Список товаров в заказе.
            type: array
            items:
              type: object
              description: Список товаров в заказе.
              required:
                - warehouseId
                - items
                - deliveryDateInterval
              properties:
                warehouseId:
                  description: "Идентификатор фулфилмент-склада Маркета.\n\nПолучите его с помощью метода [POST\_v2/campaigns/{campaignId}/delivery-options](../../reference/delivery-options/getDeliveryOptions.md).\n"
                  type: integer
                  format: int64
                  minimum: 1
                items:
                  type: array
                  description: >
                    Список товаров в заказе.
  
  
                    В рамках одного запроса все значения `offerId` должны быть
                    уникальными. Не допускается передача двух объектов с
                    одинаковым `offerId`.
                  minItems: 1
                  maxItems: 1000
                  items:
                    description: Товар в заказе.
                    type: object
                    required:
                      - price
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
                          price:
                            description: Цена товара.
                            type: object
                            required:
                              - value
                              - currencyId
                            properties:
                              value:
                                description: Цена товара.
                                type: number
                                minimum: 0
                                exclusiveMinimum: true
                              currencyId:
                                description: Валюта.
                                $ref: '#/$defs/CurrencyType'
                          vat:
                            description: НДС на товар.
                            x-hidden: true
                            $ref: '#/$defs/OrderVatType'
                deliveryDateInterval:
                  type: object
                  description: Интервал дат доставки.
                  required:
                    - fromDate
                    - toDate
                  properties:
                    fromDate:
                      type: string
                      format: date
                      description: |
                        Начало интервала.
  
                        Формат даты: `ГГГГ-ММ-ДД`.
                    toDate:
                      type: string
                      format: date
                      description: |
                        Конец интервала.
  
                        Формат даты: `ГГГГ-ММ-ДД`.
                deliveryTimeInterval:
                  description: |
                    Интервал времени доставки.
  
                    Обязателен для курьерской доставки.
                  $ref: '#/$defs/TimeIntervalDTO'
            minItems: 1
            maxItems: 1000
          destination:
            type: object
            description: |
              Информация о доставке.
  
              Не передавайте одновременно `courierDelivery` и `pickupDelivery`.
            properties:
              pickupDelivery:
                type: object
                description: |
                  Информация о доставке в пункт выдачи.
  
                  Не передавайте вместе с `courierDelivery`.
                required:
                  - logisticPointId
                properties:
                  logisticPointId:
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
                  - address
                properties:
                  address:
                    type: object
                    description: Адрес доставки.
                    allOf:
                      - type: object
                        description: Адрес доставки.
                        required:
                          - fullAddress
                        properties:
                          fullAddress:
                            type: string
                            description: Полный адрес с точностью до номера дома.
                            minLength: 1
                            maxLength: 512
                      - properties:
                          entrance:
                            type: string
                            description: Номер подъезда.
                            minLength: 1
                            maxLength: 16
                          floor:
                            type: integer
                            format: int32
                            description: Этаж.
                          apartment:
                            type: string
                            description: Номер квартиры или офиса.
                            minLength: 1
                            maxLength: 16
                  notes:
                    type: string
                    description: Комментарий к заказу.
                    minLength: 1
                    maxLength: 3000
          customer:
            type: object
            description: Данные получателя заказа или отправителя возврата.
            required:
              - firstName
              - lastName
              - phone
            properties:
              firstName:
                type: string
                description: Имя.
                minLength: 1
                maxLength: 512
              lastName:
                type: string
                description: Фамилия.
                minLength: 1
                maxLength: 512
              middleName:
                type: string
                description: Отчество.
                minLength: 1
                maxLength: 512
              phone:
                type: string
                description: |
                  Номер телефона.
  
                  Формат: `+<код_страны><код_региона><номер_телефона>`.
                minLength: 5
                maxLength: 16
                pattern: ^\+[0-9]+$
          customerUid:
            type: integer
            format: int64
            description: >-
              UID получателя в Яндексе. Поддерживается только для внутренних
              партнеров.
            x-hidden: true
          packaging:
            type: object
            description: Правила упаковки товаров в заказе.
            properties:
              packageType:
                description: >
                  Требования к упаковке:
  
  
                  * `WHITELABEL` — коробка.
  
  
                  * `BRAND` — [брендированная упаковка](*brand-package) магазина.
  
  
                  Если не передать `packageType`, заказ приедет в коробке или без
                  упаковки.
                type: string
                enum:
                  - WHITELABEL
                  - BRAND
          paymentType:
            description: |
              Тип оплаты заказа:
  
              * `PREPAID` — оплата при оформлении заказа.
            type: string
            enum:
              - PREPAID
          draft:
            type: boolean
            description: >
              Признак создания черновика заказа.
  
  
              * `true` — Маркет создаст заказ в статусе `RESERVED` и будет ждать
              подтверждения от магазина.
  
              * `false` — Маркет создаст заказ в статусе `PROCESSING` с
              подстатусом `STARTED` и начнёт его обработку, дополнительных
              подтверждений не требуется.
            default: false
          fake:
            type: boolean
            description: >
              Признак тестового заказа.
  
  
              * `true` — позволяет проверить работу магазина и его API на
              [тестовых заказах](../../concepts/sandbox.md). Такой заказ не будет
              отгружен и не влияет на остатки.
  
              * `false` — настоящий заказ.
            default: false
          clientServices:
            description: Услуги, запрашиваемые клиентом для заказа.
            type: array
            nullable: true
            minItems: 1
            maxItems: 10
            x-hidden: true
            items:
              type: object
              description: Услуга, запрашиваемая клиентом для заказа.
              required:
                - type
                - isRequired
              properties:
                type:
                  description: |
                    Тип услуги, запрашиваемой клиентом для заказа:
  
                    * `IDENTIFICATION` — идентификация получателя.
                  type: string
                  enum:
                    - IDENTIFICATION
                isRequired:
                  type: boolean
                  description: Признак обязательности услуги.
    $defs:
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/CurrencyType:
        type: string
        description: |
          Коды валют:
  
          * `RUR` — российский рубль.
          * `UAH` — украинская гривна.
          * `BYR` — белорусский рубль.
          * `KZT` — казахстанский тенге.
          * `UZS` — узбекский сум.
        enum:
          - RUR
          - USD
          - EUR
          - UAH
          - AUD
          - GBP
          - BYR
          - BYN
          - DKK
          - ISK
          - KZT
          - CAD
          - CNY
          - NOK
          - XDR
          - SGD
          - TRY
          - SEK
          - CHF
          - JPY
          - AZN
          - ALL
          - DZD
          - AOA
          - ARS
          - AMD
          - AFN
          - BHD
          - BGN
          - BOB
          - BWP
          - BND
          - BRL
          - BIF
          - HUF
          - VEF
          - KPW
          - VND
          - GMD
          - GHS
          - GNF
          - HKD
          - GEL
          - AED
          - EGP
          - ZMK
          - ILS
          - INR
          - IDR
          - JOD
          - IQD
          - IRR
          - YER
          - QAR
          - KES
          - KGS
          - COP
          - CDF
          - CRC
          - KWD
          - CUP
          - LAK
          - LVL
          - SLL
          - LBP
          - LYD
          - SZL
          - LTL
          - MUR
          - MRO
          - MKD
          - MWK
          - MGA
          - MYR
          - MAD
          - MXN
          - MZN
          - MDL
          - MNT
          - NPR
          - NGN
          - NIO
          - NZD
          - OMR
          - PKR
          - PYG
          - PEN
          - PLN
          - KHR
          - SAR
          - RON
          - SCR
          - SYP
          - SKK
          - SOS
          - SDG
          - SRD
          - TJS
          - THB
          - TWD
          - BDT
          - TZS
          - TND
          - TMM
          - UGX
          - UZS
          - UYU
          - PHP
          - DJF
          - XAF
          - XOF
          - HRK
          - CZK
          - CLP
          - LKR
          - EEK
          - ETB
          - RSD
          - ZAR
          - KRW
          - NAD
          - TL
          - UE
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/orders/schemas.yaml#/OrderVatType:
        description: >
          НДС на товар или доставку:
  
  
          * `NO_VAT` — НДС не облагается, используется только для отдельных видов
          услуг.
  
  
          * `VAT_0` — НДС 0%. Например, используется при продаже товаров,
          вывезенных в таможенной процедуре экспорта, или при оказании услуг по
          международной перевозке товаров.
  
  
          * `VAT_10` — НДС 10%. Например, используется при реализации отдельных
          продовольственных и медицинских товаров.
  
  
          * `VAT_10_110` — НДС 10/110. НДС 10%, применяется только при предоплате.
  
  
          * `VAT_20` — НДС 20%. Основной НДС с 2019 года до 1 января 2026 года.
  
  
          * `VAT_20_120` — НДС 20/120. НДС 20%, применяется только при предоплате.
  
  
          * `VAT_18` — НДС 18%. Основной НДС до 2019 года.
  
  
          * `VAT_18_118` — НДС 18/118. НДС использовался до 1 января 2019 года при
          предоплате.
  
  
          * `VAT_12` — НДС 12%. Используется только в Узбекистане.
  
  
          * `VAT_05` — НДС 5%. НДС для упрощенной системы налогообложения (УСН).
  
  
          * `VAT_07` — НДС 7%. НДС для упрощенной системы налогообложения (УСН).
  
  
          * `VAT_22` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  
          * `UNKNOWN_VALUE` — неизвестный тип.
        type: string
        enum:
          - NO_VAT
          - VAT_0
          - VAT_10
          - VAT_10_110
          - VAT_20
          - VAT_20_120
          - VAT_18
          - VAT_18_118
          - VAT_12
          - VAT_05
          - VAT_07
          - VAT_22
          - UNKNOWN_VALUE
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/TimeIntervalDTO:
        type: object
        description: Интервал времени доставки.
        required:
          - fromTime
          - toTime
        properties:
          fromTime:
            type: string
            description: |
              Начало интервала.
  
              Формат: `ЧЧ:ММ`.
            pattern: ^([0-1][0-9]|2[0-3]):[0-5][0-9]$
          toTime:
            type: string
            description: |
              Конец интервала.
  
              Формат: `ЧЧ:ММ`.
            pattern: ^([0-1][0-9]|2[0-3]):[0-5][0-9]$
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
  path: v1/campaigns/{campaignId}/orders/create
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/createOrder.md -->

[*brand-package]: Заранее привезите ее на склад Маркета, где хранятся ваши товары.

[*Deprecated]: No longer supported, please use an alternative and newer version.
