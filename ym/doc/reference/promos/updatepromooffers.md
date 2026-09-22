---
title: Добавление товаров в акцию/изменение их цен
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md"
fetched_at: "2026-09-22T02:27:01Z"
content_sha: 62b26402794a04e8
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/promos/updatePromoOffers.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/promos/updatePromoOffers.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/promos/updatePromoOffers.md -->
<div class="openapi">

# Добавление товаров в акцию или изменение их цен

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updatePromoOffers.md -->
  **Метод доступен для моделей: [FBY, FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updatePromoOffers.md -->
  
  Добавляет товары в акцию или изменяет цены на товары, которые участвуют в акции.
  
  Изменения начинают действовать в течение 4–6 часов. Узнать, применились ли они, можно с помощью параметра `processing` в ответе метода [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md).
  
  <!-- source: ru/_auto/method_limits/updatePromoOffers.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updatePromoOffers.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/promos/offers/update
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
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "promoId": "example",
    "offers": [
      {
        "offerId": "example",
        "params": {
          "discountParams": {
            "price": 1,
            "promoPrice": 1
          }
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
  **Type**: [UpdatePromoOfferDTO](#entity-UpdatePromoOfferDTO)[]
  
  Товары, которые необходимо добавить в акцию или цены которых нужно изменить.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `500`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "params": {
        "discountParams": {
          "price": 1,
          "promoPrice": 1
        }
      }
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _promoId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор акции.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
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
  
  ### UpdatePromoOfferDiscountParamsDTO {#entity-UpdatePromoOfferDiscountParamsDTO}
  
  Параметры товара в акции с типом `DIRECT_DISCOUNT` или `BLUE_FLASH`.
  
  Обязательный параметр для акций с этими типами.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _price_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Зачеркнутая цена — та, по которой товар продавался до акции.
  
  Указывается в рублях.
  
  Число должно быть целым.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _promoPrice_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Цена по акции — та, по которой вы хотите продавать товар.
  
  Указывается в рублях.
  
  Число должно быть целым.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "price": 1,
    "promoPrice": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdatePromoOfferParamsDTO {#entity-UpdatePromoOfferParamsDTO}
  
  Параметры товара, который участвует в акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _discountParams_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [UpdatePromoOfferDiscountParamsDTO](#entity-UpdatePromoOfferDiscountParamsDTO)
  
  Параметры товара в акции с типом `DIRECT_DISCOUNT` или `BLUE_FLASH`.
  
  Обязательный параметр для акций с этими типами.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "price": 1,
    "promoPrice": 1
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
      "price": 1,
      "promoPrice": 1
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdatePromoOfferDTO {#entity-UpdatePromoOfferDTO}
  
  Описание товаров, которые участвуют в акции.
  
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
  
  _params_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [UpdatePromoOfferParamsDTO](#entity-UpdatePromoOfferParamsDTO)
  
  Параметры товара, который участвует в акции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "discountParams": {
      "price": 1,
      "promoPrice": 1
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
    "offerId": "example",
    "params": {
      "discountParams": {
        "price": 1,
        "promoPrice": 1
      }
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Результат добавления товаров в акцию или обновления их цен.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "rejectedOffers": [
        {
          "offerId": "example",
          "reason": "OFFER_DOES_NOT_EXIST"
        }
      ],
      "warningOffers": [
        {
          "offerId": null,
          "warnings": [
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
    **Type**: [UpdatePromoOffersResultDTO](#entity-UpdatePromoOffersResultDTO)
  
    Ошибки и предупреждения, которые появились при добавлении товаров в акцию.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "rejectedOffers": [
        {
          "offerId": "example",
          "reason": "OFFER_DOES_NOT_EXIST"
        }
      ],
      "warningOffers": [
        {
          "offerId": null,
          "warnings": [
            {
              "code": "DEEP_DISCOUNT_OFFER",
              "campaignIds": [
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
        "rejectedOffers": [
          {
            "offerId": "example",
            "reason": "OFFER_DOES_NOT_EXIST"
          }
        ],
        "warningOffers": [
          {
            "offerId": null,
            "warnings": [
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
  
  ### RejectedPromoOfferUpdateReasonType {#entity-RejectedPromoOfferUpdateReasonType}
  
  Причина отклонения изменения:
  
  * `OFFER_DOES_NOT_EXIST` — в кабинете нет товара с таким SKU.
  
  * `OFFER_DUPLICATION` — один и тот же товар передан несколько раз.
  
  * `OFFER_NOT_ELIGIBLE_FOR_PROMO` — товар не подходит под условия акции.
  
  * `OFFER_PROMOS_MAX_BYTE_SIZE_EXCEEDED` — товар не добавлен в акцию по техническим причинам.
  
  * `DEADLINE_FOR_FOCUS_PROMOS_EXCEEDED` — истек срок добавления товаров в акцию.
  
  * `EMPTY_OLD_PRICE` — не указана зачеркнутая цена.
  
  * `EMPTY_PROMO_PRICE` — не указана цена по акции.
  
  * `MAX_PROMO_PRICE_EXCEEDED` — цена по акции превышает максимально возможную цену для участия в акции.
  
  * `PROMO_PRICE_BIGGER_THAN_MAX` — цена по акции больше 95% от зачеркнутой цены.
  
  * `PROMO_PRICE_SMALLER_THAN_MIN` — цена по акции меньше 1% от зачеркнутой цены.
  
  * `PRICE_TOO_BIG` — слишком большая цена по акции.
  
  * `OLD_PRICE_TOO_BIG` — слишком большая зачеркнутая цена.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OFFER_DOES_NOT_EXIST`, `OFFER_DUPLICATION`, `OFFER_NOT_ELIGIBLE_FOR_PROMO`, `OFFER_PROMOS_MAX_BYTE_SIZE_EXCEEDED`, `DEADLINE_FOR_FOCUS_PROMOS_EXCEEDED`, `EMPTY_OLD_PRICE`, `EMPTY_PROMO_PRICE`, `MAX_PROMO_PRICE_EXCEEDED`, `PROMO_PRICE_BIGGER_THAN_MAX`, `PROMO_PRICE_SMALLER_THAN_MIN`, `PRICE_TOO_BIG`, `OLD_PRICE_TOO_BIG`
  
  </div>
  
  <div class="openapi-entity">
  
  ### RejectedPromoOfferUpdateDTO {#entity-RejectedPromoOfferUpdateDTO}
  
  Описание отклоненного изменения.
  
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
  
  _reason_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [RejectedPromoOfferUpdateReasonType](#entity-RejectedPromoOfferUpdateReasonType)
  
  Причина отклонения изменения:
  
  * `OFFER_DOES_NOT_EXIST` — в кабинете нет товара с таким SKU.
  
  * `OFFER_DUPLICATION` — один и тот же товар передан несколько раз.
  
  * `OFFER_NOT_ELIGIBLE_FOR_PROMO` — товар не подходит под условия акции.
  
  * `OFFER_PROMOS_MAX_BYTE_SIZE_EXCEEDED` — товар не добавлен в акцию по техническим причинам.
  
  * `DEADLINE_FOR_FOCUS_PROMOS_EXCEEDED` — истек срок добавления товаров в акцию.
  
  * `EMPTY_OLD_PRICE` — не указана зачеркнутая цена.
  
  * `EMPTY_PROMO_PRICE` — не указана цена по акции.
  
  * `MAX_PROMO_PRICE_EXCEEDED` — цена по акции превышает максимально возможную цену для участия в акции.
  
  * `PROMO_PRICE_BIGGER_THAN_MAX` — цена по акции больше 95% от зачеркнутой цены.
  
  * `PROMO_PRICE_SMALLER_THAN_MIN` — цена по акции меньше 1% от зачеркнутой цены.
  
  * `PRICE_TOO_BIG` — слишком большая цена по акции.
  
  * `OLD_PRICE_TOO_BIG` — слишком большая зачеркнутая цена.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OFFER_DOES_NOT_EXIST`, `OFFER_DUPLICATION`, `OFFER_NOT_ELIGIBLE_FOR_PROMO`, `OFFER_PROMOS_MAX_BYTE_SIZE_EXCEEDED`, `DEADLINE_FOR_FOCUS_PROMOS_EXCEEDED`, `EMPTY_OLD_PRICE`, `EMPTY_PROMO_PRICE`, `MAX_PROMO_PRICE_EXCEEDED`, `PROMO_PRICE_BIGGER_THAN_MAX`, `PROMO_PRICE_SMALLER_THAN_MIN`, `PRICE_TOO_BIG`, `OLD_PRICE_TOO_BIG`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "reason": "OFFER_DOES_NOT_EXIST"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoOfferUpdateWarningCodeType {#entity-PromoOfferUpdateWarningCodeType}
  
  Предупреждение, которое появилось при добавлении товара:
  
  * `DEEP_DISCOUNT_OFFER` — большая разница с ценой в каталоге. Проверьте, нет ли ошибки.
  
  * `CATALOG_PRICE_IS_LOWER_THAN_PROMO` — цена, которая действует во всех магазинах, ниже цены по акции. У товара не будет отображаться цена по акции.
  
  * `SHOP_PRICES_ARE_LOWER_THAN_PROMO` — цена в отдельном магазине ниже цены по акции. У товара в акции будет отображаться цена в магазине. Для остальных магазинов будет действовать цена по акции.
  
  * `SHOP_OFFER_NOT_ELIGIBLE_FOR_PROMO` — товар в отдельном магазине не подходит под условия акции.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEEP_DISCOUNT_OFFER`, `CATALOG_PRICE_IS_LOWER_THAN_PROMO`, `SHOP_PRICES_ARE_LOWER_THAN_PROMO`, `SHOP_OFFER_NOT_ELIGIBLE_FOR_PROMO`
  
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
  
  ### PromoOfferUpdateWarningDTO {#entity-PromoOfferUpdateWarningDTO}
  
  Предупреждение, которое появилось при добавлении товара в акцию или изменении его цен.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PromoOfferUpdateWarningCodeType](#entity-PromoOfferUpdateWarningCodeType)
  
  Предупреждение, которое появилось при добавлении товара:
  
  * `DEEP_DISCOUNT_OFFER` — большая разница с ценой в каталоге. Проверьте, нет ли ошибки.
  
  * `CATALOG_PRICE_IS_LOWER_THAN_PROMO` — цена, которая действует во всех магазинах, ниже цены по акции. У товара не будет отображаться цена по акции.
  
  * `SHOP_PRICES_ARE_LOWER_THAN_PROMO` — цена в отдельном магазине ниже цены по акции. У товара в акции будет отображаться цена в магазине. Для остальных магазинов будет действовать цена по акции.
  
  * `SHOP_OFFER_NOT_ELIGIBLE_FOR_PROMO` — товар в отдельном магазине не подходит под условия акции.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEEP_DISCOUNT_OFFER`, `CATALOG_PRICE_IS_LOWER_THAN_PROMO`, `SHOP_PRICES_ARE_LOWER_THAN_PROMO`, `SHOP_OFFER_NOT_ELIGIBLE_FOR_PROMO`
  {.table-cell}
  ||
  ||
  
  _campaignIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)[] &#124; null
  
  Идентификаторы кампаний тех магазинов, для которых получены предупреждения.
  
  Не возвращается, если предупреждения действуют для всех магазинов в кабинете.
  
  
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
    "code": "DEEP_DISCOUNT_OFFER",
    "campaignIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarningPromoOfferUpdateDTO {#entity-WarningPromoOfferUpdateDTO}
  
  Описание предупреждения, которое появилось при добавлении товара.
  
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
  
  _warnings_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PromoOfferUpdateWarningDTO](#entity-PromoOfferUpdateWarningDTO)[]
  
  Предупреждения, которые появились при добавлении товара в акцию или изменении его цен.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "code": "DEEP_DISCOUNT_OFFER",
      "campaignIds": [
        1
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
    "offerId": "example",
    "warnings": [
      {
        "code": "DEEP_DISCOUNT_OFFER",
        "campaignIds": [
          1
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdatePromoOffersResultDTO {#entity-UpdatePromoOffersResultDTO}
  
  Ошибки и предупреждения, которые появились при добавлении товаров в акцию.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _rejectedOffers_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RejectedPromoOfferUpdateDTO](#entity-RejectedPromoOfferUpdateDTO)[] &#124; null
  
  Изменения, которые были отклонены.
  
  Возвращается, только если есть отклоненные изменения.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "reason": "OFFER_DOES_NOT_EXIST"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warningOffers_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [WarningPromoOfferUpdateDTO](#entity-WarningPromoOfferUpdateDTO)[] &#124; null
  
  Изменения, по которым есть предупреждения. Они информируют о возможных проблемах. Информация о товарах обновится.
  
  Возвращается, только если есть предупреждения.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "warnings": [
        {
          "code": "DEEP_DISCOUNT_OFFER",
          "campaignIds": [
            1
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
    "rejectedOffers": [
      {
        "offerId": "example",
        "reason": "OFFER_DOES_NOT_EXIST"
      }
    ],
    "warningOffers": [
      {
        "offerId": null,
        "warnings": [
          {
            "code": "DEEP_DISCOUNT_OFFER",
            "campaignIds": [
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
  searchParams: []
  headers: []
  body: |-
    {
      "promoId": "example",
      "offers": [
        {
          "offerId": "example",
          "params": {
            "discountParams": {
              "price": 1,
              "promoPrice": 1
            }
          }
        }
      ]
    }
  schema:
    description: >
      Добавление товаров в акцию или обновление их параметров.
  
  
      Чтобы добавить товары в акцию или обновить параметры каких-то товаров,
      передайте их в параметре `offers`.
    type: object
    required:
      - promoId
      - offers
    properties:
      promoId:
        description: Идентификатор акции.
        type: string
      offers:
        description: >-
          Товары, которые необходимо добавить в акцию или цены которых нужно
          изменить.
        type: array
        minItems: 1
        maxItems: 500
        items:
          description: Описание товаров, которые участвуют в акции.
          type: object
          required:
            - offerId
          properties:
            offerId:
              description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
              type: string
              pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
              x-transform: trim
              minLength: 1
              maxLength: 255
            params:
              description: Параметры товара, который участвует в акции.
              type: object
              properties:
                discountParams:
                  description: >
                    Параметры товара в акции с типом `DIRECT_DISCOUNT` или
                    `BLUE_FLASH`.
  
  
                    Обязательный параметр для акций с этими типами.
                  type: object
                  properties:
                    price:
                      description: >
                        Зачеркнутая цена — та, по которой товар продавался до
                        акции.
  
  
                        Указывается в рублях.
  
  
                        Число должно быть целым.
                      type: integer
                      format: int64
                      minimum: 1
                    promoPrice:
                      description: |
                        Цена по акции — та, по которой вы хотите продавать товар.
  
                        Указывается в рублях.
  
                        Число должно быть целым.
                      type: integer
                      format: int64
                      minimum: 1
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
  path: v2/businesses/{businessId}/promos/offers/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/promos/updatePromoOffers.md -->

[*basic-price]: Цена, которая действует во всех магазинах.

[*Deprecated]: No longer supported, please use an alternative and newer version.
