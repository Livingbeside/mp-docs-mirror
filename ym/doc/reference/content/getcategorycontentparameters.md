---
title: Списки характеристик товаров по категориям
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md"
fetched_at: "2026-09-11T01:57:39Z"
content_sha: ca93095faba9decd
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/content/getCategoryContentParameters.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/content/getCategoryContentParameters.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/content/getCategoryContentParameters.md -->
<div class="openapi">

# Списки характеристик товаров по категориям

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getCategoryContentParameters.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getCategoryContentParameters.md -->
  
  Возвращает список характеристик с допустимыми значениями для заданной [листовой категории](*list-category).
  
  Поля в ответе определяют правила передачи характеристики в методах:
  - [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
  - [POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)
  
  <!-- source: ru/_auto/method_limits/getCategoryContentParameters.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getCategoryContentParameters.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/category/{categoryId}/parameters
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор категории на Маркете.
  
  Чтобы узнать идентификатор категории, к которой относится интересующий вас товар, воспользуйтесь запросом [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  Передайте параметр, чтобы получить характеристики, которые являются особенностями варианта товара в данном кабинете.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список характеристик товаров из заданной категории.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "categoryId": 0,
      "parameters": [
        {
          "id": 1,
          "name": "example",
          "type": "TEXT",
          "unit": {},
          "description": "example",
          "recommendationTypes": [
            null
          ],
          "required": true,
          "filtering": true,
          "distinctive": true,
          "multivalue": true,
          "allowCustomValues": true,
          "values": [
            null
          ],
          "constraints": {},
          "valueRestrictions": [
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
    **Type**: [CategoryContentParametersDTO](#entity-CategoryContentParametersDTO)
  
    Информация о параметрах категории.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "categoryId": 0,
      "parameters": [
        {
          "id": 1,
          "name": "example",
          "type": "TEXT",
          "unit": {
            "defaultUnitId": 0,
            "units": [
              {}
            ]
          },
          "description": "example",
          "recommendationTypes": [
            "HAS_VIDEO"
          ],
          "required": true,
          "filtering": true,
          "distinctive": true,
          "multivalue": true,
          "allowCustomValues": true,
          "values": [
            {
              "id": 0,
              "value": "example",
              "description": "example"
            }
          ],
          "constraints": {
            "minValue": 0.5,
            "maxValue": 0.5,
            "maxLength": 0
          },
          "valueRestrictions": [
            {
              "limitingParameterId": 1,
              "limitedValues": [
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
        "categoryId": 0,
        "parameters": [
          {
            "id": 1,
            "name": "example",
            "type": "TEXT",
            "unit": {
              "defaultUnitId": 0,
              "units": [
                null
              ]
            },
            "description": "example",
            "recommendationTypes": [
              "HAS_VIDEO"
            ],
            "required": true,
            "filtering": true,
            "distinctive": true,
            "multivalue": true,
            "allowCustomValues": true,
            "values": [
              {}
            ],
            "constraints": {
              "minValue": 0.5,
              "maxValue": 0.5,
              "maxLength": 0
            },
            "valueRestrictions": [
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
  
  ### CategoryId {#entity-CategoryId}
  
  Идентификатор категории на Маркете.
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ParameterType {#entity-ParameterType}
  
  Тип данных:
  
  * `TEXT` — текст.
  * `ENUM` — список возможных значений.
  * `BOOLEAN` — `true` или `false`.
  * `NUMERIC` — число.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `TEXT`, `ENUM`, `BOOLEAN`, `NUMERIC`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UnitDTO {#entity-UnitDTO}
  
  Единица измерения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fullName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Полное название единицы измерения.
  
  _Example:_{.json-schema-reset .json-schema-example} `килограмм`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор единицы измерения.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Сокращенное название единицы измерения.
  
  _Example:_{.json-schema-reset .json-schema-example} `кг`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "кг",
    "fullName": "килограмм"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CategoryParameterUnitDTO {#entity-CategoryParameterUnitDTO}
  
  Единицы измерения характеристики товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _defaultUnitId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Единица измерения по умолчанию.
  {.table-cell}
  ||
  ||
  
  _units_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UnitDTO](#entity-UnitDTO)[]
  
  Допустимые единицы измерения.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "name": "кг",
      "fullName": "килограмм"
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
    "defaultUnitId": 0,
    "units": [
      {
        "id": 0,
        "name": "кг",
        "fullName": "килограмм"
      }
    ]
  }
  ```
  
  {% endcut %}
  
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
  
  ### ParameterValueOptionDTO {#entity-ParameterValueOptionDTO}
  
  Значение характеристики.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения.
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Значение.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _description_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание значения.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "value": "example",
    "description": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ParameterValueConstraintsDTO {#entity-ParameterValueConstraintsDTO}
  
  Ограничения на значения характеристик.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _maxLength_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Максимальная длина текста.
  {.table-cell}
  ||
  ||
  
  _maxValue_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Максимальное число.
  {.table-cell}
  ||
  ||
  
  _minValue_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Минимальное число.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "minValue": 0.5,
    "maxValue": 0.5,
    "maxLength": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OptionValuesLimitedDTO {#entity-OptionValuesLimitedDTO}
  
  Значение ограничивающей характеристики и список допустимых значений ограничиваемой характеристики.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _limitingOptionValueId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения ограничивающей характеристики.
  {.table-cell}
  ||
  ||
  
  _optionValueIds_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer[]
  
  Идентификаторы допустимых значений ограничиваемой характеристики.
  
  
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
    "limitingOptionValueId": 0,
    "optionValueIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ValueRestrictionDTO {#entity-ValueRestrictionDTO}
  
  Ограничение на возможные значения, накладываемое другой характеристикой.
  
  Если ограничивающая характеристика принимает определенное значение, список возможных значений ограничиваемой характеристики сокращается.
  
  **Пример**
  
  Характеристика **размер** сама по себе может принимать девять разных значений: `S`, `M`, `L`, `44`, `46`, `48`, `42/164`, `46/176`, `44S`.
  
  Если ограничивающая характеристика **размерная сетка** принимает значение `RU`, список возможных значений размера сокращается до `44`, `46`, `48`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _limitedValues_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OptionValuesLimitedDTO](#entity-OptionValuesLimitedDTO)[]
  
  Значения ограничивающей характеристики и соответствующие допустимые значения текущей характеристики.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "limitingOptionValueId": 0,
      "optionValueIds": [
        1
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _limitingParameterId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор ограничивающей характеристики.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "limitingParameterId": 1,
    "limitedValues": [
      {
        "limitingOptionValueId": 0,
        "optionValueIds": [
          1
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CategoryParameterDTO {#entity-CategoryParameterDTO}
  
  Характеристика товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _allowCustomValues_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Можно ли передавать собственное значение, которого нет в списке вариантов Маркета. Только для характеристик типа `ENUM`.
  {.table-cell}
  ||
  ||
  
  _distinctive_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Является ли характеристика особенностью варианта.
  {.table-cell}
  ||
  ||
  
  _filtering_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Используется ли характеристика в фильтре.
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор характеристики.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _multivalue_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Можно ли передать сразу несколько значений.
  {.table-cell}
  ||
  ||
  
  _required_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Обязательность характеристики.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ParameterType](#entity-ParameterType)
  
  Тип данных.
  
  Тип данных:
  
  * `TEXT` — текст.
  * `ENUM` — список возможных значений.
  * `BOOLEAN` — `true` или `false`.
  * `NUMERIC` — число.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `TEXT`, `ENUM`, `BOOLEAN`, `NUMERIC`
  {.table-cell}
  ||
  ||
  
  _constraints_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ParameterValueConstraintsDTO](#entity-ParameterValueConstraintsDTO)
  
  Ограничения на значения. Только для характеристик типа `TEXT` и `NUMERIC`.
  
  - Для `NUMERIC` используются поля `minValue` и `maxValue`.
  - Для `TEXT` используется поле `maxLength`.
  
  
  Ограничения на значения характеристик.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "minValue": 0.5,
    "maxValue": 0.5,
    "maxLength": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _description_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание характеристики.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название характеристики.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _recommendationTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferCardRecommendationType](#entity-OfferCardRecommendationType)[] &#124; null
  
  Перечень возможных рекомендаций по заполнению карточки, к которым относится данная характеристика.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "HAS_VIDEO"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _unit_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CategoryParameterUnitDTO](#entity-CategoryParameterUnitDTO)
  
  Единицы измерения характеристики товара.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "defaultUnitId": 0,
    "units": [
      {
        "id": 0,
        "name": "кг",
        "fullName": "килограмм"
      }
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _valueRestrictions_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ValueRestrictionDTO](#entity-ValueRestrictionDTO)[] &#124; null
  
  Ограничения на значения, накладываемые другими характеристиками. Только для характеристик типа `ENUM`.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "limitingParameterId": 1,
      "limitedValues": [
        {
          "limitingOptionValueId": 0,
          "optionValueIds": [
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
  ||
  
  _values_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ParameterValueOptionDTO](#entity-ParameterValueOptionDTO)[] &#124; null
  
  Список допустимых значений параметра. Только для характеристик типа `ENUM`.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "value": "example",
      "description": "example"
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
    "id": 1,
    "name": "example",
    "type": "TEXT",
    "unit": {
      "defaultUnitId": 0,
      "units": [
        {
          "id": 0,
          "name": "кг",
          "fullName": "килограмм"
        }
      ]
    },
    "description": "example",
    "recommendationTypes": [
      "HAS_VIDEO"
    ],
    "required": true,
    "filtering": true,
    "distinctive": true,
    "multivalue": true,
    "allowCustomValues": true,
    "values": [
      {
        "id": 0,
        "value": "example",
        "description": "example"
      }
    ],
    "constraints": {
      "minValue": 0.5,
      "maxValue": 0.5,
      "maxLength": 0
    },
    "valueRestrictions": [
      {
        "limitingParameterId": 1,
        "limitedValues": [
          {
            "limitingOptionValueId": 0,
            "optionValueIds": [
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
  
  <div class="openapi-entity">
  
  ### CategoryContentParametersDTO {#entity-CategoryContentParametersDTO}
  
  Информация о параметрах категории.
  
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
  
  _parameters_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CategoryParameterDTO](#entity-CategoryParameterDTO)[] &#124; null
  
  Список характеристик.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 1,
      "name": "example",
      "type": "TEXT",
      "unit": {
        "defaultUnitId": 0,
        "units": [
          {
            "id": 0,
            "name": "кг",
            "fullName": "килограмм"
          }
        ]
      },
      "description": "example",
      "recommendationTypes": [
        "HAS_VIDEO"
      ],
      "required": true,
      "filtering": true,
      "distinctive": true,
      "multivalue": true,
      "allowCustomValues": true,
      "values": [
        {
          "id": 0,
          "value": "example",
          "description": "example"
        }
      ],
      "constraints": {
        "minValue": 0.5,
        "maxValue": 0.5,
        "maxLength": 0
      },
      "valueRestrictions": [
        {
          "limitingParameterId": 1,
          "limitedValues": [
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
    "categoryId": 0,
    "parameters": [
      {
        "id": 1,
        "name": "example",
        "type": "TEXT",
        "unit": {
          "defaultUnitId": 0,
          "units": [
            {}
          ]
        },
        "description": "example",
        "recommendationTypes": [
          "HAS_VIDEO"
        ],
        "required": true,
        "filtering": true,
        "distinctive": true,
        "multivalue": true,
        "allowCustomValues": true,
        "values": [
          {
            "id": 0,
            "value": "example",
            "description": "example"
          }
        ],
        "constraints": {
          "minValue": 0.5,
          "maxValue": 0.5,
          "maxLength": 0
        },
        "valueRestrictions": [
          {
            "limitingParameterId": 1,
            "limitedValues": [
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с категориями](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#categories)
  
  
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
    - in: path
      name: categoryId
      description: "Идентификатор категории на Маркете.\n\nЧтобы узнать идентификатор категории, к которой относится интересующий вас товар, воспользуйтесь запросом [POST\_v2/categories/tree](../../reference/categories/getCategoriesTree.md).\n"
      required: true
      schema:
        type: integer
        format: int64
        minimum: 0
        exclusiveMinimum: true
  searchParams:
    - description: "Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nПередайте параметр, чтобы получить характеристики, которые являются особенностями варианта товара в данном кабинете.\n"
      name: businessId
      in: query
      required: false
      schema:
        type: integer
        format: int64
        minimum: 1
  headers: []
  body: null
  schema: {}
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
  path: v2/category/{categoryId}/parameters
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/content/getCategoryContentParameters.md -->

[*list-category]:
Категория, у которой нет дочерних.

[*Deprecated]: No longer supported, please use an alternative and newer version.
