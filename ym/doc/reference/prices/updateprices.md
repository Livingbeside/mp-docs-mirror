---
title: В магазине
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md"
fetched_at: "2026-09-10T01:56:09Z"
content_sha: 129295c98dc25b4a
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/prices/updatePrices.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/prices/updatePrices.md
  - href: ru/reference/prices/updatePrices.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/prices/updatePrices.md -->
<div class="openapi">

# Установка цен на товары в конкретном магазине

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updatePrices.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updatePrices.md -->
  
  Устанавливает цены на товары в магазине. Чтобы получить рекомендации Маркета, касающиеся цен, выполните запрос [POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md).
  
  {% note warning "Метод только для отдельных магазинов" %}
  
  Вам доступен этот метод, если в кабинете продавца на Маркете есть возможность установить уникальные цены в отдельных магазинах. Как это проверить — в методе [POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md) в параметре `onlyDefaultPrice` возвращается значение `false`.
  
  В ином случае используйте метод управления ценами, которые действуют во всех магазинах, — [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md).
  
  {% endnote %}
  
  {% note info "Данные в каталоге обновляются не мгновенно" %}
  
  Это занимает до нескольких минут.
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/updatePrices.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 товаров в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updatePrices.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/offer-prices/updates
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
    "offers": [
      {
        "offerId": "example",
        "price": {
          "value": 0,
          "discountBase": 0,
          "currencyId": "RUR",
          "vat": 0
        }
      }
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferPriceDTO](#entity-OfferPriceDTO)[]
  
  Список товаров.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `2000`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "price": {
        "value": 0,
        "discountBase": 0,
        "currencyId": "RUR",
        "vat": 0
      }
    }
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
  
  <div class="openapi-entity">
  
  ### InternalOfferId {#entity-InternalOfferId}
  
  Внутренний идентификатор товара в системах Маркета. Нужен для создания товаров Лавки с отличными offerId и article.
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DiscountBase {#entity-DiscountBase}
  
  Зачеркнутая цена.
  
  Число должно быть целым. Вы можете указать цену со скидкой от 5 до 99%.
  
  Передавайте этот параметр при каждом обновлении цены, если предоставляете скидку на товар.
  
  
  **Type**: number
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
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
  
  ### VatType {#entity-VatType}
  
  Идентификатор НДС, применяемый для товара:
  
  * `2` — НДС 10%. Например, используется при реализации отдельных продовольственных и медицинских товаров.
  * `5` — НДС 0%. Например, используется при продаже товаров, вывезенных в таможенной процедуре экспорта, или при оказании услуг по международной перевозке товаров.
  * `6` — НДС не облагается, используется только для отдельных видов услуг.
  * `7` — НДС 20%. Основной НДС с 2019 года до 1 января 2026 года. При передаче автоматически заменяется на НДС 22% (14). С 1 июля 2026 года значение будет больше недоступно для передачи.
  * `10` — НДС 5%. НДС для упрощенной системы налогообложения (УСН).
  * `11` — НДС 7%. НДС для упрощенной системы налогообложения (УСН).
  * `14` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  Если параметр не указан, используется НДС, установленный в кабинете.
  
  **Для продавцов Market Yandex Go** недоступна передача и получение НДС.
  
  
  **Type**: integer
  
  </div>
  
  <div class="openapi-entity">
  
  ### PriceDTO {#entity-PriceDTO}
  
  Цена с указанием скидки, валюты и времени последнего обновления.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _currencyId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта, в которой указана цена товара.
  
  
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
  
  _discountBase_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DiscountBase](#entity-DiscountBase)
  
  Зачеркнутая цена.
  
  Число должно быть целым. Вы можете указать цену со скидкой от 5 до 99%.
  
  Передавайте этот параметр при каждом обновлении цены, если предоставляете скидку на товар.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Цена товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _vat_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [VatType](#entity-VatType)
  
  Идентификатор НДС, применяемый для товара:
  
  * `2` — НДС 10%. Например, используется при реализации отдельных продовольственных и медицинских товаров.
  * `5` — НДС 0%. Например, используется при продаже товаров, вывезенных в таможенной процедуре экспорта, или при оказании услуг по международной перевозке товаров.
  * `6` — НДС не облагается, используется только для отдельных видов услуг.
  * `7` — НДС 20%. Основной НДС с 2019 года до 1 января 2026 года. При передаче автоматически заменяется на НДС 22% (14). С 1 июля 2026 года значение будет больше недоступно для передачи.
  * `10` — НДС 5%. НДС для упрощенной системы налогообложения (УСН).
  * `11` — НДС 7%. НДС для упрощенной системы налогообложения (УСН).
  * `14` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  Если параметр не указан, используется НДС, установленный в кабинете.
  
  **Для продавцов Market Yandex Go** недоступна передача и получение НДС.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "discountBase": 0,
    "currencyId": "RUR",
    "vat": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferPriceDTO {#entity-OfferPriceDTO}
  
  Товар с информацией о новой цене на него.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property}
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
  
  _price_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PriceDTO](#entity-PriceDTO)
  
  Цена с указанием скидки, валюты и времени последнего обновления.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "discountBase": 0,
    "currencyId": "RUR",
    "vat": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "price": {
      "value": 0,
      "discountBase": 0,
      "currencyId": "RUR",
      "vat": 0
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Маркет принял информацию о новых ценах.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK"
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
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
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с ценами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#prices)
  
  
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
  
  <div class="openapi__response__code__423">
  
  ## 423 Locked
  
  К ресурсу нельзя применить указанный метод. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#423)
  
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
      "offers": [
        {
          "offerId": "example",
          "price": {
            "value": 0,
            "discountBase": 0,
            "currencyId": "RUR",
            "vat": 0
          }
        }
      ]
    }
  schema:
    description: Запрос на установку цен на товары.
    type: object
    required:
      - offers
    properties:
      offers:
        description: Список товаров.
        type: array
        minItems: 1
        maxItems: 2000
        items:
          description: Товар с информацией о новой цене на него.
          type: object
          properties:
            offerId:
              description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
              type: string
              pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
              x-transform: trim
              minLength: 1
              maxLength: 255
            internalOfferId:
              x-hidden: true
              $ref: '#/$defs/InternalOfferId'
            price:
              description: Цена с указанием скидки, валюты и времени последнего обновления.
              type: object
              properties:
                value:
                  description: Цена товара.
                  type: number
                  minimum: 0
                  exclusiveMinimum: true
                discountBase:
                  description: >
                    Зачеркнутая цена.
  
  
                    Число должно быть целым. Вы можете указать цену со скидкой от
                    5 до 99%.
  
  
                    Передавайте этот параметр при каждом обновлении цены, если
                    предоставляете скидку на товар.
                  type: number
                  minimum: 0
                  exclusiveMinimum: true
                currencyId:
                  description: |
                    Валюта, в которой указана цена товара.
                  $ref: '#/$defs/CurrencyType'
                vat:
                  description: >
                    Идентификатор НДС, применяемый для товара:
  
  
                    * `2` — НДС 10%. Например, используется при реализации
                    отдельных продовольственных и медицинских товаров.
  
                    * `5` — НДС 0%. Например, используется при продаже товаров,
                    вывезенных в таможенной процедуре экспорта, или при оказании
                    услуг по международной перевозке товаров.
  
                    * `6` — НДС не облагается, используется только для отдельных
                    видов услуг.
  
                    * `7` — НДС 20%. Основной НДС с 2019 года до 1 января 2026
                    года. При передаче автоматически заменяется на НДС 22% (14). С
                    1 июля 2026 года значение будет больше недоступно для
                    передачи.
  
                    * `10` — НДС 5%. НДС для упрощенной системы налогообложения
                    (УСН).
  
                    * `11` — НДС 7%. НДС для упрощенной системы налогообложения
                    (УСН).
  
                    * `14` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  
                    Если параметр не указан, используется НДС, установленный в
                    кабинете.
  
  
                    **Для продавцов Market Yandex Go** недоступна
                    передача и получение НДС.
                  type: integer
                  format: int32
            id:
              description: |
                {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
                Вместо него используйте `offerId`.
  
                {% endnote %}
  
                Идентификатор предложения из прайс-листа.
              deprecated: true
              x-deprecation-config:
                shutdown-date: '2026-10-12'
                replacement-field: offerId
              x-hidden: true
              $ref: '#/$defs/ShopSku'
            shopSku:
              description: |
                {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
                Вместо него используйте `offerId`.
  
                Не используйте этот параметр.
  
                {% endnote %}
              deprecated: true
              x-deprecation-config:
                shutdown-date: '2026-10-12'
                replacement-field: offerId
              x-hidden: true
              $ref: '#/$defs/ShopSku'
    $defs:
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/InternalOfferId:
        description: >-
          Внутренний идентификатор товара в системах Маркета. Нужен для создания
          товаров Лавки с отличными offerId и article.
        type: string
        minLength: 1
        maxLength: 255
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/CurrencyType:
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
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/ShopSku:
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
  path: v2/campaigns/{campaignId}/offer-prices/updates
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/prices/updatePrices.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
