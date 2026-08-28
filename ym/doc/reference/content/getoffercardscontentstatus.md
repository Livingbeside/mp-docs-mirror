---
title: Информация о заполненности карточек
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md"
fetched_at: "2026-08-28T11:51:53Z"
content_sha: f5e9b904107c56a9
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/content/getOfferCardsContentStatus.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/content/getOfferCardsContentStatus.md
  - href: ru/reference/content/getOfferCardsContentStatus.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/content/getOfferCardsContentStatus.md -->
<div class="openapi">

# Получение информации о заполненности карточек магазина

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOfferCardsContentStatus.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOfferCardsContentStatus.md -->
  
  Возвращает сведения о состоянии контента для заданных товаров:
  
  * создана ли карточка товара и в каком она статусе;
  * рейтинг карточки — на сколько процентов она заполнена;
  * переданные характеристики товаров;
  * есть ли ошибки или предупреждения, связанные с контентом;
  * рекомендации по заполнению карточки.
  
  Чтобы получить другие характеристики товаров, воспользуйтесь методом [POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md).
  
  <!-- source: ru/_auto/method_limits/getOfferCardsContentStatus.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 100 запросов в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 600 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOfferCardsContentStatus.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/offer-cards
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
    "cardStatuses": [
      "HAS_CARD_CAN_NOT_UPDATE"
    ],
    "categoryIds": [
      0
    ],
    "withRecommendations": false
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
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
  **Type**: [CategoryId](#entity-CategoryId)[] &#124; null
  
  Фильтр по категориям на Маркете.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `200`
  
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
  <br><br>
  ⚠️ Не используйте это поле одновременно с фильтрами по статусам карточек, категориям, брендам или тегам. Если вы хотите воспользоваться фильтрами, оставьте поле пустым.
  
  
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
  
  _withRecommendations_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Возвращать ли список рекомендаций к заполнению карточки и средний рейтинг карточки у товаров той категории, которая указана в `marketCategoryId`.
  
  Значение по умолчанию: `false`. Если информация нужна, передайте значение `true`.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `false`
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
  
  <div class="openapi-entity">
  
  ### CategoryId {#entity-CategoryId}
  
  Идентификатор категории на Маркете.
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о карточках указанных товаров.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "offerCards": [
        {
          "offerId": "example",
          "mapping": {},
          "parameterValues": [
            null
          ],
          "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
          "contentRating": 0,
          "averageContentRating": 0,
          "contentRatingStatus": "UPDATING",
          "recommendations": [
            null
          ],
          "groupId": "example",
          "errors": [
            null
          ],
          "warnings": [
            null
          ]
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
    **Type**: [OfferCardsContentStatusDTO](#entity-OfferCardsContentStatusDTO)
  
    Список товаров с информацией о состоянии карточек.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offerCards": [
        {
          "offerId": "example",
          "mapping": {
            "marketSku": 1,
            "marketSkuName": "example",
            "marketModelName": "example",
            "marketCategoryId": 0,
            "marketCategoryName": "example"
          },
          "parameterValues": [
            {
              "parameterId": 1,
              "unitId": 0,
              "valueId": 0,
              "value": "example"
            }
          ],
          "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
          "contentRating": 0,
          "averageContentRating": 0,
          "contentRatingStatus": "UPDATING",
          "recommendations": [
            {
              "type": "HAS_VIDEO",
              "percent": 0,
              "remainingRatingPoints": 1
            }
          ],
          "groupId": "example",
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
        "offerCards": [
          {
            "offerId": "example",
            "mapping": {},
            "parameterValues": [
              {}
            ],
            "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
            "contentRating": 0,
            "averageContentRating": 0,
            "contentRatingStatus": "UPDATING",
            "recommendations": [
              {}
            ],
            "groupId": "example",
            "errors": [
              {}
            ],
            "warnings": [
              null
            ]
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
  
  ### ParameterValueDTO {#entity-ParameterValueDTO}
  
  Значение характеристики.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _parameterId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор характеристики.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _unitId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор единицы измерения. Если вы не передали параметр `unitId`, используется единица измерения по умолчанию.
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Значение.
  
  Для характеристик типа `ENUM` передавайте:
  - вместе с `valueId`, если значение берете из справочника;
  - без `valueId`, если значение собственное.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _valueId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения.
  
  - Обязательно указывайте идентификатор, если передаете значение из перечня допустимых значений, полученного от Маркета.
  - Не указывайте для собственных значений.
  - Только для характеристик типа `ENUM`.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "parameterId": 1,
    "unitId": 0,
    "valueId": 0,
    "value": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferCardContentStatusType {#entity-OfferCardContentStatusType}
  
  Статус вычисления рейтинга карточки товара и рекомендаций:
  
  * `UPDATING` — рейтинг обновляется.
  * `ACTUAL` — рейтинг актуальный.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UPDATING`, `ACTUAL`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferCardRecommendationType {#entity-OfferCardRecommendationType}
  
  Рекомендация по дополнению или замене контента. Не возвращается для карточек, которые заполнены Маркетом или содержат бывшие в употреблении товары.
  
  Часть рекомендаций относятся к **основным параметрам**, которые есть у товаров любых категорий. Другие — к тем **характеристикам**, которые есть у товара потому, что он относится к определенной категории.
  
  **1. Рекомендации, относящиеся к основным параметрам**
  
  Каждая такая рекомендация относится к **единственному параметру**. Чтобы заполнить этот параметр, пользуйтесь запросом [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md).
  
  Рекомендации по заполнению параметров в `updateOfferMappings`:
  
  * `RECOGNIZED_VENDOR` — напишите название производителя так, как его пишет сам производитель (параметр `vendor`).
  * `PICTURE_COUNT` — добавьте изображения (параметр `pictures`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/images)
  
    Для рекомендации приходит процент ее выполнения.
  * `FIRST_PICTURE_SIZE`— замените первое изображение более крупным (параметр `pictures`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/images)
  * `TITLE_LENGTH` — измените название (параметр `name`). Составьте название по схеме: тип + бренд или производитель + модель + особенности, если есть (размер, вес, цвет). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/title)
  * `DESCRIPTION_LENGTH` — добавьте описание рекомендуемого размера (параметр `description`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/description)
  * `AVERAGE_PICTURE_SIZE` — замените все изображения на изображения высокого качества (параметр `pictures`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/images)
  * `FIRST_VIDEO_LENGTH` — добавьте первое видео рекомендуемой длины (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  * `FIRST_VIDEO_SIZE` — замените первое видео на видео высокого качества (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  * `AVERAGE_VIDEO_SIZE` — замените все видео на видео высокого качества (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  * `VIDEO_COUNT` — добавьте хотя бы одно видео (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  
    Для рекомендации приходит процент ее выполнения.
  
  **2. Рекомендации, относящиеся к характеристикам по категориям**
  
  Каждая такая рекомендация предполагает заполнение **одной или нескольких характеристик**. Чтобы узнать, какие именно характеристики нужно заполнить, воспользуйтесь запросом [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md). Например, если вы получили рекомендацию `MAIN`, нужно заполнить характеристики, имеющие `MAIN` в массиве `recommendationTypes`.
  
  Рекомендации:
  
  * `MAIN` — заполните ключевые характеристики товара, которые используются в поиске и фильтрах.
  
    Для рекомендации приходит процент ее выполнения.
  * `ADDITIONAL` — заполните дополнительные характеристики товара.
  
    Для рекомендации приходит процент ее выполнения.
  * `DISTINCTIVE` — заполните характеристики, которыми отличаются друг от друга варианты товара.
  
    Для рекомендации приходит процент ее выполнения.
  
  **3. Устаревшие рекомендации**
  
  * `HAS_VIDEO`.
  * `FILTERABLE`.
  * `HAS_DESCRIPTION`.
  * `HAS_BARCODE`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `HAS_VIDEO`, `RECOGNIZED_VENDOR`, `MAIN`, `ADDITIONAL`, `DISTINCTIVE`, `FILTERABLE`, `PICTURE_COUNT`, `HAS_DESCRIPTION`, `HAS_BARCODE`, `FIRST_PICTURE_SIZE`, `TITLE_LENGTH`, `DESCRIPTION_LENGTH`, `AVERAGE_PICTURE_SIZE`, `FIRST_VIDEO_SIZE`, `FIRST_VIDEO_LENGTH`, `AVERAGE_VIDEO_SIZE`, `VIDEO_COUNT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferCardRecommendationDTO {#entity-OfferCardRecommendationDTO}
  
  Рекомендация по заполнению карточки товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferCardRecommendationType](#entity-OfferCardRecommendationType)
  
  Рекомендация.
  
  Рекомендация по дополнению или замене контента. Не возвращается для карточек, которые заполнены Маркетом или содержат бывшие в употреблении товары.
  
  Часть рекомендаций относятся к **основным параметрам**, которые есть у товаров любых категорий. Другие — к тем **характеристикам**, которые есть у товара потому, что он относится к определенной категории.
  
  **1. Рекомендации, относящиеся к основным параметрам**
  
  Каждая такая рекомендация относится к **единственному параметру**. Чтобы заполнить этот параметр, пользуйтесь запросом [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md).
  
  Рекомендации по заполнению параметров в `updateOfferMappings`:
  
  * `RECOGNIZED_VENDOR` — напишите название производителя так, как его пишет сам производитель (параметр `vendor`).
  * `PICTURE_COUNT` — добавьте изображения (параметр `pictures`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/images)
  
    Для рекомендации приходит процент ее выполнения.
  * `FIRST_PICTURE_SIZE`— замените первое изображение более крупным (параметр `pictures`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/images)
  * `TITLE_LENGTH` — измените название (параметр `name`). Составьте название по схеме: тип + бренд или производитель + модель + особенности, если есть (размер, вес, цвет). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/title)
  * `DESCRIPTION_LENGTH` — добавьте описание рекомендуемого размера (параметр `description`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/description)
  * `AVERAGE_PICTURE_SIZE` — замените все изображения на изображения высокого качества (параметр `pictures`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/images)
  * `FIRST_VIDEO_LENGTH` — добавьте первое видео рекомендуемой длины (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  * `FIRST_VIDEO_SIZE` — замените первое видео на видео высокого качества (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  * `AVERAGE_VIDEO_SIZE` — замените все видео на видео высокого качества (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  * `VIDEO_COUNT` — добавьте хотя бы одно видео (параметр `videos`). [Требования](https://yandex.ru/support2/marketplace/ru/assortment/fields/video)
  
    Для рекомендации приходит процент ее выполнения.
  
  **2. Рекомендации, относящиеся к характеристикам по категориям**
  
  Каждая такая рекомендация предполагает заполнение **одной или нескольких характеристик**. Чтобы узнать, какие именно характеристики нужно заполнить, воспользуйтесь запросом [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md). Например, если вы получили рекомендацию `MAIN`, нужно заполнить характеристики, имеющие `MAIN` в массиве `recommendationTypes`.
  
  Рекомендации:
  
  * `MAIN` — заполните ключевые характеристики товара, которые используются в поиске и фильтрах.
  
    Для рекомендации приходит процент ее выполнения.
  * `ADDITIONAL` — заполните дополнительные характеристики товара.
  
    Для рекомендации приходит процент ее выполнения.
  * `DISTINCTIVE` — заполните характеристики, которыми отличаются друг от друга варианты товара.
  
    Для рекомендации приходит процент ее выполнения.
  
  **3. Устаревшие рекомендации**
  
  * `HAS_VIDEO`.
  * `FILTERABLE`.
  * `HAS_DESCRIPTION`.
  * `HAS_BARCODE`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `HAS_VIDEO`, `RECOGNIZED_VENDOR`, `MAIN`, `ADDITIONAL`, `DISTINCTIVE`, `FILTERABLE`, `PICTURE_COUNT`, `HAS_DESCRIPTION`, `HAS_BARCODE`, `FIRST_PICTURE_SIZE`, `TITLE_LENGTH`, `DESCRIPTION_LENGTH`, `AVERAGE_PICTURE_SIZE`, `FIRST_VIDEO_SIZE`, `FIRST_VIDEO_LENGTH`, `AVERAGE_VIDEO_SIZE`, `VIDEO_COUNT`
  {.table-cell}
  ||
  ||
  
  _percent_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Процент выполнения рекомендации.
  
  Указывается для рекомендаций некоторых типов:
  
  * `PICTURE_COUNT`.
  * `VIDEO_COUNT`.
  * `MAIN`.
  * `ADDITIONAL`.
  * `DISTINCTIVE`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `100`
  
  _Exclusive max:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  ||
  
  _remainingRatingPoints_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Максимальное количество баллов рейтинга карточки, которые можно получить за выполнение рекомендаций.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `100`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "HAS_VIDEO",
    "percent": 0,
    "remainingRatingPoints": 1
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
  
  ### OfferCardDTO {#entity-OfferCardDTO}
  
  Информация о состоянии карточки товара.
  
  Если поле `mapping` отсутствует в ответе, Маркет еще не успел обработать информацию о товаре. Чтобы определить категорию такого товара, повторите запрос через несколько минут.
  
  
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
  
  _averageContentRating_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Средний рейтинг карточки у товаров той категории, которая указана в `marketCategoryId`.
  
  Возвращается, только если параметр `withRecommendations` имеет значение `true`.
  
  {.table-cell}
  ||
  ||
  
  _cardStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferCardStatusType](#entity-OfferCardStatusType)
  
  Статус карточки.
  
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
  
  _contentRating_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Рейтинг карточки.
  {.table-cell}
  ||
  ||
  
  _contentRatingStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferCardContentStatusType](#entity-OfferCardContentStatusType)
  
  Статус вычисления рейтинга карточки и рекомендаций.
  
  Статус вычисления рейтинга карточки товара и рекомендаций:
  
  * `UPDATING` — рейтинг обновляется.
  * `ACTUAL` — рейтинг актуальный.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UPDATING`, `ACTUAL`
  {.table-cell}
  ||
  ||
  
  _errors_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferErrorDTO](#entity-OfferErrorDTO)[] &#124; null
  
  Ошибки в контенте, препятствующие размещению товара на витрине.
  
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
  
  _mapping_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GetMappingDTO](#entity-GetMappingDTO)
  
  Основная информация о карточке товара.
  
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
  
  _parameterValues_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ParameterValueDTO](#entity-ParameterValueDTO)[] &#124; null
  
  Список характеристик с их значениями.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "parameterId": 1,
      "unitId": 0,
      "valueId": 0,
      "value": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _recommendations_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferCardRecommendationDTO](#entity-OfferCardRecommendationDTO)[] &#124; null
  
  Список рекомендаций к заполнению карточки.
  
  Возвращается, только если параметр `withRecommendations` имеет значение `true`.
  
  Рекомендации Маркета помогают заполнять карточку так, чтобы покупателям было проще найти ваш товар и решиться на покупку.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "HAS_VIDEO",
      "percent": 0,
      "remainingRatingPoints": 1
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warnings_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferErrorDTO](#entity-OfferErrorDTO)[] &#124; null
  
  Связанные с контентом предупреждения, не препятствующие размещению товара на витрине.
  
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
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "mapping": {
      "marketSku": 1,
      "marketSkuName": "example",
      "marketModelName": "example",
      "marketCategoryId": 0,
      "marketCategoryName": "example"
    },
    "parameterValues": [
      {
        "parameterId": 1,
        "unitId": 0,
        "valueId": 0,
        "value": "example"
      }
    ],
    "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
    "contentRating": 0,
    "averageContentRating": 0,
    "contentRatingStatus": "UPDATING",
    "recommendations": [
      {
        "type": "HAS_VIDEO",
        "percent": 0,
        "remainingRatingPoints": 1
      }
    ],
    "groupId": "example",
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
  
  ### OfferCardsContentStatusDTO {#entity-OfferCardsContentStatusDTO}
  
  Список товаров с информацией о состоянии карточек.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerCards_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferCardDTO](#entity-OfferCardDTO)[]
  
  Страница списка товаров с информацией о состоянии карточек.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "mapping": {
        "marketSku": 1,
        "marketSkuName": "example",
        "marketModelName": "example",
        "marketCategoryId": 0,
        "marketCategoryName": "example"
      },
      "parameterValues": [
        {
          "parameterId": 1,
          "unitId": 0,
          "valueId": 0,
          "value": "example"
        }
      ],
      "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
      "contentRating": 0,
      "averageContentRating": 0,
      "contentRatingStatus": "UPDATING",
      "recommendations": [
        {
          "type": "HAS_VIDEO",
          "percent": 0,
          "remainingRatingPoints": 1
        }
      ],
      "groupId": "example",
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
    "offerCards": [
      {
        "offerId": "example",
        "mapping": {
          "marketSku": 1,
          "marketSkuName": "example",
          "marketModelName": "example",
          "marketCategoryId": 0,
          "marketCategoryName": "example"
        },
        "parameterValues": [
          {
            "parameterId": 1,
            "unitId": 0,
            "valueId": 0,
            "value": "example"
          }
        ],
        "cardStatus": "HAS_CARD_CAN_NOT_UPDATE",
        "contentRating": 0,
        "averageContentRating": 0,
        "contentRatingStatus": "UPDATING",
        "recommendations": [
          {
            "type": "HAS_VIDEO",
            "percent": 0,
            "remainingRatingPoints": 1
          }
        ],
        "groupId": "example",
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
      "cardStatuses": [
        "HAS_CARD_CAN_NOT_UPDATE"
      ],
      "categoryIds": [
        0
      ],
      "withRecommendations": false
    }
  schema:
    type: object
    properties:
      offerIds:
        description: >
          Идентификаторы товаров, информация о которых нужна.
  
          <br><br>
  
          ⚠️ Не используйте это поле одновременно с фильтрами по статусам
          карточек, категориям, брендам или тегам. Если вы хотите воспользоваться
          фильтрами, оставьте поле пустым.
        type: array
        maxItems: 200
        uniqueItems: true
        nullable: true
        minItems: 1
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
        uniqueItems: true
        nullable: true
        minItems: 1
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
        maxItems: 200
        uniqueItems: true
        nullable: true
        minItems: 1
        items:
          description: "Идентификатор категории на Маркете.\n\nПри изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.\n\nСписок категорий Маркета можно получить с помощью запроса  [POST\_v2/categories/tree](../../reference/categories/getCategoriesTree.md).\n"
          format: int32
          type: integer
          minimum: 0
          exclusiveMinimum: true
      withRecommendations:
        description: >
          Возвращать ли список рекомендаций к заполнению карточки и средний
          рейтинг карточки у товаров той категории, которая указана в
          `marketCategoryId`.
  
  
          Значение по умолчанию: `false`. Если информация нужна, передайте
          значение `true`.
        type: boolean
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
  path: v2/businesses/{businessId}/offer-cards
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/content/getOfferCardsContentStatus.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
