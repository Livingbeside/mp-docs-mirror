---
title: Список складов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md"
fetched_at: "2026-09-24T02:14:54Z"
content_sha: 4f509501ca5c5209
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/warehouses/getPartnerWarehouses.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/warehouses/getPartnerWarehouses.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/warehouses/getPartnerWarehouses.md -->
<div class="openapi">

# Список складов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getPartnerWarehouses.md -->
  **Метод доступен для моделей: [FBS, Экспресс и DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getPartnerWarehouses.md -->
  
  Возвращает список складов кабинета и информацию о них.
  
  Для каждого склада возвращается список моделей работы (FBS, DBS, Экспресс) и доступность API для каждой модели.
  
  {% note warning "Метод подходит, только если в кабинете нет групп складов" %}
  
  Метод возвращает только отдельные склады и не возвращает группы складов. Если в кабинете есть группы складов, используйте метод [POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md). [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks).
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/getPartnerWarehouses.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getPartnerWarehouses.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v3/businesses/{businessId}/warehouses
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
  
  
  _Default:_{.json-schema-reset .json-schema-value} `15`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `30`
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
    "warehouseIds": [
      1
    ],
    "components": [
      "ADDRESS"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _components_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PartnerWarehouseComponentType](#entity-PartnerWarehouseComponentType)[] &#124; null
  
  Свойства складов, которые необходимо вернуть. Если какое-то значение параметра не задано, этой информации в ответе не будет.
  
  Передавайте параметр, только если нужна информация, которую он возвращает.
  
  
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
  
  _warehouseIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Список идентификаторов складов, которые необходимо вернуть.
  
  Если параметр не указан, возвращаются все склады кабинета.
  
  
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
  
  </div>
  
  <div class="openapi-entity">
  
  ### PartnerWarehouseComponentType {#entity-PartnerWarehouseComponentType}
  
  Свойства складов, которые необходимо вернуть:
  
  * `ADDRESS` — адрес склада.
  
  
  **Type**: string
  
  _Const:_{.json-schema-reset .json-schema-value} `ADDRESS`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список складов и их свойства, которые вы запрашивали.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "warehouses": [
        {
          "id": 1,
          "name": "example",
          "models": [
            null
          ],
          "address": {}
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
    **Type**: [PartnerWarehousesDTO](#entity-PartnerWarehousesDTO)
  
    Информация о складах в кабинете.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "warehouses": [
        {
          "id": 1,
          "name": "example",
          "models": [
            {
              "placementType": "FBS",
              "apiAvailability": "AVAILABLE"
            }
          ],
          "address": {
            "city": "example",
            "street": "example",
            "number": "example",
            "building": "example",
            "block": "example",
            "gps": {
              "latitude": 0.5,
              "longitude": 0.5
            }
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
        "warehouses": [
          {
            "id": 1,
            "name": "example",
            "models": [
              {}
            ],
            "address": {
              "city": "example",
              "street": "example",
              "number": "example",
              "building": "example",
              "block": "example",
              "gps": {}
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
  
  ### WarehouseProgramType {#entity-WarehouseProgramType}
  
  Модель работы:
  
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBS`, `DBS`, `EXPRESS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiAvailabilityStatusType {#entity-ApiAvailabilityStatusType}
  
  Возможность использовать API:
  
  * `AVAILABLE` — методы API доступны для выполнения запросов.
  * `DISABLED_BY_INACTIVITY` — методы API недоступны, так как магазин не размещал товары на витрине больше 90 дней.
  * `DISABLED_BY_NO_ACTIVE_CONTRACT` — методы API недоступны из-за отсутствия активного договора с Маркетом.
  * `MANUALLY_DISABLED` — методы API недоступны, так как интеграция выключена вручную.
  * `DISABLED_BY_NO_PLACEMENT_TYPE` — методы API недоступны, так как магазин не подключен к программе размещения.
  
  [Подробная инструкция по восстановлению доступа](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md)
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `AVAILABLE`, `DISABLED_BY_INACTIVITY`, `DISABLED_BY_NO_ACTIVE_CONTRACT`, `MANUALLY_DISABLED`, `DISABLED_BY_NO_PLACEMENT_TYPE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PartnerWarehouseModelDTO {#entity-PartnerWarehouseModelDTO}
  
  Информация о модели работы склада.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _apiAvailability_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ApiAvailabilityStatusType](#entity-ApiAvailabilityStatusType)
  
  Возможность использовать API:
  
  * `AVAILABLE` — методы API доступны для выполнения запросов.
  * `DISABLED_BY_INACTIVITY` — методы API недоступны, так как магазин не размещал товары на витрине больше 90 дней.
  * `DISABLED_BY_NO_ACTIVE_CONTRACT` — методы API недоступны из-за отсутствия активного договора с Маркетом.
  * `MANUALLY_DISABLED` — методы API недоступны, так как интеграция выключена вручную.
  * `DISABLED_BY_NO_PLACEMENT_TYPE` — методы API недоступны, так как магазин не подключен к программе размещения.
  
  [Подробная инструкция по восстановлению доступа](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md)
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `AVAILABLE`, `DISABLED_BY_INACTIVITY`, `DISABLED_BY_NO_ACTIVE_CONTRACT`, `MANUALLY_DISABLED`, `DISABLED_BY_NO_PLACEMENT_TYPE`
  {.table-cell}
  ||
  ||
  
  _placementType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseProgramType](#entity-WarehouseProgramType)
  
  Модель работы:
  
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBS`, `DBS`, `EXPRESS`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "placementType": "FBS",
    "apiAvailability": "AVAILABLE"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GpsDTO {#entity-GpsDTO}
  
  GPS-координаты широты и долготы.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _latitude_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Широта.
  {.table-cell}
  ||
  ||
  
  _longitude_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Долгота.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "latitude": 0.5,
    "longitude": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseAddressDTO {#entity-WarehouseAddressDTO}
  
  Адрес склада.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _city_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Город.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `200`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _gps_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GpsDTO](#entity-GpsDTO)
  
  GPS-координаты широты и долготы.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "latitude": 0.5,
    "longitude": 0.5
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _block_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер корпуса.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _building_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер строения.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _number_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер дома.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `256`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _street_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Улица.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "city": "example",
    "street": "example",
    "number": "example",
    "building": "example",
    "block": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PartnerWarehouseDTO {#entity-PartnerWarehouseDTO}
  
  Информация о складе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _models_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PartnerWarehouseModelDTO](#entity-PartnerWarehouseModelDTO)[]
  
  Модели работы, доступные для склада.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "placementType": "FBS",
      "apiAvailability": "AVAILABLE"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название склада.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _address_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [WarehouseAddressDTO](#entity-WarehouseAddressDTO)
  
  Адрес склада.
  
  Возвращается, только если в запросе параметр `components` принимает значение `ADDRESS`.
  
  
  Адрес склада.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "city": "example",
    "street": "example",
    "number": "example",
    "building": "example",
    "block": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
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
    "id": 1,
    "name": "example",
    "models": [
      {
        "placementType": "FBS",
        "apiAvailability": "AVAILABLE"
      }
    ],
    "address": {
      "city": "example",
      "street": "example",
      "number": "example",
      "building": "example",
      "block": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
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
  
  ### PartnerWarehousesDTO {#entity-PartnerWarehousesDTO}
  
  Информация о складах в кабинете.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _warehouses_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PartnerWarehouseDTO](#entity-PartnerWarehouseDTO)[]
  
  Список складов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 1,
      "name": "example",
      "models": [
        {
          "placementType": "FBS",
          "apiAvailability": "AVAILABLE"
        }
      ],
      "address": {
        "city": "example",
        "street": "example",
        "number": "example",
        "building": "example",
        "block": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        }
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
    "warehouses": [
      {
        "id": 1,
        "name": "example",
        "models": [
          {
            "placementType": "FBS",
            "apiAvailability": "AVAILABLE"
          }
        ],
        "address": {
          "city": "example",
          "street": "example",
          "number": "example",
          "building": "example",
          "block": "example",
          "gps": {
            "latitude": 0.5,
            "longitude": 0.5
          }
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
        default: 15
        maximum: 30
  headers: []
  body: |-
    {
      "warehouseIds": [
        1
      ],
      "components": [
        "ADDRESS"
      ]
    }
  schema:
    description: Запрос на получение складов кабинета.
    type: object
    properties:
      warehouseIds:
        description: |
          Список идентификаторов складов, которые необходимо вернуть.
  
          Если параметр не указан, возвращаются все склады кабинета.
        type: array
        nullable: true
        uniqueItems: true
        minItems: 1
        items:
          type: integer
          format: int64
          minimum: 1
      components:
        description: >
          Свойства складов, которые необходимо вернуть. Если какое-то значение
          параметра не задано, этой информации в ответе не будет.
  
  
          Передавайте параметр, только если нужна информация, которую он
          возвращает.
        type: array
        nullable: true
        uniqueItems: true
        minItems: 1
        items:
          description: |
            Свойства складов, которые необходимо вернуть:
  
            * `ADDRESS` — адрес склада.
          type: string
          enum:
            - ADDRESS
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
  path: v3/businesses/{businessId}/warehouses
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/warehouses/getPartnerWarehouses.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
