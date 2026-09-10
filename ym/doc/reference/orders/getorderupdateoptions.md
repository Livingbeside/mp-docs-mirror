---
title: Получение временных интервалов для изменения заказа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderUpdateOptions.md"
fetched_at: "2026-09-10T01:56:28Z"
content_sha: 5b2abf60f05227c0
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/getOrderUpdateOptions.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderUpdateOptions.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/getOrderUpdateOptions.md
  - href: ru/reference/orders/getOrderUpdateOptions.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/getOrderUpdateOptions.md -->
<div class="openapi">

# Получение временных интервалов для изменения заказа

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOrderUpdateOptions.md -->
  **Метод доступен для модели [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOrderUpdateOptions.md -->
  
  Возвращает список доступных интервалов для изменения даты и времени курьерской доставки.
  
  <!-- source: ru/_auto/method_limits/getOrderUpdateOptions.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOrderUpdateOptions.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/campaigns/{campaignId}/orders/update-options
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
    "id": 0
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderUpdateOptionType {#entity-OrderUpdateOptionType}
  
  Тип изменения заказа:
  
  * `UPDATE_DELIVERY_INTERVAL` — изменение интервала курьерской доставки.
  
  
  **Type**: string
  
  _Default:_{.json-schema-reset .json-schema-value} `UPDATE_DELIVERY_INTERVAL`
  
  _Const:_{.json-schema-reset .json-schema-value} `UPDATE_DELIVERY_INTERVAL`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список доступных интервалов.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "deliveryIntervals": {
        "availableDeliveryIntervals": [
          {}
        ]
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
    **Type**: [OrderUpdateOptionsDTO](#entity-OrderUpdateOptionsDTO)
  
    Список доступных интервалов.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "deliveryIntervals": {
        "availableDeliveryIntervals": [
          {
            "deliveryDateInterval": {
              "fromDate": "2025-01-01",
              "toDate": "2025-01-01"
            },
            "deliveryTimeInterval": {
              "fromTime": "example",
              "toTime": "example"
            }
          }
        ]
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
        "deliveryIntervals": {
          "availableDeliveryIntervals": [
            {
              "deliveryDateInterval": {},
              "deliveryTimeInterval": {}
            }
          ]
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
  
  ### DeliveryDateIntervalDTO {#entity-DeliveryDateIntervalDTO}
  
  Интервал дат доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начало интервала.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _toDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конец интервала.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TimeIntervalDTO {#entity-TimeIntervalDTO}
  
  Интервал времени доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Начало интервала.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _toTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Конец интервала.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromTime": "example",
    "toTime": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryIntervalsUpdateOptionDTO {#entity-DeliveryIntervalsUpdateOptionDTO}
  
  Интервалы дат и времени.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryDateInterval_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryDateIntervalDTO](#entity-DeliveryDateIntervalDTO)
  
  Интервал дат доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryTimeInterval_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TimeIntervalDTO](#entity-TimeIntervalDTO)
  
  Интервал времени доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromTime": "example",
    "toTime": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "deliveryDateInterval": {
      "fromDate": "2025-01-01",
      "toDate": "2025-01-01"
    },
    "deliveryTimeInterval": {
      "fromTime": "example",
      "toTime": "example"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryIntervalsUpdateOptionsDTO {#entity-DeliveryIntervalsUpdateOptionsDTO}
  
  Доступные интервалы для курьерской доставки.
  
  Возвращается только для типа изменения `UPDATE_DELIVERY_INTERVAL`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _availableDeliveryIntervals_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryIntervalsUpdateOptionDTO](#entity-DeliveryIntervalsUpdateOptionDTO)[]
  
  Интервалы дат и времени.
  
  Если доступных интервалов нет, возвращается пустой массив.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "deliveryDateInterval": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01"
      },
      "deliveryTimeInterval": {
        "fromTime": "example",
        "toTime": "example"
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
    "availableDeliveryIntervals": [
      {
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        }
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderUpdateOptionsDTO {#entity-OrderUpdateOptionsDTO}
  
  Список доступных интервалов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryIntervals_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DeliveryIntervalsUpdateOptionsDTO](#entity-DeliveryIntervalsUpdateOptionsDTO)
  
  Доступные интервалы для курьерской доставки.
  
  Возвращается только для типа изменения `UPDATE_DELIVERY_INTERVAL`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "availableDeliveryIntervals": [
      {
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        }
      }
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
    "deliveryIntervals": {
      "availableDeliveryIntervals": [
        {
          "deliveryDateInterval": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01"
          },
          "deliveryTimeInterval": {
            "fromTime": "example",
            "toTime": "example"
          }
        }
      ]
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
      "id": 0
    }
  schema:
    type: object
    description: Запрос вариантов изменения интервала курьерской доставки.
    required:
      - id
    properties:
      id:
        description: Идентификатор заказа.
        type: integer
        format: int64
      orderUpdateOption:
        x-hidden: true
        $ref: '#/$defs/OrderUpdateOptionType'
    $defs:
      /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/orders/api/getOrderUpdateOptions.yaml#/OrderUpdateOptionType:
        description: |
          Тип изменения заказа:
  
          * `UPDATE_DELIVERY_INTERVAL` — изменение интервала курьерской доставки.
        type: string
        enum:
          - UPDATE_DELIVERY_INTERVAL
        default: UPDATE_DELIVERY_INTERVAL
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
  path: v1/campaigns/{campaignId}/orders/update-options
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/getOrderUpdateOptions.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
