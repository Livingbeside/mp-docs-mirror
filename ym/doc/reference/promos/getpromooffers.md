---
title: Список товаров в акции
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md"
fetched_at: "2026-09-24T02:13:52Z"
content_sha: 4303e6641479462e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/promos/getPromoOffers.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/promos/getPromoOffers.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/promos/getPromoOffers.md -->
<div class="openapi">

# Получение списка товаров, которые участвуют или могут участвовать в акции

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getPromoOffers.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * pricing:read-only — [Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md)
  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * promotion:read-only — [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getPromoOffers.md -->
  
  Возвращает список товаров, которые участвуют или могут участвовать в акции.
  
  {% note warning "Условия участия в акциях могут меняться" %}
  
  Например, `maxPromoPrice` и `bestPriceLevels`.
  
  Установленные цены меняться не будут — `price` и `promoPrice`.
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/getPromoOffers.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getPromoOffers.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/promos/offers
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
  
  
  _Default:_{.json-schema-reset .json-schema-value} `250`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `500`
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
    "promoId": "example",
    "statusType": "MANUALLY_ADDED",
    "statuses": [
      "MANUALLY_ADDED"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _promoId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор акции.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _statuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PromoOfferParticipationStatusMultiFilterType](#entity-PromoOfferParticipationStatusMultiFilterType)[] &#124; null
  
  Фильтр для товаров, которые могут участвовать в акции. Можно задать несколько значений.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "MANUALLY_ADDED"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _statusType_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [PromoOfferParticipationStatusFilterType](#entity-PromoOfferParticipationStatusFilterType)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `statuses`.
  
  {% endnote %}
  
  Фильтр для товаров, которые добавлены в акцию вручную.
  
  Если не передать параметр `statusType`, вернутся все товары.
  
  
  Фильтр для товаров, которые добавлены в акцию вручную:
  
  * `MANUALLY_ADDED` — товары, которые добавлены вручную.
  
  * `NOT_MANUALLY_ADDED`— товары, которые не участвуют в акции и те, которые добавлены автоматически.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MANUALLY_ADDED`, `NOT_MANUALLY_ADDED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoOfferParticipationStatusFilterType {#entity-PromoOfferParticipationStatusFilterType}
  
  Фильтр для товаров, которые добавлены в акцию вручную:
  
  * `MANUALLY_ADDED` — товары, которые добавлены вручную.
  
  * `NOT_MANUALLY_ADDED`— товары, которые не участвуют в акции и те, которые добавлены автоматически.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MANUALLY_ADDED`, `NOT_MANUALLY_ADDED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoOfferParticipationStatusMultiFilterType {#entity-PromoOfferParticipationStatusMultiFilterType}
  
  Фильтр для товаров, которые могут участвовать в акции:
  
  * `MANUALLY_ADDED` — товары, которые добавлены вручную.
  
  * `RENEWED` — товары, которые добавлены автоматически из предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  * `RENEW_FAILED` — товары, которые не получилось перенести из предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  * `NOT_MANUALLY_ADDED` — товары, которые не участвуют в акции и те, которые добавлены автоматически.
  
  * `MINIMUM_FOR_PROMOS` — товары с [установленным минимумом по цене для акций](*minimumForBestseller), который соответствует порогу `maxPromoPrice`. Такие товары участвуют в акции с ценой `maxPromoPrice`. Только для акций «Бестселлеры Маркета».
  
  Если не передать параметр `statuses`, вернутся все товары.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MANUALLY_ADDED`, `RENEWED`, `RENEW_FAILED`, `NOT_MANUALLY_ADDED`, `MINIMUM_FOR_PROMOS`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список товаров, которые участвуют или могут участвовать в акции.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "offers": [
        {
          "offerId": "example",
          "status": "AUTO",
          "params": {},
          "autoParticipatingDetails": {}
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
    **Type**: [GetPromoOffersResultDTO](#entity-GetPromoOffersResultDTO)
  
    Список товаров, которые участвуют или могут участвовать в акции.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offers": [
        {
          "offerId": "example",
          "status": "AUTO",
          "params": {
            "discountParams": {
              "price": 0,
              "promoPrice": 0,
              "maxPromoPrice": 0,
              "bestPriceLevels": {}
            }
          },
          "autoParticipatingDetails": {
            "campaignIds": [
              1
            ]
          }
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
        "offers": [
          {
            "offerId": "example",
            "status": "AUTO",
            "params": {
              "discountParams": {}
            },
            "autoParticipatingDetails": {
              "campaignIds": [
                null
              ]
            }
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
  
  ### PromoOfferParticipationStatusType {#entity-PromoOfferParticipationStatusType}
  
  Статус товара в акции:
  
  * `AUTO` — добавлен автоматически во всех магазинах кабинета, в которых товар доступен для покупки.
  
  * `PARTIALLY_AUTO` — добавлен автоматически у части магазинов.
  
  * `MANUAL` — добавлен вручную.
  
  * `NOT_PARTICIPATING` — не участвует в акции.
  
  * `RENEWED` — успешно перенесен из предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  * `RENEW_FAILED` — не получилось перенести из предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  * `MINIMUM_FOR_PROMOS` — участвует в акции с ценой `maxPromoPrice` ([установлен минимум по цене для акций](*minimumForBestseller), который соответствует порогу `maxPromoPrice`). Только для акций «Бестселлеры Маркета».
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `AUTO`, `PARTIALLY_AUTO`, `MANUAL`, `NOT_PARTICIPATING`, `RENEWED`, `RENEW_FAILED`, `MINIMUM_FOR_PROMOS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoOfferBestPriceLevelsDTO {#entity-PromoOfferBestPriceLevelsDTO}
  
  Максимальные цены для участия в акции «Бестселлеры Маркета» по уровням:
  
  * **Лайт-бестселлер** — `lightBestLevel`
  * **Бестселлер** — `bestLevel`
  * **Супербестселлер** — `superBestLevel`
  * **Топ-бестселлер** — `topBestLevel`
  
  Чтобы товар участвовал на определенном уровне, цена по акции должна быть не выше порога этого уровня.
  
  Параметр возвращается только для акций «Бестселлеры Маркета». Подробнее об этой акции читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/bestsellers).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _bestLevel_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная цена для участия на уровне **Бестселлер**.
  
  Указывается в рублях.
  
  {.table-cell}
  ||
  ||
  
  _lightBestLevel_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная цена для участия на уровне **Лайт-бестселлер**.
  
  Указывается в рублях.
  
  {.table-cell}
  ||
  ||
  
  _superBestLevel_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная цена для участия на уровне **Супербестселлер**.
  
  Указывается в рублях.
  
  {.table-cell}
  ||
  ||
  
  _topBestLevel_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная цена для участия на уровне **Топ-бестселлер**.
  
  Указывается в рублях.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "lightBestLevel": 0,
    "bestLevel": 0,
    "superBestLevel": 0,
    "topBestLevel": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoOfferDiscountParamsDTO {#entity-PromoOfferDiscountParamsDTO}
  
  Параметры товара в акции с типом `DIRECT_DISCOUNT` или `BLUE_FLASH`.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _bestPriceLevels_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PromoOfferBestPriceLevelsDTO](#entity-PromoOfferBestPriceLevelsDTO)
  
  Максимальные цены для участия в акции «Бестселлеры Маркета» по уровням:
  
  * **Лайт-бестселлер** — `lightBestLevel`
  * **Бестселлер** — `bestLevel`
  * **Супербестселлер** — `superBestLevel`
  * **Топ-бестселлер** — `topBestLevel`
  
  Чтобы товар участвовал на определенном уровне, цена по акции должна быть не выше порога этого уровня.
  
  Параметр возвращается только для акций «Бестселлеры Маркета». Подробнее об этой акции читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/bestsellers).
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "lightBestLevel": 0,
    "bestLevel": 0,
    "superBestLevel": 0,
    "topBestLevel": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _maxPromoPrice_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Максимально возможная цена для участия в акции.
  Если значение не заполнено, ограничение отсутствует.
  
  Указывается в рублях.
  
  Для акции «Бестселлеры Маркета» пороги по уровням возвращаются в параметре `bestPriceLevels`.
  
  {.table-cell}
  ||
  ||
  
  _price_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Зачеркнутая цена — та, по которой товар продавался до акции.
  
  Указывается в рублях.
  
  Возвращается, только если товар участвует в акции.
  
  {.table-cell}
  ||
  ||
  
  _promoPrice_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Цена по акции — та, по которой вы хотите продавать товар.
  
  Указывается в рублях.
  
  Возвращается, только если товар участвует в акции.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "price": 0,
    "promoPrice": 0,
    "maxPromoPrice": 0,
    "bestPriceLevels": {
      "lightBestLevel": 0,
      "bestLevel": 0,
      "superBestLevel": 0,
      "topBestLevel": 0
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoOfferParamsDTO {#entity-PromoOfferParamsDTO}
  
  Параметры товара в акции.
  
  Возвращается параметр, который соответствует типу акции.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _discountParams_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PromoOfferDiscountParamsDTO](#entity-PromoOfferDiscountParamsDTO)
  
  Параметры товара в акции с типом `DIRECT_DISCOUNT` или `BLUE_FLASH`.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "price": 0,
    "promoPrice": 0,
    "maxPromoPrice": 0,
    "bestPriceLevels": {
      "lightBestLevel": 0,
      "bestLevel": 0,
      "superBestLevel": 0,
      "topBestLevel": 0
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "discountParams": {
      "price": 0,
      "promoPrice": 0,
      "maxPromoPrice": 0,
      "bestPriceLevels": {
        "lightBestLevel": 0,
        "bestLevel": 0,
        "superBestLevel": 0,
        "topBestLevel": 0
      }
    }
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
  
  ### PromoOfferAutoParticipatingDetailsDTO {#entity-PromoOfferAutoParticipatingDetailsDTO}
  
  Информация об автоматическом добавлении товара в акцию.
  
  Причины, по которым товар не был добавлен автоматически в других магазинах, можно узнать в кабинете продавца на Маркете на странице акции.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)[] &#124; null
  
  Идентификаторы кампаний тех магазинов, в которых товар добавлен в акцию автоматически.
  
  Возвращается, если статус товара в акции — `PARTIALLY_AUTO`.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
    "campaignIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoOfferDTO {#entity-GetPromoOfferDTO}
  
  Товар, который участвует или может участвовать в акции.
  
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
  
  _params_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PromoOfferParamsDTO](#entity-PromoOfferParamsDTO)
  
  Параметры товара в акции.
  
  Возвращается параметр, который соответствует типу акции.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "discountParams": {
      "price": 0,
      "promoPrice": 0,
      "maxPromoPrice": 0,
      "bestPriceLevels": {
        "lightBestLevel": 0,
        "bestLevel": 0,
        "superBestLevel": 0,
        "topBestLevel": 0
      }
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PromoOfferParticipationStatusType](#entity-PromoOfferParticipationStatusType)
  
  Статус товара в акции:
  
  * `AUTO` — добавлен автоматически во всех магазинах кабинета, в которых товар доступен для покупки.
  
  * `PARTIALLY_AUTO` — добавлен автоматически у части магазинов.
  
  * `MANUAL` — добавлен вручную.
  
  * `NOT_PARTICIPATING` — не участвует в акции.
  
  * `RENEWED` — успешно перенесен из предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  * `RENEW_FAILED` — не получилось перенести из предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  * `MINIMUM_FOR_PROMOS` — участвует в акции с ценой `maxPromoPrice` ([установлен минимум по цене для акций](*minimumForBestseller), который соответствует порогу `maxPromoPrice`). Только для акций «Бестселлеры Маркета».
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `AUTO`, `PARTIALLY_AUTO`, `MANUAL`, `NOT_PARTICIPATING`, `RENEWED`, `RENEW_FAILED`, `MINIMUM_FOR_PROMOS`
  {.table-cell}
  ||
  ||
  
  _autoParticipatingDetails_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PromoOfferAutoParticipatingDetailsDTO](#entity-PromoOfferAutoParticipatingDetailsDTO)
  
  Информация об автоматическом добавлении товара в акцию.
  
  Причины, по которым товар не был добавлен автоматически в других магазинах, можно узнать в кабинете продавца на Маркете на странице акции.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "campaignIds": [
      1
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
    "offerId": "example",
    "status": "AUTO",
    "params": {
      "discountParams": {
        "price": 0,
        "promoPrice": 0,
        "maxPromoPrice": 0,
        "bestPriceLevels": {
          "lightBestLevel": 0,
          "bestLevel": 0,
          "superBestLevel": 0,
          "topBestLevel": 0
        }
      }
    },
    "autoParticipatingDetails": {
      "campaignIds": [
        1
      ]
    }
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
  
  ### GetPromoOffersResultDTO {#entity-GetPromoOffersResultDTO}
  
  Список товаров, которые участвуют или могут участвовать в акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetPromoOfferDTO](#entity-GetPromoOfferDTO)[]
  
  Товары, которые участвуют или могут участвовать в акции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "status": "AUTO",
      "params": {
        "discountParams": {
          "price": 0,
          "promoPrice": 0,
          "maxPromoPrice": 0,
          "bestPriceLevels": {
            "lightBestLevel": 0,
            "bestLevel": 0,
            "superBestLevel": 0,
            "topBestLevel": 0
          }
        }
      },
      "autoParticipatingDetails": {
        "campaignIds": [
          1
        ]
      }
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
    "offers": [
      {
        "offerId": "example",
        "status": "AUTO",
        "params": {
          "discountParams": {
            "price": 0,
            "promoPrice": 0,
            "maxPromoPrice": 0,
            "bestPriceLevels": {}
          }
        },
        "autoParticipatingDetails": {
          "campaignIds": [
            1
          ]
        }
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с акциями](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#promos)
  
  
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
        default: 250
        maximum: 500
  headers: []
  body: |-
    {
      "promoId": "example",
      "statusType": "MANUALLY_ADDED",
      "statuses": [
        "MANUALLY_ADDED"
      ]
    }
  schema:
    description: Получение списка товаров, которые участвуют или могут участвовать в акции.
    type: object
    required:
      - promoId
    properties:
      promoId:
        description: Идентификатор акции.
        type: string
      statusType:
        description: |
          {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
          Вместо него используйте `statuses`.
  
          {% endnote %}
  
          Фильтр для товаров, которые добавлены в акцию вручную.
  
          Если не передать параметр `statusType`, вернутся все товары.
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-12'
          replacement-field: statuses
        $ref: '#/$defs/PromoOfferParticipationStatusFilterType'
      statuses:
        description: >-
          Фильтр для товаров, которые могут участвовать в акции. Можно задать
          несколько значений.
        type: array
        nullable: true
        uniqueItems: true
        minItems: 1
        items:
          description: >
            Фильтр для товаров, которые могут участвовать в акции:
  
  
            * `MANUALLY_ADDED` — товары, которые добавлены вручную.
  
  
            * `RENEWED` — товары, которые добавлены автоматически из предыдущей
            акции «Бестселлеры Маркета». Только для акций «Бестселлеры Маркета».
  
  
            * `RENEW_FAILED` — товары, которые не получилось перенести из
            предыдущей акции «Бестселлеры Маркета». Только для акций «Бестселлеры
            Маркета».
  
  
            * `NOT_MANUALLY_ADDED` — товары, которые не участвуют в акции и те,
            которые добавлены автоматически.
  
  
            * `MINIMUM_FOR_PROMOS` — товары с [установленным минимумом по цене для
            акций](*minimumForBestseller), который соответствует порогу
            `maxPromoPrice`. Такие товары участвуют в акции с ценой
            `maxPromoPrice`. Только для акций «Бестселлеры Маркета».
  
  
            Если не передать параметр `statuses`, вернутся все товары.
  
  
            Об автоматическом и ручном добавлении товаров в акцию читайте [в
            Справке Маркета для
            продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
          type: string
          enum:
            - MANUALLY_ADDED
            - RENEWED
            - RENEW_FAILED
            - NOT_MANUALLY_ADDED
            - MINIMUM_FOR_PROMOS
    $defs:
      /home/sandbox/.ya/build/build_root/pyur/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/promos/api/getPromoOffers.yaml#/PromoOfferParticipationStatusFilterType:
        description: >
          Фильтр для товаров, которые добавлены в акцию вручную:
  
  
          * `MANUALLY_ADDED` — товары, которые добавлены вручную.
  
  
          * `NOT_MANUALLY_ADDED`— товары, которые не участвуют в акции и те,
          которые добавлены автоматически.
  
  
          Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке
          Маркета для
          продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
        type: string
        enum:
          - MANUALLY_ADDED
          - NOT_MANUALLY_ADDED
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
  path: v2/businesses/{businessId}/promos/offers
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/promos/getPromoOffers.md -->

[*minimumForBestseller]: В методе [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md).

[*Deprecated]: No longer supported, please use an alternative and newer version.
