---
title: Размерные сетки и обмеры для таблиц размеров
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeCharts.md"
fetched_at: "2026-11-26T02:38:18Z"
content_sha: d0d22a778a1f99ec
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.71.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/content/getContentSizeCharts.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeCharts.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/content/getContentSizeCharts.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeCharts.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22296102
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22296102

<!-- source: ru/api/content/getContentSizeCharts.md -->
<div class="openapi">

# Размерные сетки и обмеры для таблиц размеров

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getContentSizeCharts.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getContentSizeCharts.md -->
  
  Возвращает размерные сетки и обмеры, из которых можно составить таблицу размеров для указанной размерной
  характеристики. Их идентификаторы передаются в `sizeChartId` ячеек в методах создания и обновления таблиц
  размеров `POST v2/businesses/{businessId}/size-tables/create` и `POST v2/businesses/{businessId}/size-tables/update`.
  
  В список входят:
  
  * стандартные размерные сетки Маркета — значения в них выбираются из справочника `sizeValues`;
  * размерные сетки, значения в которых задаются текстом;
  * обмеры — значения в них тоже задаются текстом.
  
  Брендовые размерные сетки в список не входят, и использовать их в своих таблицах нельзя: для них
  возвращается ошибка `UNKNOWN_SIZE_CHART`.
  
  Обязательные размерные сетки отмечены `required: true`. В таблице должна быть хотя бы одна из них,
  а каждую обязательную сетку в таблице нужно заполнить во всех строках.
  
  Для неизвестного идентификатора размерной характеристики возвращается ошибка `UNKNOWN_SIZE_PARAMETER`.
  
  **Пошаговые инструкции**
  
  * [Таблицы размеров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/size-tables.md)
  
  <!-- source: ru/_auto/method_limits/getContentSizeCharts.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getContentSizeCharts.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/size-tables/charts
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
    "sizeParameterId": 1
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _sizeParameterId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор размерной характеристики.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Размерные сетки и обмеры размерной характеристики.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "sizeParameterId": 0,
      "sizeCharts": [
        {
          "sizeChartId": 0,
          "sizeChartName": "example",
          "columnType": "SIZE_CHART",
          "required": true,
          "sizeValues": [
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
    **Type**: [GetSizeChartsResultDTO](#entity-GetSizeChartsResultDTO)
  
    Размерные сетки и обмеры размерной характеристики.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "sizeParameterId": 0,
      "sizeCharts": [
        {
          "sizeChartId": 0,
          "sizeChartName": "example",
          "columnType": "SIZE_CHART",
          "required": true,
          "sizeValues": [
            {
              "sizeValueId": 0,
              "sizeValue": "example"
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
        "sizeParameterId": 0,
        "sizeCharts": [
          {
            "sizeChartId": 0,
            "sizeChartName": "example",
            "columnType": "SIZE_CHART",
            "required": true,
            "sizeValues": [
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
  
  ### SizeTableColumnType {#entity-SizeTableColumnType}
  
  Тип колонки таблицы размеров:
  
  * `SIZE_CHART` — размерная сетка, по которой определяется размер товара.
  * `MEASUREMENT` — обмер, например обхват груди или длина стопы. В определении размера товара не участвует.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SIZE_CHART`, `MEASUREMENT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeChartValueDTO {#entity-SizeChartValueDTO}
  
  Значение из справочника размерной сетки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _sizeValue_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Текст значения.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _sizeValueId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения. Передавайте его в `sizeValueId` ячейки таблицы.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeValueId": 0,
    "sizeValue": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeChartInfoDTO {#entity-SizeChartInfoDTO}
  
  Размерная сетка или обмер, которые можно использовать как колонку таблицы размеров.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _columnType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeTableColumnType](#entity-SizeTableColumnType)
  
  Тип колонки таблицы размеров:
  
  * `SIZE_CHART` — размерная сетка, по которой определяется размер товара.
  * `MEASUREMENT` — обмер, например обхват груди или длина стопы. В определении размера товара не участвует.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `SIZE_CHART`, `MEASUREMENT`
  {.table-cell}
  ||
  ||
  
  _required_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Обязательная ли размерная сетка. В таблице должна быть хотя бы одна обязательная сетка,
  а каждую обязательную сетку в таблице нужно заполнить во всех строках. У обмеров всегда `false`.
  
  {.table-cell}
  ||
  ||
  
  _sizeChartId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор размерной сетки или обмера. Передавайте его в `sizeChartId` ячейки таблицы.
  {.table-cell}
  ||
  ||
  
  _sizeChartName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название размерной сетки или обмера.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _sizeValues_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeChartValueDTO](#entity-SizeChartValueDTO)[]
  
  Справочник значений размерной сетки. Заполнен только у стандартных размерных сеток Маркета: в ячейке
  такой колонки передавайте значение из справочника.
  
  Если список пустой, значение задается текстом.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeValueId": 0,
      "sizeValue": "example"
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
    "sizeChartId": 0,
    "sizeChartName": "example",
    "columnType": "SIZE_CHART",
    "required": true,
    "sizeValues": [
      {
        "sizeValueId": 0,
        "sizeValue": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetSizeChartsResultDTO {#entity-GetSizeChartsResultDTO}
  
  Размерные сетки и обмеры размерной характеристики.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _sizeCharts_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeChartInfoDTO](#entity-SizeChartInfoDTO)[]
  
  Размерные сетки и обмеры, которые можно использовать в таблицах размеров: сначала сетки, затем обмеры.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeChartId": 0,
      "sizeChartName": "example",
      "columnType": "SIZE_CHART",
      "required": true,
      "sizeValues": [
        {
          "sizeValueId": 0,
          "sizeValue": "example"
        }
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _sizeParameterId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор размерной характеристики из запроса.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeParameterId": 0,
    "sizeCharts": [
      {
        "sizeChartId": 0,
        "sizeChartName": "example",
        "columnType": "SIZE_CHART",
        "required": true,
        "sizeValues": [
          {
            "sizeValueId": 0,
            "sizeValue": "example"
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#400)
  
  Коды ошибок:
  
  * `BAD_REQUEST` — запрос не соответствует описанию метода.
  * `UNKNOWN_SIZE_PARAMETER` — `sizeParameterId` не из списка допустимых значений.
  
  
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
      "sizeParameterId": 1
    }
  schema:
    description: Размерная характеристика, для которой нужны размерные сетки и обмеры.
    type: object
    required:
      - sizeParameterId
    properties:
      sizeParameterId:
        description: Идентификатор размерной характеристики.
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
  path: v2/businesses/{businessId}/size-tables/charts
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/content/getContentSizeCharts.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
