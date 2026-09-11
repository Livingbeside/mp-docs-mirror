---
title: Информация о заявках
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md"
fetched_at: "2026-09-11T01:58:26Z"
content_sha: b770b4417e1bb1aa
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/supply-requests/getSupplyRequests.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/supply-requests/getSupplyRequests.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/supply-requests/getSupplyRequests.md -->
<div class="openapi">

# Получение информации о заявках на поставку, вывоз и утилизацию

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getSupplyRequests.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md) и [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * supplies-management:read-only — [Получение информации по FBY-заявкам](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getSupplyRequests.md -->
  
  По указанным фильтрам возвращает заявки на поставку, вывоз и утилизацию, а также информацию по ним.
  
  <!-- source: ru/_auto/method_limits/getSupplyRequests.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getSupplyRequests.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/supply-requests
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
    "requestIds": [
      1
    ],
    "requestDateFrom": "2025-01-01T00:00:00Z",
    "requestDateTo": "2025-01-01T00:00:00Z",
    "requestTypes": [
      "SUPPLY"
    ],
    "requestSubtypes": [
      "DEFAULT"
    ],
    "requestStatuses": [
      "CREATED"
    ],
    "sorting": {
      "direction": "ASC",
      "attribute": "ID"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _requestDateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt; &#124; null
  
  Дата начала периода для фильтрации заявок.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _requestDateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt; &#124; null
  
  Дата окончания периода для фильтрации заявок.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _requestIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestId](#entity-SupplyRequestId)[] &#124; null
  
  Идентификаторы заявок.
  
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
  ||
  
  _requestStatuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestStatusType](#entity-SupplyRequestStatusType)[] &#124; null
  
  Статусы заявок для фильтрации.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "CREATED"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _requestSubtypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestSubType](#entity-SupplyRequestSubType)[] &#124; null
  
  Подтипы заявок для фильтрации.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "DEFAULT"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _requestTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestType](#entity-SupplyRequestType)[] &#124; null
  
  Типы заявок для фильтрации.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "SUPPLY"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _sorting_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestSortingDTO](#entity-SupplyRequestSortingDTO)
  
  Параметры сортировки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "direction": "ASC",
    "attribute": "ID"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestId {#entity-SupplyRequestId}
  
  Идентификатор заявки.
  
  {% note warning "Используется только в API" %}
  
  По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`.
  
  {% endnote %}
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestType {#entity-SupplyRequestType}
  
  Тип заявки:
  
  * `SUPPLY` — поставка товаров.
  * `WITHDRAW` — вывоз товаров.
  * `UTILIZATION` — утилизация товаров.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SUPPLY`, `WITHDRAW`, `UTILIZATION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestSubType {#entity-SupplyRequestSubType}
  
  Подтип заявки:
  
  * `DEFAULT` — поставка товаров на склад хранения или вывоз с него.
  * `XDOC` — поставка товаров через транзитный склад или вывоз с него.
  * `INVENTORYING_SUPPLY` — инвентаризация на складе по запросу магазина.
  * `INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER` — инвентаризация на складе по запросу склада.
  * `MOVEMENT_SUPPLY` — входящее перемещение между складами.
  
      При перемещении между складами создаются 2 заявки — `MOVEMENT_SUPPLY` и `MOVEMENT_WITHDRAW`.
  * `ADDITIONAL_SUPPLY` — дополнительная поставка непринятых товаров.
  * `VIRTUAL_DISTRIBUTION_CENTER` — родительская заявка при поставке товаров на склад хранения или [мультипоставке](*multisupply).
  * `VIRTUAL_DISTRIBUTION_CENTER_CHILD` — дочерняя заявка при поставке товаров на склад хранения или [мультипоставке](*multisupply).
  
      Для нее не возвращается `transitLocation`.
  * `FORCE_PLAN` — автоматическая утилизация по запросу склада.
  * `FORCE_PLAN_ANOMALY_PER_SUPPLY` — утилизация непринятых товаров.
  * `PLAN_BY_SUPPLIER` — утилизация по запросу магазина.
  * `ANOMALY_WITHDRAW` — вывоз непринятых товаров.
  * `FIX_LOST_INVENTORYING` — товары, которые не нашли после второй инвентаризации.
  * `OPER_LOST_INVENTORYING` — товары, которые не нашли после первой инвентаризации.
  * `MOVEMENT_WITHDRAW` — исходящее перемещение между складами.
  
      При перемещении между складами создаются 2 заявки — `MOVEMENT_SUPPLY` и `MOVEMENT_WITHDRAW`.
  * `MISGRADING_SUPPLY` — пересортица в большую сторону.
  * `MISGRADING_WITHDRAW` — пересортица в меньшую сторону.
  * `MAN_UTIL` — ручная утилизация по запросу склада.
  * `WITHDRAW_AUTO_UTILIZATION` — автоматическая утилизация товаров в заявке на вывоз, когда истек срок их хранения.
  * `EXTERNAL_WITHDRAW_INT_OZON` — вывоз товаров на маркетплейс Ozon. Заявка на поставку оформлена в Личном кабинете Ozon.
  * `EXTERNAL_WITHDRAW_INT_WB` — вывоз товаров на маркетплейс Wildberries. Заявка на поставку оформлена в Личном кабинете Wildberries.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEFAULT`, `XDOC`, `INVENTORYING_SUPPLY`, `INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER`, `MOVEMENT_SUPPLY`, `ADDITIONAL_SUPPLY`, `VIRTUAL_DISTRIBUTION_CENTER`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD`, `FORCE_PLAN`, `FORCE_PLAN_ANOMALY_PER_SUPPLY`, `PLAN_BY_SUPPLIER`, `ANOMALY_WITHDRAW`, `FIX_LOST_INVENTORYING`, `OPER_LOST_INVENTORYING`, `MOVEMENT_WITHDRAW`, `MISGRADING_SUPPLY`, `MISGRADING_WITHDRAW`, `MAN_UTIL`, `WITHDRAW_AUTO_UTILIZATION`, `EXTERNAL_WITHDRAW_INT_OZON`, `EXTERNAL_WITHDRAW_INT_WB`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestStatusType {#entity-SupplyRequestStatusType}
  
  Статус заявки на поставку:
  
  * `CREATED` — заявка создана.
  * `FINISHED` — заявка завершена, товары:
    * приняты на складе;
    * переданы на другой склад при перемещении;
    * переданы продавцу при вывозе;
    * утилизированы.
  * `CANCELLED` — заявка отменена.
  * `INVALID` — ошибка обработки.
  * `VALIDATED` — заявка в обработке.
  * `PUBLISHED` — заявка отправлена на утверждение.
  * `ARRIVED_TO_SERVICE` — поставка отгружена.
  * `ARRIVED_TO_XDOC_SERVICE` — поставка ждет отправки на конечный склад.
  * `SHIPPED_TO_SERVICE` — поставка отправлена с транзитного склада на склад хранения.
  * `CANCELLATION_REQUESTED` — запрошена отмена заявки.
  * `CANCELLATION_REJECTED` — заявка не будет отменена.
  * `REGISTERED_IN_ELECTRONIC_QUEUE` — поставка зарегистрирована в электронной очереди.
  * `READY_FOR_UTILIZATION` — товары готовы к утилизации.
  * `TRANSIT_MOVING` — перемещение товаров на склад вывоза.
  * `WAREHOUSE_HANDLING` — вторичная приемка товаров или их сборка для вывоза или утилизации (потоварная приемка).
  * `ACCEPTED_BY_WAREHOUSE_SYSTEM` — заявка утверждена.
  * `READY_TO_WITHDRAW` — товары готовы к выдаче.
  * `NEED_PREPARATION` — ожидается информация от продавца.
  * `WAREHOUSE_SIGNED_ACT` — ЭАПП подписан складом.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `FINISHED`, `CANCELLED`, `INVALID`, `VALIDATED`, `PUBLISHED`, `ARRIVED_TO_SERVICE`, `ARRIVED_TO_XDOC_SERVICE`, `SHIPPED_TO_SERVICE`, `CANCELLATION_REQUESTED`, `CANCELLATION_REJECTED`, `REGISTERED_IN_ELECTRONIC_QUEUE`, `READY_FOR_UTILIZATION`, `TRANSIT_MOVING`, `WAREHOUSE_HANDLING`, `ACCEPTED_BY_WAREHOUSE_SYSTEM`, `READY_TO_WITHDRAW`, `NEED_PREPARATION`, `WAREHOUSE_SIGNED_ACT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SortOrderType {#entity-SortOrderType}
  
  Направление сортировки:
  
  - `ASC` — сортировка по возрастанию.
  - `DESC` — сортировка по убыванию.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ASC`, `DESC`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestSortAttributeType {#entity-SupplyRequestSortAttributeType}
  
  По какому параметру сортировать заявки:
  
  * `ID` — идентификатор заявки.
  * `REQUESTED_DATE` — дата поставки на склад хранения.
  
      Если товары проходили через транзитный склад, сортирует по датам поставки на оба склада.
  * `UPDATED_AT` — время обновления заявки.
  * `STATUS` — статус заявки.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ID`, `REQUESTED_DATE`, `UPDATED_AT`, `STATUS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestSortingDTO {#entity-SupplyRequestSortingDTO}
  
  Параметры сортировки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _attribute_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestSortAttributeType](#entity-SupplyRequestSortAttributeType)
  
  По какому параметру сортировать заявки:
  
  * `ID` — идентификатор заявки.
  * `REQUESTED_DATE` — дата поставки на склад хранения.
  
      Если товары проходили через транзитный склад, сортирует по датам поставки на оба склада.
  * `UPDATED_AT` — время обновления заявки.
  * `STATUS` — статус заявки.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ID`, `REQUESTED_DATE`, `UPDATED_AT`, `STATUS`
  {.table-cell}
  ||
  ||
  
  _direction_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SortOrderType](#entity-SortOrderType)
  
  Направление сортировки:
  
  - `ASC` — сортировка по возрастанию.
  - `DESC` — сортировка по убыванию.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ASC`, `DESC`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "direction": "ASC",
    "attribute": "ID"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список заявок и информация по ним.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "requests": [
        {
          "id": {},
          "type": "SUPPLY",
          "subtype": "DEFAULT",
          "status": "CREATED",
          "updatedAt": "2025-01-01T00:00:00Z",
          "counters": {},
          "parentLink": {},
          "childrenLinks": [
            null
          ],
          "targetLocation": {},
          "transitLocation": null,
          "etrnIdentifier": {}
        }
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
    **Type**: [GetSupplyRequestsDTO](#entity-GetSupplyRequestsDTO)
  
    Список заявок и информация по ним.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "requests": [
        {
          "id": {
            "id": 1,
            "marketplaceRequestId": "example",
            "warehouseRequestId": "example"
          },
          "type": "SUPPLY",
          "subtype": "DEFAULT",
          "status": "CREATED",
          "updatedAt": "2025-01-01T00:00:00Z",
          "counters": {
            "planCount": 0,
            "factCount": 0,
            "undefinedCount": 0,
            "surplusCount": 0,
            "shortageCount": 0,
            "defectCount": 0,
            "acceptableCount": 0,
            "unacceptableCount": 0,
            "actualPalletsCount": 0,
            "actualBoxCount": 0
          },
          "parentLink": {
            "id": null,
            "type": "VIRTUAL_DISTRIBUTION"
          },
          "childrenLinks": [
            null
          ],
          "targetLocation": {
            "requestedDate": "2025-01-01T00:00:00Z",
            "serviceId": 0,
            "name": "example",
            "address": {
              "fullAddress": "example",
              "gps": {}
            },
            "type": "FULFILLMENT"
          },
          "transitLocation": null,
          "etrnIdentifier": {
            "identifier": "YLOG_ID",
            "value": "SCM_123456"
          }
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
        "requests": [
          {
            "id": {
              "id": 1,
              "marketplaceRequestId": "example",
              "warehouseRequestId": "example"
            },
            "type": "SUPPLY",
            "subtype": "DEFAULT",
            "status": "CREATED",
            "updatedAt": "2025-01-01T00:00:00Z",
            "counters": {
              "planCount": 0,
              "factCount": 0,
              "undefinedCount": 0,
              "surplusCount": 0,
              "shortageCount": 0,
              "defectCount": 0,
              "acceptableCount": 0,
              "unacceptableCount": 0,
              "actualPalletsCount": 0,
              "actualBoxCount": 0
            },
            "parentLink": {
              "id": null,
              "type": "VIRTUAL_DISTRIBUTION"
            },
            "childrenLinks": [
              null
            ],
            "targetLocation": {
              "requestedDate": "2025-01-01T00:00:00Z",
              "serviceId": 0,
              "name": "example",
              "address": {},
              "type": "FULFILLMENT"
            },
            "transitLocation": null,
            "etrnIdentifier": {
              "identifier": "YLOG_ID",
              "value": "SCM_123456"
            }
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
  
  ### SupplyRequestIdDTO {#entity-SupplyRequestIdDTO}
  
  Идентификатор и номера заявки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestId](#entity-SupplyRequestId)
  
  Идентификатор заявки.
  
  {% note warning "Используется только в API" %}
  
  По нему не получится найти заявки в кабинете продавца на Маркете. Для этого используйте `marketplaceRequestId` или `warehouseRequestId`.
  
  {% endnote %}
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _marketplaceRequestId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер заявки на маркетплейсе.
  
  Также указывается в кабинете продавца на Маркете.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _warehouseRequestId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер заявки на складе.
  
  Также указывается в кабинете продавца на Маркете.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "marketplaceRequestId": "example",
    "warehouseRequestId": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestCountersDTO {#entity-SupplyRequestCountersDTO}
  
  Количество товаров, коробок и палет в заявке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _acceptableCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров, которые можно привезти дополнительно.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _actualBoxCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество коробок, которые приняты на складе.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _actualPalletsCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество палет, которые приняты на складе.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _defectCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров с браком.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _factCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров, которые приняты на складе.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _planCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров в заявке на поставку.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _shortageCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров с недостатками.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _surplusCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество лишних товаров.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _unacceptableCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество товаров, которые нельзя привезти дополнительно.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _undefinedCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество непринятых товаров.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "planCount": 0,
    "factCount": 0,
    "undefinedCount": 0,
    "surplusCount": 0,
    "shortageCount": 0,
    "defectCount": 0,
    "acceptableCount": 0,
    "unacceptableCount": 0,
    "actualPalletsCount": 0,
    "actualBoxCount": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestReferenceType {#entity-SupplyRequestReferenceType}
  
  Тип связи между двумя заявками:
  
  * `VIRTUAL_DISTRIBUTION` — [мультипоставка](*multisupply).
  
  * `WITHDRAW` — вывоз непринятых товаров.
  
      Подтипы заявки: `DEFAULT`, `XDOC`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD` и `ANOMALY_WITHDRAW`.
  
  * `UTILIZATION` — утилизация непринятых товаров.
  
      Подтипы заявки: `DEFAULT`, `XDOC`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD` и `FORCE_PLAN_ANOMALY_PER_SUPPLY`.
  
  * `ADDITIONAL_SUPPLY` — дополнительная поставка.
  
      Подтипы заявки: `DEFAULT`, `XDOC`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD` и `ADDITIONAL_SUPPLY`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `VIRTUAL_DISTRIBUTION`, `WITHDRAW`, `UTILIZATION`, `ADDITIONAL_SUPPLY`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestReferenceDTO {#entity-SupplyRequestReferenceDTO}
  
  Информация о связанных заявках.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestIdDTO](#entity-SupplyRequestIdDTO)
  
  Идентификаторы связанной заявки.
  
  Идентификатор и номера заявки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "marketplaceRequestId": "example",
    "warehouseRequestId": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestReferenceType](#entity-SupplyRequestReferenceType)
  
  Тип связи.
  
  Тип связи между двумя заявками:
  
  * `VIRTUAL_DISTRIBUTION` — [мультипоставка](*multisupply).
  
  * `WITHDRAW` — вывоз непринятых товаров.
  
      Подтипы заявки: `DEFAULT`, `XDOC`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD` и `ANOMALY_WITHDRAW`.
  
  * `UTILIZATION` — утилизация непринятых товаров.
  
      Подтипы заявки: `DEFAULT`, `XDOC`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD` и `FORCE_PLAN_ANOMALY_PER_SUPPLY`.
  
  * `ADDITIONAL_SUPPLY` — дополнительная поставка.
  
      Подтипы заявки: `DEFAULT`, `XDOC`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD` и `ADDITIONAL_SUPPLY`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `VIRTUAL_DISTRIBUTION`, `WITHDRAW`, `UTILIZATION`, `ADDITIONAL_SUPPLY`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": {
      "id": 1,
      "marketplaceRequestId": "example",
      "warehouseRequestId": "example"
    },
    "type": "VIRTUAL_DISTRIBUTION"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### GpsDTO {#entity-GpsDTO}
  
  GPS-координаты широты и долготы.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _latitude_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Широта.
  {.table-cell}
  ||
  ||
  
  _longitude_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Долгота.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "latitude": 0.5,
    "longitude": 0.5
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestLocationAddressDTO {#entity-SupplyRequestLocationAddressDTO}
  
  Адрес склада или ПВЗ.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fullAddress_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Полный адрес склада или ПВЗ.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _gps_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [GpsDTO](#entity-GpsDTO)
  
  GPS-координаты широты и долготы.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "latitude": 0.5,
    "longitude": 0.5
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestLocationType {#entity-SupplyRequestLocationType}
  
  Тип склада или ПВЗ:
  
  * `FULFILLMENT` — склад хранения.
  * `XDOC` — транзитный склад.
  * `PICKUP_POINT` — ПВЗ.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FULFILLMENT`, `XDOC`, `PICKUP_POINT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestLocationDTO {#entity-SupplyRequestLocationDTO}
  
  Информации о складе или ПВЗ в заявке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestLocationAddressDTO](#entity-SupplyRequestLocationAddressDTO)
  
  Адрес склада или ПВЗ.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullAddress": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название склада или ПВЗ.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _serviceId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор склада или логистического партнера ПВЗ.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestLocationType](#entity-SupplyRequestLocationType)
  
  Тип склада или ПВЗ:
  
  * `FULFILLMENT` — склад хранения.
  * `XDOC` — транзитный склад.
  * `PICKUP_POINT` — ПВЗ.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FULFILLMENT`, `XDOC`, `PICKUP_POINT`
  {.table-cell}
  ||
  ||
  
  _requestedDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время поставки на склад или в ПВЗ.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "requestedDate": "2025-01-01T00:00:00Z",
    "serviceId": 0,
    "name": "example",
    "address": {
      "fullAddress": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "type": "FULFILLMENT"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### EtrnIdentifierDTO {#entity-EtrnIdentifierDTO}
  
  Идентификатор поставки для создания электронной транспортной накладной.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _identifier_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Наименование идентификатора.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `7`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `7`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^YLOG_ID$`
  
  _Example:_{.json-schema-reset .json-schema-example} `YLOG_ID`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Значение идентификатора.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `5`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `23`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^SCM_[0-9]{1,19}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `SCM_123456`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "identifier": "YLOG_ID",
    "value": "SCM_123456"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### SupplyRequestDTO {#entity-SupplyRequestDTO}
  
  Информация о заявке на поставку, вывоз или утилизацию.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _counters_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestCountersDTO](#entity-SupplyRequestCountersDTO)
  
  Количество товаров, коробок и палет в заявке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "planCount": 0,
    "factCount": 0,
    "undefinedCount": 0,
    "surplusCount": 0,
    "shortageCount": 0,
    "defectCount": 0,
    "acceptableCount": 0,
    "unacceptableCount": 0,
    "actualPalletsCount": 0,
    "actualBoxCount": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestIdDTO](#entity-SupplyRequestIdDTO)
  
  Идентификатор и номера заявки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 1,
    "marketplaceRequestId": "example",
    "warehouseRequestId": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestStatusType](#entity-SupplyRequestStatusType)
  
  Статус заявки.
  
  Статус заявки на поставку:
  
  * `CREATED` — заявка создана.
  * `FINISHED` — заявка завершена, товары:
    * приняты на складе;
    * переданы на другой склад при перемещении;
    * переданы продавцу при вывозе;
    * утилизированы.
  * `CANCELLED` — заявка отменена.
  * `INVALID` — ошибка обработки.
  * `VALIDATED` — заявка в обработке.
  * `PUBLISHED` — заявка отправлена на утверждение.
  * `ARRIVED_TO_SERVICE` — поставка отгружена.
  * `ARRIVED_TO_XDOC_SERVICE` — поставка ждет отправки на конечный склад.
  * `SHIPPED_TO_SERVICE` — поставка отправлена с транзитного склада на склад хранения.
  * `CANCELLATION_REQUESTED` — запрошена отмена заявки.
  * `CANCELLATION_REJECTED` — заявка не будет отменена.
  * `REGISTERED_IN_ELECTRONIC_QUEUE` — поставка зарегистрирована в электронной очереди.
  * `READY_FOR_UTILIZATION` — товары готовы к утилизации.
  * `TRANSIT_MOVING` — перемещение товаров на склад вывоза.
  * `WAREHOUSE_HANDLING` — вторичная приемка товаров или их сборка для вывоза или утилизации (потоварная приемка).
  * `ACCEPTED_BY_WAREHOUSE_SYSTEM` — заявка утверждена.
  * `READY_TO_WITHDRAW` — товары готовы к выдаче.
  * `NEED_PREPARATION` — ожидается информация от продавца.
  * `WAREHOUSE_SIGNED_ACT` — ЭАПП подписан складом.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `FINISHED`, `CANCELLED`, `INVALID`, `VALIDATED`, `PUBLISHED`, `ARRIVED_TO_SERVICE`, `ARRIVED_TO_XDOC_SERVICE`, `SHIPPED_TO_SERVICE`, `CANCELLATION_REQUESTED`, `CANCELLATION_REJECTED`, `REGISTERED_IN_ELECTRONIC_QUEUE`, `READY_FOR_UTILIZATION`, `TRANSIT_MOVING`, `WAREHOUSE_HANDLING`, `ACCEPTED_BY_WAREHOUSE_SYSTEM`, `READY_TO_WITHDRAW`, `NEED_PREPARATION`, `WAREHOUSE_SIGNED_ACT`
  {.table-cell}
  ||
  ||
  
  _subtype_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestSubType](#entity-SupplyRequestSubType)
  
  Подтип заявки.
  
  Подтип заявки:
  
  * `DEFAULT` — поставка товаров на склад хранения или вывоз с него.
  * `XDOC` — поставка товаров через транзитный склад или вывоз с него.
  * `INVENTORYING_SUPPLY` — инвентаризация на складе по запросу магазина.
  * `INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER` — инвентаризация на складе по запросу склада.
  * `MOVEMENT_SUPPLY` — входящее перемещение между складами.
  
      При перемещении между складами создаются 2 заявки — `MOVEMENT_SUPPLY` и `MOVEMENT_WITHDRAW`.
  * `ADDITIONAL_SUPPLY` — дополнительная поставка непринятых товаров.
  * `VIRTUAL_DISTRIBUTION_CENTER` — родительская заявка при поставке товаров на склад хранения или [мультипоставке](*multisupply).
  * `VIRTUAL_DISTRIBUTION_CENTER_CHILD` — дочерняя заявка при поставке товаров на склад хранения или [мультипоставке](*multisupply).
  
      Для нее не возвращается `transitLocation`.
  * `FORCE_PLAN` — автоматическая утилизация по запросу склада.
  * `FORCE_PLAN_ANOMALY_PER_SUPPLY` — утилизация непринятых товаров.
  * `PLAN_BY_SUPPLIER` — утилизация по запросу магазина.
  * `ANOMALY_WITHDRAW` — вывоз непринятых товаров.
  * `FIX_LOST_INVENTORYING` — товары, которые не нашли после второй инвентаризации.
  * `OPER_LOST_INVENTORYING` — товары, которые не нашли после первой инвентаризации.
  * `MOVEMENT_WITHDRAW` — исходящее перемещение между складами.
  
      При перемещении между складами создаются 2 заявки — `MOVEMENT_SUPPLY` и `MOVEMENT_WITHDRAW`.
  * `MISGRADING_SUPPLY` — пересортица в большую сторону.
  * `MISGRADING_WITHDRAW` — пересортица в меньшую сторону.
  * `MAN_UTIL` — ручная утилизация по запросу склада.
  * `WITHDRAW_AUTO_UTILIZATION` — автоматическая утилизация товаров в заявке на вывоз, когда истек срок их хранения.
  * `EXTERNAL_WITHDRAW_INT_OZON` — вывоз товаров на маркетплейс Ozon. Заявка на поставку оформлена в Личном кабинете Ozon.
  * `EXTERNAL_WITHDRAW_INT_WB` — вывоз товаров на маркетплейс Wildberries. Заявка на поставку оформлена в Личном кабинете Wildberries.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEFAULT`, `XDOC`, `INVENTORYING_SUPPLY`, `INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER`, `MOVEMENT_SUPPLY`, `ADDITIONAL_SUPPLY`, `VIRTUAL_DISTRIBUTION_CENTER`, `VIRTUAL_DISTRIBUTION_CENTER_CHILD`, `FORCE_PLAN`, `FORCE_PLAN_ANOMALY_PER_SUPPLY`, `PLAN_BY_SUPPLIER`, `ANOMALY_WITHDRAW`, `FIX_LOST_INVENTORYING`, `OPER_LOST_INVENTORYING`, `MOVEMENT_WITHDRAW`, `MISGRADING_SUPPLY`, `MISGRADING_WITHDRAW`, `MAN_UTIL`, `WITHDRAW_AUTO_UTILIZATION`, `EXTERNAL_WITHDRAW_INT_OZON`, `EXTERNAL_WITHDRAW_INT_WB`
  {.table-cell}
  ||
  ||
  
  _targetLocation_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestLocationDTO](#entity-SupplyRequestLocationDTO)
  
  Информация о складе хранения или ПВЗ.
  
  Информации о складе или ПВЗ в заявке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "requestedDate": "2025-01-01T00:00:00Z",
    "serviceId": 0,
    "name": "example",
    "address": {
      "fullAddress": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "type": "FULFILLMENT"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestType](#entity-SupplyRequestType)
  
  Тип заявки.
  
  Тип заявки:
  
  * `SUPPLY` — поставка товаров.
  * `WITHDRAW` — вывоз товаров.
  * `UTILIZATION` — утилизация товаров.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `SUPPLY`, `WITHDRAW`, `UTILIZATION`
  {.table-cell}
  ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время последнего обновления заявки.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _childrenLinks_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestReferenceDTO](#entity-SupplyRequestReferenceDTO)[] &#124; null
  
  Ссылки на дочерние заявки.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": {
        "id": 1,
        "marketplaceRequestId": "example",
        "warehouseRequestId": "example"
      },
      "type": "VIRTUAL_DISTRIBUTION"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _etrnIdentifier_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [EtrnIdentifierDTO](#entity-EtrnIdentifierDTO)
  
  Идентификатор для [создания ЭТрН](https://yandex.ru/support/marketplace/ru/storage/shipment/etrn).
  
  Идентификатор поставки для создания электронной транспортной накладной.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "identifier": "YLOG_ID",
    "value": "SCM_123456"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _parentLink_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestReferenceDTO](#entity-SupplyRequestReferenceDTO) &#124; null
  
  Ссылка на родительскую заявку.
  
  Информация о связанных заявках.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": {
      "id": 1,
      "marketplaceRequestId": "example",
      "warehouseRequestId": "example"
    },
    "type": "VIRTUAL_DISTRIBUTION"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _transitLocation_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SupplyRequestLocationDTO](#entity-SupplyRequestLocationDTO)
  
  Информация о транзитном складе или ПВЗ.
  
  Информации о складе или ПВЗ в заявке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "requestedDate": "2025-01-01T00:00:00Z",
    "serviceId": 0,
    "name": "example",
    "address": {
      "fullAddress": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "type": "FULFILLMENT"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": {
      "id": 1,
      "marketplaceRequestId": "example",
      "warehouseRequestId": "example"
    },
    "type": "SUPPLY",
    "subtype": "DEFAULT",
    "status": "CREATED",
    "updatedAt": "2025-01-01T00:00:00Z",
    "counters": {
      "planCount": 0,
      "factCount": 0,
      "undefinedCount": 0,
      "surplusCount": 0,
      "shortageCount": 0,
      "defectCount": 0,
      "acceptableCount": 0,
      "unacceptableCount": 0,
      "actualPalletsCount": 0,
      "actualBoxCount": 0
    },
    "parentLink": {
      "id": null,
      "type": "VIRTUAL_DISTRIBUTION"
    },
    "childrenLinks": [
      null
    ],
    "targetLocation": {
      "requestedDate": "2025-01-01T00:00:00Z",
      "serviceId": 0,
      "name": "example",
      "address": {
        "fullAddress": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        }
      },
      "type": "FULFILLMENT"
    },
    "transitLocation": null,
    "etrnIdentifier": {
      "identifier": "YLOG_ID",
      "value": "SCM_123456"
    }
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
  
  ### GetSupplyRequestsDTO {#entity-GetSupplyRequestsDTO}
  
  Список заявок и информация по ним.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _requests_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [SupplyRequestDTO](#entity-SupplyRequestDTO)[]
  
  Список заявок.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `100`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": {
        "id": 1,
        "marketplaceRequestId": "example",
        "warehouseRequestId": "example"
      },
      "type": "SUPPLY",
      "subtype": "DEFAULT",
      "status": "CREATED",
      "updatedAt": "2025-01-01T00:00:00Z",
      "counters": {
        "planCount": 0,
        "factCount": 0,
        "undefinedCount": 0,
        "surplusCount": 0,
        "shortageCount": 0,
        "defectCount": 0,
        "acceptableCount": 0,
        "unacceptableCount": 0,
        "actualPalletsCount": 0,
        "actualBoxCount": 0
      },
      "parentLink": {
        "id": null,
        "type": "VIRTUAL_DISTRIBUTION"
      },
      "childrenLinks": [
        null
      ],
      "targetLocation": {
        "requestedDate": "2025-01-01T00:00:00Z",
        "serviceId": 0,
        "name": "example",
        "address": {
          "fullAddress": "example",
          "gps": {
            "latitude": 0.5,
            "longitude": 0.5
          }
        },
        "type": "FULFILLMENT"
      },
      "transitLocation": null,
      "etrnIdentifier": {
        "identifier": "YLOG_ID",
        "value": "SCM_123456"
      }
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
  
  Информация о страницах с результатами.
  
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
    "requests": [
      {
        "id": {
          "id": 1,
          "marketplaceRequestId": "example",
          "warehouseRequestId": "example"
        },
        "type": "SUPPLY",
        "subtype": "DEFAULT",
        "status": "CREATED",
        "updatedAt": "2025-01-01T00:00:00Z",
        "counters": {
          "planCount": 0,
          "factCount": 0,
          "undefinedCount": 0,
          "surplusCount": 0,
          "shortageCount": 0,
          "defectCount": 0,
          "acceptableCount": 0,
          "unacceptableCount": 0,
          "actualPalletsCount": 0,
          "actualBoxCount": 0
        },
        "parentLink": {
          "id": null,
          "type": "VIRTUAL_DISTRIBUTION"
        },
        "childrenLinks": [
          null
        ],
        "targetLocation": {
          "requestedDate": "2025-01-01T00:00:00Z",
          "serviceId": 0,
          "name": "example",
          "address": {
            "fullAddress": "example",
            "gps": {}
          },
          "type": "FULFILLMENT"
        },
        "transitLocation": null,
        "etrnIdentifier": {
          "identifier": "YLOG_ID",
          "value": "SCM_123456"
        }
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
        default: 50
        maximum: 100
  headers: []
  body: |-
    {
      "requestIds": [
        1
      ],
      "requestDateFrom": "2025-01-01T00:00:00Z",
      "requestDateTo": "2025-01-01T00:00:00Z",
      "requestTypes": [
        "SUPPLY"
      ],
      "requestSubtypes": [
        "DEFAULT"
      ],
      "requestStatuses": [
        "CREATED"
      ],
      "sorting": {
        "direction": "ASC",
        "attribute": "ID"
      }
    }
  schema:
    type: object
    description: >
      Модель для фильтрации и сортировки заявок на поставку.
  
      Фильтры по `requestDateFrom` и `requestDateTo` отбирают заявки по
      targetLocation->requestedDate и transitLocation->requestedDate.
    properties:
      requestIds:
        type: array
        description: Идентификаторы заявок.
        minItems: 1
        maxItems: 100
        uniqueItems: true
        nullable: true
        items:
          type: integer
          format: int64
          minimum: 1
          description: >
            Идентификатор заявки.
  
  
            {% note warning "Используется только в API" %}
  
  
            По нему не получится найти заявки в кабинете продавца на Маркете. Для
            этого используйте `marketplaceRequestId` или `warehouseRequestId`.
  
  
            {% endnote %}
      requestDateFrom:
        type: string
        format: date-time
        nullable: true
        description: Дата начала периода для фильтрации заявок.
      requestDateTo:
        type: string
        format: date-time
        nullable: true
        description: Дата окончания периода для фильтрации заявок.
      requestTypes:
        type: array
        description: Типы заявок для фильтрации.
        minItems: 1
        uniqueItems: true
        nullable: true
        items:
          type: string
          description: |
            Тип заявки:
  
            * `SUPPLY` — поставка товаров.
            * `WITHDRAW` — вывоз товаров.
            * `UTILIZATION` — утилизация товаров.
          enum:
            - SUPPLY
            - WITHDRAW
            - UTILIZATION
      requestSubtypes:
        type: array
        description: Подтипы заявок для фильтрации.
        minItems: 1
        uniqueItems: true
        nullable: true
        items:
          type: string
          description: >
            Подтип заявки:
  
  
            * `DEFAULT` — поставка товаров на склад хранения или вывоз с него.
  
            * `XDOC` — поставка товаров через транзитный склад или вывоз с него.
  
            * `INVENTORYING_SUPPLY` — инвентаризация на складе по запросу
            магазина.
  
            * `INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER` — инвентаризация
            на складе по запросу склада.
  
            * `MOVEMENT_SUPPLY` — входящее перемещение между складами.
  
                При перемещении между складами создаются 2 заявки — `MOVEMENT_SUPPLY` и `MOVEMENT_WITHDRAW`.
            * `ADDITIONAL_SUPPLY` — дополнительная поставка непринятых товаров.
  
            * `VIRTUAL_DISTRIBUTION_CENTER` — родительская заявка при поставке
            товаров на склад хранения или [мультипоставке](*multisupply).
  
            * `VIRTUAL_DISTRIBUTION_CENTER_CHILD` — дочерняя заявка при поставке
            товаров на склад хранения или [мультипоставке](*multisupply).
  
                Для нее не возвращается `transitLocation`.
            * `FORCE_PLAN` — автоматическая утилизация по запросу склада.
  
            * `FORCE_PLAN_ANOMALY_PER_SUPPLY` — утилизация непринятых товаров.
  
            * `PLAN_BY_SUPPLIER` — утилизация по запросу магазина.
  
            * `ANOMALY_WITHDRAW` — вывоз непринятых товаров.
  
            * `FIX_LOST_INVENTORYING` — товары, которые не нашли после второй
            инвентаризации.
  
            * `OPER_LOST_INVENTORYING` — товары, которые не нашли после первой
            инвентаризации.
  
            * `MOVEMENT_WITHDRAW` — исходящее перемещение между складами.
  
                При перемещении между складами создаются 2 заявки — `MOVEMENT_SUPPLY` и `MOVEMENT_WITHDRAW`.
            * `MISGRADING_SUPPLY` — пересортица в большую сторону.
  
            * `MISGRADING_WITHDRAW` — пересортица в меньшую сторону.
  
            * `MAN_UTIL` — ручная утилизация по запросу склада.
  
            * `WITHDRAW_AUTO_UTILIZATION` — автоматическая утилизация товаров в
            заявке на вывоз, когда истек срок их хранения.
  
            * `EXTERNAL_WITHDRAW_INT_OZON` — вывоз товаров на маркетплейс Ozon.
            Заявка на поставку оформлена в Личном кабинете Ozon.
  
            * `EXTERNAL_WITHDRAW_INT_WB` — вывоз товаров на маркетплейс
            Wildberries. Заявка на поставку оформлена в Личном кабинете
            Wildberries.
          enum:
            - DEFAULT
            - XDOC
            - INVENTORYING_SUPPLY
            - INVENTORYING_SUPPLY_WAREHOUSE_BASED_PER_SUPPLIER
            - MOVEMENT_SUPPLY
            - ADDITIONAL_SUPPLY
            - VIRTUAL_DISTRIBUTION_CENTER
            - VIRTUAL_DISTRIBUTION_CENTER_CHILD
            - FORCE_PLAN
            - FORCE_PLAN_ANOMALY_PER_SUPPLY
            - PLAN_BY_SUPPLIER
            - ANOMALY_WITHDRAW
            - FIX_LOST_INVENTORYING
            - OPER_LOST_INVENTORYING
            - MOVEMENT_WITHDRAW
            - MISGRADING_SUPPLY
            - MISGRADING_WITHDRAW
            - MAN_UTIL
            - WITHDRAW_AUTO_UTILIZATION
            - EXTERNAL_WITHDRAW_INT_OZON
            - EXTERNAL_WITHDRAW_INT_WB
      requestStatuses:
        type: array
        description: Статусы заявок для фильтрации.
        minItems: 1
        uniqueItems: true
        nullable: true
        items:
          type: string
          description: >
            Статус заявки на поставку:
  
  
            * `CREATED` — заявка создана.
  
            * `FINISHED` — заявка завершена, товары:
              * приняты на складе;
              * переданы на другой склад при перемещении;
              * переданы продавцу при вывозе;
              * утилизированы.
            * `CANCELLED` — заявка отменена.
  
            * `INVALID` — ошибка обработки.
  
            * `VALIDATED` — заявка в обработке.
  
            * `PUBLISHED` — заявка отправлена на утверждение.
  
            * `ARRIVED_TO_SERVICE` — поставка отгружена.
  
            * `ARRIVED_TO_XDOC_SERVICE` — поставка ждет отправки на конечный
            склад.
  
            * `SHIPPED_TO_SERVICE` — поставка отправлена с транзитного склада на
            склад хранения.
  
            * `CANCELLATION_REQUESTED` — запрошена отмена заявки.
  
            * `CANCELLATION_REJECTED` — заявка не будет отменена.
  
            * `REGISTERED_IN_ELECTRONIC_QUEUE` — поставка зарегистрирована в
            электронной очереди.
  
            * `READY_FOR_UTILIZATION` — товары готовы к утилизации.
  
            * `TRANSIT_MOVING` — перемещение товаров на склад вывоза.
  
            * `WAREHOUSE_HANDLING` — вторичная приемка товаров или их сборка для
            вывоза или утилизации (потоварная приемка).
  
            * `ACCEPTED_BY_WAREHOUSE_SYSTEM` — заявка утверждена.
  
            * `READY_TO_WITHDRAW` — товары готовы к выдаче.
  
            * `NEED_PREPARATION` — ожидается информация от продавца.
  
            * `WAREHOUSE_SIGNED_ACT` — ЭАПП подписан складом.
          enum:
            - CREATED
            - FINISHED
            - CANCELLED
            - INVALID
            - VALIDATED
            - PUBLISHED
            - ARRIVED_TO_SERVICE
            - ARRIVED_TO_XDOC_SERVICE
            - SHIPPED_TO_SERVICE
            - CANCELLATION_REQUESTED
            - CANCELLATION_REJECTED
            - REGISTERED_IN_ELECTRONIC_QUEUE
            - READY_FOR_UTILIZATION
            - TRANSIT_MOVING
            - WAREHOUSE_HANDLING
            - ACCEPTED_BY_WAREHOUSE_SYSTEM
            - READY_TO_WITHDRAW
            - NEED_PREPARATION
            - WAREHOUSE_SIGNED_ACT
      sorting:
        type: object
        description: Параметры сортировки.
        required:
          - direction
          - attribute
        properties:
          direction:
            type: string
            description: |
              Направление сортировки:
  
              - `ASC` — сортировка по возрастанию.
              - `DESC` — сортировка по убыванию.
            enum:
              - ASC
              - DESC
          attribute:
            type: string
            description: |
              По какому параметру сортировать заявки:
  
              * `ID` — идентификатор заявки.
              * `REQUESTED_DATE` — дата поставки на склад хранения.
  
                  Если товары проходили через транзитный склад, сортирует по датам поставки на оба склада.
              * `UPDATED_AT` — время обновления заявки.
              * `STATUS` — статус заявки.
            enum:
              - ID
              - REQUESTED_DATE
              - UPDATED_AT
              - STATUS
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
  path: v2/campaigns/{campaignId}/supply-requests
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/supply-requests/getSupplyRequests.md -->

[*multisupply]:
О том, что это такое, читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/storage/shipment/application#create).

[*Deprecated]: No longer supported, please use an alternative and newer version.
