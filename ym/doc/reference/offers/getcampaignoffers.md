---
title: В магазине
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md"
fetched_at: "2026-09-22T02:26:48Z"
content_sha: 064646111f7d0e90
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/offers/getCampaignOffers.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/offers/getCampaignOffers.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/offers/getCampaignOffers.md -->
<div class="openapi">

# Информация о товарах, которые размещены в заданном магазине

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getCampaignOffers.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getCampaignOffers.md -->
  
  Возвращает список товаров, которые размещены в заданном магазине. Для каждого товара указываются параметры размещения.
  
  <!-- source: ru/_auto/method_limits/getCampaignOffers.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 000 запросов в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 10 000 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getCampaignOffers.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/offers
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
    "offerIds": [
      "example"
    ],
    "statuses": [
      "PUBLISHED"
    ],
    "categoryIds": [
      0
    ],
    "vendorNames": [
      "example"
    ],
    "tags": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Фильтр по категориям на Маркете.
  
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
  
  _offerIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)[] &#124; null
  
  Идентификаторы товаров, информация о которых нужна.
  
  {% note warning "Такой список возвращается только целиком" %}
  
  Не используйте это поле одновременно с фильтрами по статусам карточек, категориям, брендам или тегам. Если вы хотите воспользоваться фильтрами, оставьте поле пустым.
  
  Если вы запрашиваете информацию по конкретным SKU, не заполняйте:
  
  * `pageToken`
  * `limit`
  
  {% endnote %}
  
   
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `200`
  
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
  
  _statuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferCampaignStatusType](#entity-OfferCampaignStatusType)[] &#124; null
  
  Фильтр по статусам товаров.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "PUBLISHED"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _tags_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Фильтр по тегам.
  
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
  
  _vendorNames_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Фильтр по брендам.
  
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
  
  ### OfferCampaignStatusType {#entity-OfferCampaignStatusType}
  
  Статус товара:
  
  * `PUBLISHED` — Готов к продаже.
  * `CHECKING` — На проверке.
  * `DISABLED_BY_PARTNER` — Скрыт вами.
  * `REJECTED_BY_MARKET` — Отклонен.
  * `DISABLED_AUTOMATICALLY` — Исправьте ошибки.
  * `CREATING_CARD` — Создается карточка.
  * `NO_CARD` — Нужна карточка.
  * `NO_STOCKS` — Нет на складе.
  * `ARCHIVED` — В архиве.
  * `READY_FOR_PUBLICATION` — Магазин в процессе подключения.
  
  [Что обозначает каждый из статусов](https://yandex.ru/support/marketplace/assortment/add/statuses.html)
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PUBLISHED`, `CHECKING`, `DISABLED_BY_PARTNER`, `DISABLED_AUTOMATICALLY`, `REJECTED_BY_MARKET`, `CREATING_CARD`, `NO_CARD`, `NO_STOCKS`, `ARCHIVED`, `READY_FOR_PUBLICATION`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список товаров, размещенных в заданном магазине.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "paging": {
        "nextPageToken": "example"
      },
      "offers": [
        {}
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
    **Type**: [GetCampaignOffersResultDTO](#entity-GetCampaignOffersResultDTO)
  
    Список товаров в заданном магазине.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "paging": {
        "nextPageToken": "example"
      },
      "offers": [
        {
          "offerId": "example",
          "available": true,
          "basicPrice": {},
          "campaignPrice": {},
          "status": "PUBLISHED",
          "errors": [
            {}
          ],
          "warnings": [
            null
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
        "paging": {
          "nextPageToken": "example"
        },
        "offers": [
          {
            "offerId": "example",
            "available": true,
            "basicPrice": {},
            "campaignPrice": {},
            "status": "PUBLISHED",
            "errors": [
              null
            ],
            "warnings": [
              null
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
  
  ### BaseCampaignOfferDTO {#entity-BaseCampaignOfferDTO}
  
  Информация о новой цене на товар.
  
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
  
  _available_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: boolean
  
  {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
  Вместо него используйте методы скрытия товаров с витрины
  
  * [GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md) — просмотр скрытых товаров;
  * [POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md) — скрытие товаров;
  * [POST v2/campaigns/{campaignId}/hidden-offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md) — возобновление показа.
  
  {% endnote %}
  
  Есть ли товар в продаже.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "available": true
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
  
  ### DiscountBase {#entity-DiscountBase}
  
  Зачеркнутая цена.
  
  Число должно быть целым. Вы можете указать цену со скидкой от 5 до 99%.
  
  Передавайте этот параметр при каждом обновлении цены, если предоставляете скидку на товар.
  
  
  **Type**: number
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PriceWithDiscountDTO {#entity-PriceWithDiscountDTO}
  
  Цена с указанием скидки.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BasePriceDTO](#entity-BasePriceDTO)
  
    Цена товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
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
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "discountBase": 0
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR",
    "discountBase": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateTimeDTO {#entity-UpdateTimeDTO}
  
  Время последнего обновления.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Время последнего обновления.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPriceWithDiscountDTO {#entity-GetPriceWithDiscountDTO}
  
  Цена с указанием валюты, скидки и времени последнего обновления.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [PriceWithDiscountDTO](#entity-PriceWithDiscountDTO)
  
    Цена с указанием скидки.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0
    }
    ```
  
    {% endcut %}
  
  - **Type**: [UpdateTimeDTO](#entity-UpdateTimeDTO)
  
    Время последнего обновления.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "updatedAt": "2025-01-01T00:00:00Z"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR",
    "discountBase": 0,
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
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
  
  ### GetPriceWithVatDTO {#entity-GetPriceWithVatDTO}
  
  Цена с указанием НДС и времени последнего обновления.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [PriceDTO](#entity-PriceDTO)
  
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
  
  - **Type**: [UpdateTimeDTO](#entity-UpdateTimeDTO)
  
    Время последнего обновления.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "updatedAt": "2025-01-01T00:00:00Z"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "discountBase": 0,
    "currencyId": "RUR",
    "vat": 0,
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferErrorDTO {#entity-OfferErrorDTO}
  
  Сообщение об ошибке, связанной с размещением товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Пояснение.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _message_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Тип ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "message": "example",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetCampaignOfferDTO {#entity-GetCampaignOfferDTO}
  
  Параметры размещения товара в магазине.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BaseCampaignOfferDTO](#entity-BaseCampaignOfferDTO)
  
    Информация о новой цене на товар.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offerId": "example",
      "available": true
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _basicPrice_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GetPriceWithDiscountDTO](#entity-GetPriceWithDiscountDTO)
  
    Цена товара для всех магазинов.
  
    Цена с указанием валюты, скидки и времени последнего обновления.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0,
      "updatedAt": "2025-01-01T00:00:00Z"
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _campaignPrice_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GetPriceWithVatDTO](#entity-GetPriceWithVatDTO)
  
    Цена, установленная в отдельном магазине.
  
    Цена с указанием НДС и времени последнего обновления.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "discountBase": 0,
      "currencyId": "RUR",
      "vat": 0,
      "updatedAt": "2025-01-01T00:00:00Z"
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _errors_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferErrorDTO](#entity-OfferErrorDTO)[] &#124; null
  
    Ошибки, препятствующие размещению товара на витрине.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "message": "example",
        "comment": "example"
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _status_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferCampaignStatusType](#entity-OfferCampaignStatusType)
  
    Статус товара.
  
  
    Статус товара:
  
    * `PUBLISHED` — Готов к продаже.
    * `CHECKING` — На проверке.
    * `DISABLED_BY_PARTNER` — Скрыт вами.
    * `REJECTED_BY_MARKET` — Отклонен.
    * `DISABLED_AUTOMATICALLY` — Исправьте ошибки.
    * `CREATING_CARD` — Создается карточка.
    * `NO_CARD` — Нужна карточка.
    * `NO_STOCKS` — Нет на складе.
    * `ARCHIVED` — В архиве.
    * `READY_FOR_PUBLICATION` — Магазин в процессе подключения.
  
    [Что обозначает каждый из статусов](https://yandex.ru/support/marketplace/assortment/add/statuses.html)
  
  
    _Enum:_{.json-schema-reset .json-schema-value} `PUBLISHED`, `CHECKING`, `DISABLED_BY_PARTNER`, `DISABLED_AUTOMATICALLY`, `REJECTED_BY_MARKET`, `CREATING_CARD`, `NO_CARD`, `NO_STOCKS`, `ARCHIVED`, `READY_FOR_PUBLICATION`
    {.table-cell}
    ||
    ||
  
    _warnings_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferErrorDTO](#entity-OfferErrorDTO)[] &#124; null
  
    Предупреждения, не препятствующие размещению товара на витрине.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "message": "example",
        "comment": "example"
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
      "basicPrice": {
        "value": 0,
        "currencyId": "RUR",
        "discountBase": 0,
        "updatedAt": "2025-01-01T00:00:00Z"
      },
      "campaignPrice": {
        "value": 0,
        "discountBase": null,
        "currencyId": null,
        "vat": 0
      },
      "status": "PUBLISHED",
      "errors": [
        {
          "message": "example",
          "comment": "example"
        }
      ],
      "warnings": [
        null
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "available": true,
    "basicPrice": {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0,
      "updatedAt": "2025-01-01T00:00:00Z"
    },
    "campaignPrice": {
      "value": 0,
      "discountBase": null,
      "currencyId": null,
      "vat": 0
    },
    "status": "PUBLISHED",
    "errors": [
      {
        "message": "example",
        "comment": "example"
      }
    ],
    "warnings": [
      null
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetCampaignOffersResultDTO {#entity-GetCampaignOffersResultDTO}
  
  Список товаров в заданном магазине.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetCampaignOfferDTO](#entity-GetCampaignOfferDTO)[]
  
  Страница списка товаров.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "available": true,
      "basicPrice": {
        "updatedAt": "2025-01-01T00:00:00Z"
      },
      "campaignPrice": {
        "value": 0,
        "discountBase": 0,
        "currencyId": "RUR",
        "vat": 0
      },
      "status": "PUBLISHED",
      "errors": [
        {
          "message": "example",
          "comment": "example"
        }
      ],
      "warnings": [
        null
      ]
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
    "paging": {
      "nextPageToken": "example"
    },
    "offers": [
      {
        "offerId": "example",
        "available": true,
        "basicPrice": {},
        "campaignPrice": {},
        "status": "PUBLISHED",
        "errors": [
          {}
        ],
        "warnings": [
          null
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
      "offerIds": [
        "example"
      ],
      "statuses": [
        "PUBLISHED"
      ],
      "categoryIds": [
        0
      ],
      "vendorNames": [
        "example"
      ],
      "tags": [
        "example"
      ]
    }
  schema:
    description: >
      Фильтрации товаров
  
  
      В запросе можно указать либо фильтр offerIds, либо любые другие фильтры
      товаров. Совместное использование фильтра `offerIds` с другими фильтрациями
      приведет к ошибке.
    type: object
    properties:
      offerIds:
        description: "Идентификаторы товаров, информация о которых нужна.\n\n{% note warning \"Такой список возвращается только целиком\" %}\n\nНе используйте это поле одновременно с фильтрами по статусам карточек, категориям, брендам или тегам. Если вы хотите воспользоваться фильтрами, оставьте поле пустым.\n\nЕсли вы запрашиваете информацию по конкретным SKU, не заполняйте:\n\n* `pageToken`\n* `limit`\n\n{% endnote %}\n\n\_\n"
        type: array
        nullable: true
        items:
          description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
          type: string
          pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
          x-transform: trim
          minLength: 1
          maxLength: 255
        minItems: 1
        maxItems: 200
        uniqueItems: true
      statuses:
        description: |
          Фильтр по статусам товаров.
        type: array
        nullable: true
        items:
          description: >
            Статус товара:
  
  
            * `PUBLISHED` — Готов к продаже.
  
            * `CHECKING` — На проверке.
  
            * `DISABLED_BY_PARTNER` — Скрыт вами.
  
            * `REJECTED_BY_MARKET` — Отклонен.
  
            * `DISABLED_AUTOMATICALLY` — Исправьте ошибки.
  
            * `CREATING_CARD` — Создается карточка.
  
            * `NO_CARD` — Нужна карточка.
  
            * `NO_STOCKS` — Нет на складе.
  
            * `ARCHIVED` — В архиве.
  
            * `READY_FOR_PUBLICATION` — Магазин в процессе подключения.
  
  
            [Что обозначает каждый из
            статусов](https://yandex.ru/support/marketplace/assortment/add/statuses.html)
          type: string
          enum:
            - PUBLISHED
            - CHECKING
            - DISABLED_BY_PARTNER
            - DISABLED_AUTOMATICALLY
            - REJECTED_BY_MARKET
            - CREATING_CARD
            - NO_CARD
            - NO_STOCKS
            - ARCHIVED
            - READY_FOR_PUBLICATION
        minItems: 1
        uniqueItems: true
      categoryIds:
        description: Фильтр по категориям на Маркете.
        type: array
        nullable: true
        items:
          type: integer
          format: int32
          minimum: 0
          exclusiveMinimum: true
        minItems: 1
        uniqueItems: true
      vendorNames:
        description: Фильтр по брендам.
        type: array
        nullable: true
        items:
          type: string
        minItems: 1
        uniqueItems: true
      tags:
        description: Фильтр по тегам.
        type: array
        nullable: true
        items:
          type: string
        minItems: 1
        uniqueItems: true
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
  path: v2/campaigns/{campaignId}/offers
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/offers/getCampaignOffers.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
