---
title: Передача кодов маркировки
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md"
fetched_at: "2026-09-04T01:58:32Z"
content_sha: ecb8a57b8549fdf7
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/provideOrderItemIdentifiers.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/provideOrderItemIdentifiers.md
  - href: ru/reference/orders/provideOrderItemIdentifiers.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/provideOrderItemIdentifiers.md -->
<div class="openapi">

# Передача кодов маркировки единиц товара

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/provideOrderItemIdentifiers.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/provideOrderItemIdentifiers.md -->
  
  {% note warning "Если вы работаете по модели FBS" %}
  
  Используйте метод [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
  
  {% endnote %}
  
  Передает Маркету коды маркировки для единиц товара в указанном заказе. Подробнее о работе с маркируемыми товарами читайте в [Справке продавца на Маркете](https://yandex.ru/support/marketplace/orders/cz.html).
  
  Маркировка товаров в системе [«Честный ЗНАК»](https://честныйзнак.рф/) **необязательна** для заказов от физических лиц, но **обязательна** для заказов от бизнеса.
  
  Для модели DBS коды маркировки в системе [«Честный ЗНАК»](https://честныйзнак.рф/) не проверяются в ГИС МТ — проверка выполняется только для моделей FBS и Экспресс.
  
  Принимаются коды следующих типов:
  
  * Коды в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  * УИН для ювелирных изделий.
  * РНПТ и ГТД для импортных прослеживаемых товаров.
  
  Для каждой позиции в заказе, требующей маркировки, нужно передать список кодов — по одному для каждой единицы товара. Например, если в заказе две пары тапочек и одна пара туфель, получится список из двух кодов для первой позиции и список из одного кода для второй.
  
  <!-- source: ru/_auto/method_limits/provideOrderItemIdentifiers.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/provideOrderItemIdentifiers.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-put);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  PUT {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/identifiers
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
  ||
  
  _orderId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "items": [
      {
        "id": 0,
        "instances": [
          {
            "cis": "example",
            "uin": "example",
            "rnpt": "example",
            "gtd": "example",
            "countryCode": "RU"
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
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemInstanceModificationDTO](#entity-OrderItemInstanceModificationDTO)[]
  
  Список позиций, требующих маркировки.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "instances": [
        {
          "cis": "example",
          "uin": "example",
          "rnpt": "example",
          "gtd": "example",
          "countryCode": "RU"
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
  
  ### Cis {#entity-Cis}
  
  [Код идентификации](*cis-regular-value) единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  {% note warning "Не экранируйте косую черту в коде символа-разделителя `\u001d`" %}
  
  ✅ `01030410947874432155Qbag!\u001d93Zjqw`
  
  ❌ `01030410947874432155Qbag!\\u001d93Zjqw`
  
  Косые черты и кавычки в других местах экранируйте по правилам JSON: `\\` и `\"`
  
  {% endnote %}
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CountryCode {#entity-CountryCode}
  
  Страна производства в формате ISO 3166-1 alpha-2. [Как получить](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^[A-Z]{2}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `RU`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BriefOrderItemInstanceDTO {#entity-BriefOrderItemInstanceDTO}
  
  Идентификатор единицы товара.
  
  Заполните только одно поле в зависимости от того, в какой системе маркирован товар.
  
  Подробно о работе с маркируемыми товарами читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/orders/cz.html).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _cis_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Cis](#entity-Cis)
  
  [Код идентификации](*cis-regular-value) единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  {% note warning "Не экранируйте косую черту в коде символа-разделителя `\u001d`" %}
  
  ✅ `01030410947874432155Qbag!\u001d93Zjqw`
  
  ❌ `01030410947874432155Qbag!\\u001d93Zjqw`
  
  Косые черты и кавычки в других местах экранируйте по правилам JSON: `\\` и `\"`
  
  {% endnote %}
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _countryCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CountryCode](#entity-CountryCode)
  
  Страна производства в формате ISO 3166-1 alpha-2. [Как получить](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^[A-Z]{2}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `RU`
  {.table-cell}
  ||
  ||
  
  _gtd_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Грузовая таможенная декларация.
  
  Представляет собой строку из трех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ.
  
  Первая часть — код таможни, которая зарегистрировала декларацию на ввезенные товары. Далее — дата и номер декларации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _rnpt_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Регистрационный номер партии товара.
  
  Представляет собой строку из четырех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ.
  
  Первая часть — код таможни, которая зарегистрировала декларацию на партию товара. Далее — дата, номер декларации и номер маркированного товара в декларации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _uin_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Уникальный идентификационный номер ювелирного изделия.
  
  Представляет собой число из 16 цифр.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "cis": "example",
    "uin": "example",
    "rnpt": "example",
    "gtd": "example",
    "countryCode": "RU"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemInstanceModificationDTO {#entity-OrderItemInstanceModificationDTO}
  
  Позиция в корзине, требующая маркировки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в заказе.
  
  Он приходит в ответе метода [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) — параметр `id` в `items`.
  
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BriefOrderItemInstanceDTO](#entity-BriefOrderItemInstanceDTO)[]
  
  Список кодов маркировки единиц товара.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "cis": "example",
      "uin": "example",
      "rnpt": "example",
      "gtd": "example",
      "countryCode": "RU"
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
    "id": 0,
    "instances": [
      {
        "cis": "example",
        "uin": "example",
        "rnpt": "example",
        "gtd": "example",
        "countryCode": "RU"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Ответ `200` обозначает, что коды успешно записались. Ответ содержит краткие сведения о промаркированных товарах.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "items": [
        {
          "id": 0,
          "vat": "NO_VAT",
          "count": 0,
          "price": 0.5,
          "offerName": "example",
          "offerId": "example",
          "instances": [
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
    **Type**: [OrderItemsModificationResultDTO](#entity-OrderItemsModificationResultDTO)
  
    Краткие сведения о промаркированных товарах. Параметр возвращается, если ответ `OK`.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "items": [
        {
          "id": 0,
          "vat": "NO_VAT",
          "count": 0,
          "price": 0.5,
          "offerName": "example",
          "offerId": "example",
          "instances": [
            {
              "cis": "example",
              "cisFull": "example",
              "uin": "example",
              "rnpt": "example",
              "gtd": "example",
              "countryCode": "RU"
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
        "items": [
          {
            "id": 0,
            "vat": "NO_VAT",
            "count": 0,
            "price": 0.5,
            "offerName": "example",
            "offerId": "example",
            "instances": [
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
  
  ### OrderVatType {#entity-OrderVatType}
  
  НДС на товар или доставку:
  
  * `NO_VAT` — НДС не облагается, используется только для отдельных видов услуг.
  
  * `VAT_0` — НДС 0%. Например, используется при продаже товаров, вывезенных в таможенной процедуре экспорта, или при оказании услуг по международной перевозке товаров.
  
  * `VAT_10` — НДС 10%. Например, используется при реализации отдельных продовольственных и медицинских товаров.
  
  * `VAT_10_110` — НДС 10/110. НДС 10%, применяется только при предоплате.
  
  * `VAT_20` — НДС 20%. Основной НДС с 2019 года до 1 января 2026 года.
  
  * `VAT_20_120` — НДС 20/120. НДС 20%, применяется только при предоплате.
  
  * `VAT_18` — НДС 18%. Основной НДС до 2019 года.
  
  * `VAT_18_118` — НДС 18/118. НДС использовался до 1 января 2019 года при предоплате.
  
  * `VAT_12` — НДС 12%. Используется только в Узбекистане.
  
  * `VAT_05` — НДС 5%. НДС для упрощенной системы налогообложения (УСН).
  
  * `VAT_07` — НДС 7%. НДС для упрощенной системы налогообложения (УСН).
  
  * `VAT_22` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  * `UNKNOWN_VALUE` — неизвестный тип.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `NO_VAT`, `VAT_0`, `VAT_10`, `VAT_10_110`, `VAT_20`, `VAT_20_120`, `VAT_18`, `VAT_18_118`, `VAT_12`, `VAT_05`, `VAT_07`, `VAT_22`, `UNKNOWN_VALUE`
  
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
  
  ### OrderItemInstanceDTO {#entity-OrderItemInstanceDTO}
  
  Переданные для данной позиции коды маркировки или УИНы. Коды «Честного знака» возвращаются в двух вариантах — с криптохвостом и без.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _cis_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Код идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) без криптохвоста или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _cisFull_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Код идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) с криптохвостом.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _countryCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CountryCode](#entity-CountryCode)
  
  Страна производства в формате ISO 3166-1 alpha-2. [Как получить](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^[A-Z]{2}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `RU`
  {.table-cell}
  ||
  ||
  
  _gtd_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Грузовая таможенная декларация.
  
  Представляет собой строку из трех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ.
  
  Первая часть — код таможни, которая зарегистрировала декларацию на ввезенные товары. Далее — дата и номер декларации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _rnpt_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Регистрационный номер партии товара.
  
  Представляет собой строку из четырех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ.
  
  Первая часть — код таможни, которая зарегистрировала декларацию на партию товара. Далее — дата, номер декларации и номер маркированного товара в декларации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _uin_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  УИН ювелирного изделия (16-значный код)
  Производитель получает УИН, когда регистрирует изделие в системе контроля за оборотом драгоценных металлов и камней — ГИИС ДМДК.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "cis": "example",
    "cisFull": "example",
    "uin": "example",
    "rnpt": "example",
    "gtd": "example",
    "countryCode": "RU"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BriefOrderItemDTO {#entity-BriefOrderItemDTO}
  
  Информация о маркированном товаре.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара.
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в заказе.
  
  Позволяет идентифицировать товар в рамках заказа.
  
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemInstanceDTO](#entity-OrderItemInstanceDTO)[] &#124; null
  
  Переданные коды маркировки.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "cis": "example",
      "cisFull": "example",
      "uin": "example",
      "rnpt": "example",
      "gtd": "example",
      "countryCode": "RU"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  Ваш идентификатор товара.
  
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
  
  _offerName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _price_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Цена товара. Указана в той валюте, которая была задана в каталоге. Разделитель целой и дробной части — точка.
  
  {.table-cell}
  ||
  ||
  
  _vat_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderVatType](#entity-OrderVatType)
  
  Налог на добавленную стоимость (НДС) на услугу доставки заказа.
  
  НДС на товар или доставку:
  
  * `NO_VAT` — НДС не облагается, используется только для отдельных видов услуг.
  
  * `VAT_0` — НДС 0%. Например, используется при продаже товаров, вывезенных в таможенной процедуре экспорта, или при оказании услуг по международной перевозке товаров.
  
  * `VAT_10` — НДС 10%. Например, используется при реализации отдельных продовольственных и медицинских товаров.
  
  * `VAT_10_110` — НДС 10/110. НДС 10%, применяется только при предоплате.
  
  * `VAT_20` — НДС 20%. Основной НДС с 2019 года до 1 января 2026 года.
  
  * `VAT_20_120` — НДС 20/120. НДС 20%, применяется только при предоплате.
  
  * `VAT_18` — НДС 18%. Основной НДС до 2019 года.
  
  * `VAT_18_118` — НДС 18/118. НДС использовался до 1 января 2019 года при предоплате.
  
  * `VAT_12` — НДС 12%. Используется только в Узбекистане.
  
  * `VAT_05` — НДС 5%. НДС для упрощенной системы налогообложения (УСН).
  
  * `VAT_07` — НДС 7%. НДС для упрощенной системы налогообложения (УСН).
  
  * `VAT_22` — НДС 22%. Основной НДС с 1 января 2026 года.
  
  * `UNKNOWN_VALUE` — неизвестный тип.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `NO_VAT`, `VAT_0`, `VAT_10`, `VAT_10_110`, `VAT_20`, `VAT_20_120`, `VAT_18`, `VAT_18_118`, `VAT_12`, `VAT_05`, `VAT_07`, `VAT_22`, `UNKNOWN_VALUE`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "vat": "NO_VAT",
    "count": 0,
    "price": 0.5,
    "offerName": "example",
    "offerId": "example",
    "instances": [
      {
        "cis": "example",
        "cisFull": "example",
        "uin": "example",
        "rnpt": "example",
        "gtd": "example",
        "countryCode": "RU"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemsModificationResultDTO {#entity-OrderItemsModificationResultDTO}
  
  Краткие сведения о промаркированных товарах. Параметр возвращается, если ответ `OK`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BriefOrderItemDTO](#entity-BriefOrderItemDTO)[]
  
  Список позиций в заказе, подлежащих маркировке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "vat": "NO_VAT",
      "count": 0,
      "price": 0.5,
      "offerName": "example",
      "offerId": "example",
      "instances": [
        {
          "cis": "example",
          "cisFull": "example",
          "uin": "example",
          "rnpt": "example",
          "gtd": "example",
          "countryCode": "RU"
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
    "items": [
      {
        "id": 0,
        "vat": "NO_VAT",
        "count": 0,
        "price": 0.5,
        "offerName": "example",
        "offerId": "example",
        "instances": [
          {
            "cis": "example",
            "cisFull": "example",
            "uin": "example",
            "rnpt": "example",
            "gtd": "example",
            "countryCode": "RU"
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
    - description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
      name: campaignId
      in: path
      required: true
      schema:
        type: integer
        format: int64
        minimum: 1
    - description: Идентификатор заказа.
      name: orderId
      in: path
      required: true
      schema:
        type: integer
        format: int64
  searchParams: []
  headers: []
  body: |-
    {
      "items": [
        {
          "id": 0,
          "instances": [
            {
              "cis": "example",
              "uin": "example",
              "rnpt": "example",
              "gtd": "example",
              "countryCode": "RU"
            }
          ]
        }
      ]
    }
  schema:
    type: object
    required:
      - items
    properties:
      items:
        description: |
          Список позиций, требующих маркировки.
        type: array
        items:
          description: Позиция в корзине, требующая маркировки.
          type: object
          required:
            - id
            - instances
          properties:
            id:
              description: "Идентификатор товара в заказе.\n\nОн приходит в ответе метода [POST\_v1/businesses/{businessId}/orders](../../reference/orders/getBusinessOrders.md) — параметр `id` в `items`.\n"
              type: integer
              format: int64
            instances:
              description: |
                Список кодов маркировки единиц товара.
              type: array
              items:
                description: >
                  Идентификатор единицы товара.
  
  
                  Заполните только одно поле в зависимости от того, в какой
                  системе маркирован товар.
  
  
                  Подробно о работе с маркируемыми товарами читайте [в Справке
                  Маркета для
                  продавцов](https://yandex.ru/support/marketplace/orders/cz.html).
                type: object
                properties:
                  cis:
                    description: >
                      [Код идентификации](*cis-regular-value) единицы товара в
                      системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL
                      BELGISI»](https://aslbelgisi.uz) (для продавцов Market
                      Yandex Go).
  
  
                      {% note warning "Не экранируйте косую черту в коде
                      символа-разделителя `\u001d`" %}
  
  
                      ✅ `01030410947874432155Qbag!\u001d93Zjqw`
  
  
                      ❌ `01030410947874432155Qbag!\\u001d93Zjqw`
  
  
                      Косые черты и кавычки в других местах экранируйте по
                      правилам JSON: `\\` и `\"`
  
  
                      {% endnote %}
                    type: string
                  uin:
                    description: |
                      Уникальный идентификационный номер ювелирного изделия.
  
                      Представляет собой число из 16 цифр.
                    type: string
                  rnpt:
                    description: >
                      Регистрационный номер партии товара.
  
  
                      Представляет собой строку из четырех чисел, разделенных
                      косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ.
  
  
                      Первая часть — код таможни, которая зарегистрировала
                      декларацию на партию товара. Далее — дата, номер декларации
                      и номер маркированного товара в декларации.
                    type: string
                  gtd:
                    description: >
                      Грузовая таможенная декларация.
  
  
                      Представляет собой строку из трех чисел, разделенных косой
                      чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ.
  
  
                      Первая часть — код таможни, которая зарегистрировала
                      декларацию на ввезенные товары. Далее — дата и номер
                      декларации.
                    type: string
                  countryCode:
                    description: >
                      Страна производства в формате ISO 3166-1 alpha-2. [Как
                      получить](../../reference/regions/getRegionsCodes.md)
                    type: string
                    minLength: 2
                    maxLength: 2
                    pattern: ^[A-Z]{2}$
                    example: RU
  bodyType: application/json
  method: put
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
  path: v2/campaigns/{campaignId}/orders/{orderId}/identifiers
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/provideOrderItemIdentifiers.md -->

[*cis-regular-value]:
Значение `cis` должно соответствовать регулярному выражению `^(?=.{1,256}$)\u001D?(\(?01\)?\d{14}\(?21\)?([!-~]{6,8}|[!-~]{13}|[!-~]{20})(\u001D\(?240\)?.{1,30})?\u001D\(?9[1,3]\)?.+)$`.<br><br>Без криптохвоста — `^(?=[!-~]{1,256}$)(\(?01\)?\d{14}\(?21\)?(.{6,8}|.{13}|.{20}))$`.

[*Deprecated]: No longer supported, please use an alternative and newer version.
