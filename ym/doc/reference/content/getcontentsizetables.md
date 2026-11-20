---
title: Таблицы размеров по идентификаторам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeTables.md"
fetched_at: "2026-11-20T02:50:14Z"
content_sha: b37ac83b372c0c7f
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.71.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/content/getContentSizeTables.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeTables.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeTables.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22204578
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22204578

<!-- source: ru/api/content/getContentSizeTables.md -->
<div class="openapi">

# Таблицы размеров по идентификаторам

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getContentSizeTables.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getContentSizeTables.md -->
  
  Возвращает таблицы размеров по их идентификаторам. Идентификаторы возвращает метод
  подбора таблиц размеров. Если `sizeTableIds` не передан, возвращает все таблицы размеров,
  созданные бизнесом.
  
  Сначала возвращаются созданные бизнесом, затем брендовые, затем стандартные таблицы;
  внутри каждой группы — по убыванию идентификатора.
  
  Результаты возвращаются постранично. Для навигации используйте параметры `pageToken` и `limit`.
  В каждом следующем запросе передавайте тот же набор `sizeTableIds`, что и в первом:
  `pageToken` привязан к нему, и с другим набором запрос будет отклонен. Порядок
  идентификаторов значения не имеет.
  
  Идентификаторы, по которым таблицу вернуть не удалось — такой таблицы нет или она
  принадлежит другому бизнесу, — возвращаются в `notFoundSizeTableIds` на первой странице.
  
  <!-- source: ru/_auto/method_limits/getContentSizeTables.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getContentSizeTables.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/size-tables
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
  
  
  _Default:_{.json-schema-reset .json-schema-value} `25`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `100`
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
    "sizeTableIds": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _sizeTableIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Идентификаторы таблиц размеров.
  
  Если параметр не передан, возвращаются все таблицы, созданные бизнесом.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
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
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Таблицы размеров.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "sizeTables": [
        {
          "sizeTableId": 0,
          "sizeTableName": "example",
          "sizeTableType": "CUSTOM",
          "sizeParameterId": 0,
          "editable": true,
          "key": {},
          "sizeCharts": [
            null
          ]
        }
      ],
      "notFoundSizeTableIds": [
        0
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
    **Type**: [GetSizeTablesResultDTO](#entity-GetSizeTablesResultDTO)
  
    Таблицы размеров.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "sizeTables": [
        {
          "sizeTableId": 0,
          "sizeTableName": "example",
          "sizeTableType": "CUSTOM",
          "sizeParameterId": 0,
          "editable": true,
          "key": {
            "categoryId": 0,
            "vendorId": 0,
            "genderId": 0
          },
          "sizeCharts": [
            {
              "sizeChartId": 0,
              "sizeChartName": "example",
              "columnType": "SIZE_CHART",
              "sizes": [
                null
              ]
            }
          ]
        }
      ],
      "notFoundSizeTableIds": [
        0
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
        "sizeTables": [
          {
            "sizeTableId": 0,
            "sizeTableName": "example",
            "sizeTableType": "CUSTOM",
            "sizeParameterId": 0,
            "editable": true,
            "key": {
              "categoryId": 0,
              "vendorId": 0,
              "genderId": 0
            },
            "sizeCharts": [
              {}
            ]
          }
        ],
        "notFoundSizeTableIds": [
          0
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
  
  ### SizeTableType {#entity-SizeTableType}
  
  Тип таблицы размеров:
  
  * `CUSTOM` — таблица, созданная бизнесом.
  * `STANDARD` — таблица Маркета: стандартная или подобранная под бренд.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CUSTOM`, `STANDARD`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeTableKeyDTO {#entity-SizeTableKeyDTO}
  
  Условия, по которым подобрана таблица.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _categoryId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор категории из запроса.
  {.table-cell}
  ||
  ||
  
  _genderId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор пола на Маркете.
  {.table-cell}
  ||
  ||
  
  _vendorId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор бренда на Маркете. Возвращается только для таблиц бренда.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "categoryId": 0,
    "vendorId": 0,
    "genderId": 0
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
  
  ### SizeValueDTO {#entity-SizeValueDTO}
  
  Значение в ячейке таблицы размеров.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _rowIndex_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Номер строки таблицы, начиная с 0. Значения с одинаковым `rowIndex` в разных колонках описывают один размер.
  
  Номера могут идти с пропусками, а порядок строк может не совпадать с порядком размеров. Собирайте строки
  по значению `rowIndex`, а не по позиции значения в `sizes`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _sizeValue_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Значение размера или обмера.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _sizeValueId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения размера. Возвращается, только если у колонки есть справочник значений — это стандартные размерные сетки Маркета.
  
  В сетках, созданных бизнесом, брендовых сетках и обмерах значение задается только текстом.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeValueId": 0,
    "sizeValue": "example",
    "rowIndex": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeChartDTO {#entity-SizeChartDTO}
  
  Колонка таблицы размеров — размерная сетка или обмер.
  
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
  
  _sizeChartId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор размерной сетки или обмера. У сеток и обмеров общее пространство идентификаторов.
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
  
  _sizes_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeValueDTO](#entity-SizeValueDTO)[]
  
  Значения колонки в порядке строк таблицы. Пустые ячейки не возвращаются.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeValueId": 0,
      "sizeValue": "example",
      "rowIndex": 0
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
    "sizes": [
      {
        "sizeValueId": 0,
        "sizeValue": "example",
        "rowIndex": 0
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeTableDTO {#entity-SizeTableDTO}
  
  Таблица размеров.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _editable_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Может ли бизнес редактировать таблицу: `true` — для таблиц, созданных бизнесом, `false` — для таблиц Маркета.
  
  {.table-cell}
  ||
  ||
  
  _sizeCharts_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeChartDTO](#entity-SizeChartDTO)[]
  
  Колонки таблицы: размерные сетки и обмеры. Колонки без значений не возвращаются.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeChartId": 0,
      "sizeChartName": "example",
      "columnType": "SIZE_CHART",
      "sizes": [
        {
          "sizeValueId": 0,
          "sizeValue": "example",
          "rowIndex": 0
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
  
  Идентификатор размерной характеристики, к которой относятся размеры из таблицы.
  {.table-cell}
  ||
  ||
  
  _sizeTableId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор таблицы размеров.
  {.table-cell}
  ||
  ||
  
  _sizeTableName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название таблицы размеров.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _sizeTableType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeTableType](#entity-SizeTableType)
  
  Тип таблицы размеров:
  
  * `CUSTOM` — таблица, созданная бизнесом.
  * `STANDARD` — таблица Маркета: стандартная или подобранная под бренд.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CUSTOM`, `STANDARD`
  {.table-cell}
  ||
  ||
  
  _key_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SizeTableKeyDTO](#entity-SizeTableKeyDTO)
  
  Условия подбора таблицы. Возвращаются, только если таблица подобрана по категории.
  
  Условия, по которым подобрана таблица.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "categoryId": 0,
    "vendorId": 0,
    "genderId": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeTableId": 0,
    "sizeTableName": "example",
    "sizeTableType": "CUSTOM",
    "sizeParameterId": 0,
    "editable": true,
    "key": {
      "categoryId": 0,
      "vendorId": 0,
      "genderId": 0
    },
    "sizeCharts": [
      {
        "sizeChartId": 0,
        "sizeChartName": "example",
        "columnType": "SIZE_CHART",
        "sizes": [
          {
            "sizeValueId": 0,
            "sizeValue": "example",
            "rowIndex": 0
          }
        ]
      }
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
  
  ### GetSizeTablesResultDTO {#entity-GetSizeTablesResultDTO}
  
  Таблицы размеров.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _notFoundSizeTableIds_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer[]
  
  Идентификаторы из запроса, по которым таблицу вернуть не удалось: такой таблицы нет
  или она принадлежит другому бизнесу.
  
  Заполняется только на первой странице. На следующих страницах и в запросе без `sizeTableIds` список пустой.
  
  
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
  
  _paging_{.json-schema-reset .json-schema-property .json-schema-required}
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
  ||
  
  _sizeTables_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeTableDTO](#entity-SizeTableDTO)[]
  
  Таблицы размеров: сначала созданные бизнесом, затем брендовые, затем стандартные;
  внутри каждой группы — по убыванию идентификатора.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeTableId": 0,
      "sizeTableName": "example",
      "sizeTableType": "CUSTOM",
      "sizeParameterId": 0,
      "editable": true,
      "key": {
        "categoryId": 0,
        "vendorId": 0,
        "genderId": 0
      },
      "sizeCharts": [
        {
          "sizeChartId": 0,
          "sizeChartName": "example",
          "columnType": "SIZE_CHART",
          "sizes": [
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
    "sizeTables": [
      {
        "sizeTableId": 0,
        "sizeTableName": "example",
        "sizeTableType": "CUSTOM",
        "sizeParameterId": 0,
        "editable": true,
        "key": {
          "categoryId": 0,
          "vendorId": 0,
          "genderId": 0
        },
        "sizeCharts": [
          {
            "sizeChartId": 0,
            "sizeChartName": "example",
            "columnType": "SIZE_CHART",
            "sizes": [
              null
            ]
          }
        ]
      }
    ],
    "notFoundSizeTableIds": [
      0
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
        default: 25
        maximum: 100
  headers: []
  body: |-
    {
      "sizeTableIds": [
        1
      ]
    }
  schema:
    description: Идентификаторы таблиц размеров.
    type: object
    properties:
      sizeTableIds:
        description: |
          Идентификаторы таблиц размеров.
  
          Если параметр не передан, возвращаются все таблицы, созданные бизнесом.
        type: array
        nullable: true
        minItems: 1
        maxItems: 100
        uniqueItems: true
        items:
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
  path: v2/businesses/{businessId}/size-tables
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/content/getContentSizeTables.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
