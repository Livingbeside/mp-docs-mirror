---
title: Стоимость услуг
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md"
fetched_at: "2026-09-10T01:56:08Z"
content_sha: ce253c52e3eed31a
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/tariffs/calculateTariffs.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/tariffs/calculateTariffs.md
  - href: ru/reference/tariffs/calculateTariffs.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/tariffs/calculateTariffs.md -->
<div class="openapi">

# Калькулятор стоимости услуг

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/calculateTariffs.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * pricing:read-only — [Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/calculateTariffs.md -->
  
  Рассчитывает стоимость услуг Маркета для товаров с заданными параметрами. Порядок товаров в запросе и ответе сохраняется, чтобы определить,
  для какого товара рассчитана стоимость услуги.
  
  Обратите внимание: калькулятор осуществляет примерные расчеты. Финальная стоимость для каждого заказа зависит от предоставленных услуг.
  
  Если у вас оформлена подписка, сниженный тариф применится в расчетах. Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).
  
  В запросе можно указать либо параметр `campaignId`, либо `sellingProgram`. Совместное использование параметров приведет к ошибке.
  
  <!-- source: ru/_auto/method_limits/calculateTariffs.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/calculateTariffs.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/tariffs/calculate
  ```
  
  </div>
  
  </div>
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "parameters": {
      "campaignId": 1,
      "sellingProgram": "FBY",
      "frequency": "DAILY",
      "paymentDelayWeeks": 0,
      "currency": "RUR"
    },
    "offers": [
      {
        "categoryId": 0,
        "price": 0,
        "length": 0,
        "width": 0,
        "height": 0,
        "weight": 0,
        "quantity": 1
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
  **Type**: [CalculateTariffsOfferDTO](#entity-CalculateTariffsOfferDTO)[]
  
  Товары, для которых нужно рассчитать стоимость услуг.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `200`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "categoryId": 0,
      "price": 0,
      "length": 0,
      "width": 0,
      "height": 0,
      "weight": 0,
      "quantity": 1
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _parameters_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CalculateTariffsParametersDTO](#entity-CalculateTariffsParametersDTO)
  
  Параметры для расчета стоимости услуг.
  
  Параметры для расчета стоимости услуг. Обязательно необходимо указать параметр `campaignId` либо `sellingProgram`. Совместное использование параметров приведет к ошибке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "campaignId": 1,
    "sellingProgram": "FBY",
    "frequency": "DAILY",
    "paymentDelayWeeks": 0,
    "currency": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  ### SellingProgramType {#entity-SellingProgramType}
  
  Модель работы:
  
  * `FBY` — FBY.
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  * `LAAS` — LaaS.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBY`, `FBS`, `DBS`, `EXPRESS`, `LAAS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PaymentFrequencyType {#entity-PaymentFrequencyType}
  
  Частота выплат:
  
  * `DAILY` — ежедневно.
  * `WEEKLY` — раз в неделю.
  * `BIWEEKLY` — раз в две недели.
  * `MONTHLY` — раз в месяц.
  
  Подробнее о графике выплат читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/introduction/rates/acquiring.html).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DAILY`, `WEEKLY`, `BIWEEKLY`, `MONTHLY`
  
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
  
  ### CalculateTariffsParametersDTO {#entity-CalculateTariffsParametersDTO}
  
  Параметры для расчета стоимости услуг. Обязательно необходимо указать параметр `campaignId` либо `sellingProgram`. Совместное использование параметров приведет к ошибке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)
  
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
  
  _currency_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта, в которой рассчитывается услуга.
  
  Значение по умолчанию: `RUR`.
  
  
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
  
  _frequency_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PaymentFrequencyType](#entity-PaymentFrequencyType)
  
  Частота выплат.
  
  Частота выплат:
  
  * `DAILY` — ежедневно.
  * `WEEKLY` — раз в неделю.
  * `BIWEEKLY` — раз в две недели.
  * `MONTHLY` — раз в месяц.
  
  Подробнее о графике выплат читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/introduction/rates/acquiring.html).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DAILY`, `WEEKLY`, `BIWEEKLY`, `MONTHLY`
  {.table-cell}
  ||
  ||
  
  _paymentDelayWeeks_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Отсрочка выплат при еженедельном графике — сколько недель назад были доставлены заказы, за которые приходит выплата.
  
  Допустимые значения: 0, 1, 2 или 4.
  
  Значения параметра `paymentDelayWeeks`, отличные от 0, допускаются только вместе с параметром `frequency` равным 'WEEKLY'.
  Использование других значений параметра `frequency` совместно с `paymentDelayWeeks` приведет к ошибке.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `4`
  {.table-cell}
  ||
  ||
  
  _sellingProgram_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SellingProgramType](#entity-SellingProgramType)
  
  Модель работы.
  
  **Для продавцов Market Yandex Go** недоступны модели DBS и Экспресс.
  
  Обязательный параметр, если не указан параметр `campaignId`. Совместное использование параметров приведет к ошибке.
  
  
  Модель работы:
  
  * `FBY` — FBY.
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  * `LAAS` — LaaS.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBY`, `FBS`, `DBS`, `EXPRESS`, `LAAS`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "campaignId": 1,
    "sellingProgram": "FBY",
    "frequency": "DAILY",
    "paymentDelayWeeks": 0,
    "currency": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CalculateTariffsOfferDTO {#entity-CalculateTariffsOfferDTO}
  
  Параметры товара, для которого нужно рассчитать стоимость услуг.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор категории товара на Маркете.
  
  Для расчета стоимости услуг необходимо указать идентификатор [листовой категории](*list-category) товара.
  
  Чтобы узнать идентификатор категории, к которой относится товар, воспользуйтесь запросом [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _height_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Высота товара в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _length_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Длина товара в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _price_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Цена товара в рублях.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _weight_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Вес товара в килограммах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _width_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Ширина товара в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _quantity_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Квант продажи — количество единиц товара в одном товарном предложении.
  
  _Default:_{.json-schema-reset .json-schema-value} `1`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "categoryId": 0,
    "price": 0,
    "length": 0,
    "width": 0,
    "height": 0,
    "weight": 0,
    "quantity": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Стоимость услуг.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "offers": [
        {
          "offer": {},
          "tariffs": [
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
    **Type**: [CalculateTariffsResponseDTO](#entity-CalculateTariffsResponseDTO)
  
    Стоимость услуг.
  
    Расчет стоимости услуг.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offers": [
        {
          "offer": {
            "categoryId": 0,
            "price": 0,
            "length": 0,
            "width": 0,
            "height": 0,
            "weight": 0,
            "quantity": 1
          },
          "tariffs": [
            {
              "type": "AGENCY_COMMISSION",
              "amount": 0.5,
              "currency": "RUR",
              "parameters": [
                null
              ]
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
        "offers": [
          {
            "offer": {
              "categoryId": 0,
              "price": 0,
              "length": 0,
              "width": 0,
              "height": 0,
              "weight": 0,
              "quantity": 1
            },
            "tariffs": [
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
  
  ### CalculatedTariffType {#entity-CalculatedTariffType}
  
  Услуга Маркета:
  
  * `AGENCY_COMMISSION` — прием платежа покупателя.
  
  * `PAYMENT_TRANSFER` — перевод платежа покупателя.
  
  * `FEE` — размещение товара на Маркете.
  
  * `DELIVERY_TO_CUSTOMER` — доставка покупателю.
  
  * `CROSSREGIONAL_DELIVERY` — доставка в федеральный округ, город или населенный пункт.
  
  * `EXPRESS_DELIVERY` — экспресс-доставка покупателю.
  
  * `SORTING` — обработка заказа.
  
  * `MIDDLE_MILE` — средняя миля.
  
  * `ITEM_BOOKING` — бронирование товара.
  
  Подробнее об услугах Маркета читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/introduction/rates/index.html).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `AGENCY_COMMISSION`, `PAYMENT_TRANSFER`, `FEE`, `DELIVERY_TO_CUSTOMER`, `CROSSREGIONAL_DELIVERY`, `EXPRESS_DELIVERY`, `SORTING`, `MIDDLE_MILE`, `ITEM_BOOKING`
  
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
  
  ### CalculatedTariffDTO {#entity-CalculatedTariffDTO}
  
  Информация об услугах Маркета.
  
  #|
  || **Name** | **Description** ||
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
  **Type**: [CalculatedTariffType](#entity-CalculatedTariffType)
  
  Услуга Маркета.
  
  Услуга Маркета:
  
  * `AGENCY_COMMISSION` — прием платежа покупателя.
  
  * `PAYMENT_TRANSFER` — перевод платежа покупателя.
  
  * `FEE` — размещение товара на Маркете.
  
  * `DELIVERY_TO_CUSTOMER` — доставка покупателю.
  
  * `CROSSREGIONAL_DELIVERY` — доставка в федеральный округ, город или населенный пункт.
  
  * `EXPRESS_DELIVERY` — экспресс-доставка покупателю.
  
  * `SORTING` — обработка заказа.
  
  * `MIDDLE_MILE` — средняя миля.
  
  * `ITEM_BOOKING` — бронирование товара.
  
  Подробнее об услугах Маркета читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/introduction/rates/index.html).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `AGENCY_COMMISSION`, `PAYMENT_TRANSFER`, `FEE`, `DELIVERY_TO_CUSTOMER`, `CROSSREGIONAL_DELIVERY`, `EXPRESS_DELIVERY`, `SORTING`, `MIDDLE_MILE`, `ITEM_BOOKING`
  {.table-cell}
  ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Стоимость услуги в рублях.
  {.table-cell}
  ||
  ||
  
  _currency_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта, в которой рассчитывается услуга.
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "AGENCY_COMMISSION",
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
  
  ### CalculateTariffsOfferInfoDTO {#entity-CalculateTariffsOfferInfoDTO}
  
  Стоимость услуг.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offer_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CalculateTariffsOfferDTO](#entity-CalculateTariffsOfferDTO)
  
  Информация о товаре, которую вы передали в запросе для расчета стоимости услуг.
  
  Параметры товара, для которого нужно рассчитать стоимость услуг.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "categoryId": 0,
    "price": 0,
    "length": 0,
    "width": 0,
    "height": 0,
    "weight": 0,
    "quantity": 1
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _tariffs_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CalculatedTariffDTO](#entity-CalculatedTariffDTO)[]
  
  Список услуг и их стоимость.
  
  По некоторым услугам могут возвращаться несколько разных стоимостей. Например, в модели FBS стоимость услуги `SORTING` (обработка заказа) зависит от способа отгрузки и количества заказов в отгрузке. Подробнее о тарифах на услуги читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/introduction/rates/models/).
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "AGENCY_COMMISSION",
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offer": {
      "categoryId": 0,
      "price": 0,
      "length": 0,
      "width": 0,
      "height": 0,
      "weight": 0,
      "quantity": 1
    },
    "tariffs": [
      {
        "type": "AGENCY_COMMISSION",
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
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CalculateTariffsResponseDTO {#entity-CalculateTariffsResponseDTO}
  
  Расчет стоимости услуг.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CalculateTariffsOfferInfoDTO](#entity-CalculateTariffsOfferInfoDTO)[]
  
  Стоимость услуг.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offer": {
        "categoryId": 0,
        "price": 0,
        "length": 0,
        "width": 0,
        "height": 0,
        "weight": 0,
        "quantity": 1
      },
      "tariffs": [
        {
          "type": "AGENCY_COMMISSION",
          "amount": 0.5,
          "currency": "RUR",
          "parameters": [
            {}
          ]
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
    "offers": [
      {
        "offer": {
          "categoryId": 0,
          "price": 0,
          "length": 0,
          "width": 0,
          "height": 0,
          "weight": 0,
          "quantity": 1
        },
        "tariffs": [
          {
            "type": "AGENCY_COMMISSION",
            "amount": 0.5,
            "currency": "RUR",
            "parameters": [
              null
            ]
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с тарифами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#tariffs)
  
  
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
  pathParams: []
  searchParams: []
  headers: []
  body: |-
    {
      "parameters": {
        "campaignId": 1,
        "sellingProgram": "FBY",
        "frequency": "DAILY",
        "paymentDelayWeeks": 0,
        "currency": "RUR"
      },
      "offers": [
        {
          "categoryId": 0,
          "price": 0,
          "length": 0,
          "width": 0,
          "height": 0,
          "weight": 0,
          "quantity": 1
        }
      ]
    }
  schema:
    type: object
    required:
      - parameters
      - offers
    properties:
      parameters:
        description: Параметры для расчета стоимости услуг.
        $ref: '#/$defs/CalculateTariffsParametersDTO'
      offers:
        description: Товары, для которых нужно рассчитать стоимость услуг.
        type: array
        minItems: 1
        maxItems: 200
        items:
          description: Параметры товара, для которого нужно рассчитать стоимость услуг.
          type: object
          required:
            - categoryId
            - price
            - length
            - width
            - height
            - weight
          properties:
            categoryId:
              description: "Идентификатор категории товара на Маркете.\n\nДля расчета стоимости услуг необходимо указать идентификатор [листовой категории](*list-category) товара.\n\nЧтобы узнать идентификатор категории, к которой относится товар, воспользуйтесь запросом [POST\_v2/categories/tree](../../reference/categories/getCategoriesTree.md).\n"
              type: integer
              format: int64
              minimum: 0
              exclusiveMinimum: true
            price:
              description: Цена товара в рублях.
              type: number
              minimum: 0
              exclusiveMinimum: true
            length:
              description: Длина товара в сантиметрах.
              type: number
              minimum: 0
              exclusiveMinimum: true
            width:
              description: Ширина товара в сантиметрах.
              type: number
              minimum: 0
              exclusiveMinimum: true
            height:
              description: Высота товара в сантиметрах.
              type: number
              minimum: 0
              exclusiveMinimum: true
            weight:
              description: Вес товара в килограммах.
              type: number
              minimum: 0
              exclusiveMinimum: true
            quantity:
              description: >-
                Квант продажи — количество единиц товара в одном товарном
                предложении.
              type: integer
              format: int32
              minimum: 1
              default: 1
    $defs:
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/SellingProgramType:
        description: |
          Модель работы:
  
          * `FBY` — FBY.
          * `FBS` — FBS.
          * `DBS` — DBS.
          * `EXPRESS` — Экспресс.
          * `LAAS` — LaaS.
        type: string
        enum:
          - FBY
          - FBS
          - DBS
          - EXPRESS
          - LAAS
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/tariffs/api/calculateTariffs.yaml#/PaymentFrequencyType:
        description: >
          Частота выплат:
  
  
          * `DAILY` — ежедневно.
  
          * `WEEKLY` — раз в неделю.
  
          * `BIWEEKLY` — раз в две недели.
  
          * `MONTHLY` — раз в месяц.
  
  
          Подробнее о графике выплат читайте [в Справке Маркета для
          продавцов](https://yandex.ru/support/marketplace/introduction/rates/acquiring.html).
        type: string
        enum:
          - DAILY
          - WEEKLY
          - BIWEEKLY
          - MONTHLY
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
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/tariffs/api/calculateTariffs.yaml#/CalculateTariffsParametersDTO:
        description: >-
          Параметры для расчета стоимости услуг. Обязательно необходимо указать
          параметр `campaignId` либо `sellingProgram`. Совместное использование
          параметров приведет к ошибке.
        type: object
        properties:
          campaignId:
            description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
            type: integer
            format: int64
            minimum: 1
          sellingProgram:
            description: >
              Модель работы.
  
  
              **Для продавцов Market Yandex Go** недоступны модели DBS и Экспресс.
  
  
              Обязательный параметр, если не указан параметр `campaignId`.
              Совместное использование параметров приведет к ошибке.
            $ref: '#/$defs/SellingProgramType'
          frequency:
            description: Частота выплат.
            $ref: '#/$defs/PaymentFrequencyType'
          paymentDelayWeeks:
            description: >
              Отсрочка выплат при еженедельном графике — сколько недель назад были
              доставлены заказы, за которые приходит выплата.
  
  
              Допустимые значения: 0, 1, 2 или 4.
  
  
              Значения параметра `paymentDelayWeeks`, отличные от 0, допускаются
              только вместе с параметром `frequency` равным 'WEEKLY'.
  
              Использование других значений параметра `frequency` совместно с
              `paymentDelayWeeks` приведет к ошибке.
            type: integer
            format: int32
            minimum: 0
            maximum: 4
          currency:
            description: |
              Валюта, в которой рассчитывается услуга.
  
              Значение по умолчанию: `RUR`.
            $ref: '#/$defs/CurrencyType'
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
  path: v2/tariffs/calculate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/tariffs/calculateTariffs.md -->

[*list-category]:
Категория, у которой нет дочерних.

[*Deprecated]: No longer supported, please use an alternative and newer version.
