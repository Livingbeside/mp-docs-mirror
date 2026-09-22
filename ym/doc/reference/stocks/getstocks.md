---
title: Просмотр остатков и оборачиваемости
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md"
fetched_at: "2026-09-22T02:26:52Z"
content_sha: 66f3edd46378f08b
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/stocks/getStocks.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/stocks/getStocks.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/stocks/getStocks.md -->
<div class="openapi">

# Информация об остатках и оборачиваемости

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getStocks.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getStocks.md -->
  
  Возвращает данные об остатках товаров (для всех моделей) и об [оборачиваемости](*turnover) товаров (для модели FBY).
  
  {% note warning "Когда использовать этот метод" %}
  
  Метод актуален:
  
  * для моделей FBY и LaaS;
  * для моделей FBS, DBS и Экспресс, если в кабинете есть группы складов.
  
  Если в кабинете нет групп складов и вы работаете с моделями FBS, DBS или Экспресс, используйте метод [POST v3/businesses/{businessId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md). [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks).
  
  {% endnote %}
  
  {% note info "По умолчанию данные по оборачивамости не возращаются" %}
  
  Чтобы они были в ответе, передавайте `true` в поле `withTurnover`.
  
  {% endnote %}
  
  **Для моделей FBY и LaaS:** информация об остатках может возвращаться с нескольких складов Маркета, у которых будут разные `warehouseId`. Получить список складов Маркета можно с помощью метода [GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md).
  
  **Для модели FBS:** в ответе может вернуться не только партнерский склад, но и склад возвратов Маркета. Это возможно, если возврат поступил в указанную продавцом точку возвратов и долго не был забран.
  
  <!-- source: ru/_auto/method_limits/getStocks.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 000 товаров в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getStocks.md -->
  
  [//]: <> (turnover: Среднее количество дней, за которое товар продается. Подробно об оборачиваемости рассказано в Справке Маркета для продавцов https://yandex.ru/support/marketplace/analytics/turnover.html.)
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/offers/stocks
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
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _limit_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество значений на одной странице. <br><br> Если значение параметра превышает максимально допустимое, оно будет уменьшено до максимума.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `50`
  
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
    "stocksWarehouseId": 1,
    "hasStocks": true,
    "withTurnover": false,
    "archived": true,
    "offerIds": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _archived_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Фильтр по нахождению в архиве.
  
  Передайте `true`, чтобы получить информацию об остатках товаров, которые находятся в архиве. Если фильтр не заполнен или передано `false`, в ответе возвращается информация о товарах, которые не находятся в архиве.
  
  {.table-cell}
  ||
  ||
  
  _hasStocks_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  **Только для моделей FBY и LaaS**
  
  Фильтр по наличию товаров. Используйте только вместе со `stocksWarehouseId`.
  
  Передайте `false`, чтобы получить информацию о товарах, которых нет в наличие. При значении `true` возвращаются данные о товарах, которые есть на указанном складе.
  
  {.table-cell}
  ||
  ||
  
  _offerIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)[] &#124; null
  
  Фильтр по вашим SKU товаров.
  
  Возвращается информация об остатках всех переданных SKU, включая товары в архиве.
  
  {% note warning "Такой список возвращается только целиком" %}
  
  Если вы запрашиваете информацию по конкретным SKU, не заполняйте:
  
  * `pageToken`
  * `limit`
  * `archived`
  * `stocksOnWarehouse`
  
  {% endnote %}
  
   
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `500`
  
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
  
  _stocksWarehouseId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада.
  
  Если параметр указан, возвращаются только товары на переданном складе.
  
  **Для моделей FBY и LaaS:** получить список складов Маркета можно с помощью метода [GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _withTurnover_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  **Только для моделей FBY и LaaS**
  
  Возвращать ли информацию по оборачиваемости.
  
  Значение по умолчанию: `false`. Если информация нужна, передайте значение `true`.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `false`
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
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Остатки товаров на складах.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "paging": {
        "nextPageToken": "example"
      },
      "warehouses": [
        {
          "warehouseId": 0,
          "offers": [
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
    **Type**: [GetWarehouseStocksDTO](#entity-GetWarehouseStocksDTO)
  
    Список складов с информацией об остатках на каждом из них.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "paging": {
        "nextPageToken": "example"
      },
      "warehouses": [
        {
          "warehouseId": 0,
          "offers": [
            {
              "offerId": "example",
              "turnoverSummary": {},
              "stocks": [
                null
              ],
              "updatedAt": "2025-01-01T00:00:00Z"
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
        "paging": {
          "nextPageToken": "example"
        },
        "warehouses": [
          {
            "warehouseId": 0,
            "offers": [
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
  
  ### TurnoverType {#entity-TurnoverType}
  
  Оценка оборачиваемости.
  
  |enum|Диапазон оборачиваемости|Комментарий|
  |-|-|-|
  |`LOW`|`turnoverDays` ≥ 120||
  |`ALMOST_LOW`|100 ≤ `turnoverDays` < 120||
  |`HIGH`|45 ≤ `turnoverDays` < 100||
  |`VERY_HIGH`|0 ≤ `turnoverDays` < 45||
  |`NO_SALES`|—|Продаж нет.|
  |`FREE_STORE`|Любое значение.|Платить за хранение товаров этой категории не требуется.|
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `LOW`, `ALMOST_LOW`, `HIGH`, `VERY_HIGH`, `NO_SALES`, `FREE_STORE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### TurnoverDTO {#entity-TurnoverDTO}
  
  Информация об оборачиваемости товара.
  
  Подробнее о хранении и оборачиваемости товаров читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/storage/logistics#turnover).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _turnover_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TurnoverType](#entity-TurnoverType)
  
  Оценка оборачиваемости.
  
  Оценка оборачиваемости.
  
  &#124;enum&#124;Диапазон оборачиваемости&#124;Комментарий&#124;
  &#124;-&#124;-&#124;-&#124;
  &#124;`LOW`&#124;`turnoverDays` ≥ 120&#124;&#124;
  &#124;`ALMOST_LOW`&#124;100 ≤ `turnoverDays` < 120&#124;&#124;
  &#124;`HIGH`&#124;45 ≤ `turnoverDays` < 100&#124;&#124;
  &#124;`VERY_HIGH`&#124;0 ≤ `turnoverDays` < 45&#124;&#124;
  &#124;`NO_SALES`&#124;—&#124;Продаж нет.&#124;
  &#124;`FREE_STORE`&#124;Любое значение.&#124;Платить за хранение товаров этой категории не требуется.&#124;
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `LOW`, `ALMOST_LOW`, `HIGH`, `VERY_HIGH`, `NO_SALES`, `FREE_STORE`
  {.table-cell}
  ||
  ||
  
  _turnoverDays_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Значение в днях.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "turnover": "LOW",
    "turnoverDays": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseStockType {#entity-WarehouseStockType}
  
  Тип остатков товаров на складе:
  
  * `AVAILABLE` (соответствует типу «Доступный к заказу» в отчете «Остатки на складе» в кабинете продавца на Маркете) — товар, доступный для продажи.
  
  * `DEFECT` (соответствует типу «Брак») — товар с браком.
  
  * `EXPIRED` (соответствует типу «Просрочен») — товар с истекшим сроком годности.
  
  * `FIT` (соответствует типу «Годный») — товар, который доступен для продажи или уже зарезервирован.
  
  * `FREEZE` — товар, который зарезервирован для заказов.
  
  * `QUARANTINE` (соответствует типу «Карантин») — товар, временно недоступный для продажи (например, товар перемещают из одного помещения склада в другое).
  
  * `UTILIZATION` — товар, который будет утилизирован.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `FREEZE`, `AVAILABLE`, `QUARANTINE`, `UTILIZATION`, `DEFECT`, `EXPIRED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseStockDTO {#entity-WarehouseStockDTO}
  
  Информация об остатках товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Значение остатков.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseStockType](#entity-WarehouseStockType)
  
  Тип остатков.
  
  Тип остатков товаров на складе:
  
  * `AVAILABLE` (соответствует типу «Доступный к заказу» в отчете «Остатки на складе» в кабинете продавца на Маркете) — товар, доступный для продажи.
  
  * `DEFECT` (соответствует типу «Брак») — товар с браком.
  
  * `EXPIRED` (соответствует типу «Просрочен») — товар с истекшим сроком годности.
  
  * `FIT` (соответствует типу «Годный») — товар, который доступен для продажи или уже зарезервирован.
  
  * `FREEZE` — товар, который зарезервирован для заказов.
  
  * `QUARANTINE` (соответствует типу «Карантин») — товар, временно недоступный для продажи (например, товар перемещают из одного помещения склада в другое).
  
  * `UTILIZATION` — товар, который будет утилизирован.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `FREEZE`, `AVAILABLE`, `QUARANTINE`, `UTILIZATION`, `DEFECT`, `EXPIRED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "FIT",
    "count": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseOfferDTO {#entity-WarehouseOfferDTO}
  
  Информация об остатках товара.
  
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
  
  _stocks_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseStockDTO](#entity-WarehouseStockDTO)[]
  
  Информация об остатках.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "FIT",
      "count": 0
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _turnoverSummary_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TurnoverDTO](#entity-TurnoverDTO)
  
  Информация об оборачиваемости.
  
  Информация об оборачиваемости товара.
  
  Подробнее о хранении и оборачиваемости товаров читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/storage/logistics#turnover).
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "turnover": "LOW",
    "turnoverDays": 0.5
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время последнего обновления информации об остатках.
  
  Формат даты и времени: ISO 8601 со смещением относительно UTC. Например, `2023-11-21T00:42:42+03:00`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "turnoverSummary": {
      "turnover": "LOW",
      "turnoverDays": 0.5
    },
    "stocks": [
      {
        "type": "FIT",
        "count": 0
      }
    ],
    "updatedAt": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### WarehouseOffersDTO {#entity-WarehouseOffersDTO}
  
  Информация об остатках товаров на складе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offers_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseOfferDTO](#entity-WarehouseOfferDTO)[]
  
  Информация об остатках.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offerId": "example",
      "turnoverSummary": {
        "turnover": "LOW",
        "turnoverDays": 0.5
      },
      "stocks": [
        {
          "type": "FIT",
          "count": 0
        }
      ],
      "updatedAt": "2025-01-01T00:00:00Z"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warehouseId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада.
  
  **Для моделей FBY и LaaS:** возвращается идентификатор склада Маркета.
  
  **Для модели FBS:** может возвращаться идентификатор как партнерского склада, так и склада возвратов Маркета.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "warehouseId": 0,
    "offers": [
      {
        "offerId": "example",
        "turnoverSummary": {
          "turnover": "LOW",
          "turnoverDays": 0.5
        },
        "stocks": [
          {
            "type": "FIT",
            "count": 0
          }
        ],
        "updatedAt": "2025-01-01T00:00:00Z"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetWarehouseStocksDTO {#entity-GetWarehouseStocksDTO}
  
  Список складов с информацией об остатках на каждом из них.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _warehouses_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [WarehouseOffersDTO](#entity-WarehouseOffersDTO)[]
  
  Страница списка складов.
  
  **Для моделей FBY и LaaS:** может содержать несколько складов Маркета.
  
  **Для модели FBS:** может содержать как партнерский склад, так и склад возвратов Маркета.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "warehouseId": 0,
      "offers": [
        {
          "offerId": "example",
          "turnoverSummary": {
            "turnover": "LOW",
            "turnoverDays": 0.5
          },
          "stocks": [
            {}
          ],
          "updatedAt": "2025-01-01T00:00:00Z"
        }
      ]
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
    "paging": {
      "nextPageToken": "example"
    },
    "warehouses": [
      {
        "warehouseId": 0,
        "offers": [
          {
            "offerId": "example",
            "turnoverSummary": {},
            "stocks": [
              null
            ],
            "updatedAt": "2025-01-01T00:00:00Z"
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
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с остатками](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#stocks)
  
  
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
        Количество значений на одной странице. <br><br> Если значение параметра превышает максимально допустимое, оно будет уменьшено до максимума.
      in: query
      required: false
      x-transform: truncateLimit
      schema:
        type: integer
        format: int32
        minimum: 1
        default: 50
        maximum: 100
  headers: []
  body: |-
    {
      "stocksWarehouseId": 1,
      "hasStocks": true,
      "withTurnover": false,
      "archived": true,
      "offerIds": [
        "example"
      ]
    }
  schema:
    description: |
      Фильтры для запроса остатков.
    type: object
    properties:
      stocksWarehouseId:
        description: "Идентификатор склада.\n\nЕсли параметр указан, возвращаются только товары на переданном складе.\n\n**Для моделей FBY и LaaS:** получить список складов Маркета можно с помощью метода [GET\_v2/warehouses](../../reference/warehouses/getFulfillmentWarehouses.md).\n"
        type: integer
        format: int64
        minimum: 1
      hasStocks:
        description: >
          **Только для моделей FBY и LaaS**
  
  
          Фильтр по наличию товаров. Используйте только вместе со
          `stocksWarehouseId`.
  
  
          Передайте `false`, чтобы получить информацию о товарах, которых нет в
          наличие. При значении `true` возвращаются данные о товарах, которые есть
          на указанном складе.
        type: boolean
      withTurnover:
        description: >
          **Только для моделей FBY и LaaS**
  
  
          Возвращать ли информацию по оборачиваемости.
  
  
          Значение по умолчанию: `false`. Если информация нужна, передайте
          значение `true`.
        type: boolean
        default: false
      archived:
        description: >
          Фильтр по нахождению в архиве.
  
  
          Передайте `true`, чтобы получить информацию об остатках товаров, которые
          находятся в архиве. Если фильтр не заполнен или передано `false`, в
          ответе возвращается информация о товарах, которые не находятся в архиве.
        type: boolean
      offerIds:
        description: "Фильтр по вашим SKU товаров.\n\nВозвращается информация об остатках всех переданных SKU, включая товары в архиве.\n\n{% note warning \"Такой список возвращается только целиком\" %}\n\nЕсли вы запрашиваете информацию по конкретным SKU, не заполняйте:\n\n* `pageToken`\n* `limit`\n* `archived`\n* `stocksOnWarehouse`\n\n{% endnote %}\n\n\_\n"
        type: array
        uniqueItems: true
        minItems: 1
        maxItems: 500
        nullable: true
        items:
          description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
          type: string
          pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
          x-transform: trim
          minLength: 1
          maxLength: 255
      fake:
        description: >
          Возвращать синтетические ненулевые остатки для тестирования интеграции.
          Только для моделей FBY и LaaS.
        type: boolean
        default: false
        x-hidden: true
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
  path: v2/campaigns/{campaignId}/offers/stocks
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/stocks/getStocks.md -->

[*turnover]:
Среднее количество дней, за которое товар продается. Подробно об оборачиваемости рассказано [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/analytics/turnover.html).

[*Deprecated]: No longer supported, please use an alternative and newer version.
