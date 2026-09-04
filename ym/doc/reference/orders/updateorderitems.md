---
title: Удаление товаров из заказа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md"
fetched_at: "2026-09-04T01:58:34Z"
content_sha: 17b3780ea90692cb
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/updateOrderItems.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/updateOrderItems.md
  - href: ru/reference/orders/updateOrderItems.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/updateOrderItems.md -->
<div class="openapi">

# Удаление товаров из заказа или уменьшение их числа

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateOrderItems.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateOrderItems.md -->
  
  {% note warning "Если вы работаете по модели FBS" %}
  
  Используйте метод [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
  
  {% endnote %}
  
  Удаляет один или несколько товаров из заказа, если магазин не может поставить их все.
  
  Заказ должен находится в статусе `"status": "PROCESSING"` этапа обработки `"substatus": "STARTED"`. Изменить состав нельзя после передачи статуса `"substatus": "READY_TO_SHIP"`.
  
  {% cut "Уменьшить количество одинаковых товаров" %}
  
  Передайте обновленное значение в параметре `count`.
  
  {% endcut %}
  
  {% cut "Удалить товар из заказа" %}
  
  Передайте значение `0` в параметре `count` или не передавайте `item`.
  
  {% endcut %}
  
  Нельзя удалить или уменьшить количество товара, если он:
  
  * добавлен по акции;
  * составляет 99% стоимости заказа;
  * единственный товар в заказе.
  
  В таком случае отмените заказ — в методе [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) передайте статус заказа `CANCELLED` с причиной отмены `SHOP_FAILED`.
  
  ### Как вернутся деньги {#money}
  
    Если покупатель оплатил товар при оформлении, Маркет вернет ему деньги за удаленные из заказа товары в течение двух дней:
  
    * при оплате банковской картой — с момента, когда магазин переведет заказ в статус `SHIPPED`;
  
    * при оплате через Apple Pay или Google Pay — с момента, когда магазин удалит товар из заказа.
  
  {% endcut %}
  
  <!-- source: ru/_auto/method_limits/updateOrderItems.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateOrderItems.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-put);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  PUT {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/items
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
        "count": 0,
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
    ],
    "reason": "PARTNER_REQUESTED_REMOVE"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemModificationDTO](#entity-OrderItemModificationDTO)[]
  
  Список товаров в заказе.
  
  Если магазин не передал информацию о товаре во входных данных, он будет удален из заказа.
  
  Обязательный параметр.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "count": 0,
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
  ||
  
  _reason_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemsModificationRequestReasonType](#entity-OrderItemsModificationRequestReasonType)
  
  Причина, почему обновился состав заказа:
  
  * `PARTNER_REQUESTED_REMOVE` — магазин удалил товар.
  * `USER_REQUESTED_REMOVE` — покупатель попросил удалить товар.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PARTNER_REQUESTED_REMOVE`, `USER_REQUESTED_REMOVE`
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
  
  ### OrderItemModificationDTO {#entity-OrderItemModificationDTO}
  
  Список товаров в заказе.
  
  Если магазин не передал информацию о товаре во входных данных, он будет удален из заказа.
  
  Обязательный параметр.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Новое количество товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в рамках заказа.
  
  Получить идентификатор можно с помощью метода:
  
  * [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md).
  
  Обязательный параметр.
  
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BriefOrderItemInstanceDTO](#entity-BriefOrderItemInstanceDTO)[] &#124; null
  
  Информация о маркировке единиц товара.
  
  Передавайте в запросе все единицы товара, который подлежит маркировке.
  
  Обязательный параметр, если в заказе от бизнеса есть товары, подлежащие маркировке в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
    "count": 0,
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
  
  <div class="openapi-entity">
  
  ### OrderItemsModificationRequestReasonType {#entity-OrderItemsModificationRequestReasonType}
  
  Причина, почему обновился состав заказа:
  
  * `PARTNER_REQUESTED_REMOVE` — магазин удалил товар.
  * `USER_REQUESTED_REMOVE` — покупатель попросил удалить товар.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PARTNER_REQUESTED_REMOVE`, `USER_REQUESTED_REMOVE`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Маркет успешно обработал ваш запрос. Выходные данные не ожидаются.
  
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
          "count": 0,
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
      ],
      "reason": "PARTNER_REQUESTED_REMOVE"
    }
  schema:
    description: Запрос на обновление состава заказа.
    type: object
    required:
      - items
    properties:
      items:
        description: >
          Список товаров в заказе.
  
  
          Если магазин не передал информацию о товаре во входных данных, он будет
          удален из заказа.
  
  
          Обязательный параметр.
        type: array
        minItems: 1
        items:
          description: >
            Список товаров в заказе.
  
  
            Если магазин не передал информацию о товаре во входных данных, он
            будет удален из заказа.
  
  
            Обязательный параметр.
          type: object
          properties:
            id:
              description: "Идентификатор товара в рамках заказа.\n\nПолучить идентификатор можно с помощью метода:\n\n* [POST\_v1/businesses/{businessId}/orders](../../reference/orders/getBusinessOrders.md).\n\nОбязательный параметр.\n"
              type: integer
              format: int64
            count:
              description: Новое количество товара.
              type: integer
              format: int32
              minimum: 0
            instances:
              description: >
                Информация о маркировке единиц товара.
  
  
                Передавайте в запросе все единицы товара, который подлежит
                маркировке.
  
  
                Обязательный параметр, если в заказе от бизнеса есть товары,
                подлежащие маркировке в системе [«Честный
                ЗНАК»](https://честныйзнак.рф/) или [«ASL
                BELGISI»](https://aslbelgisi.uz) (для продавцов
                Market Yandex Go).
              type: array
              nullable: true
              minItems: 1
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
          required:
            - id
            - count
      reason:
        description: |
          Причина, почему обновился состав заказа:
  
          * `PARTNER_REQUESTED_REMOVE` — магазин удалил товар.
          * `USER_REQUESTED_REMOVE` — покупатель попросил удалить товар.
        type: string
        enum:
          - PARTNER_REQUESTED_REMOVE
          - USER_REQUESTED_REMOVE
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
  path: v2/campaigns/{campaignId}/orders/{orderId}/items
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/updateOrderItems.md -->

[*cis-regular-value]:
Значение `cis` должно соответствовать регулярному выражению `^(?=.{1,256}$)\u001D?(\(?01\)?\d{14}\(?21\)?([!-~]{6,8}|[!-~]{13}|[!-~]{20})(\u001D\(?240\)?.{1,30})?\u001D\(?9[1,3]\)?.+)$`.<br><br>Без криптохвоста — `^(?=[!-~]{1,256}$)(\(?01\)?\d{14}\(?21\)?(.{6,8}|.{13}|.{20}))$`.

[*Deprecated]: No longer supported, please use an alternative and newer version.
