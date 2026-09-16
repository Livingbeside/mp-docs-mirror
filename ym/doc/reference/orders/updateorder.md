---
title: Изменение заказа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md"
fetched_at: "2026-09-16T02:27:34Z"
content_sha: bcbcf3bd677ec31e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/updateOrder.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/updateOrder.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/updateOrder.md -->
<div class="openapi">

# Изменение заказа

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateOrder.md -->
  **Метод доступен для модели [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  Пока недоступен для продавцов Market Yandex Go.

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateOrder.md -->
  
  Изменяет в заказе:
  
  * данные получателя;
  * интервал дат курьерской доставки;
  * срок хранения заказа в пункте выдачи.
  
  Передавайте только ту информацию, которую хотите изменить. При необходимости вы можете передать несколько изменений одновременно.
  
  Заказ можно изменить в любом статусе до вручения покупателю или отмены (`DELIVERED` или `CANCELLED`).
  
  {% note info "Данные заказа обновляются не мгновенно" %}
  
  Изменения применяются в течение нескольких минут и только в случае успешного завершения операции. [Как проверить статус операции](https://yandex.ru/dev/market/partner-api/doc/ru/reference/operations/getOperations.md)
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/updateOrder.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateOrder.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/campaigns/{campaignId}/orders/update
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
    "order": {
      "id": 0,
      "deliveryInterval": {
        "deliveryDateInterval": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01"
        },
        "deliveryTimeInterval": {
          "fromTime": "example",
          "toTime": "example"
        }
      },
      "customer": {
        "firstName": "example",
        "lastName": "example",
        "middleName": "example",
        "phone": "example"
      },
      "extendStoragePeriod": true
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _order_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateOrderDTO](#entity-UpdateOrderDTO)
  
  Информация, которую нужно изменить.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "deliveryInterval": {
      "deliveryDateInterval": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01"
      },
      "deliveryTimeInterval": {
        "fromTime": "example",
        "toTime": "example"
      }
    },
    "customer": {
      "firstName": "example",
      "lastName": "example",
      "middleName": "example",
      "phone": "example"
    },
    "extendStoragePeriod": true
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  ### CustomerDTO {#entity-CustomerDTO}
  
  Данные получателя заказа или отправителя возврата.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _firstName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Имя.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _lastName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Фамилия.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _phone_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Номер телефона.
  
  Формат: `+<код_страны><код_региона><номер_телефона>`.
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `5`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^\+[0-9]+$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _middleName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Отчество.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "firstName": "example",
    "lastName": "example",
    "middleName": "example",
    "phone": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOrderDTO {#entity-UpdateOrderDTO}
  
  Информация, которую нужно изменить.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа, в котором нужны изменения.
  {.table-cell}
  ||
  ||
  
  _customer_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CustomerDTO](#entity-CustomerDTO)
  
  Данные получателя заказа.
  
  Данные получателя заказа или отправителя возврата.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "firstName": "example",
    "lastName": "example",
    "middleName": "example",
    "phone": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryInterval_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DeliveryIntervalsUpdateOptionDTO](#entity-DeliveryIntervalsUpdateOptionDTO)
  
  Интервалы дат и времени, на которые можно изменить.
  
  Только для курьерской доставки.
  
  
  Интервалы дат и времени.
  
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
  {.table-cell}
  ||
  ||
  
  _extendStoragePeriod_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Продлить срок хранения заказа в пункте выдачи.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "deliveryInterval": {
      "deliveryDateInterval": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01"
      },
      "deliveryTimeInterval": {
        "fromTime": "example",
        "toTime": "example"
      }
    },
    "customer": {
      "firstName": "example",
      "lastName": "example",
      "middleName": "example",
      "phone": "example"
    },
    "extendStoragePeriod": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация об операции по изменению заказа.
  
  {% note warning "Ответ `200` не значит, что данные изменены" %}
  
  При успешном выполнении запроса это произойдет через некоторое время. [Как проверить статус операции](https://yandex.ru/dev/market/partner-api/doc/ru/reference/operations/getOperations.md)
  
  {% endnote %}
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "operations": [
        {
          "id": "example",
          "type": "ORDER_RECIPIENT_UPDATE"
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
    **Type**: [UpdateOrderResultDTO](#entity-UpdateOrderResultDTO)
  
    Информация об операции по изменению заказа.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "operations": [
        {
          "id": "example",
          "type": "ORDER_RECIPIENT_UPDATE"
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
        "operations": [
          {
            "id": "example",
            "type": "ORDER_RECIPIENT_UPDATE"
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
  
  ### OperationId {#entity-OperationId}
  
  Идентификатор операции.
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `1000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OperationType {#entity-OperationType}
  
  Тип операции:
  
  * `ORDER_RECIPIENT_UPDATE` — изменение данных получателя.
  
  * `ORDER_DELIVERY_INTERVAL_UPDATE` — изменение интервала дат доставки.
  
  * `ORDER_STORAGE_LIMIT_DATE_UPDATE` — продление срока хранения заказа.
  
  * `ORDER_STATUS_UPDATE` — обновление статуса заказа для его отмены.
  
  * `RETURN_CANCELLATION` — отмена возврата.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ORDER_RECIPIENT_UPDATE`, `ORDER_DELIVERY_INTERVAL_UPDATE`, `ORDER_STORAGE_LIMIT_DATE_UPDATE`, `ORDER_STATUS_UPDATE`, `RETURN_CANCELLATION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OperationDTO {#entity-OperationDTO}
  
  Информация об операции.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OperationId](#entity-OperationId)
  
  Идентификатор операции.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `1000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OperationType](#entity-OperationType)
  
  Тип операции:
  
  * `ORDER_RECIPIENT_UPDATE` — изменение данных получателя.
  
  * `ORDER_DELIVERY_INTERVAL_UPDATE` — изменение интервала дат доставки.
  
  * `ORDER_STORAGE_LIMIT_DATE_UPDATE` — продление срока хранения заказа.
  
  * `ORDER_STATUS_UPDATE` — обновление статуса заказа для его отмены.
  
  * `RETURN_CANCELLATION` — отмена возврата.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ORDER_RECIPIENT_UPDATE`, `ORDER_DELIVERY_INTERVAL_UPDATE`, `ORDER_STORAGE_LIMIT_DATE_UPDATE`, `ORDER_STATUS_UPDATE`, `RETURN_CANCELLATION`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "type": "ORDER_RECIPIENT_UPDATE"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOrderResultDTO {#entity-UpdateOrderResultDTO}
  
  Информация об операции по изменению заказа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _operations_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OperationDTO](#entity-OperationDTO)[]
  
  Информация о запущенных операциях по изменению заказа.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": "example",
      "type": "ORDER_RECIPIENT_UPDATE"
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
    "operations": [
      {
        "id": "example",
        "type": "ORDER_RECIPIENT_UPDATE"
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
      "order": {
        "id": 0,
        "deliveryInterval": {
          "deliveryDateInterval": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01"
          },
          "deliveryTimeInterval": {
            "fromTime": "example",
            "toTime": "example"
          }
        },
        "customer": {
          "firstName": "example",
          "lastName": "example",
          "middleName": "example",
          "phone": "example"
        },
        "extendStoragePeriod": true
      }
    }
  schema:
    type: object
    required:
      - order
    properties:
      order:
        type: object
        description: Информация, которую нужно изменить.
        required:
          - id
        properties:
          id:
            description: Идентификатор заказа, в котором нужны изменения.
            type: integer
            format: int64
          deliveryInterval:
            description: |
              Интервалы дат и времени, на которые можно изменить.
  
              Только для курьерской доставки.
            $ref: '#/$defs/DeliveryIntervalsUpdateOptionDTO'
          customer:
            description: Данные получателя заказа.
            $ref: '#/$defs/CustomerDTO'
          extendStoragePeriod:
            description: Продлить срок хранения заказа в пункте выдачи.
            type: boolean
    $defs:
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/orders/schemas.yaml#/DeliveryIntervalsUpdateOptionDTO:
        type: object
        description: Интервалы дат и времени.
        required:
          - deliveryDateInterval
          - deliveryTimeInterval
        properties:
          deliveryDateInterval:
            type: object
            description: Интервал дат доставки.
            required:
              - fromDate
              - toDate
            properties:
              fromDate:
                type: string
                format: date
                description: |
                  Начало интервала.
  
                  Формат даты: `ГГГГ-ММ-ДД`.
              toDate:
                type: string
                format: date
                description: |
                  Конец интервала.
  
                  Формат даты: `ГГГГ-ММ-ДД`.
          deliveryTimeInterval:
            type: object
            description: Интервал времени доставки.
            required:
              - fromTime
              - toTime
            properties:
              fromTime:
                type: string
                description: |
                  Начало интервала.
  
                  Формат: `ЧЧ:ММ`.
                pattern: ^([0-1][0-9]|2[0-3]):[0-5][0-9]$
              toTime:
                type: string
                description: |
                  Конец интервала.
  
                  Формат: `ЧЧ:ММ`.
                pattern: ^([0-1][0-9]|2[0-3]):[0-5][0-9]$
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/CustomerDTO:
        type: object
        description: Данные получателя заказа или отправителя возврата.
        required:
          - firstName
          - lastName
          - phone
        properties:
          firstName:
            type: string
            description: Имя.
            minLength: 1
            maxLength: 512
          lastName:
            type: string
            description: Фамилия.
            minLength: 1
            maxLength: 512
          middleName:
            type: string
            description: Отчество.
            minLength: 1
            maxLength: 512
          phone:
            type: string
            description: |
              Номер телефона.
  
              Формат: `+<код_страны><код_региона><номер_телефона>`.
            minLength: 5
            maxLength: 16
            pattern: ^\+[0-9]+$
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
  path: v1/campaigns/{campaignId}/orders/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/updateOrder.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
