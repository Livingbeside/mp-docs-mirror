---
title: Список акций
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md"
fetched_at: "2026-09-10T01:56:13Z"
content_sha: f512679fd7e05849
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/promos/getPromos.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/promos/getPromos.md
  - href: ru/reference/promos/getPromos.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/promos/getPromos.md -->
<div class="openapi">

# Получение списка акций

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getPromos.md -->
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
  <!-- endsource: ru/_auto/method_scopes/getPromos.md -->
  
  Возвращает информацию об акциях Маркета. Не возвращает данные об акциях, которые создал продавец.
  
  По умолчанию возвращаются акции, в которых продавец участвует или может принять участие.
  
  Чтобы получить текущие или завершенные акции, передайте параметр `participation`.
  
  Типы акций, которые возвращаются в ответе:
  
  * прямая скидка;
  * флеш-акция;
  * скидка по промокоду.
  
  <!-- source: ru/_auto/method_limits/getPromos.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getPromos.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/promos
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
    "participation": "PARTICIPATING_NOW",
    "mechanics": "DIRECT_DISCOUNT"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _mechanics_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MechanicsType](#entity-MechanicsType)
  
  Фильтр по типу акции.
  
  По умолчанию возвращаются все типы акций.
  
  
  Тип акции:
  
  * `DIRECT_DISCOUNT` — прямая скидка.
  
  * `BLUE_FLASH` — флеш-акция.
  
  * `MARKET_PROMOCODE` — скидка по промокоду.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DIRECT_DISCOUNT`, `BLUE_FLASH`, `MARKET_PROMOCODE`
  {.table-cell}
  ||
  ||
  
  _participation_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PromoParticipationType](#entity-PromoParticipationType)
  
  Без указания фильтра возвращаются акции, в которых продавец участвует или может принять участие.
  
  Какие акции вернутся при указании фильтра:
  
  * `PARTICIPATING_NOW` — текущие акции, в которых участвует продавец.
  
  * `PARTICIPATED` — завершенные акции, в которых продавец участвовал за последний год. Если за год их было меньше 15, в ответе придут 15 последних акций за все время.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PARTICIPATING_NOW`, `PARTICIPATED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PromoParticipationType {#entity-PromoParticipationType}
  
  Без указания фильтра возвращаются акции, в которых продавец участвует или может принять участие.
  
  Какие акции вернутся при указании фильтра:
  
  * `PARTICIPATING_NOW` — текущие акции, в которых участвует продавец.
  
  * `PARTICIPATED` — завершенные акции, в которых продавец участвовал за последний год. Если за год их было меньше 15, в ответе придут 15 последних акций за все время.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PARTICIPATING_NOW`, `PARTICIPATED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### MechanicsType {#entity-MechanicsType}
  
  Тип акции:
  
  * `DIRECT_DISCOUNT` — прямая скидка.
  
  * `BLUE_FLASH` — флеш-акция.
  
  * `MARKET_PROMOCODE` — скидка по промокоду.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DIRECT_DISCOUNT`, `BLUE_FLASH`, `MARKET_PROMOCODE`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список акций Маркета.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "promos": [
        {
          "id": "example",
          "name": "example",
          "period": {},
          "participating": true,
          "assortmentInfo": {},
          "mechanicsInfo": {},
          "bestsellerInfo": {},
          "channels": [
            null
          ],
          "constraints": {}
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
    **Type**: [GetPromosResultDTO](#entity-GetPromosResultDTO)
  
    Информация об акциях Маркета.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "promos": [
        {
          "id": "example",
          "name": "example",
          "period": {
            "dateTimeFrom": "2025-01-01T00:00:00Z",
            "dateTimeTo": "2025-01-01T00:00:00Z"
          },
          "participating": true,
          "assortmentInfo": {
            "activeOffers": 0,
            "potentialOffers": 0,
            "processing": true
          },
          "mechanicsInfo": {
            "type": "DIRECT_DISCOUNT",
            "promocodeInfo": {
              "promocode": "example",
              "discount": 0
            }
          },
          "bestsellerInfo": {
            "bestseller": true,
            "entryDeadline": "2025-01-01T00:00:00Z",
            "renewalEnabled": true
          },
          "channels": [
            "PUSH"
          ],
          "constraints": {
            "warehouseIds": [
              0
            ]
          }
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
        "promos": [
          {
            "id": "example",
            "name": "example",
            "period": {
              "dateTimeFrom": "2025-01-01T00:00:00Z",
              "dateTimeTo": "2025-01-01T00:00:00Z"
            },
            "participating": true,
            "assortmentInfo": {
              "activeOffers": 0,
              "potentialOffers": 0,
              "processing": true
            },
            "mechanicsInfo": {
              "type": "DIRECT_DISCOUNT",
              "promocodeInfo": {}
            },
            "bestsellerInfo": {
              "bestseller": true,
              "entryDeadline": "2025-01-01T00:00:00Z",
              "renewalEnabled": true
            },
            "channels": [
              "PUSH"
            ],
            "constraints": {
              "warehouseIds": [
                null
              ]
            }
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
  
  ### PromoPeriodDTO {#entity-PromoPeriodDTO}
  
  Время проведения акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dateTimeFrom_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время начала акции.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _dateTimeTo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время окончания акции.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "dateTimeFrom": "2025-01-01T00:00:00Z",
    "dateTimeTo": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoAssortmentInfoDTO {#entity-GetPromoAssortmentInfoDTO}
  
  Информация о товарах в акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _activeOffers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров, которые участвуют или участвовали в акции.
  
  Не учитываются товары, которые были добавлены автоматически.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  {.table-cell}
  ||
  ||
  
  _potentialOffers_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество доступных товаров в акции.
  
  Параметр возвращается только для текущих и будущих акций.
  
  {.table-cell}
  ||
  ||
  
  _processing_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Есть ли изменения в ассортименте, которые еще не применились. Сохранение изменений занимает некоторое время.
  
  Параметр возвращается только для текущих и будущих акций.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "activeOffers": 0,
    "potentialOffers": 0,
    "processing": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoPromocodeInfoDTO {#entity-GetPromoPromocodeInfoDTO}
  
  Информация для типа `MARKET_PROMOCODE`.
  
  Параметр заполняется только для этого типа акции.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _discount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Процент скидки по промокоду.
  {.table-cell}
  ||
  ||
  
  _promocode_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Промокод.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "promocode": "example",
    "discount": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoMechanicsInfoDTO {#entity-GetPromoMechanicsInfoDTO}
  
  Информация о типе акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [MechanicsType](#entity-MechanicsType)
  
  Тип акции:
  
  * `DIRECT_DISCOUNT` — прямая скидка.
  
  * `BLUE_FLASH` — флеш-акция.
  
  * `MARKET_PROMOCODE` — скидка по промокоду.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DIRECT_DISCOUNT`, `BLUE_FLASH`, `MARKET_PROMOCODE`
  {.table-cell}
  ||
  ||
  
  _promocodeInfo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GetPromoPromocodeInfoDTO](#entity-GetPromoPromocodeInfoDTO)
  
  Информация для типа `MARKET_PROMOCODE`.
  
  Параметр заполняется только для этого типа акции.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "promocode": "example",
    "discount": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "DIRECT_DISCOUNT",
    "promocodeInfo": {
      "promocode": "example",
      "discount": 0
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoBestsellerInfoDTO {#entity-GetPromoBestsellerInfoDTO}
  
  Информация об акции «Бестселлеры Маркета».
  
  #|
  || **Name** | **Description** ||
  ||
  
  _bestseller_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Является ли акция «Бестселлером Маркета». Подробнее об этой акции читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/bestsellers).
  {.table-cell}
  ||
  ||
  
  _entryDeadline_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  До какой даты можно добавить товар в акцию «Бестселлеры Маркета».
  
  Параметр возвращается только для текущих и будущих акций «Бестселлеры Маркета».
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _renewalEnabled_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Включен ли автоматический перенос ассортимента между акциями «Бестселлеры Маркета». О том, как это работает, читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/promos/market/bestsellers#next).
  
  Параметр возвращается только для текущих и будущих акций «Бестселлеры Маркета».
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "bestseller": true,
    "entryDeadline": "2025-01-01T00:00:00Z",
    "renewalEnabled": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ChannelType {#entity-ChannelType}
  
  Каналы продвижения товаров:
  
  * `PUSH` — пуш-уведомление из приложения Яндекс Маркет.
  
  * `STRETCH_MAIN` — верхний баннер-растяжка на главной странице Яндекс Маркета.
  
  * `MAIN_PAGE_CAROUSEL` — карусель акций на главной странице Яндекс Маркета.
  
  * `PRODUCT_RETAIL_PAGE` — товар на странице ритейл-повода.
  
  * `MAIN_PAGE_CAROUSEL_WEB` — карусель акций на главной странице веб версии Яндекс Маркета.
  
  * `PRODUCT_SEPARATE_LANDING` — товар на лендинге акции.
  
  * `SUPER_SHELF_CATEGORY` — полка в категориях.
  
  * `CAROUSEL_RETAIL_PAGE` — карусель на лендинге ритейл-повода.
  
  * `POPUP_APPLICATION` — всплывающее окно в приложении Яндекс Маркет.
  
  * `POST_TELEGRAM` — пост в Телеграм-канале Яндекс Маркета.
  
  * `CPA` — реклама в партнерской сети Яндекс Маркета.
  
  * `WEB_PERFORMANCE_DIRECT` — реклама в Яндекс Директе.
  
  * `APP_PERFORMANCE` — реклама в AppStore и Google Play.
  
  * `BANNER_PICKUP_POINT` — баннер в ПВЗ Маркета.
  
  * `BLOGGER_PERFORMANCE` — рекламная интеграция у блогеров.
  
  * `DIGITAL_CHANNEL_BANNER` — баннер в digital-каналах и социальных сетях VK, Одноклассники.
  
  * `YANDEX_ECOSYSTEM_CHANNELS` — реклама в других сервисах Яндекса: GO, Delivery, Еда.
  
  * `PARTNERS_MAIN_BANNER` — баннер на главной странице mail.ru, auto.ru, ya.ru.
  
  * `OTHER` — прочее.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PUSH`, `STRETCH_MAIN`, `MAIN_PAGE_CAROUSEL`, `PRODUCT_RETAIL_PAGE`, `MAIN_PAGE_CAROUSEL_WEB`, `PRODUCT_SEPARATE_LANDING`, `SUPER_SHELF_CATEGORY`, `CAROUSEL_RETAIL_PAGE`, `POPUP_APPLICATION`, `POST_TELEGRAM`, `CPA`, `WEB_PERFORMANCE_DIRECT`, `APP_PERFORMANCE`, `BANNER_PICKUP_POINT`, `BLOGGER_PERFORMANCE`, `DIGITAL_CHANNEL_BANNER`, `YANDEX_ECOSYSTEM_CHANNELS`, `PARTNERS_MAIN_BANNER`, `OTHER`
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoConstraintsDTO {#entity-GetPromoConstraintsDTO}
  
  Ограничения в акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _warehouseIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Идентификаторы складов, для которых действует акция. Товары, которые лежат на других складах, не будут продаваться по акции.
  
  Параметр возвращается, только если в условиях акции есть ограничение по складу.
  
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "warehouseIds": [
      0
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromoDTO {#entity-GetPromoDTO}
  
  Информация об акции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _assortmentInfo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetPromoAssortmentInfoDTO](#entity-GetPromoAssortmentInfoDTO)
  
  Информация о товарах в акции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "activeOffers": 0,
    "potentialOffers": 0,
    "processing": true
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _bestsellerInfo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetPromoBestsellerInfoDTO](#entity-GetPromoBestsellerInfoDTO)
  
  Информация об акции «Бестселлеры Маркета».
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "bestseller": true,
    "entryDeadline": "2025-01-01T00:00:00Z",
    "renewalEnabled": true
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор акции.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _mechanicsInfo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetPromoMechanicsInfoDTO](#entity-GetPromoMechanicsInfoDTO)
  
  Информация о типе акции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "DIRECT_DISCOUNT",
    "promocodeInfo": {
      "promocode": "example",
      "discount": 0
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название акции.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _participating_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Участвует или участвовал ли продавец в этой акции.
  
  Для текущих и будущих акций возвращается со значением `true`, если в акции есть товары, которые были добавлены вручную. Если товары не участвуют в акции или добавлены в нее автоматически, параметр возвращается со значением `false`.
  
  Для прошедших акций всегда возвращается со значением `true`.
  
  Об автоматическом и ручном добавлении товаров в акцию читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/marketing/promos/market/index).
  
  {.table-cell}
  ||
  ||
  
  _period_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PromoPeriodDTO](#entity-PromoPeriodDTO)
  
  Время проведения акции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "dateTimeFrom": "2025-01-01T00:00:00Z",
    "dateTimeTo": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _channels_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ChannelType](#entity-ChannelType)[] &#124; null
  
  Список каналов продвижения товаров.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "PUSH"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _constraints_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GetPromoConstraintsDTO](#entity-GetPromoConstraintsDTO)
  
  Ограничения в акции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "warehouseIds": [
      0
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
    "id": "example",
    "name": "example",
    "period": {
      "dateTimeFrom": "2025-01-01T00:00:00Z",
      "dateTimeTo": "2025-01-01T00:00:00Z"
    },
    "participating": true,
    "assortmentInfo": {
      "activeOffers": 0,
      "potentialOffers": 0,
      "processing": true
    },
    "mechanicsInfo": {
      "type": "DIRECT_DISCOUNT",
      "promocodeInfo": {
        "promocode": "example",
        "discount": 0
      }
    },
    "bestsellerInfo": {
      "bestseller": true,
      "entryDeadline": "2025-01-01T00:00:00Z",
      "renewalEnabled": true
    },
    "channels": [
      "PUSH"
    ],
    "constraints": {
      "warehouseIds": [
        0
      ]
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetPromosResultDTO {#entity-GetPromosResultDTO}
  
  Информация об акциях Маркета.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _promos_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GetPromoDTO](#entity-GetPromoDTO)[]
  
  Акции Маркета.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": "example",
      "name": "example",
      "period": {
        "dateTimeFrom": "2025-01-01T00:00:00Z",
        "dateTimeTo": "2025-01-01T00:00:00Z"
      },
      "participating": true,
      "assortmentInfo": {
        "activeOffers": 0,
        "potentialOffers": 0,
        "processing": true
      },
      "mechanicsInfo": {
        "type": "DIRECT_DISCOUNT",
        "promocodeInfo": {
          "promocode": "example",
          "discount": 0
        }
      },
      "bestsellerInfo": {
        "bestseller": true,
        "entryDeadline": "2025-01-01T00:00:00Z",
        "renewalEnabled": true
      },
      "channels": [
        "PUSH"
      ],
      "constraints": {
        "warehouseIds": [
          0
        ]
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
    "promos": [
      {
        "id": "example",
        "name": "example",
        "period": {
          "dateTimeFrom": "2025-01-01T00:00:00Z",
          "dateTimeTo": "2025-01-01T00:00:00Z"
        },
        "participating": true,
        "assortmentInfo": {
          "activeOffers": 0,
          "potentialOffers": 0,
          "processing": true
        },
        "mechanicsInfo": {
          "type": "DIRECT_DISCOUNT",
          "promocodeInfo": {
            "promocode": "example",
            "discount": 0
          }
        },
        "bestsellerInfo": {
          "bestseller": true,
          "entryDeadline": "2025-01-01T00:00:00Z",
          "renewalEnabled": true
        },
        "channels": [
          "PUSH"
        ],
        "constraints": {
          "warehouseIds": [
            0
          ]
        }
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
  searchParams: []
  headers: []
  body: |-
    {
      "participation": "PARTICIPATING_NOW",
      "mechanics": "DIRECT_DISCOUNT"
    }
  schema:
    description: Фильтры для получения списка акций.
    type: object
    properties:
      participation:
        description: >
          Без указания фильтра возвращаются акции, в которых продавец участвует
          или может принять участие.
  
  
          Какие акции вернутся при указании фильтра:
  
  
          * `PARTICIPATING_NOW` — текущие акции, в которых участвует продавец.
  
  
          * `PARTICIPATED` — завершенные акции, в которых продавец участвовал за
          последний год. Если за год их было меньше 15, в ответе придут 15
          последних акций за все время.
        type: string
        enum:
          - PARTICIPATING_NOW
          - PARTICIPATED
      mechanics:
        description: |
          Фильтр по типу акции.
  
          По умолчанию возвращаются все типы акций.
        $ref: '#/$defs/MechanicsType'
    $defs:
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/promos/schemas.yaml#/MechanicsType:
        description: |
          Тип акции:
  
          * `DIRECT_DISCOUNT` — прямая скидка.
  
          * `BLUE_FLASH` — флеш-акция.
  
          * `MARKET_PROMOCODE` — скидка по промокоду.
        type: string
        enum:
          - DIRECT_DISCOUNT
          - BLUE_FLASH
          - MARKET_PROMOCODE
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
  path: v2/businesses/{businessId}/promos
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/promos/getPromos.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
