---
title: Создание таблиц размеров
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/createContentSizeTables.md"
fetched_at: "2026-11-21T02:45:47Z"
content_sha: f00627db131bc667
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.71.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/content/createContentSizeTables.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/createContentSizeTables.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/content/createContentSizeTables.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/createContentSizeTables.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22228850
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22228850

<!-- source: ru/api/content/createContentSizeTables.md -->
<div class="openapi">

# Создание таблиц размеров

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/createContentSizeTables.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/createContentSizeTables.md -->
  
  Создает таблицы размеров бизнеса. За один запрос можно создать до 10 таблиц, в которых суммарно не больше
  5000 ячеек. Если таблиц или ячеек больше, запрос отклоняется с ошибкой `BAD_REQUEST` и ни одна таблица
  не создается.
  
  Таблица относится к размерной характеристике, а не к категории: она подбирается для всех категорий
  с той же размерной характеристикой.
  
  Размерную характеристику категории возвращает метод подбора таблиц размеров
  `POST v2/businesses/{businessId}/size-tables/suggest` в поле `result.sizeParameterId`, характеристику
  существующей таблицы — метод `POST v2/businesses/{businessId}/size-tables` в поле `sizeParameterId`.
  Если в запросе есть неизвестный идентификатор размерной характеристики, запрос отклоняется с ошибкой
  `UNKNOWN_SIZE_PARAMETER` и ни одна таблица не создается.
  
  Размерные сетки и обмеры, которые можно использовать в таблице, их значения и обязательные сетки
  возвращает метод `POST v2/businesses/{businessId}/size-tables/charts`.
  
  {% cut "Как заполнить таблицу" %}
  
  <!-- source: ru/_includes/common/size-tables-filling.md -->
  Каждый элемент `rows` — строка таблицы: один размер во всех размерных сетках и обмерах. В `values`
  передайте по одной ячейке на колонку: идентификатор сетки или обмера в `sizeChartId` или название
  в `sizeChartName` и значение в `sizeValueId`, `sizeValue` или в обоих полях. Ячейку без значения можно не передавать или передать
  с пустым `sizeValue` — она сохранится как «нет значения».

  Требования к таблице:

  * В таблице должна быть хотя бы одна обязательная размерная сетка (`required: true`), иначе вернется ошибка
    `ABSENT_MANDATORY_SIZE_CHART`. Обмеры и сетки с `required: false` это требование не выполняют.
  * Каждую обязательную сетку, которая есть в таблице, заполните во всех строках, иначе вернется ошибка `EMPTY_CELL`.
  * В каждой колонке должно быть хотя бы одно значение, кроме пустого и «нет значения», иначе вернется ошибка
    `NONE_COLUMN`. Если заполнить колонку нечем, не передавайте ее ячейки.
  * Строки не должны совпадать, иначе вернется ошибка `DUPLICATE_ROWS`. Допустимы ли повторы значений в колонке
    (`DUPLICATE_SIZES`, `DUPLICATE_MEASURES`), зависит от размерной характеристики.
  <!-- endsource: ru/_includes/common/size-tables-filling.md -->
  
  {% endcut %}
  
  {% cut "Чем сохраненная таблица отличается от переданной" %}
  
  <!-- source: ru/_includes/common/size-tables-saved-differences.md -->
  Метод `POST v2/businesses/{businessId}/size-tables` возвращает таблицу по колонкам: у каждого значения
  есть номер строки `rowIndex`. Чтобы получить строки, сгруппируйте значения по `rowIndex`.

  Сохраненная таблица может отличаться от переданной:

  * строки и колонки идут в порядке, который задает Маркет, а `rowIndex` не совпадает с номером строки в запросе;
  * в стандартных размерных сетках возвращаются текст значения из справочника и его `sizeValueId`;
  * в обмерах запятые заменены точками: `42,5` → `42.5`;
  * ячейки «нет значения» и непереданные ячейки не возвращаются;
  * пробелы в начале и в конце названия и значений удалены.
  <!-- endsource: ru/_includes/common/size-tables-saved-differences.md -->
  
  Значения из ответа можно без изменений передать в метод обновления таблиц размеров
  `POST v2/businesses/{businessId}/size-tables/update`: поля `columnType` и `rowIndex` в нем не учитываются.
  
  {% endcut %}
  
  Чтобы привязать таблицу к товару, передайте ее идентификатор в `value` характеристики с `parameterId: 73979829`
  в запросе [POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md).
  Когда таблица изменяется, новое содержимое применяется к привязанным товарам автоматически.
  
  {% note warning "Повторный запрос создает таблицы еще раз" %}
  
  Метод не идемпотентен: каждый запрос создает новые таблицы, даже если такие же уже есть.
  
  Если запрос завершился ошибкой с кодом 5xx, часть таблиц могла сохраниться. Получите таблицы бизнеса методом
  `POST v2/businesses/{businessId}/size-tables` и только после этого повторите запрос для таблиц, которых там нет.
  
  {% endnote %}
  
  Количество таблиц у бизнеса ограничено — суммарно по всем размерным характеристикам. Удалить таблицу нельзя.
  Если лимит исчерпан, таблица не создается и для нее возвращается ошибка `LIMIT_TABLES`. При одновременных
  запросах лимит проверяется нестрого, и таблиц может создаться больше.
  
  <!-- source: ru/_auto/method_limits/createContentSizeTables.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 5 запросов в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 10 запросов в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/createContentSizeTables.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/size-tables/create
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
    "sizeTables": [
      {
        "sizeParameterId": 1,
        "sizeTableName": "example",
        "rows": [
          {
            "values": [
              null
            ]
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
  
  _sizeTables_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CreateSizeTableDTO](#entity-CreateSizeTableDTO)[]
  
  Таблицы размеров. Обрабатываются по порядку, каждая независимо от остальных.
  
  Суммарно во всех таблицах — не больше 5000 ячеек. Если ячеек больше, запрос не обрабатывается.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `10`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeParameterId": 1,
      "sizeTableName": "example",
      "rows": [
        {
          "values": [
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
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeTableCellDTO {#entity-SizeTableCellDTO}
  
  Ячейка таблицы размеров: значение размера в размерной сетке или значение обмера.
  
  Укажите колонку в `sizeChartId`, `sizeChartName` или в обоих полях, а значение — в `sizeValueId`, `sizeValue`
  или в обоих полях. Ячейка, в которой нет ни `sizeChartId`, ни `sizeChartName` или ни `sizeValueId`,
  ни `sizeValue`, — ошибка `INVALID_REQUEST`.
  
  Колонка по `sizeChartName` ищется среди размерных сеток и обмеров размерной характеристики таблицы
  из ответа метода `POST v2/businesses/{businessId}/size-tables/charts`: название сравнивается без учета регистра
  и пробелов в начале и в конце. Если название совпадает с несколькими колонками или ни с одной, возвращается
  ошибка `UNKNOWN_SIZE_CHART`. Переданный вместе с `sizeChartId` параметр `sizeChartName` должен совпадать
  с названием этой колонки, иначе вернется ошибка `INVALID_REQUEST`.
  
  Как обрабатывается значение:
  
  * Если передан `sizeValueId`, он должен быть из справочника этой размерной сетки (`sizeValues` в ответе метода
    `POST v2/businesses/{businessId}/size-tables/charts`). Сохраняется текст значения из справочника.
    Переданный вместе с `sizeValueId` параметр `sizeValue` должен совпадать с этим текстом без учета регистра
    и пробелов в начале и в конце.
  * Если передан только `sizeValue`, из него удаляются пробелы в начале и в конце, а затем:
    * пустое значение сохраняется как «нет значения»;
    * «нет значения» принимается в любой колонке и сохраняется как `—`;
    * в колонке со справочником значение сравнивается со справочником без учета регистра — если совпадает
      ровно одно значение, сохраняется оно с текстом из справочника;
    * в колонке без справочника сохраняется переданный текст не длиннее 20 символов, а в обмерах запятые
      заменяются точками: `42,5` → `42.5`.
  
  Если значение не подходит колонке, возвращается ошибка `INVALID_SIZE_VALUE`.
  
  {% cut "Какие значения считаются «нет значения»" %}
  
  Значение целиком, без учета регистра: `Нет`, `Пусто`, `Нет значения`, `Не соответствует`, `Нет подходящего`,
  `Отсутствует`, `Неприменимо`, `Без значения` или один либо несколько символов `-`, `‐`, `‑`, `‒`, `–`, `—`, `―`.
  Знак минуса `−` к ним не относится.
  
  В обязательной размерной сетке такое значение, как и пустое значение или непереданная ячейка, — ошибка `EMPTY_CELL`.
  
  {% endcut %}
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _sizeChartId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор размерной сетки или обмера из ответа метода `POST v2/businesses/{businessId}/size-tables/charts`.
  У сеток и обмеров общее пространство идентификаторов. Обязателен, если не передан `sizeChartName`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _sizeChartName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название размерной сетки или обмера из ответа метода `POST v2/businesses/{businessId}/size-tables/charts`.
  Сравнивается без учета регистра и пробелов в начале и в конце. Обязательно, если не передан `sizeChartId`.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _sizeValue_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Значение размера или обмера. В колонках без справочника — не длиннее 20 символов.
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _sizeValueId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения из справочника размерной сетки. Справочник есть только у стандартных размерных сеток Маркета.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeChartId": 1,
    "sizeChartName": "example",
    "sizeValueId": 1,
    "sizeValue": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeTableRowDTO {#entity-SizeTableRowDTO}
  
  Строка таблицы размеров — один размер во всех размерных сетках и обмерах таблицы.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _values_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeTableCellDTO](#entity-SizeTableCellDTO)[]
  
  Ячейки строки в любом порядке. Каждая размерная сетка или обмер — не больше одного раза в строке,
  иначе вернется ошибка `INVALID_REQUEST`.
  
  Ячейку без значения можно не передавать или передать с пустым `sizeValue`: она сохранится
  как «нет значения». В обязательной размерной сетке это ошибка `EMPTY_CELL`.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeChartId": 1,
      "sizeChartName": "example",
      "sizeValueId": 1,
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
    "values": [
      {
        "sizeChartId": 1,
        "sizeChartName": "example",
        "sizeValueId": 1,
        "sizeValue": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CreateSizeTableDTO {#entity-CreateSizeTableDTO}
  
  Новая таблица размеров.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _rows_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeTableRowDTO](#entity-SizeTableRowDTO)[]
  
  Строки таблицы: каждая описывает один размер. При сохранении порядок строк может измениться.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `200`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "values": [
        {
          "sizeChartId": 1,
          "sizeChartName": "example",
          "sizeValueId": 1,
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
  
  Идентификатор размерной характеристики, к которой относятся размеры из таблицы.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _sizeTableName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название таблицы размеров. Пробелы в начале и в конце удаляются. Название из одних пробелов —
  ошибка `INVALID_REQUEST`.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `256`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeParameterId": 1,
    "sizeTableName": "example",
    "rows": [
      {
        "values": [
          {
            "sizeChartId": 1,
            "sizeChartName": "example",
            "sizeValueId": 1,
            "sizeValue": "example"
          }
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Результаты создания таблиц в порядке запроса.
  
  Если хотя бы одну таблицу не удалось создать, поле `status` принимает значение `ERROR`.
  Остальные таблицы при этом обрабатываются и сохраняются.
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "results": [
        {
          "sizeTableId": 0,
          "sizeTableName": "example",
          "errors": [
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
    **Type**: [SaveSizeTablesResultDTO](#entity-SaveSizeTablesResultDTO)
  
    Результаты сохранения таблиц размеров.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "results": [
        {
          "sizeTableId": 0,
          "sizeTableName": "example",
          "errors": [
            {
              "code": "INVALID_REQUEST",
              "rowIndex": 0,
              "sizeChartId": 0,
              "sizeChartIds": [
                null
              ],
              "sizeChartNames": [
                null
              ],
              "rowIndices": [
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
        "results": [
          {
            "sizeTableId": 0,
            "sizeTableName": "example",
            "errors": [
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
  
  ### SizeTableErrorCodeType {#entity-SizeTableErrorCodeType}
  
  Код ошибки сохранения таблицы размеров:
  
  * `INVALID_REQUEST` — нарушена структура таблицы: название из одних пробелов, ячейка без `sizeChartId`
    и `sizeChartName` (`rowIndex`), повтор колонки в строке, ячейка без `sizeValueId` и `sizeValue` или ячейка,
    в которой `sizeChartName` не совпадает с названием колонки `sizeChartId` (`rowIndex`, `sizeChartId`).
  * `UNKNOWN_SIZE_CHART` — размерных сеток или обмеров из `sizeChartIds` нет среди доступных
    для размерной характеристики таблицы, а названиям из `sizeChartNames` не нашлось ровно одной такой колонки.
  * `INVALID_SIZE_VALUE` — значение не подходит колонке (`rowIndex`, `sizeChartId`).
  * `EMPTY_TABLE` — в таблице нет ни одной ячейки. Для запросов, которые соответствуют схеме, не возвращается.
    Если в колонке только «нет значения», возвращается `NONE_COLUMN`.
  * `EMPTY_CELL` — не заполнена ячейка обязательной размерной сетки (`rowIndex`, `sizeChartId`).
  * `NONE_COLUMN` — в колонках из `sizeChartIds` нет ни одного значения, кроме «нет значения».
  * `DUPLICATE_ROWS` — строки из `rowIndices` совпадают.
  * `DUPLICATE_SIZES` — значения повторяются в размерных сетках из `sizeChartIds`. Зависит от размерной
    характеристики: для одних характеристик ошибка возвращается при повторах в любой сетке, для других —
    только если повторы есть во всех сетках таблицы.
  * `DUPLICATE_MEASURES` — значения повторяются в обмерах из `sizeChartIds`. Зависит от размерной
    характеристики: для некоторых характеристик повторы в обмерах допускаются.
  * `ABSENT_MANDATORY_SIZE_CHART` — в таблице нет обязательной размерной сетки.
  * `LIMIT_TABLES` — у бизнеса уже максимальное количество таблиц. Только при создании.
  * `NOT_FOUND` — таблицы нет. Только при обновлении.
  * `FORBIDDEN` — это таблица Маркета (`sizeTableType: STANDARD`), ее нельзя изменить. Только при обновлении.
  * `CONCURRENT_MODIFICATION` — таблицу изменили во время обработки запроса. Повторите запрос. Только при обновлении.
  * `INTERNAL_ERROR` — внутренняя ошибка, таблица не сохранена.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `INVALID_REQUEST`, `UNKNOWN_SIZE_CHART`, `INVALID_SIZE_VALUE`, `EMPTY_TABLE`, `EMPTY_CELL`, `NONE_COLUMN`, `DUPLICATE_ROWS`, `DUPLICATE_SIZES`, `DUPLICATE_MEASURES`, `ABSENT_MANDATORY_SIZE_CHART`, `LIMIT_TABLES`, `NOT_FOUND`, `FORBIDDEN`, `CONCURRENT_MODIFICATION`, `INTERNAL_ERROR`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SizeTableErrorDTO {#entity-SizeTableErrorDTO}
  
  Ошибка сохранения таблицы размеров. Место ошибки указывают поля `rowIndex`, `sizeChartId`, `sizeChartIds`,
  `sizeChartNames` и `rowIndices`: какие из них возвращаются, зависит от кода ошибки.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SizeTableErrorCodeType](#entity-SizeTableErrorCodeType)
  
  Код ошибки сохранения таблицы размеров:
  
  * `INVALID_REQUEST` — нарушена структура таблицы: название из одних пробелов, ячейка без `sizeChartId`
    и `sizeChartName` (`rowIndex`), повтор колонки в строке, ячейка без `sizeValueId` и `sizeValue` или ячейка,
    в которой `sizeChartName` не совпадает с названием колонки `sizeChartId` (`rowIndex`, `sizeChartId`).
  * `UNKNOWN_SIZE_CHART` — размерных сеток или обмеров из `sizeChartIds` нет среди доступных
    для размерной характеристики таблицы, а названиям из `sizeChartNames` не нашлось ровно одной такой колонки.
  * `INVALID_SIZE_VALUE` — значение не подходит колонке (`rowIndex`, `sizeChartId`).
  * `EMPTY_TABLE` — в таблице нет ни одной ячейки. Для запросов, которые соответствуют схеме, не возвращается.
    Если в колонке только «нет значения», возвращается `NONE_COLUMN`.
  * `EMPTY_CELL` — не заполнена ячейка обязательной размерной сетки (`rowIndex`, `sizeChartId`).
  * `NONE_COLUMN` — в колонках из `sizeChartIds` нет ни одного значения, кроме «нет значения».
  * `DUPLICATE_ROWS` — строки из `rowIndices` совпадают.
  * `DUPLICATE_SIZES` — значения повторяются в размерных сетках из `sizeChartIds`. Зависит от размерной
    характеристики: для одних характеристик ошибка возвращается при повторах в любой сетке, для других —
    только если повторы есть во всех сетках таблицы.
  * `DUPLICATE_MEASURES` — значения повторяются в обмерах из `sizeChartIds`. Зависит от размерной
    характеристики: для некоторых характеристик повторы в обмерах допускаются.
  * `ABSENT_MANDATORY_SIZE_CHART` — в таблице нет обязательной размерной сетки.
  * `LIMIT_TABLES` — у бизнеса уже максимальное количество таблиц. Только при создании.
  * `NOT_FOUND` — таблицы нет. Только при обновлении.
  * `FORBIDDEN` — это таблица Маркета (`sizeTableType: STANDARD`), ее нельзя изменить. Только при обновлении.
  * `CONCURRENT_MODIFICATION` — таблицу изменили во время обработки запроса. Повторите запрос. Только при обновлении.
  * `INTERNAL_ERROR` — внутренняя ошибка, таблица не сохранена.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `INVALID_REQUEST`, `UNKNOWN_SIZE_CHART`, `INVALID_SIZE_VALUE`, `EMPTY_TABLE`, `EMPTY_CELL`, `NONE_COLUMN`, `DUPLICATE_ROWS`, `DUPLICATE_SIZES`, `DUPLICATE_MEASURES`, `ABSENT_MANDATORY_SIZE_CHART`, `LIMIT_TABLES`, `NOT_FOUND`, `FORBIDDEN`, `CONCURRENT_MODIFICATION`, `INTERNAL_ERROR`
  {.table-cell}
  ||
  ||
  
  _rowIndex_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Номер строки с ошибкой в `rows` запроса, начиная с 0. Может не совпадать с `rowIndex` сохраненной таблицы.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _rowIndices_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Номера совпадающих строк в `rows` запроса, начиная с 0.
  
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
  ||
  
  _sizeChartId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор размерной сетки или обмера, в колонке которого ошибка.
  {.table-cell}
  ||
  ||
  
  _sizeChartIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Идентификаторы размерных сеток и обмеров, в колонках которых ошибка.
  
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
  ||
  
  _sizeChartNames_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Названия колонок из `sizeChartName` запроса, которым не нашлось ровно одной размерной сетки или обмера.
  
  
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
    "code": "INVALID_REQUEST",
    "rowIndex": 0,
    "sizeChartId": 0,
    "sizeChartIds": [
      0
    ],
    "sizeChartNames": [
      "example"
    ],
    "rowIndices": [
      0
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SaveSizeTableResultDTO {#entity-SaveSizeTableResultDTO}
  
  Результат сохранения таблицы размеров. Если таблица сохранена, возвращаются `sizeTableId` и `sizeTableName`,
  если нет — только `errors`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _errors_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SizeTableErrorDTO](#entity-SizeTableErrorDTO)[] &#124; null
  
  Ошибки, из-за которых таблица не сохранена.
  
  Сначала проверяются структура таблицы, ее колонки и значения ячеек — ошибки `INVALID_REQUEST`,
  `UNKNOWN_SIZE_CHART` и `INVALID_SIZE_VALUE`. Если они есть, остальные проверки не выполняются,
  поэтому после исправления могут вернуться другие ошибки.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "code": "INVALID_REQUEST",
      "rowIndex": 0,
      "sizeChartId": 0,
      "sizeChartIds": [
        0
      ],
      "sizeChartNames": [
        "example"
      ],
      "rowIndices": [
        0
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _sizeTableId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор сохраненной таблицы размеров.
  {.table-cell}
  ||
  ||
  
  _sizeTableName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название сохраненной таблицы размеров.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "sizeTableId": 0,
    "sizeTableName": "example",
    "errors": [
      {
        "code": "INVALID_REQUEST",
        "rowIndex": 0,
        "sizeChartId": 0,
        "sizeChartIds": [
          0
        ],
        "sizeChartNames": [
          "example"
        ],
        "rowIndices": [
          0
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SaveSizeTablesResultDTO {#entity-SaveSizeTablesResultDTO}
  
  Результаты сохранения таблиц размеров.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _results_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SaveSizeTableResultDTO](#entity-SaveSizeTableResultDTO)[]
  
  Результаты по таблицам из запроса в том же порядке: `results[i]` относится к `sizeTables[i]`.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "sizeTableId": 0,
      "sizeTableName": "example",
      "errors": [
        {
          "code": "INVALID_REQUEST",
          "rowIndex": 0,
          "sizeChartId": 0,
          "sizeChartIds": [
            0
          ],
          "sizeChartNames": [
            "example"
          ],
          "rowIndices": [
            0
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
    "results": [
      {
        "sizeTableId": 0,
        "sizeTableName": "example",
        "errors": [
          {
            "code": "INVALID_REQUEST",
            "rowIndex": 0,
            "sizeChartId": 0,
            "sizeChartIds": [
              null
            ],
            "sizeChartNames": [
              null
            ],
            "rowIndices": [
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
  
  Запрос содержит неправильные данные, ни одна таблица не создается. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#400)
  
  Коды ошибок:
  
  * `BAD_REQUEST` — запрос не соответствует описанию метода: например, превышено количество таблиц, строк или ячеек.
  * `UNKNOWN_SIZE_PARAMETER` — у одной из таблиц `sizeParameterId` не из списка допустимых значений.
  
  
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
      "sizeTables": [
        {
          "sizeParameterId": 1,
          "sizeTableName": "example",
          "rows": [
            {
              "values": [
                null
              ]
            }
          ]
        }
      ]
    }
  schema:
    description: Таблицы размеров для создания.
    type: object
    required:
      - sizeTables
    properties:
      sizeTables:
        description: >
          Таблицы размеров. Обрабатываются по порядку, каждая независимо от
          остальных.
  
  
          Суммарно во всех таблицах — не больше 5000 ячеек. Если ячеек больше,
          запрос не обрабатывается.
        type: array
        minItems: 1
        maxItems: 10
        items:
          description: Новая таблица размеров.
          type: object
          required:
            - sizeParameterId
            - sizeTableName
            - rows
          properties:
            sizeParameterId:
              description: >
                Идентификатор размерной характеристики, к которой относятся
                размеры из таблицы.
              type: integer
              format: int64
              minimum: 1
            sizeTableName:
              description: >
                Название таблицы размеров. Пробелы в начале и в конце удаляются.
                Название из одних пробелов —
  
                ошибка `INVALID_REQUEST`.
              type: string
              minLength: 1
              maxLength: 256
            rows:
              description: >
                Строки таблицы: каждая описывает один размер. При сохранении
                порядок строк может измениться.
              type: array
              minItems: 1
              maxItems: 200
              items:
                description: >-
                  Строка таблицы размеров — один размер во всех размерных сетках и
                  обмерах таблицы.
                type: object
                required:
                  - values
                properties:
                  values:
                    description: >
                      Ячейки строки в любом порядке. Каждая размерная сетка или
                      обмер — не больше одного раза в строке,
  
                      иначе вернется ошибка `INVALID_REQUEST`.
  
  
                      Ячейку без значения можно не передавать или передать с
                      пустым `sizeValue`: она сохранится
  
                      как «нет значения». В обязательной размерной сетке это
                      ошибка `EMPTY_CELL`.
                    type: array
                    minItems: 1
                    maxItems: 50
                    items:
                      description: >
                        Ячейка таблицы размеров: значение размера в размерной
                        сетке или значение обмера.
  
  
                        Укажите колонку в `sizeChartId`, `sizeChartName` или в
                        обоих полях, а значение — в `sizeValueId`, `sizeValue`
  
                        или в обоих полях. Ячейка, в которой нет ни `sizeChartId`,
                        ни `sizeChartName` или ни `sizeValueId`,
  
                        ни `sizeValue`, — ошибка `INVALID_REQUEST`.
  
  
                        Колонка по `sizeChartName` ищется среди размерных сеток и
                        обмеров размерной характеристики таблицы
  
                        из ответа метода `POST
                        v2/businesses/{businessId}/size-tables/charts`: название
                        сравнивается без учета регистра
  
                        и пробелов в начале и в конце. Если название совпадает с
                        несколькими колонками или ни с одной, возвращается
  
                        ошибка `UNKNOWN_SIZE_CHART`. Переданный вместе с
                        `sizeChartId` параметр `sizeChartName` должен совпадать
  
                        с названием этой колонки, иначе вернется ошибка
                        `INVALID_REQUEST`.
  
  
                        Как обрабатывается значение:
  
  
                        * Если передан `sizeValueId`, он должен быть из
                        справочника этой размерной сетки (`sizeValues` в ответе
                        метода
                          `POST v2/businesses/{businessId}/size-tables/charts`). Сохраняется текст значения из справочника.
                          Переданный вместе с `sizeValueId` параметр `sizeValue` должен совпадать с этим текстом без учета регистра
                          и пробелов в начале и в конце.
                        * Если передан только `sizeValue`, из него удаляются
                        пробелы в начале и в конце, а затем:
                          * пустое значение сохраняется как «нет значения»;
                          * «нет значения» принимается в любой колонке и сохраняется как `—`;
                          * в колонке со справочником значение сравнивается со справочником без учета регистра — если совпадает
                            ровно одно значение, сохраняется оно с текстом из справочника;
                          * в колонке без справочника сохраняется переданный текст не длиннее 20 символов, а в обмерах запятые
                            заменяются точками: `42,5` → `42.5`.
  
                        Если значение не подходит колонке, возвращается ошибка
                        `INVALID_SIZE_VALUE`.
  
  
                        {% cut "Какие значения считаются «нет значения»" %}
  
  
                        Значение целиком, без учета регистра: `Нет`, `Пусто`, `Нет
                        значения`, `Не соответствует`, `Нет подходящего`,
  
                        `Отсутствует`, `Неприменимо`, `Без значения` или один либо
                        несколько символов `-`, `‐`, `‑`, `‒`, `–`, `—`, `―`.
  
                        Знак минуса `−` к ним не относится.
  
  
                        В обязательной размерной сетке такое значение, как и
                        пустое значение или непереданная ячейка, — ошибка
                        `EMPTY_CELL`.
  
  
                        {% endcut %}
                      type: object
                      properties:
                        sizeChartId:
                          description: >
                            Идентификатор размерной сетки или обмера из ответа
                            метода `POST
                            v2/businesses/{businessId}/size-tables/charts`.
  
                            У сеток и обмеров общее пространство идентификаторов.
                            Обязателен, если не передан `sizeChartName`.
                          type: integer
                          format: int64
                          minimum: 1
                        sizeChartName:
                          description: >
                            Название размерной сетки или обмера из ответа метода
                            `POST v2/businesses/{businessId}/size-tables/charts`.
  
                            Сравнивается без учета регистра и пробелов в начале и
                            в конце. Обязательно, если не передан `sizeChartId`.
                          type: string
                          minLength: 1
                          maxLength: 255
                        sizeValueId:
                          description: >
                            Идентификатор значения из справочника размерной сетки.
                            Справочник есть только у стандартных размерных сеток
                            Маркета.
                          type: integer
                          format: int64
                          minimum: 1
                        sizeValue:
                          description: >
                            Значение размера или обмера. В колонках без
                            справочника — не длиннее 20 символов.
                          type: string
                          maxLength: 255
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
  path: v2/businesses/{businessId}/size-tables/create
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/content/createContentSizeTables.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
