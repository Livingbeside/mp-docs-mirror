---
title: В кабинете
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md"
fetched_at: "2026-09-08T13:01:11Z"
content_sha: 081a25bfc0c50af6
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/business-offer-mappings/getOfferMappings.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/business-offer-mappings/getOfferMappings.md
  - href: ru/reference/business-offer-mappings/getOfferMappings.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/business-offer-mappings/getOfferMappings.md -->
<div class="openapi">

# Информация о товарах в каталоге

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOfferMappings.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOfferMappings.md -->
  
  Возвращает список товаров в каталоге, их категории на Маркете и характеристики каждого товара.
  
  Можно использовать тремя способами:
  * задать список интересующих SKU;
  * задать фильтр — в этом случае результаты возвращаются постранично;
  * не передавать тело запроса, чтобы получить список всех товаров в каталоге.
  
  Чтобы получить категорийные характеристики товаров, воспользуйтесь методом [POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md).
  
  <!-- source: ru/_auto/method_limits/getOfferMappings.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 100 запросов в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 600 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOfferMappings.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/offer-mappings
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
  
  _language_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CatalogLanguageType](#entity-CatalogLanguageType)
  
  Язык, на котором принимаются и возвращаются значения в параметрах `name` и `description`.
  
  Значение по умолчанию: `RU`.
  
  
  Язык:
  
  * `RU` — русский.
  * `UZ` — узбекский.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `UZ`
  {.table-cell}
  ||
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
  
  ### CatalogLanguageType {#entity-CatalogLanguageType}
  
  Язык:
  
  * `RU` — русский.
  * `UZ` — узбекский.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `UZ`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "offerIds": [
      "example"
    ],
    "cardStatuses": [
      "HAS_CARD_CAN_NOT_UPDATE"
    ],
    "categoryIds": [
      0
    ],
    "vendorNames": [
      "example"
    ],
    "tags": [
      "example"
    ],
    "archived": true
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _archived_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Фильтр по нахождению в архиве.
  
  Передайте `true`, чтобы получить товары, находящиеся в архиве. Если фильтр не заполнен или передано `false`, в ответе возвращаются товары, не находящиеся в архиве.
  
  {.table-cell}
  ||
  ||
  
  _cardStatuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferCardStatusType](#entity-OfferCardStatusType)[] &#124; null
  
  Фильтр по статусам карточек.
  
  [Что такое карточка товара](https://yandex.ru/support/marketplace/assortment/content/index.html)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "HAS_CARD_CAN_NOT_UPDATE"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
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
  
  Если вы запрашиваете информацию по конкретным SKU, не заполняйте:
  * `pageToken`;
  * `limit`;
  * `cardStatuses`;
  * `categoryIds`;
  * `vendorNames`;
  * `tags`;
  * `archived`.
  
  {% endnote %}
  
   
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
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
  
  ### OfferCardStatusType {#entity-OfferCardStatusType}
  
  Статус карточки товара:
  
  * `HAS_CARD_CAN_NOT_UPDATE` — Карточка Маркета.
  * `HAS_CARD_CAN_UPDATE` — Можно дополнить.
  * `HAS_CARD_CAN_UPDATE_ERRORS` — Изменения не приняты.
  * `HAS_CARD_CAN_UPDATE_PROCESSING` — Изменения на проверке.
  * `NO_CARD_NEED_CONTENT` — Создайте карточку.
  * `NO_CARD_MARKET_WILL_CREATE` — Создаст Маркет.
  * `NO_CARD_ERRORS` — Не создана из-за ошибки.
  * `NO_CARD_PROCESSING` — Проверяем данные.
  * `NO_CARD_ADD_TO_CAMPAIGN` — Разместите товар в магазине.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `HAS_CARD_CAN_NOT_UPDATE`, `HAS_CARD_CAN_UPDATE`, `HAS_CARD_CAN_UPDATE_ERRORS`, `HAS_CARD_CAN_UPDATE_PROCESSING`, `NO_CARD_NEED_CONTENT`, `NO_CARD_MARKET_WILL_CREATE`, `NO_CARD_ERRORS`, `NO_CARD_PROCESSING`, `NO_CARD_ADD_TO_CAMPAIGN`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о товарах в каталоге.
  
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
      "offerMappings": [
        {
          "offer": {},
          "mapping": {},
          "showcaseUrls": [
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
    **Type**: [GetOfferMappingsResultDTO](#entity-GetOfferMappingsResultDTO)
  
    Информация о товарах.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "paging": {
        "nextPageToken": "example"
      },
      "offerMappings": [
        {
          "offer": {
            "offerId": "example",
            "name": "Ударная дрель Makita HP1630, 710 Вт",
            "marketCategoryId": 0,
            "category": "example",
            "pictures": [
              null
            ],
            "videos": [
              null
            ],
            "manuals": [
              null
            ],
            "vendor": "LEVENHUK",
            "barcodes": [
              null
            ],
            "description": "example",
            "manufacturerCountries": [
              null
            ],
            "weightDimensions": {},
            "vendorCode": "VNDR-0005A",
            "tags": [
              null
            ],
            "shelfLife": {},
            "lifeTime": null,
            "guaranteePeriod": null,
            "customsCommodityCode": "8517610008",
            "commodityCodes": [
              null
            ],
            "certificates": [
              null
            ],
            "boxCount": 1,
            "condition": {},
            "type": "DEFAULT",
            "downloadable": true,
            "adult": true,
            "age": {},
            "params": [
              null
            ],
            "basicPrice": {},
            "purchasePrice": {},
            "additionalExpenses": null,
            "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
            "campaigns": [
              null
            ],
            "sellingPrograms": [
              null
            ],
            "mediaFiles": {},
            "archived": true,
            "groupId": "example"
          },
          "mapping": {
            "marketSku": 1,
            "marketSkuName": "example",
            "marketModelName": "example",
            "marketCategoryId": 0,
            "marketCategoryName": "example"
          },
          "showcaseUrls": [
            {
              "showcaseType": "B2B",
              "showcaseUrl": "example"
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
        "paging": {
          "nextPageToken": "example"
        },
        "offerMappings": [
          {
            "offer": {},
            "mapping": {},
            "showcaseUrls": [
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
  
  ### PartnerMarketCategoryId {#entity-PartnerMarketCategoryId}
  
  Идентификатор категории на Маркете, к которой вы относите свой товар.
  
  {% note warning "Всегда указывайте, когда передаете `parameterValues`" %}
  
  Если при изменении характеристик передать `parameterValues` и не указать `marketCategoryId`, характеристики обновятся, но в ответе придет предупреждение (параметр `warnings`).
  
  Если не передать их оба, будет использована информация из устаревших параметров `params` и `category`, а `marketCategoryId` будет определен автоматически.
  
  {% endnote %}
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferCategory {#entity-OfferCategory}
  
  _Deprecated_{.json-schema-reset .json-schema-deprecated-title}{title="This entity is deprecated and may be removed in future versions."}
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `marketCategoryId`.
  
  {% endnote %}
  
  Категория товара в вашем магазине.
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Url {#entity-Url}
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferManualDTO {#entity-OfferManualDTO}
  
  Инструкция по использованию товара.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _url_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Url](#entity-Url)
  
  Ссылка на инструкцию.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _title_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название инструкции, которое будет отображаться на карточке товара.
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `500`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "url": "example",
    "title": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferVendor {#entity-OfferVendor}
  
  Название бренда или производителя. Должно быть записано так, как его пишет сам бренд.
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `LEVENHUK`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferBarcodes {#entity-OfferBarcodes}
  
  Штрихкод.
  
  Указывайте в виде последовательности цифр. Подойдут коды EAN-13, EAN-8, UPC-A, UPC-E или Code 128. Для книг — ISBN.
  
  Для товаров [определенных категорий и торговых марок](https://yastatic.net/s3/doc-binary/src/support/market/ru/yandex-market-list-for-gtin.xlsx) штрихкод должен быть действительным кодом GTIN. Обратите внимание: внутренние штрихкоды, начинающиеся на 2 или 02, и коды формата Code 128 не являются GTIN.
  
  [Что такое GTIN](*gtin)
  
  
  **Type**: string[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "46012300000000"
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferManufacturerCountries {#entity-BaseOfferManufacturerCountries}
  
  Страна, где был произведен товар.
  
  Записывайте названия стран так, как они записаны в [списке](https://yastatic.net/s3/doc-binary/src/support/market/ru/countries.xlsx).
  
  
  **Type**: string[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "Россия"
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferWeightDimensionsDTO {#entity-OfferWeightDimensionsDTO}
  
  Габариты упаковки и вес товара.
  
  Если товар занимает несколько коробок, перед измерением размеров сложите их компактно.
  
  ![Схема измерения многоместных грузов](../../_images/reference/boxes-measure.png)
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _height_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Высота упаковки в см.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _length_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Длина упаковки в см.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _weight_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Вес товара в кг с учетом упаковки (брутто).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _width_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Ширина упаковки в см.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "length": 65.55,
    "width": 50.7,
    "height": 20,
    "weight": 1.001
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferVendorCode {#entity-OfferVendorCode}
  
  Артикул товара от производителя.
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `VNDR-0005A`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferTags {#entity-BaseOfferTags}
  
  Метки товара, которые использует магазин. Покупателям теги не видны. По тегам можно группировать и фильтровать разные товары в каталоге — например, товары одной серии, коллекции или линейки.
  
  Максимальная длина тега — 20 символов. У одного товара может быть максимум 10 тегов.
  
  
  **Type**: string[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "до 500 рублей"
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TimeUnitType {#entity-TimeUnitType}
  
  Единица измерения времени:
  
  * `HOUR` — час.
  * `DAY` — сутки.
  * `WEEK` — неделя.
  * `MONTH` — месяц.
  * `YEAR` — год.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `HOUR`, `DAY`, `WEEK`, `MONTH`, `YEAR`
  
  </div>
  
  <div class="openapi-entity">
  
  ### TimePeriodDTO {#entity-TimePeriodDTO}
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _timePeriod_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Продолжительность в указанных единицах.
  {.table-cell}
  ||
  ||
  
  _timeUnit_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TimeUnitType](#entity-TimeUnitType)
  
  Единица измерения.
  
  Единица измерения времени:
  
  * `HOUR` — час.
  * `DAY` — сутки.
  * `WEEK` — неделя.
  * `MONTH` — месяц.
  * `YEAR` — год.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `HOUR`, `DAY`, `WEEK`, `MONTH`, `YEAR`
  {.table-cell}
  ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `500`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferCustomsCommodityCode {#entity-BaseOfferCustomsCommodityCode}
  
  _Deprecated_{.json-schema-reset .json-schema-deprecated-title}{title="This entity is deprecated and may be removed in future versions."}
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `commodityCodes` с типом `CUSTOMS_COMMODITY_CODE`.
  
  {% endnote %}
  
  Код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  
  Обязательно укажите, если он есть.
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `8517610008`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CommodityCodeType {#entity-CommodityCodeType}
  
  Тип товарного кода:
  
  * `CUSTOMS_COMMODITY_CODE` — код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  * `IKPU_CODE` — идентификационный код продукции и услуг (ИКПУ) в Узбекистане – 17 цифр без пробелов.
  * `OKPD2_CODE` — код по Общероссийскому классификатору продукции по видам экономической деятельности (ОКПД2) — 2, 3, 4, 5, 6 или 9 цифр, разделенных точками: XX, XX.X, XX.XX, XX.XX.X, XX.XX.XX или XX.XX.XX.XXX.
  
  Не передавайте несколько кодов одного типа.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CUSTOMS_COMMODITY_CODE`, `IKPU_CODE`, `OKPD2_CODE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CommodityCodeDTO {#entity-CommodityCodeDTO}
  
  Товарный код.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Товарный код.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CommodityCodeType](#entity-CommodityCodeType)
  
  Тип товарного кода.
  
  Тип товарного кода:
  
  * `CUSTOMS_COMMODITY_CODE` — код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  * `IKPU_CODE` — идентификационный код продукции и услуг (ИКПУ) в Узбекистане – 17 цифр без пробелов.
  * `OKPD2_CODE` — код по Общероссийскому классификатору продукции по видам экономической деятельности (ОКПД2) — 2, 3, 4, 5, 6 или 9 цифр, разделенных точками: XX, XX.X, XX.XX, XX.XX.X, XX.XX.XX или XX.XX.XX.XXX.
  
  Не передавайте несколько кодов одного типа.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CUSTOMS_COMMODITY_CODE`, `IKPU_CODE`, `OKPD2_CODE`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "code": "example",
    "type": "CUSTOMS_COMMODITY_CODE"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferCommodityCodes {#entity-BaseOfferCommodityCodes}
  
  Товарные коды.
  
  
  **Type**: [CommodityCodeDTO](#entity-CommodityCodeDTO)[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "code": "example",
      "type": "CUSTOMS_COMMODITY_CODE"
    }
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferBoxCount {#entity-BaseOfferBoxCount}
  
  Количество грузовых мест.
  
  Параметр используется, если товар представляет собой несколько коробок, упаковок и так далее. Например, кондиционер занимает два места — внешний и внутренний блоки в двух коробках.
  
  Для товаров, занимающих одно место, не передавайте этот параметр.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferConditionType {#entity-OfferConditionType}
  
  Тип уценки:
  
  * `PREOWNED` —  бывший в употреблении товар, раньше принадлежал другому человеку.
  * `SHOWCASESAMPLE` — витринный образец.
  * `REFURBISHED` — повторная продажа товара.
  * `REDUCTION` — товар с дефектами.
  * `RENOVATED` — восстановленный товар.
  * `NOT_SPECIFIED` — не выбран.
  
  `REFURBISHED` — специальное значение для одежды, обуви и аксессуаров. Используется только для уцененных товаров из этой категории. Другие значения для одежды, обуви и аксессуаров не используются.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREOWNED`, `SHOWCASESAMPLE`, `REFURBISHED`, `REDUCTION`, `RENOVATED`, `NOT_SPECIFIED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferConditionQualityType {#entity-OfferConditionQualityType}
  
  Внешний вид товара:
  
  * `PERFECT` — идеальный.
  * `EXCELLENT` — отличный.
  * `GOOD` — хороший.
  * `NOT_SPECIFIED` — не выбран.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERFECT`, `EXCELLENT`, `GOOD`, `NOT_SPECIFIED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferConditionDTO {#entity-OfferConditionDTO}
  
  Состояние уцененного товара.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _quality_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferConditionQualityType](#entity-OfferConditionQualityType)
  
  Внешний вид товара.
  
  
  Внешний вид товара:
  
  * `PERFECT` — идеальный.
  * `EXCELLENT` — отличный.
  * `GOOD` — хороший.
  * `NOT_SPECIFIED` — не выбран.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERFECT`, `EXCELLENT`, `GOOD`, `NOT_SPECIFIED`
  {.table-cell}
  ||
  ||
  
  _reason_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание товара. Подробно опишите дефекты, насколько они заметны и где их искать.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferConditionType](#entity-OfferConditionType)
  
  Тип уценки.
  
  
  Тип уценки:
  
  * `PREOWNED` —  бывший в употреблении товар, раньше принадлежал другому человеку.
  * `SHOWCASESAMPLE` — витринный образец.
  * `REFURBISHED` — повторная продажа товара.
  * `REDUCTION` — товар с дефектами.
  * `RENOVATED` — восстановленный товар.
  * `NOT_SPECIFIED` — не выбран.
  
  `REFURBISHED` — специальное значение для одежды, обуви и аксессуаров. Используется только для уцененных товаров из этой категории. Другие значения для одежды, обуви и аксессуаров не используются.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREOWNED`, `SHOWCASESAMPLE`, `REFURBISHED`, `REDUCTION`, `RENOVATED`, `NOT_SPECIFIED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "PREOWNED",
    "quality": "PERFECT",
    "reason": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferType {#entity-OfferType}
  
  Особый тип товара:
  
  * `DEFAULT` — товары, для которых вы передавали особый тип ранее и хотите убрать его.
  * `MEDICINE` — лекарства.
  * `BOOK` — бумажные и электронные книги.
  * `AUDIOBOOK` — аудиокниги.
  * `ARTIST_TITLE` — музыкальная и видеопродукция.
  * `ON_DEMAND` — товары на заказ.
  * `ALCOHOL` — алкоголь.
  
  {% note info "Если ваш товар — книга" %}
  
  Укажите год издания в характеристиках товара. [Подробнее о параметре](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md#offerparamdto)
  
  {% endnote %}
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEFAULT`, `MEDICINE`, `BOOK`, `AUDIOBOOK`, `ARTIST_TITLE`, `ON_DEMAND`, `ALCOHOL`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferDownloadable {#entity-BaseOfferDownloadable}
  
  Признак цифрового товара. Укажите `true`, если товар доставляется по электронной почте.
  
  [Как работать с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)
  
  
  **Type**: boolean
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferAdult {#entity-BaseOfferAdult}
  
  Параметр включает для товара пометку 18+. Устанавливайте ее только для товаров, которые относятся к удовлетворению сексуальных потребностей.
  
  
  **Type**: boolean
  
  </div>
  
  <div class="openapi-entity">
  
  ### AgeUnitType {#entity-AgeUnitType}
  
  Единицы измерения возраста:
  
  * `YEAR` — год.
  * `MONTH` — месяц.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `YEAR`, `MONTH`
  
  </div>
  
  <div class="openapi-entity">
  
  ### AgeDTO {#entity-AgeDTO}
  
  Возраст в заданных единицах измерения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _ageUnit_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [AgeUnitType](#entity-AgeUnitType)
  
  Единица измерения.
  
  
  Единицы измерения возраста:
  
  * `YEAR` — год.
  * `MONTH` — месяц.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `YEAR`, `MONTH`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Значение.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "ageUnit": "YEAR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferParamDTO {#entity-OfferParamDTO}
  
  Параметры товара.
  
  Если у товара несколько значений одного параметра, передайте их с одним и тем же `name`, но разными `value`.
  
  {% cut "Пример" %}
  
  ```json translate=no
  "params": [
    {
      "name": "Цвет для фильтра",
      "value": "Зеленый"
    },
    {
      "name": "Цвет для фильтра",
      "value": "Желтый"
    }
  ]
  ```
  
  {% endcut %}
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название характеристики.
  
  Должно совпадать с названием характеристики на Маркете. Узнать его можно из Excel-шаблона категории или через запрос [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `200`
  
  _Example:_{.json-schema-reset .json-schema-example} `Wi-Fi`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Значение.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `есть`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "name": "Wi-Fi",
    "value": "есть"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferParams {#entity-BaseOfferParams}
  
  _Deprecated_{.json-schema-reset .json-schema-deprecated-title}{title="This entity is deprecated and may be removed in future versions."}
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  При передаче характеристик используйте `parameterValues`.
  
  {% endnote %}
  
  Характеристики, которые есть только у товаров конкретной категории — например, диаметр колес велосипеда или материал подошвы обуви.
  
  
  **Type**: [OfferParamDTO](#entity-OfferParamDTO)[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "name": "Wi-Fi",
      "value": "есть"
    }
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferResponseDTO {#entity-BaseOfferResponseDTO}
  
  Основные параметры товара.
  
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
  
  _adult_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferAdult](#entity-BaseOfferAdult)
  
  Параметр включает для товара пометку 18+. Устанавливайте ее только для товаров, которые относятся к удовлетворению сексуальных потребностей.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `true`
  {.table-cell}
  ||
  ||
  
  _age_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [AgeDTO](#entity-AgeDTO)
  
  Если товар не предназначен для детей младше определенного возраста, укажите это.
  
  Возрастное ограничение можно задавать в годах (с нуля, с 6, 12, 16 или 18) или в месяцах (любое число от 0 до 12).
  
  
  Возраст в заданных единицах измерения.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "ageUnit": "YEAR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _barcodes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferBarcodes](#entity-OfferBarcodes)
  
  Штрихкод.
  
  Указывайте в виде последовательности цифр. Подойдут коды EAN-13, EAN-8, UPC-A, UPC-E или Code 128. Для книг — ISBN.
  
  Для товаров [определенных категорий и торговых марок](https://yastatic.net/s3/doc-binary/src/support/market/ru/yandex-market-list-for-gtin.xlsx) штрихкод должен быть действительным кодом GTIN. Обратите внимание: внутренние штрихкоды, начинающиеся на 2 или 02, и коды формата Code 128 не являются GTIN.
  
  [Что такое GTIN](*gtin)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "46012300000000"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _boxCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferBoxCount](#entity-BaseOfferBoxCount)
  
  Количество грузовых мест.
  
  Параметр используется, если товар представляет собой несколько коробок, упаковок и так далее. Например, кондиционер занимает два места — внешний и внутренний блоки в двух коробках.
  
  Для товаров, занимающих одно место, не передавайте этот параметр.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _category_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [OfferCategory](#entity-OfferCategory)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `marketCategoryId`.
  
  {% endnote %}
  
  Категория товара в вашем магазине.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _certificates_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Номера документов на товар: сертификата, декларации соответствия и т. п.
  
  Передавать можно только номера документов, сканы которого загружены в кабинете продавца по [инструкции](https://yandex.ru/support/marketplace/assortment/restrictions/certificates.html).
  
  
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
  
  _commodityCodes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferCommodityCodes](#entity-BaseOfferCommodityCodes)
  
  Товарные коды.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "code": "example",
      "type": "CUSTOMS_COMMODITY_CODE"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _condition_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferConditionDTO](#entity-OfferConditionDTO)
  
  Состояние уцененного товара.
  
  Используется только для товаров, продаваемых с уценкой.
  
  [Правила продажи уцененных товаров](https://yandex.ru/support/marketplace/assortment/restrictions/used-goods.html)
  
  
  Состояние уцененного товара.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "PREOWNED",
    "quality": "PERFECT",
    "reason": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _customsCommodityCode_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [BaseOfferCustomsCommodityCode](#entity-BaseOfferCustomsCommodityCode)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `commodityCodes` с типом `CUSTOMS_COMMODITY_CODE`.
  
  {% endnote %}
  
  Код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  
  Обязательно укажите, если он есть.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `8517610008`
  {.table-cell}
  ||
  ||
  
  _description_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Подробное описание товара: например, его преимущества и особенности.
  
  Не давайте в описании инструкций по установке и сборке. Не используйте слова «скидка», «распродажа», «дешевый», «подарок» (кроме подарочных категорий), «бесплатно», «акция», «специальная цена», «новинка», «new», «аналог», «заказ», «хит». Не указывайте никакой контактной информации и не давайте ссылок.
  
  Для форматирования текста можно использовать теги HTML:
  
  * \<h>, \<h1>, \<h2> и так далее — для заголовков;
  * \<br> и \<p> — для переноса строки;
  * \<ol> — для нумерованного списка;
  * \<ul> — для маркированного списка;
  * \<li> — для создания элементов списка (должен находиться внутри \<ol> или \<ul>);
  * \<div> — поддерживается, но не влияет на отображение текста.
  
  Оптимальная длина — 400–600 символов.
  
  [Рекомендации и правила](https://yandex.ru/support/marketplace/assortment/fields/description.html)
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _downloadable_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferDownloadable](#entity-BaseOfferDownloadable)
  
  Признак цифрового товара. Укажите `true`, если товар доставляется по электронной почте.
  
  [Как работать с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)
  
  
  _Example:_{.json-schema-reset .json-schema-example} `true`
  {.table-cell}
  ||
  ||
  
  _guaranteePeriod_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimePeriodDTO](#entity-TimePeriodDTO)
  
  Гарантийный срок — период, в течение которого можно заменить или починить товар без дополнительной платы.
  
  Обязательно указывайте срок, если он есть.
  
  В комментарии опишите особенности гарантийного обслуживания. Например, `Гарантия на аккумулятор — 6 месяцев`.
  
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _lifeTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimePeriodDTO](#entity-TimePeriodDTO)
  
  Срок службы — период, в течение которого товар должен исправно выполнять свою функцию.
  
  Обязательно указывайте срок, если он есть.
  
  В комментарии укажите условия хранения. Например, `Использовать при температуре не ниже −10 градусов`.
  
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _manuals_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferManualDTO](#entity-OfferManualDTO)[] &#124; null
  
  Список инструкций по использованию товара.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "url": "example",
      "title": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _manufacturerCountries_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferManufacturerCountries](#entity-BaseOfferManufacturerCountries)
  
  Страна, где был произведен товар.
  
  Записывайте названия стран так, как они записаны в [списке](https://yastatic.net/s3/doc-binary/src/support/market/ru/countries.xlsx).
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "Россия"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _marketCategoryId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PartnerMarketCategoryId](#entity-PartnerMarketCategoryId)
  
  Идентификатор категории на Маркете, к которой вы относите свой товар.
  
  {% note warning "Всегда указывайте, когда передаете `parameterValues`" %}
  
  Если при изменении характеристик передать `parameterValues` и не указать `marketCategoryId`, характеристики обновятся, но в ответе придет предупреждение (параметр `warnings`).
  
  Если не передать их оба, будет использована информация из устаревших параметров `params` и `category`, а `marketCategoryId` будет определен автоматически.
  
  {% endnote %}
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Составляйте название по схеме: тип + бренд или производитель + модель + особенности, если есть (например, цвет, размер или вес) и количество в упаковке.
  
  Не включайте в название условия продажи (например, «скидка», «бесплатная доставка» и т. д.), эмоциональные характеристики («хит», «супер» и т. д.). Не пишите слова большими буквами — кроме устоявшихся названий брендов и моделей.
  
  Оптимальная длина — 50–60 символов.
  
  [Рекомендации и правила](https://yandex.ru/support/marketplace/assortment/fields/title.html)
  
  
  _Example:_{.json-schema-reset .json-schema-example} `Ударная дрель Makita HP1630, 710 Вт`
  {.table-cell}
  ||
  ||
  
  _params_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [BaseOfferParams](#entity-BaseOfferParams)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  При передаче характеристик используйте `parameterValues`.
  
  {% endnote %}
  
  Характеристики, которые есть только у товаров конкретной категории — например, диаметр колес велосипеда или материал подошвы обуви.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "name": "Wi-Fi",
      "value": "есть"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pictures_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)[] &#124; null
  
  Ссылки на изображения товара. Изображение по первой ссылке считается основным, остальные дополнительными.
  
  **Требования к ссылкам**
  
  * Ссылок может быть до 30.
  * Указывайте ссылку целиком, включая протокол http или https.
  * Максимальная длина — 512 символов.
  * Русские буквы в URL можно.
  * Можно использовать прямые ссылки на изображения и на Яндекс Диск. Ссылки на Яндекс Диске нужно копировать с помощью функции **Поделиться**. Относительные ссылки и ссылки на другие облачные хранилища — не работают.
  
  ✅ `https://example-shop.ru/images/sku12345.jpg`
  
  ✅ `https://yadi.sk/i/NaBoRsimVOLov`
  
  ❌ `/images/sku12345.jpg`
  
  ❌ `https://www.dropbox.com/s/818f/tovar.jpg`
  
  Ссылки на изображение должны быть постоянными. Нельзя использовать динамические ссылки, меняющиеся от выгрузки к выгрузке.
  
  Если нужно заменить изображение, выложите новое изображение по новой ссылке, а ссылку на старое удалите. Если просто заменить изображение по старой ссылке, оно не обновится.
  
  [Требования к изображениям](https://yandex.ru/support/marketplace/assortment/fields/images.html)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  _shelfLife_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimePeriodDTO](#entity-TimePeriodDTO)
  
  Срок годности — период, по прошествии которого товар становится непригоден.
  
  Указывайте срок, указанный на банке или упаковке. Текущая дата, дата поставки или дата отгрузки значения не имеет.
  
  Обязательно указывайте срок, если он есть.
  
  В комментарии укажите условия хранения. Например, `Хранить в сухом помещении`.
  
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _tags_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferTags](#entity-BaseOfferTags)
  
  Метки товара, которые использует магазин. Покупателям теги не видны. По тегам можно группировать и фильтровать разные товары в каталоге — например, товары одной серии, коллекции или линейки.
  
  Максимальная длина тега — 20 символов. У одного товара может быть максимум 10 тегов.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "до 500 рублей"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferType](#entity-OfferType)
  
  Особый тип товара. Указывается, если товар:
  
  * имеет особый тип, который хотите убрать;
  * лекарство;
  * бумажная или электронная книга;
  * аудиокнига;
  * музыка или видео;
  * изготовляется на заказ;
  * алкоголь.
  
  
  Особый тип товара:
  
  * `DEFAULT` — товары, для которых вы передавали особый тип ранее и хотите убрать его.
  * `MEDICINE` — лекарства.
  * `BOOK` — бумажные и электронные книги.
  * `AUDIOBOOK` — аудиокниги.
  * `ARTIST_TITLE` — музыкальная и видеопродукция.
  * `ON_DEMAND` — товары на заказ.
  * `ALCOHOL` — алкоголь.
  
  {% note info "Если ваш товар — книга" %}
  
  Укажите год издания в характеристиках товара. [Подробнее о параметре](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md#offerparamdto)
  
  {% endnote %}
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEFAULT`, `MEDICINE`, `BOOK`, `AUDIOBOOK`, `ARTIST_TITLE`, `ON_DEMAND`, `ALCOHOL`
  {.table-cell}
  ||
  ||
  
  _vendor_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferVendor](#entity-OfferVendor)
  
  Название бренда или производителя. Должно быть записано так, как его пишет сам бренд.
  
  _Example:_{.json-schema-reset .json-schema-example} `LEVENHUK`
  {.table-cell}
  ||
  ||
  
  _vendorCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferVendorCode](#entity-OfferVendorCode)
  
  Артикул товара от производителя.
  
  _Example:_{.json-schema-reset .json-schema-example} `VNDR-0005A`
  {.table-cell}
  ||
  ||
  
  _videos_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)[] &#124; null
  
  Ссылки (URL) на видео товара.
  
  **Требования к ссылке**
  
  * Указывайте ссылку целиком, включая протокол http или https.
  * Максимальная длина — 512 символов.
  * Русские буквы в URL можно.
  * Можно использовать прямые ссылки на видео и на Яндекс Диск. Ссылки на Яндекс Диске нужно копировать с помощью функции **Поделиться**. Относительные ссылки и ссылки на другие облачные хранилища — не работают.
  
  ✅ `https://example-shop.ru/video/sku12345.avi`
  
  ✅ `https://yadi.sk/i/NaBoRsimVOLov`
  
  ❌ `/video/sku12345.avi`
  
  ❌ `https://www.dropbox.com/s/818f/super-tovar.avi`
  
  Ссылки на видео должны быть постоянными. Нельзя использовать динамические ссылки, меняющиеся от выгрузки к выгрузке.
  
  Если нужно заменить видео, выложите новое видео по новой ссылке, а ссылку на старое удалите. Если просто заменить видео по старой ссылке, оно не обновится.
  
  [Требования к видео](https://yandex.ru/support/marketplace/assortment/fields/video.html)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  _weightDimensions_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferWeightDimensionsDTO](#entity-OfferWeightDimensionsDTO)
  
  Габариты упаковки и вес товара.
  
  
  Габариты упаковки и вес товара.
  
  Если товар занимает несколько коробок, перед измерением размеров сложите их компактно.
  
  ![Схема измерения многоместных грузов](../../_images/reference/boxes-measure.png)
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "length": 65.55,
    "width": 50.7,
    "height": 20,
    "weight": 1.001
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
    "name": "Ударная дрель Makita HP1630, 710 Вт",
    "marketCategoryId": 0,
    "category": "example",
    "pictures": [
      "example"
    ],
    "videos": [
      null
    ],
    "manuals": [
      {
        "url": null,
        "title": "example"
      }
    ],
    "vendor": "LEVENHUK",
    "barcodes": [
      "46012300000000"
    ],
    "description": "example",
    "manufacturerCountries": [
      "Россия"
    ],
    "weightDimensions": {
      "length": 65.55,
      "width": 50.7,
      "height": 20,
      "weight": 1.001
    },
    "vendorCode": "VNDR-0005A",
    "tags": [
      "до 500 рублей"
    ],
    "shelfLife": {
      "timePeriod": 0,
      "timeUnit": "HOUR",
      "comment": "example"
    },
    "lifeTime": null,
    "guaranteePeriod": null,
    "customsCommodityCode": "8517610008",
    "commodityCodes": [
      {
        "code": "example",
        "type": "CUSTOMS_COMMODITY_CODE"
      }
    ],
    "certificates": [
      "example"
    ],
    "boxCount": 1,
    "condition": {
      "type": "PREOWNED",
      "quality": "PERFECT",
      "reason": "example"
    },
    "type": "DEFAULT",
    "downloadable": true,
    "adult": true,
    "age": {
      "value": 0,
      "ageUnit": "YEAR"
    },
    "params": [
      {
        "name": "Wi-Fi",
        "value": "есть"
      }
    ]
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
  
  ### GetPriceDTO {#entity-GetPriceDTO}
  
  Цена с указанием времени последнего обновления.
  
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
    "updatedAt": "2025-01-01T00:00:00Z"
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
  
  <div class="openapi-entity">
  
  ### OfferCampaignStatusDTO {#entity-OfferCampaignStatusDTO}
  
  Статус товара в магазине.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
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
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "campaignId": 1,
    "status": "PUBLISHED"
  }
  ```
  
  {% endcut %}
  
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
  
  ### OfferSellingProgramStatusType {#entity-OfferSellingProgramStatusType}
  
  Информация о доступности или недоступности.
  
  * `FINE` — доступно.
  * `REJECT` — недоступно.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FINE`, `REJECT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferSellingProgramDTO {#entity-OfferSellingProgramDTO}
  
  Информация о том, по каким моделям можно продавать товар, а по каким нельзя.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _sellingProgram_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SellingProgramType](#entity-SellingProgramType)
  
  Модель работы.
  
  
  Модель работы:
  
  * `FBY` — FBY.
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  * `LAAS` — LaaS.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBY`, `FBS`, `DBS`, `EXPRESS`, `LAAS`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferSellingProgramStatusType](#entity-OfferSellingProgramStatusType)
  
  Информация о том, можно ли по этой модели продавать товар.
  
  
  Информация о доступности или недоступности.
  
  * `FINE` — доступно.
  * `REJECT` — недоступно.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FINE`, `REJECT`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sellingProgram": "FBY",
    "status": "FINE"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### MediaFileUploadStateType {#entity-MediaFileUploadStateType}
  
  Состояние загрузки медиафайла:
  
  * `UPLOADING` — загружается.
  * `UPLOADED` — успешно загружен.
  * `FAILED` — при загрузке произошла ошибка. Повторите попытку позже.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UPLOADING`, `UPLOADED`, `FAILED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferMediaFileDTO {#entity-OfferMediaFileDTO}
  
  Информация о медиафайле товара.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _title_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название медиафайла.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _uploadState_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MediaFileUploadStateType](#entity-MediaFileUploadStateType)
  
  Состояние загрузки медиафайла.
  
  
  Состояние загрузки медиафайла:
  
  * `UPLOADING` — загружается.
  * `UPLOADED` — успешно загружен.
  * `FAILED` — при загрузке произошла ошибка. Повторите попытку позже.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UPLOADING`, `UPLOADED`, `FAILED`
  {.table-cell}
  ||
  ||
  
  _url_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)
  
  Ссылка на медиафайл.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "url": "example",
    "title": "example",
    "uploadState": "UPLOADING"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferMediaFilesDTO {#entity-OfferMediaFilesDTO}
  
  Информация о медиафайлах товара.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _firstVideoAsCover_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: boolean
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
   
  
  {% endnote %}
  
  Использовать первое видео в карточке как видеообложку.
  
  Передайте `true`, чтобы первое видео использовалось как видеообложка, или `false`, чтобы видеообложка не отображалась в карточке товара.
  
  {.table-cell}
  ||
  ||
  
  _manuals_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferMediaFileDTO](#entity-OfferMediaFileDTO)[] &#124; null
  
  Руководства по использованию товара.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "url": "example",
      "title": "example",
      "uploadState": "UPLOADING"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pictures_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferMediaFileDTO](#entity-OfferMediaFileDTO)[] &#124; null
  
  Изображения товара.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "url": "example",
      "title": "example",
      "uploadState": "UPLOADING"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _videos_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferMediaFileDTO](#entity-OfferMediaFileDTO)[] &#124; null
  
  Видеофайлы товара.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "url": "example",
      "title": "example",
      "uploadState": "UPLOADING"
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
    "firstVideoAsCover": true,
    "videos": [
      {
        "url": "example",
        "title": "example",
        "uploadState": "UPLOADING"
      }
    ],
    "pictures": [
      null
    ],
    "manuals": [
      null
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetOfferDTO {#entity-GetOfferDTO}
  
  Параметры товара.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BaseOfferResponseDTO](#entity-BaseOfferResponseDTO)
  
    Основные параметры товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offerId": "example",
      "name": "Ударная дрель Makita HP1630, 710 Вт",
      "marketCategoryId": 0,
      "category": "example",
      "pictures": [
        "example"
      ],
      "videos": [
        null
      ],
      "manuals": [
        {
          "url": null,
          "title": "example"
        }
      ],
      "vendor": "LEVENHUK",
      "barcodes": [
        "46012300000000"
      ],
      "description": "example",
      "manufacturerCountries": [
        "Россия"
      ],
      "weightDimensions": {
        "length": 65.55,
        "width": 50.7,
        "height": 20,
        "weight": 1.001
      },
      "vendorCode": "VNDR-0005A",
      "tags": [
        "до 500 рублей"
      ],
      "shelfLife": {
        "timePeriod": 0,
        "timeUnit": "HOUR",
        "comment": "example"
      },
      "lifeTime": null,
      "guaranteePeriod": null,
      "customsCommodityCode": "8517610008",
      "commodityCodes": [
        {
          "code": "example",
          "type": "CUSTOMS_COMMODITY_CODE"
        }
      ],
      "certificates": [
        "example"
      ],
      "boxCount": 1,
      "condition": {
        "type": "PREOWNED",
        "quality": "PERFECT",
        "reason": "example"
      },
      "type": "DEFAULT",
      "downloadable": true,
      "adult": true,
      "age": {
        "value": 0,
        "ageUnit": "YEAR"
      },
      "params": [
        {
          "name": "Wi-Fi",
          "value": "есть"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _additionalExpenses_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GetPriceDTO](#entity-GetPriceDTO)
  
    Дополнительные расходы на товар. Например, на доставку или упаковку.
  
  
    Цена с указанием времени последнего обновления.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR",
      "updatedAt": "2025-01-01T00:00:00Z"
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _archived_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: boolean
  
    Товар помещен в архив.
  
    {.table-cell}
    ||
    ||
  
    _basicPrice_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GetPriceWithDiscountDTO](#entity-GetPriceWithDiscountDTO)
  
    Цена.
  
  
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
  
    _campaigns_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferCampaignStatusDTO](#entity-OfferCampaignStatusDTO)[] &#124; null
  
    Список магазинов, в которых размещен товар.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "campaignId": 1,
        "status": "PUBLISHED"
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _cardStatus_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferCardStatusType](#entity-OfferCardStatusType)
  
    Статус карточки товара.
  
  
    Статус карточки товара:
  
    * `HAS_CARD_CAN_NOT_UPDATE` — Карточка Маркета.
    * `HAS_CARD_CAN_UPDATE` — Можно дополнить.
    * `HAS_CARD_CAN_UPDATE_ERRORS` — Изменения не приняты.
    * `HAS_CARD_CAN_UPDATE_PROCESSING` — Изменения на проверке.
    * `NO_CARD_NEED_CONTENT` — Создайте карточку.
    * `NO_CARD_MARKET_WILL_CREATE` — Создаст Маркет.
    * `NO_CARD_ERRORS` — Не создана из-за ошибки.
    * `NO_CARD_PROCESSING` — Проверяем данные.
    * `NO_CARD_ADD_TO_CAMPAIGN` — Разместите товар в магазине.
  
  
    _Enum:_{.json-schema-reset .json-schema-value} `HAS_CARD_CAN_NOT_UPDATE`, `HAS_CARD_CAN_UPDATE`, `HAS_CARD_CAN_UPDATE_ERRORS`, `HAS_CARD_CAN_UPDATE_PROCESSING`, `NO_CARD_NEED_CONTENT`, `NO_CARD_MARKET_WILL_CREATE`, `NO_CARD_ERRORS`, `NO_CARD_PROCESSING`, `NO_CARD_ADD_TO_CAMPAIGN`
    {.table-cell}
    ||
    ||
  
    _groupId_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Идентификатор группы товаров.
  
    У товаров, которые объединены в одну группу, будет одинаковый идентификатор.
  
    [Как объединить товары на карточке](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md#combine-variants)
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _mediaFiles_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferMediaFilesDTO](#entity-OfferMediaFilesDTO)
  
    Информация о медиафайлах товара.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "firstVideoAsCover": true,
      "videos": [
        {
          "url": "example",
          "title": "example",
          "uploadState": "UPLOADING"
        }
      ],
      "pictures": [
        null
      ],
      "manuals": [
        null
      ]
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _purchasePrice_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [GetPriceDTO](#entity-GetPriceDTO)
  
    Себестоимость — затраты на самостоятельное производство товара или закупку у производителя или поставщиков.
  
  
    Цена с указанием времени последнего обновления.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR",
      "updatedAt": "2025-01-01T00:00:00Z"
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _sellingPrograms_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OfferSellingProgramDTO](#entity-OfferSellingProgramDTO)[] &#124; null
  
    Информация о том, какие для товара доступны модели размещения.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "sellingProgram": "FBY",
        "status": "FINE"
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
      "purchasePrice": null,
      "additionalExpenses": null,
      "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
      "campaigns": [
        {
          "campaignId": 1,
          "status": "PUBLISHED"
        }
      ],
      "sellingPrograms": [
        {
          "sellingProgram": "FBY",
          "status": "FINE"
        }
      ],
      "mediaFiles": {
        "firstVideoAsCover": true,
        "videos": [
          {
            "url": "example",
            "title": "example",
            "uploadState": "UPLOADING"
          }
        ],
        "pictures": [
          null
        ],
        "manuals": [
          null
        ]
      },
      "archived": true,
      "groupId": "example"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "name": "Ударная дрель Makita HP1630, 710 Вт",
    "marketCategoryId": 0,
    "category": "example",
    "pictures": [
      "example"
    ],
    "videos": [
      null
    ],
    "manuals": [
      {
        "url": null,
        "title": "example"
      }
    ],
    "vendor": "LEVENHUK",
    "barcodes": [
      "46012300000000"
    ],
    "description": "example",
    "manufacturerCountries": [
      "Россия"
    ],
    "weightDimensions": {
      "length": 65.55,
      "width": 50.7,
      "height": 20,
      "weight": 1.001
    },
    "vendorCode": "VNDR-0005A",
    "tags": [
      "до 500 рублей"
    ],
    "shelfLife": {
      "timePeriod": 0,
      "timeUnit": "HOUR",
      "comment": "example"
    },
    "lifeTime": null,
    "guaranteePeriod": null,
    "customsCommodityCode": "8517610008",
    "commodityCodes": [
      {
        "code": "example",
        "type": "CUSTOMS_COMMODITY_CODE"
      }
    ],
    "certificates": [
      "example"
    ],
    "boxCount": 1,
    "condition": {
      "type": "PREOWNED",
      "quality": "PERFECT",
      "reason": "example"
    },
    "type": "DEFAULT",
    "downloadable": true,
    "adult": true,
    "age": {
      "value": 0,
      "ageUnit": "YEAR"
    },
    "params": [
      {
        "name": "Wi-Fi",
        "value": "есть"
      }
    ],
    "basicPrice": {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0,
      "updatedAt": "2025-01-01T00:00:00Z"
    },
    "purchasePrice": null,
    "additionalExpenses": null,
    "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
    "campaigns": [
      {
        "campaignId": 1,
        "status": "PUBLISHED"
      }
    ],
    "sellingPrograms": [
      {
        "sellingProgram": "FBY",
        "status": "FINE"
      }
    ],
    "mediaFiles": {
      "firstVideoAsCover": true,
      "videos": [
        {
          "url": null,
          "title": "example",
          "uploadState": "UPLOADING"
        }
      ],
      "pictures": [
        null
      ],
      "manuals": [
        null
      ]
    },
    "archived": true,
    "groupId": "example"
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
  
  ### UpdateMappingDTO {#entity-UpdateMappingDTO}
  
  Карточка на Маркете, которая, с вашей точки зрения, подходит товару. Чтобы определить идентификатор подходящей карточки, воспользуйтесь поиском в кабинете (**Товары** → **Каталог** → **Загрузить товары**).
  
  По результатам проверки Маркет может привязать товар к более подходящей карточке.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _marketSku_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MarketSku](#entity-MarketSku)
  
  Идентификатор карточки на Маркете.
  
  
  Идентификатор карточки товара на Маркете.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "marketSku": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetMappingDTO {#entity-GetMappingDTO}
  
  Информация о товарах в каталоге.
  
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [UpdateMappingDTO](#entity-UpdateMappingDTO)
  
    Идентификатор карточки на Маркете. Показывает текущую привязку товара к карточке.
  
    Может отсутствовать в ответе, если товар еще не привязан к карточке. Проверьте статус карточки или исправьте ошибки.
  
  
    Карточка на Маркете, которая, с вашей точки зрения, подходит товару. Чтобы определить идентификатор подходящей карточки, воспользуйтесь поиском в кабинете (**Товары** → **Каталог** → **Загрузить товары**).
  
    По результатам проверки Маркет может привязать товар к более подходящей карточке.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "marketSku": 1
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _marketCategoryId_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: integer
  
    Идентификатор категории на Маркете, в которую попал товар.
  
    Может отсутствовать в ответе, если Маркет еще не определил категорию товара.
  
    {.table-cell}
    ||
    ||
  
    _marketCategoryName_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Название категории карточки на Маркете.
  
    Может отсутствовать в ответе, если Маркет еще не определил категорию товара.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _marketModelName_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
    {.table-cell}|
    **Type**: string
  
    {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
     
  
    {% endnote %}
  
    Название модели на Маркете.
  
    Может отсутствовать в ответе, если товар еще не привязан к карточке.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _marketSkuName_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Название карточки товара.
  
    Может отсутствовать в ответе, если товар еще не привязан к карточке.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "marketSkuName": "example",
      "marketModelName": "example",
      "marketCategoryId": 0,
      "marketCategoryName": "example"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "marketSku": 1,
    "marketSkuName": "example",
    "marketModelName": "example",
    "marketCategoryId": 0,
    "marketCategoryName": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ShowcaseType {#entity-ShowcaseType}
  
  Тип витрины:
  
  * `B2B` — [Яндекс Маркет для бизнеса](https://business.market.yandex.ru/) (товары для юридических лиц и ИП). Подробнее о сервисе читайте в [Справке](https://yandex.ru/support/market-for-enterprise/ru/).
  * `B2C` — [основная витрина Маркета](https://market.yandex.ru/) (товары для физических лиц).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `B2B`, `B2C`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ShowcaseUrlDTO {#entity-ShowcaseUrlDTO}
  
  Ссылка на товар на витрине и ее тип.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _showcaseType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShowcaseType](#entity-ShowcaseType)
  
  Тип витрины.
  
  Тип витрины:
  
  * `B2B` — [Яндекс Маркет для бизнеса](https://business.market.yandex.ru/) (товары для юридических лиц и ИП). Подробнее о сервисе читайте в [Справке](https://yandex.ru/support/market-for-enterprise/ru/).
  * `B2C` — [основная витрина Маркета](https://market.yandex.ru/) (товары для физических лиц).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `B2B`, `B2C`
  {.table-cell}
  ||
  ||
  
  _showcaseUrl_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Ссылка на товар.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "showcaseType": "B2B",
    "showcaseUrl": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetOfferMappingDTO {#entity-GetOfferMappingDTO}
  
  Информация о товаре.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _mapping_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GetMappingDTO](#entity-GetMappingDTO)
  
  Информация о карточке товара на Маркете.
  
  Информация о товарах в каталоге.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "marketSku": 1,
    "marketSkuName": "example",
    "marketModelName": "example",
    "marketCategoryId": 0,
    "marketCategoryName": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _offer_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GetOfferDTO](#entity-GetOfferDTO)
  
  Основные параметры товара.
  
  Параметры товара.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "name": "Ударная дрель Makita HP1630, 710 Вт",
    "marketCategoryId": 0,
    "category": "example",
    "pictures": [
      "example"
    ],
    "videos": [
      null
    ],
    "manuals": [
      {
        "url": null,
        "title": "example"
      }
    ],
    "vendor": "LEVENHUK",
    "barcodes": [
      "46012300000000"
    ],
    "description": "example",
    "manufacturerCountries": [
      "Россия"
    ],
    "weightDimensions": {
      "length": 65.55,
      "width": 50.7,
      "height": 20,
      "weight": 1.001
    },
    "vendorCode": "VNDR-0005A",
    "tags": [
      "до 500 рублей"
    ],
    "shelfLife": {
      "timePeriod": 0,
      "timeUnit": "HOUR",
      "comment": "example"
    },
    "lifeTime": null,
    "guaranteePeriod": null,
    "customsCommodityCode": "8517610008",
    "commodityCodes": [
      {
        "code": "example",
        "type": "CUSTOMS_COMMODITY_CODE"
      }
    ],
    "certificates": [
      "example"
    ],
    "boxCount": 1,
    "condition": {
      "type": "PREOWNED",
      "quality": "PERFECT",
      "reason": "example"
    },
    "type": "DEFAULT",
    "downloadable": true,
    "adult": true,
    "age": {
      "value": 0,
      "ageUnit": "YEAR"
    },
    "params": [
      {
        "name": "Wi-Fi",
        "value": "есть"
      }
    ],
    "basicPrice": {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0,
      "updatedAt": "2025-01-01T00:00:00Z"
    },
    "purchasePrice": null,
    "additionalExpenses": null,
    "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
    "campaigns": [
      {
        "campaignId": 1,
        "status": "PUBLISHED"
      }
    ],
    "sellingPrograms": [
      {
        "sellingProgram": "FBY",
        "status": "FINE"
      }
    ],
    "mediaFiles": {
      "firstVideoAsCover": true,
      "videos": [
        {
          "url": null,
          "title": "example",
          "uploadState": "UPLOADING"
        }
      ],
      "pictures": [
        null
      ],
      "manuals": [
        null
      ]
    },
    "archived": true,
    "groupId": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _showcaseUrls_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShowcaseUrlDTO](#entity-ShowcaseUrlDTO)[] &#124; null
  
  Ссылки на один и тот же товар на разных витринах Маркета.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "showcaseType": "B2B",
      "showcaseUrl": "example"
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
      "offerId": "example",
      "name": "Ударная дрель Makita HP1630, 710 Вт",
      "marketCategoryId": 0,
      "category": "example",
      "pictures": [
        "example"
      ],
      "videos": [
        null
      ],
      "manuals": [
        {
          "url": null,
          "title": "example"
        }
      ],
      "vendor": "LEVENHUK",
      "barcodes": [
        "46012300000000"
      ],
      "description": "example",
      "manufacturerCountries": [
        "Россия"
      ],
      "weightDimensions": {
        "length": 65.55,
        "width": 50.7,
        "height": 20,
        "weight": 1.001
      },
      "vendorCode": "VNDR-0005A",
      "tags": [
        "до 500 рублей"
      ],
      "shelfLife": {
        "timePeriod": 0,
        "timeUnit": "HOUR",
        "comment": "example"
      },
      "lifeTime": null,
      "guaranteePeriod": null,
      "customsCommodityCode": "8517610008",
      "commodityCodes": [
        {
          "code": "example",
          "type": "CUSTOMS_COMMODITY_CODE"
        }
      ],
      "certificates": [
        "example"
      ],
      "boxCount": 1,
      "condition": {
        "type": "PREOWNED",
        "quality": "PERFECT",
        "reason": "example"
      },
      "type": "DEFAULT",
      "downloadable": true,
      "adult": true,
      "age": {
        "value": 0,
        "ageUnit": "YEAR"
      },
      "params": [
        {
          "name": "Wi-Fi",
          "value": "есть"
        }
      ],
      "basicPrice": {
        "updatedAt": "2025-01-01T00:00:00Z"
      },
      "purchasePrice": null,
      "additionalExpenses": null,
      "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
      "campaigns": [
        {
          "campaignId": 1,
          "status": "PUBLISHED"
        }
      ],
      "sellingPrograms": [
        {
          "sellingProgram": "FBY",
          "status": "FINE"
        }
      ],
      "mediaFiles": {
        "firstVideoAsCover": true,
        "videos": [
          {}
        ],
        "pictures": [
          null
        ],
        "manuals": [
          null
        ]
      },
      "archived": true,
      "groupId": "example"
    },
    "mapping": {
      "marketSku": 1,
      "marketSkuName": "example",
      "marketModelName": "example",
      "marketCategoryId": 0,
      "marketCategoryName": "example"
    },
    "showcaseUrls": [
      {
        "showcaseType": "B2B",
        "showcaseUrl": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetOfferMappingsResultDTO {#entity-GetOfferMappingsResultDTO}
  
  Информация о товарах.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerMappings_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetOfferMappingDTO](#entity-GetOfferMappingDTO)[]
  
  Информация о товарах.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offer": {
        "offerId": "example",
        "name": "Ударная дрель Makita HP1630, 710 Вт",
        "marketCategoryId": 0,
        "category": "example",
        "pictures": [
          "example"
        ],
        "videos": [
          null
        ],
        "manuals": [
          {}
        ],
        "vendor": "LEVENHUK",
        "barcodes": [
          "46012300000000"
        ],
        "description": "example",
        "manufacturerCountries": [
          "Россия"
        ],
        "weightDimensions": {
          "length": 65.55,
          "width": 50.7,
          "height": 20,
          "weight": 1.001
        },
        "vendorCode": "VNDR-0005A",
        "tags": [
          "до 500 рублей"
        ],
        "shelfLife": {
          "timePeriod": 0,
          "timeUnit": "HOUR",
          "comment": "example"
        },
        "lifeTime": null,
        "guaranteePeriod": null,
        "customsCommodityCode": "8517610008",
        "commodityCodes": [
          {}
        ],
        "certificates": [
          "example"
        ],
        "boxCount": 1,
        "condition": {
          "type": "PREOWNED",
          "quality": "PERFECT",
          "reason": "example"
        },
        "type": "DEFAULT",
        "downloadable": true,
        "adult": true,
        "age": {
          "value": 0,
          "ageUnit": "YEAR"
        },
        "params": [
          {}
        ],
        "basicPrice": {},
        "purchasePrice": {},
        "additionalExpenses": null,
        "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
        "campaigns": [
          {}
        ],
        "sellingPrograms": [
          {}
        ],
        "mediaFiles": {
          "firstVideoAsCover": true,
          "videos": [
            null
          ],
          "pictures": [
            null
          ],
          "manuals": [
            null
          ]
        },
        "archived": true,
        "groupId": "example"
      },
      "mapping": {
        "marketSku": 1,
        "marketSkuName": "example",
        "marketModelName": "example",
        "marketCategoryId": 0,
        "marketCategoryName": "example"
      },
      "showcaseUrls": [
        {
          "showcaseType": "B2B",
          "showcaseUrl": "example"
        }
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
    "offerMappings": [
      {
        "offer": {
          "offerId": "example",
          "name": "Ударная дрель Makita HP1630, 710 Вт",
          "marketCategoryId": 0,
          "category": "example",
          "pictures": [
            null
          ],
          "videos": [
            null
          ],
          "manuals": [
            null
          ],
          "vendor": "LEVENHUK",
          "barcodes": [
            null
          ],
          "description": "example",
          "manufacturerCountries": [
            null
          ],
          "weightDimensions": {},
          "vendorCode": "VNDR-0005A",
          "tags": [
            null
          ],
          "shelfLife": {},
          "lifeTime": null,
          "guaranteePeriod": null,
          "customsCommodityCode": "8517610008",
          "commodityCodes": [
            null
          ],
          "certificates": [
            null
          ],
          "boxCount": 1,
          "condition": {},
          "type": "DEFAULT",
          "downloadable": true,
          "adult": true,
          "age": {},
          "params": [
            null
          ],
          "basicPrice": {},
          "purchasePrice": {},
          "additionalExpenses": null,
          "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
          "campaigns": [
            null
          ],
          "sellingPrograms": [
            null
          ],
          "mediaFiles": {},
          "archived": true,
          "groupId": "example"
        },
        "mapping": {
          "marketSku": 1,
          "marketSkuName": "example",
          "marketModelName": "example",
          "marketCategoryId": 0,
          "marketCategoryName": "example"
        },
        "showcaseUrls": [
          {
            "showcaseType": "B2B",
            "showcaseUrl": "example"
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
    - description: >
        Язык, на котором принимаются и возвращаются значения в параметрах `name` и
        `description`.
  
  
        Значение по умолчанию: `RU`.
      name: language
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/54qq/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/CatalogLanguageType
  headers: []
  body: |-
    {
      "offerIds": [
        "example"
      ],
      "cardStatuses": [
        "HAS_CARD_CAN_NOT_UPDATE"
      ],
      "categoryIds": [
        0
      ],
      "vendorNames": [
        "example"
      ],
      "tags": [
        "example"
      ],
      "archived": true
    }
  schema:
    type: object
    properties:
      offerIds:
        description: "Идентификаторы товаров, информация о которых нужна.\n\n{% note warning \"Такой список возвращается только целиком\" %}\n\nЕсли вы запрашиваете информацию по конкретным SKU, не заполняйте:\n* `pageToken`;\n* `limit`;\n* `cardStatuses`;\n* `categoryIds`;\n* `vendorNames`;\n* `tags`;\n* `archived`.\n\n{% endnote %}\n\n\_\n"
        type: array
        nullable: true
        minItems: 1
        maxItems: 100
        uniqueItems: true
        items:
          description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
          type: string
          pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
          x-transform: trim
          minLength: 1
          maxLength: 255
      cardStatuses:
        description: >
          Фильтр по статусам карточек.
  
  
          [Что такое карточка
          товара](https://yandex.ru/support/marketplace/assortment/content/index.html)
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: |
            Статус карточки товара:
  
            * `HAS_CARD_CAN_NOT_UPDATE` — Карточка Маркета.
            * `HAS_CARD_CAN_UPDATE` — Можно дополнить.
            * `HAS_CARD_CAN_UPDATE_ERRORS` — Изменения не приняты.
            * `HAS_CARD_CAN_UPDATE_PROCESSING` — Изменения на проверке.
            * `NO_CARD_NEED_CONTENT` — Создайте карточку.
            * `NO_CARD_MARKET_WILL_CREATE` — Создаст Маркет.
            * `NO_CARD_ERRORS` — Не создана из-за ошибки.
            * `NO_CARD_PROCESSING` — Проверяем данные.
            * `NO_CARD_ADD_TO_CAMPAIGN` — Разместите товар в магазине.
          type: string
          enum:
            - HAS_CARD_CAN_NOT_UPDATE
            - HAS_CARD_CAN_UPDATE
            - HAS_CARD_CAN_UPDATE_ERRORS
            - HAS_CARD_CAN_UPDATE_PROCESSING
            - NO_CARD_NEED_CONTENT
            - NO_CARD_MARKET_WILL_CREATE
            - NO_CARD_ERRORS
            - NO_CARD_PROCESSING
            - NO_CARD_ADD_TO_CAMPAIGN
      categoryIds:
        description: Фильтр по категориям на Маркете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          type: integer
          format: int32
          minimum: 0
          exclusiveMinimum: true
      vendorNames:
        description: Фильтр по брендам.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          type: string
      tags:
        description: Фильтр по тегам.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          type: string
      archived:
        description: >
          Фильтр по нахождению в архиве.
  
  
          Передайте `true`, чтобы получить товары, находящиеся в архиве. Если
          фильтр не заполнен или передано `false`, в ответе возвращаются товары,
          не находящиеся в архиве.
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
  path: v2/businesses/{businessId}/offer-mappings
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/business-offer-mappings/getOfferMappings.md -->

[*gtin]:
<b>Что такое GTIN</b><br>GTIN — это уникальный номер, присвоенный товару в единой международной базе [GS1](https://ru.wikipedia.org/wiki/GS1). Из этого номера получается штрихкод формата EAN, UPC или ISBN.<br><br><b>Как убедиться, что товар есть в базе</b><br>Проверить код можно на [странице проверки](https://gepir.gs1.org/index.php/search-by-gtin) на сайте ассоциации GS1. Если товар не находится, запросите код GTIN у вашего поставщика.<br><br><b>Как получить GTIN для своих товаров</b><br>Чтобы получить коды GTIN, производителю нужно вступить в ассоциацию GS1 и зарегистрировать товары.

[*Deprecated]: No longer supported, please use an alternative and newer version.
