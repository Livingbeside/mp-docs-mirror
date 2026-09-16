---
title: Редактирование категорийных характеристик товара
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md"
fetched_at: "2026-09-16T02:27:11Z"
content_sha: fd5cc2c58a6a8c26
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/content/updateOfferContent.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/content/updateOfferContent.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/content/updateOfferContent.md -->
<div class="openapi">

# Редактирование категорийных характеристик товара

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateOfferContent.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateOfferContent.md -->
  
  Редактирует характеристики товара, которые специфичны для категории, к которой он относится.
  
  {% note warning "Здесь только то, что относится к конкретной категории" %}
  
  Если вам нужно изменить основные параметры товара (название, описание, изображения, видео, производитель, штрихкод), воспользуйтесь запросом [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md).
  
  {% endnote %}
  
  Чтобы удалить характеристики, которые заданы в параметрах с типом `string`, передайте пустое значение.
  
  {% note info "Данные в каталоге обновляются не мгновенно" %}
  
  Это занимает до нескольких минут.
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/updateOfferContent.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 5 000 товаров в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 10 000 товаров в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateOfferContent.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/offer-cards/update
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
    "offersContent": [
      {
        "offerId": "example",
        "categoryId": 0,
        "parameterValues": [
          {
            "parameterId": 1,
            "unitId": 0,
            "valueId": 0,
            "value": "example"
          }
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offersContent_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferContentDTO](#entity-OfferContentDTO)[]
  
  Список товаров с указанными характеристиками.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "categoryId": 0,
      "parameterValues": [
        {
          "parameterId": 1,
          "unitId": 0,
          "valueId": 0,
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
  
  ### CategoryId {#entity-CategoryId}
  
  Идентификатор категории на Маркете.
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
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
  
  ### OfferContentDTO {#entity-OfferContentDTO}
  
  Товар с указанными характеристиками.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CategoryId](#entity-CategoryId)
  
  Идентификатор категории на Маркете.
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
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
  
  _parameterValues_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ParameterValueDTO](#entity-ParameterValueDTO)[]
  
  Список характеристик с их значениями.
  
  При **изменении** характеристик передавайте только те, значение которых нужно обновить. Если в `categoryId` вы меняете категорию, значения общих характеристик для старой и новой категории сохранятся, передавать их не нужно.
  
  Подробнее читайте в [«Передача значений характеристики»](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/parameter-values.md).
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `300`
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "categoryId": 0,
    "parameterValues": [
      {
        "parameterId": 1,
        "unitId": 0,
        "valueId": 0,
        "value": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Запрос выполнен корректно, данные обработаны.
  
  {% note warning "Ответ `200` сам по себе не значит, что переданные значения корректны" %}
  
  Обязательно посмотрите детали ответа: `status`, а также перечень ошибок (`results.errors`) и замечаний (`results.warnings`), если они есть.
  
  - Если хотя бы по одному товару вернулась ошибка (`results.errors`), поле `status` = `ERROR`. Изменения по всем переданным товарам не будут применены.
  - Если ошибок нет, но хотя бы по одному товару вернулось замечание (`results.warnings`), поле `status` = `OK`, и изменения будут применены.
  
  {% endnote %}
  
  Если в `status` вернулось `ERROR`, убедитесь, что:
  
  * все обязательные характеристики заполнены;
  * характеристики действительно существуют в указанных категориях;
  * значения соответствуют характеристикам;
  * ваши собственные значения имеют нужный тип данных.
  
  Найти проблемы помогут поля `errors` и `warnings`.
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "results": [
      {
        "offerId": "example",
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
  
    _results_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [UpdateOfferContentResultDTO](#entity-UpdateOfferContentResultDTO)[] &#124; null
  
    Ошибки и предупреждения, которые появились при обработке переданных значений. Каждый элемент списка соответствует одному товару.
  
    Если ошибок и предупреждений нет, поле не передается.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "offerId": "example",
        "errors": [
          {
            "type": "OFFER_NOT_FOUND",
            "parameterId": 0,
            "message": "example"
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
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "results": [
        {
          "offerId": "example",
          "errors": [
            {
              "type": "OFFER_NOT_FOUND",
              "parameterId": 0,
              "message": "example"
            }
          ],
          "warnings": [
            null
          ]
        }
      ]
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
  
  ### OfferContentErrorType {#entity-OfferContentErrorType}
  
  Типы ошибок и предупреждений:
  
  * `OFFER_NOT_FOUND` — такого товара нет в каталоге.
  * `UNKNOWN_CATEGORY` — указана неизвестная категория.
  * `INVALID_CATEGORY` — указана нелистовая категория. Укажите ту, которая не имеет дочерних категорий.
  * `UNKNOWN_PARAMETER` — передана характеристика, которой нет среди характеристик категории.
  * `UNEXPECTED_BOOLEAN_VALUE` — вместо boolean-значения передано что-то другое.
  * `NUMBER_FORMAT` — передана строка, не обозначающая число, вместо числа.
  * `INVALID_UNIT_ID` — передана единица измерения, недопустимая для характеристики.
  * `INVALID_GROUP_ID_LENGTH` — в названии превышено допустимое значение символов — 255.
  * `INVALID_GROUP_ID_CHARACTERS` — переданы [недопустимые символы](*ascii-code).
  
  Проверить, какие категорийные характеристики доступны для заданной категории, и получить их настройки можно с помощью запроса [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OFFER_NOT_FOUND`, `UNKNOWN_CATEGORY`, `INVALID_CATEGORY`, `UNKNOWN_PARAMETER`, `UNEXPECTED_BOOLEAN_VALUE`, `NUMBER_FORMAT`, `INVALID_UNIT_ID`, `INVALID_GROUP_ID_LENGTH`, `INVALID_GROUP_ID_CHARACTERS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferContentErrorDTO {#entity-OfferContentErrorDTO}
  
  Текст ошибки или предупреждения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _message_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Текст ошибки или предупреждения.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferContentErrorType](#entity-OfferContentErrorType)
  
  Типы ошибок и предупреждений:
  
  * `OFFER_NOT_FOUND` — такого товара нет в каталоге.
  * `UNKNOWN_CATEGORY` — указана неизвестная категория.
  * `INVALID_CATEGORY` — указана нелистовая категория. Укажите ту, которая не имеет дочерних категорий.
  * `UNKNOWN_PARAMETER` — передана характеристика, которой нет среди характеристик категории.
  * `UNEXPECTED_BOOLEAN_VALUE` — вместо boolean-значения передано что-то другое.
  * `NUMBER_FORMAT` — передана строка, не обозначающая число, вместо числа.
  * `INVALID_UNIT_ID` — передана единица измерения, недопустимая для характеристики.
  * `INVALID_GROUP_ID_LENGTH` — в названии превышено допустимое значение символов — 255.
  * `INVALID_GROUP_ID_CHARACTERS` — переданы [недопустимые символы](*ascii-code).
  
  Проверить, какие категорийные характеристики доступны для заданной категории, и получить их настройки можно с помощью запроса [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OFFER_NOT_FOUND`, `UNKNOWN_CATEGORY`, `INVALID_CATEGORY`, `UNKNOWN_PARAMETER`, `UNEXPECTED_BOOLEAN_VALUE`, `NUMBER_FORMAT`, `INVALID_UNIT_ID`, `INVALID_GROUP_ID_LENGTH`, `INVALID_GROUP_ID_CHARACTERS`
  {.table-cell}
  ||
  ||
  
  _parameterId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор характеристики, с которой связана ошибка или предупреждение.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "OFFER_NOT_FOUND",
    "parameterId": 0,
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOfferContentResultDTO {#entity-UpdateOfferContentResultDTO}
  
  Ошибки и предупреждения, которые появились из-за переданных характеристик.
  
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
  
  _errors_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferContentErrorDTO](#entity-OfferContentErrorDTO)[] &#124; null
  
  Ошибки.
  
  Если хотя бы по одному товару есть ошибка, информация в каталоге не обновится по всем переданным товарам.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "OFFER_NOT_FOUND",
      "parameterId": 0,
      "message": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warnings_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferContentErrorDTO](#entity-OfferContentErrorDTO)[] &#124; null
  
  Предупреждения.
  
  Информация в каталоге обновится.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "OFFER_NOT_FOUND",
      "parameterId": 0,
      "message": "example"
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
    "errors": [
      {
        "type": "OFFER_NOT_FOUND",
        "parameterId": 0,
        "message": "example"
      }
    ],
    "warnings": [
      null
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
      "offersContent": [
        {
          "offerId": "example",
          "categoryId": 0,
          "parameterValues": [
            {
              "parameterId": 1,
              "unitId": 0,
              "valueId": 0,
              "value": "example"
            }
          ]
        }
      ]
    }
  schema:
    description: Запрос на установку новых значений для параметров.
    type: object
    required:
      - offersContent
    properties:
      offersContent:
        description: Список товаров с указанными характеристиками.
        type: array
        minItems: 1
        maxItems: 100
        items:
          description: Товар с указанными характеристиками.
          type: object
          required:
            - offerId
            - categoryId
            - parameterValues
          properties:
            offerId:
              description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
              type: string
              pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
              x-transform: trim
              minLength: 1
              maxLength: 255
            categoryId:
              description: "Идентификатор категории на Маркете.\n\nПри изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.\n\nСписок категорий Маркета можно получить с помощью запроса  [POST\_v2/categories/tree](../../reference/categories/getCategoriesTree.md).\n"
              format: int32
              type: integer
              minimum: 0
              exclusiveMinimum: true
            parameterValues:
              description: >
                Список характеристик с их значениями.
  
  
                При **изменении** характеристик передавайте только те, значение
                которых нужно обновить. Если в `categoryId` вы меняете категорию,
                значения общих характеристик для старой и новой категории
                сохранятся, передавать их не нужно.
  
  
                Подробнее читайте в [«Передача значений
                характеристики»](../../step-by-step/parameter-values.md).
              type: array
              maxItems: 300
              minItems: 1
              items:
                description: |
                  Значение характеристики.
                type: object
                required:
                  - parameterId
                properties:
                  parameterId:
                    description: Идентификатор характеристики.
                    type: integer
                    format: int64
                    minimum: 1
                  unitId:
                    description: >-
                      Идентификатор единицы измерения. Если вы не передали
                      параметр `unitId`, используется единица измерения по
                      умолчанию.
                    type: integer
                    format: int64
                  valueId:
                    description: >
                      Идентификатор значения.
  
  
                      - Обязательно указывайте идентификатор, если передаете
                      значение из перечня допустимых значений, полученного от
                      Маркета.
  
                      - Не указывайте для собственных значений.
  
                      - Только для характеристик типа `ENUM`.
                    type: integer
                    format: int64
                  value:
                    description: |
                      Значение.
  
                      Для характеристик типа `ENUM` передавайте:
                      - вместе с `valueId`, если значение берете из справочника;
                      - без `valueId`, если значение собственное.
                    type: string
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
  path: v2/businesses/{businessId}/offer-cards/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/content/updateOfferContent.md -->

[*ascii-code]:
Запрещены ASCII символы с 0 по 31 (кроме 9) и 127 [из таблицы](https://www.ascii-code.com/compact).

[*Deprecated]: No longer supported, please use an alternative and newer version.
