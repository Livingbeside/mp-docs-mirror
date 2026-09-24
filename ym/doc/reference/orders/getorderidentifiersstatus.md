---
title: Статусы проверки кодов маркировки
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md"
fetched_at: "2026-09-24T02:13:58Z"
content_sha: bf6ad299ca8b64fe
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/getOrderIdentifiersStatus.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/getOrderIdentifiersStatus.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/getOrderIdentifiersStatus.md -->
<div class="openapi">

# Статусы проверки кодов маркировки

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOrderIdentifiersStatus.md -->
  **Метод доступен для моделей: [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOrderIdentifiersStatus.md -->
  
  Возвращает статусы проверки кодов маркировки в заказе.
  
  Заказ, в котором есть ювелирные изделия или товары с обязательной маркировкой в системе [«Честный ЗНАК»](https://честныйзнак.рф/), можно перевести в статус `READY_TO_SHIP`, только когда:
  
  1. В методе [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) вы передадите Маркету:
  
      * [УИНы](*uin) по каждому ювелирному изделию в заказе;
  
      * коды маркировки в системе «Честный ЗНАК» по всем товарам в заказе, для которых она обязательна.
  2. Все коды маркировки успешно пройдут проверку.
  
  <!-- source: ru/_auto/method_limits/getOrderIdentifiersStatus.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOrderIdentifiersStatus.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status
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
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация по проверке кодов маркировки.
  
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
          "uin": [
            null
          ],
          "cis": [
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
    **Type**: [GetOrderIdentifiersStatusDTO](#entity-GetOrderIdentifiersStatusDTO)
  
    Информация по проверке кодов маркировки.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "items": [
        {
          "id": 0,
          "uin": [
            {
              "value": "example",
              "status": "OK",
              "substatus": "UIN_MERCHANT_MISMATCH"
            }
          ],
          "cis": [
            {
              "value": "example",
              "status": "OK",
              "substatus": "WRONG_OWNER_INN",
              "crptRequestId": "example",
              "crptRequestDateTime": "2025-01-01T00:00:00Z"
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
            "uin": [
              {}
            ],
            "cis": [
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
  
  ### UinStatusType {#entity-UinStatusType}
  
  Статус проверки УИНа:
  
  * `FAILED` — не прошел проверку.
  
  * `IN_PROGRESS` — в процессе проверки.
  
  * `NOT_ON_VALIDATION` — УИН не отправлен на проверку или переданы не все УИНы в заказе.
  
  * `OK` — проверка успешно пройдена.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `IN_PROGRESS`, `FAILED`, `NOT_ON_VALIDATION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UinSubstatusType {#entity-UinSubstatusType}
  
  Детализация ошибки при проверке УИНа.
  
  * `UIN_MERCHANT_MISMATCH` — УИН не принадлежит вашему магазину.
  
  * `UIN_MERCHANT_UNREGISTERED` — магазин не подключен к системе ГИИС ДМДК.
  
  * `UIN_NO_DATA` — УИН не найден или заблокирован.
  
  Возвращается только для статуса `FAILED`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UIN_MERCHANT_MISMATCH`, `UIN_MERCHANT_UNREGISTERED`, `UIN_NO_DATA`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UinDTO {#entity-UinDTO}
  
  Статус проверки и УИН.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UinStatusType](#entity-UinStatusType)
  
  Статус проверки УИНа:
  
  * `FAILED` — не прошел проверку.
  
  * `IN_PROGRESS` — в процессе проверки.
  
  * `NOT_ON_VALIDATION` — УИН не отправлен на проверку или переданы не все УИНы в заказе.
  
  * `OK` — проверка успешно пройдена.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `IN_PROGRESS`, `FAILED`, `NOT_ON_VALIDATION`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  УИН товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _substatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [UinSubstatusType](#entity-UinSubstatusType)
  
  Детализация ошибки при проверке УИНа.
  
  * `UIN_MERCHANT_MISMATCH` — УИН не принадлежит вашему магазину.
  
  * `UIN_MERCHANT_UNREGISTERED` — магазин не подключен к системе ГИИС ДМДК.
  
  * `UIN_NO_DATA` — УИН не найден или заблокирован.
  
  Возвращается только для статуса `FAILED`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UIN_MERCHANT_MISMATCH`, `UIN_MERCHANT_UNREGISTERED`, `UIN_NO_DATA`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": "example",
    "status": "OK",
    "substatus": "UIN_MERCHANT_MISMATCH"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CisStatusType {#entity-CisStatusType}
  
  Статус проверки кода маркировки в системе «Честный ЗНАК»:
  
  * `FAILED` — не удалось проверить код.
  
    Повторите попытку позже или удалите код маркировки.
  
  * `IN_PROGRESS` — в процессе проверки.
  
  * `NOT_ON_VALIDATION` — код маркировки не отправлен на проверку.
  
  * `OK` — проверка успешно пройдена.
  
  * `INVALID` — проверка не пройдена. Продажа товара с этим кодом запрещена.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `FAILED`, `IN_PROGRESS`, `INVALID`, `NOT_ON_VALIDATION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CisSubstatusType {#entity-CisSubstatusType}
  
  Детализация ошибки при проверке кода маркировки в системе «Честный ЗНАК»:
  
  * `WRONG_OWNER_INN` — проверка не пройдена. ИНН владельца кода отличается от ИНН продавца.
  
  * `CIS_VALIDATION_ERROR` — проверка не пройдена.
  
  * `CIS_GTIN_NOT_FOUND` — код маркировки не содержит [GTIN](*gtin).
  
  * `CIS_SERIAL_NUMBER_NOT_FOUND` — код маркировки не содержит серийный номер.
  
  * `INVALID_SYMBOLS_FOUND` — код маркировки содержит недопустимые символы.
  
  * `CRYPTO_TAIL_FORMAT_MISMATCH_CIS_TYPE` — формат криптоподписи не соответствует типу кода маркировки.
  
  * `INVALID_CRYPTO_TAIL` — криптоподпись не валидна.
  
  * `INVALID_CRYPTO_KEY` — криптоключ не валиден.
  
  * `VERIFICATION_FAILED_IN_EMITTER_COUNTRY` — код маркировки не прошел верификацию в стране эмитента.
  
  * `UNSUPPORTED_AI_FOUND` — найденные в коде маркировки AI не поддерживаются.
  
  * `CIS_NOT_FOUND_IN_GIS_MT` — код маркировки не найден в ГИС МТ.
  
  * `NOT_PLACED_ON_MARKET` — код маркировки не введен в оборот.
  
  * `NOT_PRINTED_ON_PACKAGE` — код маркировки не нанесен на упаковку.
  
  * `EXPIRED_ITEM` — у маркированного товара истек срок годности.
  
  * `SALE_BLOCKED_BY_OGB` — розничная продажа продукции заблокирована по решению ОГВ.
  
  * `ITEM_SOLD` — маркированный товар был продан.
  
  Возвращается только для статуса `INVALID`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `WRONG_OWNER_INN`, `CIS_VALIDATION_ERROR`, `CIS_GTIN_NOT_FOUND`, `CIS_SERIAL_NUMBER_NOT_FOUND`, `INVALID_SYMBOLS_FOUND`, `CRYPTO_TAIL_FORMAT_MISMATCH_CIS_TYPE`, `INVALID_CRYPTO_TAIL`, `INVALID_CRYPTO_KEY`, `VERIFICATION_FAILED_IN_EMITTER_COUNTRY`, `UNSUPPORTED_AI_FOUND`, `CIS_NOT_FOUND_IN_GIS_MT`, `NOT_PLACED_ON_MARKET`, `NOT_PRINTED_ON_PACKAGE`, `EXPIRED_ITEM`, `SALE_BLOCKED_BY_OGB`, `ITEM_SOLD`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CisDTO {#entity-CisDTO}
  
  Статус проверки и код маркировки в системе «Честный ЗНАК».
  
  #|
  || **Name** | **Description** ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CisStatusType](#entity-CisStatusType)
  
  Статус проверки кода маркировки в системе «Честный ЗНАК»:
  
  * `FAILED` — не удалось проверить код.
  
    Повторите попытку позже или удалите код маркировки.
  
  * `IN_PROGRESS` — в процессе проверки.
  
  * `NOT_ON_VALIDATION` — код маркировки не отправлен на проверку.
  
  * `OK` — проверка успешно пройдена.
  
  * `INVALID` — проверка не пройдена. Продажа товара с этим кодом запрещена.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `FAILED`, `IN_PROGRESS`, `INVALID`, `NOT_ON_VALIDATION`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Код маркировки в системе «Честный ЗНАК».
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _crptRequestDateTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  **Только для модели LaaS**
  
  Время проверки кода маркировки в [ЦРПТ](https://crpt.ru/), на основании которой принято решение о продаже товара.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _crptRequestId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  **Только для модели LaaS**
  
  Идентификатор запроса проверки кода маркировки в [ЦРПТ](https://crpt.ru/), на основании которой принято решение о продаже товара.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _substatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CisSubstatusType](#entity-CisSubstatusType)
  
  Детализация ошибки при проверке кода маркировки в системе «Честный ЗНАК»:
  
  * `WRONG_OWNER_INN` — проверка не пройдена. ИНН владельца кода отличается от ИНН продавца.
  
  * `CIS_VALIDATION_ERROR` — проверка не пройдена.
  
  * `CIS_GTIN_NOT_FOUND` — код маркировки не содержит [GTIN](*gtin).
  
  * `CIS_SERIAL_NUMBER_NOT_FOUND` — код маркировки не содержит серийный номер.
  
  * `INVALID_SYMBOLS_FOUND` — код маркировки содержит недопустимые символы.
  
  * `CRYPTO_TAIL_FORMAT_MISMATCH_CIS_TYPE` — формат криптоподписи не соответствует типу кода маркировки.
  
  * `INVALID_CRYPTO_TAIL` — криптоподпись не валидна.
  
  * `INVALID_CRYPTO_KEY` — криптоключ не валиден.
  
  * `VERIFICATION_FAILED_IN_EMITTER_COUNTRY` — код маркировки не прошел верификацию в стране эмитента.
  
  * `UNSUPPORTED_AI_FOUND` — найденные в коде маркировки AI не поддерживаются.
  
  * `CIS_NOT_FOUND_IN_GIS_MT` — код маркировки не найден в ГИС МТ.
  
  * `NOT_PLACED_ON_MARKET` — код маркировки не введен в оборот.
  
  * `NOT_PRINTED_ON_PACKAGE` — код маркировки не нанесен на упаковку.
  
  * `EXPIRED_ITEM` — у маркированного товара истек срок годности.
  
  * `SALE_BLOCKED_BY_OGB` — розничная продажа продукции заблокирована по решению ОГВ.
  
  * `ITEM_SOLD` — маркированный товар был продан.
  
  Возвращается только для статуса `INVALID`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `WRONG_OWNER_INN`, `CIS_VALIDATION_ERROR`, `CIS_GTIN_NOT_FOUND`, `CIS_SERIAL_NUMBER_NOT_FOUND`, `INVALID_SYMBOLS_FOUND`, `CRYPTO_TAIL_FORMAT_MISMATCH_CIS_TYPE`, `INVALID_CRYPTO_TAIL`, `INVALID_CRYPTO_KEY`, `VERIFICATION_FAILED_IN_EMITTER_COUNTRY`, `UNSUPPORTED_AI_FOUND`, `CIS_NOT_FOUND_IN_GIS_MT`, `NOT_PLACED_ON_MARKET`, `NOT_PRINTED_ON_PACKAGE`, `EXPIRED_ITEM`, `SALE_BLOCKED_BY_OGB`, `ITEM_SOLD`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": "example",
    "status": "OK",
    "substatus": "WRONG_OWNER_INN",
    "crptRequestId": "example",
    "crptRequestDateTime": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemValidationStatusDTO {#entity-OrderItemValidationStatusDTO}
  
  Идентификаторы товаров и информация по проверке их кодов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в заказе.
  {.table-cell}
  ||
  ||
  
  _cis_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CisDTO](#entity-CisDTO)[] &#124; null
  
  Информация по проверке кодов маркировки в системе «Честный ЗНАК».
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "value": "example",
      "status": "OK",
      "substatus": "WRONG_OWNER_INN",
      "crptRequestId": "example",
      "crptRequestDateTime": "2025-01-01T00:00:00Z"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _uin_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [UinDTO](#entity-UinDTO)[] &#124; null
  
  Информация по проверке УИНов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "value": "example",
      "status": "OK",
      "substatus": "UIN_MERCHANT_MISMATCH"
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
    "uin": [
      {
        "value": "example",
        "status": "OK",
        "substatus": "UIN_MERCHANT_MISMATCH"
      }
    ],
    "cis": [
      {
        "value": "example",
        "status": "OK",
        "substatus": "WRONG_OWNER_INN",
        "crptRequestId": "example",
        "crptRequestDateTime": "2025-01-01T00:00:00Z"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GetOrderIdentifiersStatusDTO {#entity-GetOrderIdentifiersStatusDTO}
  
  Информация по проверке кодов маркировки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemValidationStatusDTO](#entity-OrderItemValidationStatusDTO)[]
  
  Список идентификаторов товаров и информация по проверке кодов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "uin": [
        {
          "value": "example",
          "status": "OK",
          "substatus": "UIN_MERCHANT_MISMATCH"
        }
      ],
      "cis": [
        {
          "value": "example",
          "status": "OK",
          "substatus": "WRONG_OWNER_INN",
          "crptRequestId": "example",
          "crptRequestDateTime": "2025-01-01T00:00:00Z"
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
        "uin": [
          {
            "value": "example",
            "status": "OK",
            "substatus": "UIN_MERCHANT_MISMATCH"
          }
        ],
        "cis": [
          {
            "value": "example",
            "status": "OK",
            "substatus": "WRONG_OWNER_INN",
            "crptRequestId": "example",
            "crptRequestDateTime": "2025-01-01T00:00:00Z"
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
  path: v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/getOrderIdentifiersStatus.md -->

[*uin]: Уникальный идентификационный номер для ювелирных изделий.<br><br>Производитель получает УИН, когда регистрирует изделие в системе контроля за оборотом драгоценных металлов и камней — ГИИС ДМДК.

[*gtin]:
<b>Что такое GTIN</b><br>GTIN — это уникальный номер, присвоенный товару в единой международной базе [GS1](https://ru.wikipedia.org/wiki/GS1). Из этого номера получается штрихкод формата EAN, UPC или ISBN.<br><br><b>Как убедиться, что товар есть в базе</b><br>Проверить код можно на [странице проверки](https://gepir.gs1.org/index.php/search-by-gtin) на сайте ассоциации GS1. Если товар не находится, запросите код GTIN у вашего поставщика.<br><br><b>Как получить GTIN для своих товаров</b><br>Чтобы получить коды GTIN, производителю нужно вступить в ассоциацию GS1 и зарегистрировать товары.

[*Deprecated]: No longer supported, please use an alternative and newer version.
