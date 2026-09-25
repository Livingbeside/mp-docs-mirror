---
title: Принятие решения по возврату (DBS)
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md"
fetched_at: "2026-09-25T02:18:19Z"
content_sha: 76e6e0d0da9b3c63
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/returns/setReturnDecision.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/returns/setReturnDecision.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/returns/setReturnDecision.md -->
<div class="openapi">

# Принятие или изменение решения по возврату

<!-- markdownlint-disable-file -->

[Deprecated](*Deprecated){.openapi-deprecated}

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/setReturnDecision.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}

  {% note warning "Метод устарел, с 18 января 2027 будет работать нестабильно и будет отключен 5 апреля 2027." %}

  Вместо него используйте [POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md).

  {% endnote %}
  <!-- endsource: ru/_auto/method_scopes/setReturnDecision.md -->
  
  Выбирает решение по возврату от покупателя. После этого для подтверждения решения нужно выполнить запрос [POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md).
  
  <!-- source: ru/_auto/method_limits/setReturnDecision.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/setReturnDecision.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision
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
  ||
  
  _returnId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор невыкупа или возврата.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "returnItemId": 1,
    "decisionType": "REFUND_MONEY_INCLUDING_SHIPMENT",
    "comment": "Вернуть 149 рублей за пересылку."
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _decisionType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ReturnRequestDecisionType](#entity-ReturnRequestDecisionType)
  
  Решение по товару в возврате.
  
  Решение по возврату:
  
  * `FAST_REFUND_MONEY` — вернуть покупателю деньги без возврата товара.
  
  * `REFUND_MONEY` — вернуть покупателю деньги за товар.
  
  * `REFUND_MONEY_INCLUDING_SHIPMENT` — вернуть покупателю деньги за товар и обратную пересылку.
  
  * `REPAIR` — отремонтировать товар.
  
  * `REPLACE` — заменить товар.
  
  * `SEND_TO_EXAMINATION` — взять товар на экспертизу.
  
  * `DECLINE_REFUND` — отказать в возврате.
  
  * `PARTIAL_MONEY_REFUND` — частичный возврат денег.
  
  * `OTHER_DECISION` — другое решение.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FAST_REFUND_MONEY`, `REFUND_MONEY`, `REFUND_MONEY_INCLUDING_SHIPMENT`, `REPAIR`, `REPLACE`, `SEND_TO_EXAMINATION`, `DECLINE_REFUND`, `PARTIAL_MONEY_REFUND`, `OTHER_DECISION`
  {.table-cell}
  ||
  ||
  
  _returnItemId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ReturnItemId](#entity-ReturnItemId)
  
  Идентификатор товара в возврате.
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnItemDecisionComment](#entity-ReturnItemDecisionComment)
  
  Комментарий к решению. Укажите:
  
  * для `REFUND_MONEY_INCLUDING_SHIPMENT`— стоимость обратной пересылки.
  
  * для `REPAIR` — когда вы устраните недостатки товара.
  
  * для `DECLINE_REFUND` — причину отказа.
  
  * для `OTHER_DECISION` — какое решение вы предлагаете.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _compensation_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BasePriceDTO](#entity-BasePriceDTO)
  
  Сумма добровольной компенсации по позиции возврата.
  Указывайте только при `decisionType` = `PARTIAL_MONEY_REFUND`.
  
  
  Цена товара.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnItemId {#entity-ReturnItemId}
  
  Идентификатор товара в возврате.
  
  **Type**: integer
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnRequestDecisionType {#entity-ReturnRequestDecisionType}
  
  Решение по возврату:
  
  * `FAST_REFUND_MONEY` — вернуть покупателю деньги без возврата товара.
  
  * `REFUND_MONEY` — вернуть покупателю деньги за товар.
  
  * `REFUND_MONEY_INCLUDING_SHIPMENT` — вернуть покупателю деньги за товар и обратную пересылку.
  
  * `REPAIR` — отремонтировать товар.
  
  * `REPLACE` — заменить товар.
  
  * `SEND_TO_EXAMINATION` — взять товар на экспертизу.
  
  * `DECLINE_REFUND` — отказать в возврате.
  
  * `PARTIAL_MONEY_REFUND` — частичный возврат денег.
  
  * `OTHER_DECISION` — другое решение.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FAST_REFUND_MONEY`, `REFUND_MONEY`, `REFUND_MONEY_INCLUDING_SHIPMENT`, `REPAIR`, `REPLACE`, `SEND_TO_EXAMINATION`, `DECLINE_REFUND`, `PARTIAL_MONEY_REFUND`, `OTHER_DECISION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnItemDecisionComment {#entity-ReturnItemDecisionComment}
  
  Комментарий к решению. Укажите:
  
  * для `REFUND_MONEY_INCLUDING_SHIPMENT`— стоимость обратной пересылки.
  
  * для `REPAIR` — когда вы устраните недостатки товара.
  
  * для `DECLINE_REFUND` — причину отказа.
  
  * для `OTHER_DECISION` — какое решение вы предлагаете.
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CurrencyType {#entity-CurrencyType}
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BasePriceDTO {#entity-BasePriceDTO}
  
  Цена товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _currencyId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта.
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Цена товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Детали возврата.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK"
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
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
    - description: Идентификатор невыкупа или возврата.
      name: returnId
      in: path
      required: true
      schema:
        type: integer
        format: int64
  searchParams: []
  headers: []
  body: |-
    {
      "returnItemId": 1,
      "decisionType": "REFUND_MONEY_INCLUDING_SHIPMENT",
      "comment": "Вернуть 149 рублей за пересылку."
    }
  schema:
    description: Решения по товару в возврате.
    type: object
    required:
      - returnItemId
      - decisionType
    properties:
      returnItemId:
        description: Идентификатор товара в возврате.
        type: integer
        format: int64
      decisionType:
        description: Решение по товару в возврате.
        $ref: '#/$defs/ReturnRequestDecisionType'
      comment:
        description: |
          Комментарий к решению. Укажите:
  
          * для `REFUND_MONEY_INCLUDING_SHIPMENT`— стоимость обратной пересылки.
  
          * для `REPAIR` — когда вы устраните недостатки товара.
  
          * для `DECLINE_REFUND` — причину отказа.
  
          * для `OTHER_DECISION` — какое решение вы предлагаете.
        type: string
      compensation:
        description: |
          Сумма добровольной компенсации по позиции возврата.
          Указывайте только при `decisionType` = `PARTIAL_MONEY_REFUND`.
        $ref: '#/$defs/BasePriceDTO'
    example:
      returnItemId: 1
      decisionType: REFUND_MONEY_INCLUDING_SHIPMENT
      comment: Вернуть 149 рублей за пересылку.
    $defs:
      /home/sandbox/.ya/build/build_root/fti6/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/returns/schemas.yaml#/ReturnRequestDecisionType:
        description: >
          Решение по возврату:
  
  
          * `FAST_REFUND_MONEY` — вернуть покупателю деньги без возврата товара.
  
  
          * `REFUND_MONEY` — вернуть покупателю деньги за товар.
  
  
          * `REFUND_MONEY_INCLUDING_SHIPMENT` — вернуть покупателю деньги за товар
          и обратную пересылку.
  
  
          * `REPAIR` — отремонтировать товар.
  
  
          * `REPLACE` — заменить товар.
  
  
          * `SEND_TO_EXAMINATION` — взять товар на экспертизу.
  
  
          * `DECLINE_REFUND` — отказать в возврате.
  
  
          * `PARTIAL_MONEY_REFUND` — частичный возврат денег.
  
  
          * `OTHER_DECISION` — другое решение.
        type: string
        enum:
          - FAST_REFUND_MONEY
          - REFUND_MONEY
          - REFUND_MONEY_INCLUDING_SHIPMENT
          - REPAIR
          - REPLACE
          - SEND_TO_EXAMINATION
          - DECLINE_REFUND
          - PARTIAL_MONEY_REFUND
          - OTHER_DECISION
      /home/sandbox/.ya/build/build_root/fti6/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/CurrencyType:
        type: string
        description: |
          Коды валют:
  
          * `RUR` — российский рубль.
          * `UAH` — украинская гривна.
          * `BYR` — белорусский рубль.
          * `KZT` — казахстанский тенге.
          * `UZS` — узбекский сум.
        enum:
          - RUR
          - USD
          - EUR
          - UAH
          - AUD
          - GBP
          - BYR
          - BYN
          - DKK
          - ISK
          - KZT
          - CAD
          - CNY
          - NOK
          - XDR
          - SGD
          - TRY
          - SEK
          - CHF
          - JPY
          - AZN
          - ALL
          - DZD
          - AOA
          - ARS
          - AMD
          - AFN
          - BHD
          - BGN
          - BOB
          - BWP
          - BND
          - BRL
          - BIF
          - HUF
          - VEF
          - KPW
          - VND
          - GMD
          - GHS
          - GNF
          - HKD
          - GEL
          - AED
          - EGP
          - ZMK
          - ILS
          - INR
          - IDR
          - JOD
          - IQD
          - IRR
          - YER
          - QAR
          - KES
          - KGS
          - COP
          - CDF
          - CRC
          - KWD
          - CUP
          - LAK
          - LVL
          - SLL
          - LBP
          - LYD
          - SZL
          - LTL
          - MUR
          - MRO
          - MKD
          - MWK
          - MGA
          - MYR
          - MAD
          - MXN
          - MZN
          - MDL
          - MNT
          - NPR
          - NGN
          - NIO
          - NZD
          - OMR
          - PKR
          - PYG
          - PEN
          - PLN
          - KHR
          - SAR
          - RON
          - SCR
          - SYP
          - SKK
          - SOS
          - SDG
          - SRD
          - TJS
          - THB
          - TWD
          - BDT
          - TZS
          - TND
          - TMM
          - UGX
          - UZS
          - UYU
          - PHP
          - DJF
          - XAF
          - XOF
          - HRK
          - CZK
          - CLP
          - LKR
          - EEK
          - ETB
          - RSD
          - ZAR
          - KRW
          - NAD
          - TL
          - UE
      /home/sandbox/.ya/build/build_root/fti6/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/catalog-common-schemas.yaml#/BasePriceDTO:
        description: Цена товара.
        type: object
        required:
          - value
          - currencyId
        properties:
          value:
            description: Цена товара.
            type: number
            minimum: 0
            exclusiveMinimum: true
          currencyId:
            description: Валюта.
            $ref: '#/$defs/CurrencyType'
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
  path: v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/returns/setReturnDecision.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
