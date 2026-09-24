---
title: Создание возврата
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md"
fetched_at: "2026-09-24T02:14:22Z"
content_sha: 07a59906dc658dab
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/returns/createReturn.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/returns/createReturn.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/returns/createReturn.md -->
<div class="openapi">

# Создание возврата

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/createReturn.md -->
  **Метод доступен для модели [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/createReturn.md -->
  
  Создает новый возврат.
  
  Это можно сделать только для заказа в статусе `DELIVERED`.
  
  {% note warning "Перед вызовом метода" %}
  
  Проверьте, подходят ли пункты выдачи для возврата указанных товаров, — [POST v1/campaigns/{campaignId}/return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md).
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/createReturn.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/createReturn.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/campaigns/{campaignId}/returns/create
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
    "newReturn": {
      "externalReturnId": "example",
      "orderId": 0,
      "items": [
        {
          "offerId": "example",
          "count": 1,
          "reasonType": "BAD_QUALITY",
          "subreasonType": "USER_DID_NOT_LIKE",
          "comment": "example",
          "pictures": [
            "example"
          ]
        }
      ],
      "customer": {
        "firstName": "example",
        "lastName": "example",
        "middleName": "example",
        "phone": "example"
      },
      "returnOption": {
        "pickupReturn": {
          "logisticPointId": 1
        }
      }
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _newReturn_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateReturnDTO](#entity-CreateReturnDTO)
  
  Информация о возврате.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "externalReturnId": "example",
    "orderId": 0,
    "items": [
      {
        "offerId": "example",
        "count": 1,
        "reasonType": "BAD_QUALITY",
        "subreasonType": "USER_DID_NOT_LIKE",
        "comment": "example",
        "pictures": [
          "example"
        ]
      }
    ],
    "customer": {
      "firstName": "example",
      "lastName": "example",
      "middleName": "example",
      "phone": "example"
    },
    "returnOption": {
      "pickupReturn": {
        "logisticPointId": 1
      }
    }
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
  
  ### ExternalReturnDecisionReasonType {#entity-ExternalReturnDecisionReasonType}
  
  Причины возврата:
  
  * `BAD_QUALITY` — бракованный товар (есть недостатки).
  
  * `DOES_NOT_FIT` — товар не подошел.
  
  * `WRONG_ITEM` — привезли не тот товар.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `BAD_QUALITY`, `DOES_NOT_FIT`, `WRONG_ITEM`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ExternalReturnDecisionSubreasonType {#entity-ExternalReturnDecisionSubreasonType}
  
  Детали причин возврата:
    * `DOES_NOT_FIT`:
      * `USER_DID_NOT_LIKE` — товар не понравился.
      * `USER_CHANGED_MIND` — передумал покупать.
      * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки.
  
    * `BAD_QUALITY`:
      * `BAD_PACKAGE` — заводская упаковка повреждена.
      * `DAMAGED` — царапины, сколы.
      * `NOT_WORKING` — не включается, не работает.
      * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару).
  
    * `WRONG_ITEM`:
      * `WRONG_ITEM` — не тот товар.
      * `WRONG_COLOR` — цвет не соответствует заявленному.
      * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER_DID_NOT_LIKE`, `USER_CHANGED_MIND`, `DELIVERED_TOO_LONG`, `BAD_PACKAGE`, `DAMAGED`, `NOT_WORKING`, `INCOMPLETENESS`, `WRONG_ITEM`, `WRONG_COLOR`, `DID_NOT_MATCH_DESCRIPTION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateReturnItemDTO {#entity-CreateReturnItemDTO}
  
  Товар в возврате.
  
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
  ||
  
  _reasonType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ExternalReturnDecisionReasonType](#entity-ExternalReturnDecisionReasonType)
  
  Причины возврата:
  
  * `BAD_QUALITY` — бракованный товар (есть недостатки).
  
  * `DOES_NOT_FIT` — товар не подошел.
  
  * `WRONG_ITEM` — привезли не тот товар.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `BAD_QUALITY`, `DOES_NOT_FIT`, `WRONG_ITEM`
  {.table-cell}
  ||
  ||
  
  _subreasonType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ExternalReturnDecisionSubreasonType](#entity-ExternalReturnDecisionSubreasonType)
  
  Детали причин возврата:
    * `DOES_NOT_FIT`:
      * `USER_DID_NOT_LIKE` — товар не понравился.
      * `USER_CHANGED_MIND` — передумал покупать.
      * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки.
  
    * `BAD_QUALITY`:
      * `BAD_PACKAGE` — заводская упаковка повреждена.
      * `DAMAGED` — царапины, сколы.
      * `NOT_WORKING` — не включается, не работает.
      * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару).
  
    * `WRONG_ITEM`:
      * `WRONG_ITEM` — не тот товар.
      * `WRONG_COLOR` — цвет не соответствует заявленному.
      * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER_DID_NOT_LIKE`, `USER_CHANGED_MIND`, `DELIVERED_TOO_LONG`, `BAD_PACKAGE`, `DAMAGED`, `NOT_WORKING`, `INCOMPLETENESS`, `WRONG_ITEM`, `WRONG_COLOR`, `DID_NOT_MATCH_DESCRIPTION`
  {.table-cell}
  ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий к товару в возврате.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `3000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _pictures_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Ссылки (URL) на изображения товара в возврате.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `10`
  
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
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "count": 1,
    "reasonType": "BAD_QUALITY",
    "subreasonType": "USER_DID_NOT_LIKE",
    "comment": "example",
    "pictures": [
      "example"
    ]
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
  
  ### LogisticPointId {#entity-LogisticPointId}
  
  Идентификатор пункта выдачи.
  
  Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderPickupReturnDTO {#entity-OrderPickupReturnDTO}
  
  Информация о пункте выдачи, в который нужно вернуть товары.
  
  [Как получить список подходящих пунктов выдачи](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md)
  
  
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
  
  ### CreateReturnOptionDTO {#entity-CreateReturnOptionDTO}
  
  Информация о способе возврата.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _pickupReturn_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderPickupReturnDTO](#entity-OrderPickupReturnDTO)
  
  Информация о пункте выдачи, в который нужно вернуть товары.
  
  [Как получить список подходящих пунктов выдачи](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md)
  
  
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
    "pickupReturn": {
      "logisticPointId": 1
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateReturnDTO {#entity-CreateReturnDTO}
  
  Информация о возврате.
  
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
  
  _externalReturnId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Внешний идентификатор возврата в системе магазина.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateReturnItemDTO](#entity-CreateReturnItemDTO)[]
  
  Список товаров в возврате.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `1000`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "count": 1,
      "reasonType": "BAD_QUALITY",
      "subreasonType": "USER_DID_NOT_LIKE",
      "comment": "example",
      "pictures": [
        "example"
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _orderId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа, по которому нужно сделать возврат.
  {.table-cell}
  ||
  ||
  
  _returnOption_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateReturnOptionDTO](#entity-CreateReturnOptionDTO)
  
  Информация о способе возврата.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "pickupReturn": {
      "logisticPointId": 1
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
    "externalReturnId": "example",
    "orderId": 0,
    "items": [
      {
        "offerId": "example",
        "count": 1,
        "reasonType": "BAD_QUALITY",
        "subreasonType": "USER_DID_NOT_LIKE",
        "comment": "example",
        "pictures": [
          "example"
        ]
      }
    ],
    "customer": {
      "firstName": "example",
      "lastName": "example",
      "middleName": "example",
      "phone": "example"
    },
    "returnOption": {
      "pickupReturn": {
        "logisticPointId": 1
      }
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о cозданном возврате.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "id": 0
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
    **Type**: [CreatedReturnDTO](#entity-CreatedReturnDTO)
  
    Информация о созданном возврате.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 0
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
        "id": 0
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
  
  ### CreatedReturnDTO {#entity-CreatedReturnDTO}
  
  Информация о созданном возврате.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор возврата.
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
      "newReturn": {
        "externalReturnId": "example",
        "orderId": 0,
        "items": [
          {
            "offerId": "example",
            "count": 1,
            "reasonType": "BAD_QUALITY",
            "subreasonType": "USER_DID_NOT_LIKE",
            "comment": "example",
            "pictures": [
              "example"
            ]
          }
        ],
        "customer": {
          "firstName": "example",
          "lastName": "example",
          "middleName": "example",
          "phone": "example"
        },
        "returnOption": {
          "pickupReturn": {
            "logisticPointId": 1
          }
        }
      }
    }
  schema:
    type: object
    required:
      - newReturn
    properties:
      newReturn:
        type: object
        description: Информация о возврате.
        required:
          - externalReturnId
          - orderId
          - items
          - customer
          - returnOption
        properties:
          externalReturnId:
            description: Внешний идентификатор возврата в системе магазина.
            type: string
            minLength: 1
          orderId:
            description: Идентификатор заказа, по которому нужно сделать возврат.
            type: integer
            format: int64
          items:
            description: Список товаров в возврате.
            type: array
            items:
              description: Товар в возврате.
              type: object
              required:
                - offerId
                - count
                - reasonType
                - subreasonType
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
                reasonType:
                  description: |
                    Причины возврата:
  
                    * `BAD_QUALITY` — бракованный товар (есть недостатки).
  
                    * `DOES_NOT_FIT` — товар не подошел.
  
                    * `WRONG_ITEM` — привезли не тот товар.
                  type: string
                  enum:
                    - BAD_QUALITY
                    - DOES_NOT_FIT
                    - WRONG_ITEM
                subreasonType:
                  description: |
                    Детали причин возврата:
                      * `DOES_NOT_FIT`:
                        * `USER_DID_NOT_LIKE` — товар не понравился.
                        * `USER_CHANGED_MIND` — передумал покупать.
                        * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки.
  
                      * `BAD_QUALITY`:
                        * `BAD_PACKAGE` — заводская упаковка повреждена.
                        * `DAMAGED` — царапины, сколы.
                        * `NOT_WORKING` — не включается, не работает.
                        * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару).
  
                      * `WRONG_ITEM`:
                        * `WRONG_ITEM` — не тот товар.
                        * `WRONG_COLOR` — цвет не соответствует заявленному.
                        * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным.
                  type: string
                  enum:
                    - USER_DID_NOT_LIKE
                    - USER_CHANGED_MIND
                    - DELIVERED_TOO_LONG
                    - BAD_PACKAGE
                    - DAMAGED
                    - NOT_WORKING
                    - INCOMPLETENESS
                    - WRONG_ITEM
                    - WRONG_COLOR
                    - DID_NOT_MATCH_DESCRIPTION
                comment:
                  description: Комментарий к товару в возврате.
                  type: string
                  minLength: 1
                  maxLength: 3000
                pictures:
                  description: Ссылки (URL) на изображения товара в возврате.
                  type: array
                  nullable: true
                  minItems: 1
                  maxItems: 10
                  uniqueItems: true
                  items:
                    type: string
                    minLength: 1
                    maxLength: 2000
            minItems: 1
            maxItems: 1000
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
          returnOption:
            type: object
            description: Информация о способе возврата.
            required:
              - pickupReturn
            properties:
              pickupReturn:
                type: object
                description: >
                  Информация о пункте выдачи, в который нужно вернуть товары.
  
  
                  [Как получить список подходящих пунктов
                  выдачи](../../reference/delivery-options/getReturnDeliveryOptions.md)
                required:
                  - logisticPointId
                properties:
                  logisticPointId:
                    type: integer
                    description: "Идентификатор пункта выдачи.\n\nЕго можно узнать с помощью метода [POST\_v1/businesses/{businessId}/logistics-points](../../reference/logistic-points/getLogisticPoints.md).\n"
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
  path: v1/campaigns/{campaignId}/returns/create
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/returns/createReturn.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
