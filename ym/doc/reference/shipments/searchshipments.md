---
title: Информация о нескольких отгрузках
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md"
fetched_at: "2026-09-16T02:27:37Z"
content_sha: ef8706aa16022286
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/shipments/searchShipments.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/shipments/searchShipments.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/shipments/searchShipments.md -->
<div class="openapi">

# Получение информации о нескольких отгрузках

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/searchShipments.md -->
  **Метод доступен для модели [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/searchShipments.md -->
  
  Возвращает информацию об отгрузках по заданным параметрам:
  
  * дате;
  * статусу;
  * идентификаторам заказов.
  
  Результаты возвращаются постранично.
  
  <!-- source: ru/_auto/method_limits/searchShipments.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 200 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/searchShipments.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-put);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  PUT {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/first-mile/shipments
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
  
  Количество значений на одной странице.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `15`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `30`
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
    "dateFrom": "2025-01-01",
    "dateTo": "2025-01-01",
    "statuses": [
      "OUTBOUND_CREATED"
    ],
    "orderIds": [
      0
    ],
    "cancelledOrders": true
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dateFrom_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начальная дата для фильтрации по дате отгрузки (включительно).
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конечная дата для фильтрации по дате отгрузки (включительно).
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _cancelledOrders_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Возвращать ли отмененные заказы.
  
  Значение по умолчанию: `true`. Если возвращать отмененные заказы не нужно, передайте значение `false`.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `true`
  {.table-cell}
  ||
  ||
  
  _orderIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Список идентификаторов заказов из отгрузок.
  
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
  
  _statuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShipmentStatusType](#entity-ShipmentStatusType)[] &#124; null
  
  Список статусов отгрузок.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "OUTBOUND_CREATED"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ShipmentStatusType {#entity-ShipmentStatusType}
  
  Статус отгрузки:
  
  * `OUTBOUND_CREATED` — формируется.
  * `OUTBOUND_READY_FOR_CONFIRMATION` — можно обрабатывать.
  * `OUTBOUND_CONFIRMED` — подтверждена и готова к отправке.
  * `OUTBOUND_SIGNED` — по ней подписан электронный акт приема-передачи.
  * `ACCEPTED` — принята в сортировочном центре или пункте приема.
  * `ACCEPTED_WITH_DISCREPANCIES` — принята с расхождениями.
  * `FINISHED` — завершена.
  * `ERROR` — отменена из-за ошибки.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OUTBOUND_CREATED`, `OUTBOUND_READY_FOR_CONFIRMATION`, `OUTBOUND_CONFIRMED`, `OUTBOUND_SIGNED`, `FINISHED`, `ACCEPTED`, `ACCEPTED_WITH_DISCREPANCIES`, `ERROR`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Найденные отгрузки.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "shipments": [
        {}
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
    **Type**: [SearchShipmentsResponseDTO](#entity-SearchShipmentsResponseDTO)
  
    Информация об отгрузках.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "shipments": [
        {
          "id": 1,
          "planIntervalFrom": "2017-11-21T00:00:00+03:00",
          "planIntervalTo": "2017-11-21T00:00:00+03:00",
          "shipmentType": "IMPORT",
          "warehouse": {
            "id": 1,
            "name": "example",
            "address": "example"
          },
          "warehouseTo": null,
          "externalId": "example",
          "deliveryService": {
            "id": 0,
            "name": "example"
          },
          "palletsCount": {
            "planned": 0,
            "fact": 0
          },
          "orderIds": [
            1
          ],
          "draftCount": 0,
          "plannedCount": 0,
          "factCount": 0,
          "signature": {
            "signed": true
          },
          "status": "OUTBOUND_CREATED",
          "statusDescription": "example",
          "statusUpdateTime": "2017-11-21T00:00:00+03:00"
        }
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
        "shipments": [
          {
            "id": 1,
            "planIntervalFrom": "2017-11-21T00:00:00+03:00",
            "planIntervalTo": "2017-11-21T00:00:00+03:00",
            "shipmentType": "IMPORT",
            "warehouse": {},
            "warehouseTo": null,
            "externalId": "example",
            "deliveryService": {},
            "palletsCount": {},
            "orderIds": [
              null
            ],
            "draftCount": 0,
            "plannedCount": 0,
            "factCount": 0,
            "signature": {},
            "status": "OUTBOUND_CREATED",
            "statusDescription": "example",
            "statusUpdateTime": "2017-11-21T00:00:00+03:00"
          }
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
  
  ### ShipmentType {#entity-ShipmentType}
  
  Способ отгрузки заказов:
  
  * `IMPORT` — вы самостоятельно привозите заказы в выбранный сортировочный центр или пункт приема заказов.
  * `WITHDRAW` — вы отгружаете заказы со своего склада курьерам Яндекс Маркета.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `IMPORT`, `WITHDRAW`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PartnerShipmentWarehouseDTO {#entity-PartnerShipmentWarehouseDTO}
  
  Данные о складе отправления.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада отправления.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _address_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Адрес склада отправления.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Наименование склада отправления.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "name": "example",
    "address": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryServiceDTO {#entity-DeliveryServiceDTO}
  
  Служба доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор службы доставки.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название службы доставки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PalletsCountDTO {#entity-PalletsCountDTO}
  
  Количество палет в отгрузке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fact_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество палет, которое приняли в сортировочном центре.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _planned_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество палет, которое заявил продавец.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "planned": 0,
    "fact": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SignatureDTO {#entity-SignatureDTO}
  
  Информация о подписи акта приема-передачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _signed_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Подписан ли акт приема-передачи.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "signed": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseShipmentDTO {#entity-BaseShipmentDTO}
  
  Информация об отгрузке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _draftCount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество заказов, которое Маркет запланировал к отгрузке.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _factCount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество заказов, принятых в сортировочном центре или пункте приема.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор отгрузки.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _orderIds_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer[]
  
  Идентификаторы заказов в отгрузке.
  
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
  ||
  
  _planIntervalFrom_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Начало планового интервала отгрузки.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2017-11-21T00:00:00+03:00`
  {.table-cell}
  ||
  ||
  
  _planIntervalTo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Конец планового интервала отгрузки.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2017-11-21T00:00:00+03:00`
  {.table-cell}
  ||
  ||
  
  _plannedCount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество заказов, которое Маркет подтвердил к отгрузке.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _signature_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SignatureDTO](#entity-SignatureDTO)
  
  Информация о подписи акта приема-передачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "signed": true
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryService_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DeliveryServiceDTO](#entity-DeliveryServiceDTO)
  
  Служба доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _externalId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор отгрузки в вашей системе. Если вы еще не передавали идентификатор, вернется идентификатор из параметра `id`.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _palletsCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PalletsCountDTO](#entity-PalletsCountDTO)
  
  Данные о палетах в отгрузке.
  
  Количество палет в отгрузке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "planned": 0,
    "fact": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _shipmentType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ShipmentType](#entity-ShipmentType)
  
  Способ отгрузки заказов.
  
  Способ отгрузки заказов:
  
  * `IMPORT` — вы самостоятельно привозите заказы в выбранный сортировочный центр или пункт приема заказов.
  * `WITHDRAW` — вы отгружаете заказы со своего склада курьерам Яндекс Маркета.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `IMPORT`, `WITHDRAW`
  {.table-cell}
  ||
  ||
  
  _warehouse_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PartnerShipmentWarehouseDTO](#entity-PartnerShipmentWarehouseDTO)
  
  Данные о складе отправления.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "name": "example",
    "address": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warehouseTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PartnerShipmentWarehouseDTO](#entity-PartnerShipmentWarehouseDTO)
  
  Данные о складе назначения.
  
  Данные о складе отправления.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "name": "example",
    "address": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "planIntervalFrom": "2017-11-21T00:00:00+03:00",
    "planIntervalTo": "2017-11-21T00:00:00+03:00",
    "shipmentType": "IMPORT",
    "warehouse": {
      "id": 1,
      "name": "example",
      "address": "example"
    },
    "warehouseTo": null,
    "externalId": "example",
    "deliveryService": {
      "id": 0,
      "name": "example"
    },
    "palletsCount": {
      "planned": 0,
      "fact": 0
    },
    "orderIds": [
      1
    ],
    "draftCount": 0,
    "plannedCount": 0,
    "factCount": 0,
    "signature": {
      "signed": true
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ShipmentInfoDTO {#entity-ShipmentInfoDTO}
  
  Список с информацией об отгрузках.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BaseShipmentDTO](#entity-BaseShipmentDTO)
  
    Информация об отгрузке.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 1,
      "planIntervalFrom": "2017-11-21T00:00:00+03:00",
      "planIntervalTo": "2017-11-21T00:00:00+03:00",
      "shipmentType": "IMPORT",
      "warehouse": {
        "id": 1,
        "name": "example",
        "address": "example"
      },
      "warehouseTo": null,
      "externalId": "example",
      "deliveryService": {
        "id": 0,
        "name": "example"
      },
      "palletsCount": {
        "planned": 0,
        "fact": 0
      },
      "orderIds": [
        1
      ],
      "draftCount": 0,
      "plannedCount": 0,
      "factCount": 0,
      "signature": {
        "signed": true
      }
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _status_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [ShipmentStatusType](#entity-ShipmentStatusType)
  
    Статус отгрузки.
  
    Статус отгрузки:
  
    * `OUTBOUND_CREATED` — формируется.
    * `OUTBOUND_READY_FOR_CONFIRMATION` — можно обрабатывать.
    * `OUTBOUND_CONFIRMED` — подтверждена и готова к отправке.
    * `OUTBOUND_SIGNED` — по ней подписан электронный акт приема-передачи.
    * `ACCEPTED` — принята в сортировочном центре или пункте приема.
    * `ACCEPTED_WITH_DISCREPANCIES` — принята с расхождениями.
    * `FINISHED` — завершена.
    * `ERROR` — отменена из-за ошибки.
  
  
    _Enum:_{.json-schema-reset .json-schema-value} `OUTBOUND_CREATED`, `OUTBOUND_READY_FOR_CONFIRMATION`, `OUTBOUND_CONFIRMED`, `OUTBOUND_SIGNED`, `FINISHED`, `ACCEPTED`, `ACCEPTED_WITH_DISCREPANCIES`, `ERROR`
    {.table-cell}
    ||
    ||
  
    _statusDescription_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Описание статуса отгрузки.
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _statusUpdateTime_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string&lt;date-time&gt;
  
    Время последнего изменения статуса отгрузки
  
    Формат даты: ISO 8601 со смещением относительно UTC.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `2017-11-21T00:00:00+03:00`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OUTBOUND_CREATED",
      "statusDescription": "example",
      "statusUpdateTime": "2017-11-21T00:00:00+03:00"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "planIntervalFrom": "2017-11-21T00:00:00+03:00",
    "planIntervalTo": "2017-11-21T00:00:00+03:00",
    "shipmentType": "IMPORT",
    "warehouse": {
      "id": 1,
      "name": "example",
      "address": "example"
    },
    "warehouseTo": null,
    "externalId": "example",
    "deliveryService": {
      "id": 0,
      "name": "example"
    },
    "palletsCount": {
      "planned": 0,
      "fact": 0
    },
    "orderIds": [
      1
    ],
    "draftCount": 0,
    "plannedCount": 0,
    "factCount": 0,
    "signature": {
      "signed": true
    },
    "status": "OUTBOUND_CREATED",
    "statusDescription": "example",
    "statusUpdateTime": "2017-11-21T00:00:00+03:00"
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
  
  ### SearchShipmentsResponseDTO {#entity-SearchShipmentsResponseDTO}
  
  Информация об отгрузках.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _shipments_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShipmentInfoDTO](#entity-ShipmentInfoDTO)[]
  
  Список с информацией об отгрузках.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 1,
      "planIntervalFrom": "2017-11-21T00:00:00+03:00",
      "planIntervalTo": "2017-11-21T00:00:00+03:00",
      "shipmentType": "IMPORT",
      "warehouse": {
        "id": 1,
        "name": "example",
        "address": "example"
      },
      "warehouseTo": null,
      "externalId": "example",
      "deliveryService": {
        "id": 0,
        "name": "example"
      },
      "palletsCount": {
        "planned": 0,
        "fact": 0
      },
      "orderIds": [
        1
      ],
      "draftCount": 0,
      "plannedCount": 0,
      "factCount": 0,
      "signature": {
        "signed": true
      },
      "status": "OUTBOUND_CREATED",
      "statusDescription": "example",
      "statusUpdateTime": "2017-11-21T00:00:00+03:00"
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
  
  Страницы с результатами поиска.
  
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
    "shipments": [
      {
        "id": 1,
        "planIntervalFrom": "2017-11-21T00:00:00+03:00",
        "planIntervalTo": "2017-11-21T00:00:00+03:00",
        "shipmentType": "IMPORT",
        "warehouse": {
          "id": 1,
          "name": "example",
          "address": "example"
        },
        "warehouseTo": null,
        "externalId": "example",
        "deliveryService": {
          "id": 0,
          "name": "example"
        },
        "palletsCount": {
          "planned": 0,
          "fact": 0
        },
        "orderIds": [
          1
        ],
        "draftCount": 0,
        "plannedCount": 0,
        "factCount": 0,
        "signature": {
          "signed": true
        },
        "status": "OUTBOUND_CREATED",
        "statusDescription": "example",
        "statusUpdateTime": "2017-11-21T00:00:00+03:00"
      }
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
        Количество значений на одной странице.
      in: query
      required: false
      schema:
        type: integer
        format: int32
        minimum: 1
        default: 15
        maximum: 30
  headers: []
  body: |-
    {
      "dateFrom": "2025-01-01",
      "dateTo": "2025-01-01",
      "statuses": [
        "OUTBOUND_CREATED"
      ],
      "orderIds": [
        0
      ],
      "cancelledOrders": true
    }
  schema:
    required:
      - dateFrom
      - dateTo
    description: Запрос информации об отгрузках.
    type: object
    properties:
      dateFrom:
        description: |
          Начальная дата для фильтрации по дате отгрузки (включительно).
  
          Формат даты: `ДД-ММ-ГГГГ`.
        type: string
        format: date
      dateTo:
        description: |
          Конечная дата для фильтрации по дате отгрузки (включительно).
  
          Формат даты: `ДД-ММ-ГГГГ`.
        type: string
        format: date
      statuses:
        description: Список статусов отгрузок.
        type: array
        uniqueItems: true
        nullable: true
        minItems: 1
        items:
          description: Статус отгрузки
          $ref: '#/$defs/ShipmentStatusType'
      orderIds:
        description: Список идентификаторов заказов из отгрузок.
        type: array
        uniqueItems: true
        nullable: true
        minItems: 1
        items:
          description: Идентификатор заказа.
          type: integer
          format: int64
      cancelledOrders:
        description: >
          Возвращать ли отмененные заказы.
  
  
          Значение по умолчанию: `true`. Если возвращать отмененные заказы не
          нужно, передайте значение `false`.
        type: boolean
        default: true
    $defs:
      /home/sandbox/.ya/build/build_root/m7cc/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/shipments/schemas.yaml#/ShipmentStatusType:
        description: |
          Статус отгрузки:
  
          * `OUTBOUND_CREATED` — формируется.
          * `OUTBOUND_READY_FOR_CONFIRMATION` — можно обрабатывать.
          * `OUTBOUND_CONFIRMED` — подтверждена и готова к отправке.
          * `OUTBOUND_SIGNED` — по ней подписан электронный акт приема-передачи.
          * `ACCEPTED` — принята в сортировочном центре или пункте приема.
          * `ACCEPTED_WITH_DISCREPANCIES` — принята с расхождениями.
          * `FINISHED` — завершена.
          * `ERROR` — отменена из-за ошибки.
        type: string
        enum:
          - OUTBOUND_CREATED
          - OUTBOUND_READY_FOR_CONFIRMATION
          - OUTBOUND_CONFIRMED
          - OUTBOUND_SIGNED
          - FINISHED
          - ACCEPTED
          - ACCEPTED_WITH_DISCREPANCIES
          - ERROR
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
  path: v2/campaigns/{campaignId}/first-mile/shipments
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/shipments/searchShipments.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
