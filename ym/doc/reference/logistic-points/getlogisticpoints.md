---
title: Получение точек ПВЗ Маркета (LaaS)
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md"
fetched_at: "2026-09-16T02:28:22Z"
content_sha: 7e63993e863e9c74
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/logistic-points/getLogisticPoints.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/logistic-points/getLogisticPoints.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/logistic-points/getLogisticPoints.md -->
<div class="openapi">

# Получение точек ПВЗ Маркета

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getLogisticPoints.md -->
  **Метод доступен для модели [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * pricing:read-only — [Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md)
  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * promotion:read-only — [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * settings-management — [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
  * supplies-management:read-only — [Получение информации по FBY-заявкам](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getLogisticPoints.md -->
  
  Возвращает список пунктов выдачи заказов Маркета.
  
  Регулярно запрашивайте эту информацию, чтобы в системе магазина хранить актуальные данные. Например, раз в день.
  
  <!-- source: ru/_auto/method_limits/getLogisticPoints.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getLogisticPoints.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/logistics-points
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
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о пунктах выдачи заказов Маркета.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "logisticPoints": [
        {
          "logisticPointId": 1,
          "brand": "MARKET",
          "address": {},
          "workingSchedule": {},
          "deliveryRestrictions": {},
          "features": [
            null
          ],
          "storagePeriod": 0
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
    **Type**: [GetLogisticsPointsDTO](#entity-GetLogisticsPointsDTO)
  
    Информация о пунктах выдачи заказов.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "logisticPoints": [
        {
          "logisticPointId": 1,
          "brand": "MARKET",
          "address": {
            "fullAddress": "example",
            "gps": {
              "latitude": 0.5,
              "longitude": 0.5
            },
            "regionId": 0,
            "city": "example",
            "street": "example",
            "house": "example",
            "building": "example",
            "block": "example",
            "km": 0,
            "additional": "example"
          },
          "workingSchedule": {
            "schedule": [
              {}
            ],
            "holidays": [
              "2025-01-01"
            ]
          },
          "deliveryRestrictions": {
            "dimensionsRestrictions": {
              "weight": 1,
              "height": 1,
              "width": 1,
              "length": 1,
              "dimensionsSum": 1
            }
          },
          "features": [
            "RETURN_ALLOWED"
          ],
          "storagePeriod": 0
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
        "logisticPoints": [
          {
            "logisticPointId": 1,
            "brand": "MARKET",
            "address": {
              "fullAddress": "example",
              "gps": {},
              "regionId": 0,
              "city": "example",
              "street": "example",
              "house": "example",
              "building": "example",
              "block": "example",
              "km": 0,
              "additional": "example"
            },
            "workingSchedule": {
              "schedule": [
                null
              ],
              "holidays": [
                null
              ]
            },
            "deliveryRestrictions": {
              "dimensionsRestrictions": {}
            },
            "features": [
              "RETURN_ALLOWED"
            ],
            "storagePeriod": 0
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
  
  ### LogisticPointId {#entity-LogisticPointId}
  
  Идентификатор пункта выдачи.
  
  Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointBrandType {#entity-LogisticPointBrandType}
  
  Тип пункта выдачи:
  
  * `MARKET` — пункт выдачи Маркета.
  
  
  **Type**: string
  
  _Const:_{.json-schema-reset .json-schema-value} `MARKET`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
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
  
  ### LogisticPointAddressDTO {#entity-LogisticPointAddressDTO}
  
  Адрес пункта выдачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fullAddress_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Полный адрес.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
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
  
  _regionId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона.
  
  Информацию о регионе можно получить c помощью метода [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md).
  
  {.table-cell}
  ||
  ||
  
  _additional_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Дополнительная информация.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `1024`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _block_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер корпуса.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _building_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер строения.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _city_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Город.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `128`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _house_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер дома.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _km_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Порядковый номер километра, на котором располагается пункт выдачи.
  
  Указывается, если в адресе нет улицы.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _street_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Улица.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `128`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
    },
    "regionId": 0,
    "city": "example",
    "street": "example",
    "house": "example",
    "building": "example",
    "block": "example",
    "km": 0,
    "additional": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DayOfWeekType {#entity-DayOfWeekType}
  
  День недели:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MONDAY`, `TUESDAY`, `WEDNESDAY`, `THURSDAY`, `FRIDAY`, `SATURDAY`, `SUNDAY`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ScheduleDayDTO {#entity-ScheduleDayDTO}
  
  День и время работы.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _day_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DayOfWeekType](#entity-DayOfWeekType)
  
  День недели.
  
  День недели:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MONDAY`, `TUESDAY`, `WEDNESDAY`, `THURSDAY`, `FRIDAY`, `SATURDAY`, `SUNDAY`
  {.table-cell}
  ||
  ||
  
  _endTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Время конца рабочего дня.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _startTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Время начала рабочего дня.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "day": "MONDAY",
    "startTime": "example",
    "endTime": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointScheduleDTO {#entity-LogisticPointScheduleDTO}
  
  Расписание работы пункта выдачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _schedule_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ScheduleDayDTO](#entity-ScheduleDayDTO)[]
  
  График работы.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "day": "MONDAY",
      "startTime": "example",
      "endTime": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _holidays_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;[] &#124; null
  
  Расписание праздничных дней.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "2025-01-01"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "schedule": [
      {
        "day": "MONDAY",
        "startTime": "example",
        "endTime": "example"
      }
    ],
    "holidays": [
      "2025-01-01"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointDimensionRestrictionsDTO {#entity-LogisticPointDimensionRestrictionsDTO}
  
  Ограничения по размеру одного товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dimensionsSum_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная сумма измерений в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _height_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная высота в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _length_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная длина в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _weight_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальный вес в граммах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _width_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Максимальная ширина в сантиметрах.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "weight": 1,
    "height": 1,
    "width": 1,
    "length": 1,
    "dimensionsSum": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointDeliveryRestrictionDTO {#entity-LogisticPointDeliveryRestrictionDTO}
  
  Ограничения на доставку в пункт выдачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dimensionsRestrictions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointDimensionRestrictionsDTO](#entity-LogisticPointDimensionRestrictionsDTO)
  
  Ограничения по размеру одного товара.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "weight": 1,
    "height": 1,
    "width": 1,
    "length": 1,
    "dimensionsSum": 1
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "dimensionsRestrictions": {
      "weight": 1,
      "height": 1,
      "width": 1,
      "length": 1,
      "dimensionsSum": 1
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointFeatureType {#entity-LogisticPointFeatureType}
  
  Свойство пункта выдачи:
  
  * `RETURN_ALLOWED` — пункт выдачи принимает возвраты.
  
  {% note warning "Проверка ограничений" %}
  
  Признак не учитывает ограничения ПВЗ на прием различных товаров в возврате.
  Для проверки по конкретному набору товаров используйте метод [POST v1/campaigns/{campaignId}/return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md).
  
  {% endnote %}
  
  
  **Type**: string
  
  _Const:_{.json-schema-reset .json-schema-value} `RETURN_ALLOWED`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryPaymentType {#entity-DeliveryPaymentType}
  
  Тип оплаты заказа:
  
  * `PREPAID` — оплата при оформлении заказа.
  
  
  **Type**: string
  
  _Const:_{.json-schema-reset .json-schema-value} `PREPAID`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointDTO {#entity-LogisticPointDTO}
  
  Информация о пункте выдачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointAddressDTO](#entity-LogisticPointAddressDTO)
  
  Адрес пункта выдачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
    },
    "regionId": 0,
    "city": "example",
    "street": "example",
    "house": "example",
    "building": "example",
    "block": "example",
    "km": 0,
    "additional": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _brand_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointBrandType](#entity-LogisticPointBrandType)
  
  Тип пункта выдачи:
  
  * `MARKET` — пункт выдачи Маркета.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MARKET`
  {.table-cell}
  ||
  ||
  
  _deliveryRestrictions_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointDeliveryRestrictionDTO](#entity-LogisticPointDeliveryRestrictionDTO)
  
  Ограничения на доставку в пункт выдачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "dimensionsRestrictions": {
      "weight": 1,
      "height": 1,
      "width": 1,
      "length": 1,
      "dimensionsSum": 1
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
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
  ||
  
  _storagePeriod_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Срок хранения заказа в пункте выдачи.
  
  Указывается в днях.
  
  {.table-cell}
  ||
  ||
  
  _workingSchedule_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointScheduleDTO](#entity-LogisticPointScheduleDTO)
  
  Расписание работы пункта выдачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "schedule": [
      {
        "day": "MONDAY",
        "startTime": "example",
        "endTime": "example"
      }
    ],
    "holidays": [
      "2025-01-01"
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _features_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [LogisticPointFeatureType](#entity-LogisticPointFeatureType)[] &#124; null
  
  Свойства пункта выдачи.
  
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
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "logisticPointId": 1,
    "brand": "MARKET",
    "address": {
      "fullAddress": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      },
      "regionId": 0,
      "city": "example",
      "street": "example",
      "house": "example",
      "building": "example",
      "block": "example",
      "km": 0,
      "additional": "example"
    },
    "workingSchedule": {
      "schedule": [
        {
          "day": "MONDAY",
          "startTime": "example",
          "endTime": "example"
        }
      ],
      "holidays": [
        "2025-01-01"
      ]
    },
    "deliveryRestrictions": {
      "dimensionsRestrictions": {
        "weight": 1,
        "height": 1,
        "width": 1,
        "length": 1,
        "dimensionsSum": 1
      }
    },
    "features": [
      "RETURN_ALLOWED"
    ],
    "storagePeriod": 0
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
  
  ### GetLogisticsPointsDTO {#entity-GetLogisticsPointsDTO}
  
  Информация о пунктах выдачи заказов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _logisticPoints_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LogisticPointDTO](#entity-LogisticPointDTO)[]
  
  Пункты выдачи заказов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "logisticPointId": 1,
      "brand": "MARKET",
      "address": {
        "fullAddress": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        },
        "regionId": 0,
        "city": "example",
        "street": "example",
        "house": "example",
        "building": "example",
        "block": "example",
        "km": 0,
        "additional": "example"
      },
      "workingSchedule": {
        "schedule": [
          {
            "day": "MONDAY",
            "startTime": "example",
            "endTime": "example"
          }
        ],
        "holidays": [
          "2025-01-01"
        ]
      },
      "deliveryRestrictions": {
        "dimensionsRestrictions": {
          "weight": 1,
          "height": 1,
          "width": 1,
          "length": 1,
          "dimensionsSum": 1
        }
      },
      "features": [
        "RETURN_ALLOWED"
      ],
      "storagePeriod": 0
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
    "logisticPoints": [
      {
        "logisticPointId": 1,
        "brand": "MARKET",
        "address": {
          "fullAddress": "example",
          "gps": {
            "latitude": 0.5,
            "longitude": 0.5
          },
          "regionId": 0,
          "city": "example",
          "street": "example",
          "house": "example",
          "building": "example",
          "block": "example",
          "km": 0,
          "additional": "example"
        },
        "workingSchedule": {
          "schedule": [
            {}
          ],
          "holidays": [
            "2025-01-01"
          ]
        },
        "deliveryRestrictions": {
          "dimensionsRestrictions": {
            "weight": 1,
            "height": 1,
            "width": 1,
            "length": 1,
            "dimensionsSum": 1
          }
        },
        "features": [
          "RETURN_ALLOWED"
        ],
        "storagePeriod": 0
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
        default: 250
        maximum: 500
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
  path: v1/businesses/{businessId}/logistics-points
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/logistic-points/getLogisticPoints.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
