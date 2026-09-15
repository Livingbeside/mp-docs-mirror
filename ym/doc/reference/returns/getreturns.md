---
title: Список невыкупов и возвратов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md"
fetched_at: "2026-09-15T02:22:22Z"
content_sha: 521a04c5374ed138
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/returns/getReturns.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/returns/getReturns.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/returns/getReturns.md -->
<div class="openapi">

# Список невыкупов и возвратов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getReturns.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getReturns.md -->
  
  Получает список невыкупов и возвратов.
  
  Чтобы получить информацию по одному невыкупу или возврату, выполните запрос [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md).
  
  {% note tip "Подключите API-уведомления" %}
  
  Маркет отправит вам запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый невыкуп или возврат.
  
  [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/getReturns.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 5 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getReturns.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-get);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  GET {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/returns
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
  
  _from_date_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `fromDate`.
  
  {% endnote %}
  
  Начальная дата для фильтрации невыкупов или возвратов по дате обновления.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2022-10-31`
  {.table-cell}
  ||
  ||
  
  _fromDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начальная дата для фильтрации невыкупов или возвратов по дате обновления.
  
  Формат: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2022-10-31`
  {.table-cell}
  ||
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
  
  _orderIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[]
  
  Идентификаторы заказов — для фильтрации результатов.
  
  Несколько идентификаторов перечисляются через запятую без пробела.
  
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} ``
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
  ||
  
  _shipmentStatuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnShipmentStatusType](#entity-ReturnShipmentStatusType)[]
  
  Фильтр по логистическим статусам невыкупов и возвратов.
  
  Несколько статусов перечисляются через запятую.
  
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} `READY_FOR_PICKUP,IN_TRANSIT`
  {.table-cell}
  ||
  ||
  
  _statuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RefundStatusType](#entity-RefundStatusType)[]
  
  Фильтр по статусам возврата денег за возвраты.
  
  Несколько статусов перечисляются через запятую.
  
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} `STARTED_BY_USER,WAITING_FOR_DECISION`
  {.table-cell}
  ||
  ||
  
  _to_date_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `toDate`.
  
  {% endnote %}
  
  Конечная дата для фильтрации невыкупов или возвратов по дате обновления.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2022-11-30`
  {.table-cell}
  ||
  ||
  
  _toDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конечная дата для фильтрации невыкупов или возвратов по дате обновления.
  
  Формат: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2022-11-30`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnType](#entity-ReturnType)
  
  Тип заказа для фильтрации:
  
  * `UNREDEEMED` — невыкуп.
  
  * `RETURN` — возврат.
  
  Если не указать, в ответе будут и невыкупы, и возвраты.
  
  
  Тип фильтрации:
  
  * `UNREDEEMED` — невыкупы.
  
  * `RETURN` — возвраты.
  
  Если не указывать, в ответе будут и невыкупы, и возвраты.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### RefundStatusType {#entity-RefundStatusType}
  
  Статус возврата денег:
  
  * `STARTED_BY_USER` — создан покупателем из личного кабинета.
  
  * `REFUND_IN_PROGRESS` — ждет решение о возврате денег (на рассмотрении).
  
  * `REFUNDED` — деньги возвращены.
  
  * `FAILED` — невозможно провести возврат покупателю.
  
  * `WAITING_FOR_DECISION` — ожидает решения (DBS).
  
  * `DECISION_MADE` — по возврату принято решение (DBS).
  
  * `REFUNDED_WITH_BONUSES` — возврат осуществлен баллами Плюса или промокодом.
  
  * `REFUNDED_BY_SHOP` — магазин сделал самостоятельно возврат денег.
  
  * `COMPLETE_WITHOUT_REFUND` — возврат денег не требуется.
  
  * `CANCELLED` — возврат отменен.
  
  * `REJECTED` — возврат отклонен модерацией или в ПВЗ.
  
  * `PREMODERATION_DISPUTE` — по возврату открыт спор (FBY, FBS и Экспресс).
  
  * `PREMODERATION_DECISION_WAITING` — ожидает решения (FBY, FBS и Экспресс).
  
  * `PREMODERATION_DECISION_MADE` — по возврату принято решение (FBY, FBS и Экспресс).
  
  * `PREMODERATION_SELECT_DELIVERY` — пользователь выбирает способ доставки (FBY, FBS и Экспресс).
  
  * `UNKNOWN` — неизвестный статус, обратитесь в поддержку.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `STARTED_BY_USER`, `REFUND_IN_PROGRESS`, `REFUNDED`, `FAILED`, `WAITING_FOR_DECISION`, `DECISION_MADE`, `REFUNDED_WITH_BONUSES`, `REFUNDED_BY_SHOP`, `CANCELLED`, `REJECTED`, `COMPLETE_WITHOUT_REFUND`, `PREMODERATION_DISPUTE`, `PREMODERATION_DECISION_WAITING`, `PREMODERATION_DECISION_MADE`, `PREMODERATION_SELECT_DELIVERY`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnShipmentStatusType {#entity-ReturnShipmentStatusType}
  
  Статус передачи возврата или невыкупа:
  
  * `CREATED` — возврат или невыкуп создан покупателем (оформлен).
  
  * `RECEIVED` — возврат подготовлен к отправке (принят у покупателя).
  
  * `IN_TRANSIT` — возврат или невыкуп в пути (отправлен).
  
  * `READY_FOR_PICKUP` — возврат или невыкуп готов к выдаче магазину.
  
  * `PICKED` — возврат или невыкуп выдан магазину.
  
  * `LOST` — возврат или невыкуп утерян (при транспортировке).
  
  * `EXPIRED` — покупатель не принес товар на возврат вовремя (возврат отменен).
  
  * `CANCELLED` — возврат или невыкуп отменен.
  
  * `FULFILMENT_RECEIVED` — возврат или невыкуп принят на складе Маркета.
  
  * `PREPARED_FOR_UTILIZATION` — возврат или невыкуп передан в очередь на утилизацию.
  
  * `NOT_IN_DEMAND` — возврат или невыкуп не забрали с почты.
  
  * `UTILIZED` — возврат или невыкуп утилизирован.
  
  * `READY_FOR_EXPROPRIATION` — товары в возврате или невыкупе направлены на перепродажу (проверка перед реализацией).
  
  * `RECEIVED_FOR_EXPROPRIATION` — товары в возврате или невыкупе приняты для перепродажи (реализация).
  
  * `UNKNOWN` — неизвестный статус, обратитесь в поддержку.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `RECEIVED`, `IN_TRANSIT`, `READY_FOR_PICKUP`, `PICKED`, `LOST`, `EXPIRED`, `CANCELLED`, `FULFILMENT_RECEIVED`, `PREPARED_FOR_UTILIZATION`, `NOT_IN_DEMAND`, `UTILIZED`, `READY_FOR_EXPROPRIATION`, `RECEIVED_FOR_EXPROPRIATION`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnType {#entity-ReturnType}
  
  Тип фильтрации:
  
  * `UNREDEEMED` — невыкупы.
  
  * `RETURN` — возвраты.
  
  Если не указывать, в ответе будут и невыкупы, и возвраты.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Постраничные невыкупы или возвраты магазина.
  
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
      "returns": [
        {
          "id": 0,
          "orderId": 0,
          "creationDate": "2020-02-02T14:30:30+03:00",
          "updateDate": "2020-02-02T14:30:30+03:00",
          "refundStatus": "STARTED_BY_USER",
          "logisticPickupPoint": {},
          "pickupTillDate": "2020-02-02T14:30:30+03:00",
          "shipmentRecipientType": "SHOP",
          "shipmentStatus": "CREATED",
          "refundAmount": 0,
          "amount": {},
          "items": [
            null
          ],
          "returnType": "UNREDEEMED",
          "fastReturn": true
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
    **Type**: [PagedReturnsDTO](#entity-PagedReturnsDTO)
  
    Невыкупы или возвраты.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "paging": {
        "nextPageToken": "example"
      },
      "returns": [
        {
          "id": 0,
          "orderId": 0,
          "creationDate": "2020-02-02T14:30:30+03:00",
          "updateDate": "2020-02-02T14:30:30+03:00",
          "refundStatus": "STARTED_BY_USER",
          "logisticPickupPoint": {
            "id": 0,
            "name": "example",
            "address": {
              "country": "Россия",
              "city": "Москва",
              "street": "Стрелецкая улица",
              "house": "9к2",
              "postcode": "123518"
            },
            "instruction": "example",
            "type": "WAREHOUSE",
            "logisticPartnerId": 0
          },
          "pickupTillDate": "2020-02-02T14:30:30+03:00",
          "shipmentRecipientType": "SHOP",
          "shipmentStatus": "CREATED",
          "refundAmount": 0,
          "amount": {
            "value": 0.5,
            "currencyId": "RUR"
          },
          "items": [
            {
              "marketSku": 1,
              "shopSku": "example",
              "count": 0,
              "decisions": [
                null
              ],
              "instances": [
                null
              ],
              "tracks": [
                null
              ]
            }
          ],
          "returnType": "UNREDEEMED",
          "fastReturn": true
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
        "returns": [
          {
            "id": 0,
            "orderId": 0,
            "creationDate": "2020-02-02T14:30:30+03:00",
            "updateDate": "2020-02-02T14:30:30+03:00",
            "refundStatus": "STARTED_BY_USER",
            "logisticPickupPoint": {
              "id": 0,
              "name": "example",
              "address": {},
              "instruction": "example",
              "type": "WAREHOUSE",
              "logisticPartnerId": 0
            },
            "pickupTillDate": "2020-02-02T14:30:30+03:00",
            "shipmentRecipientType": "SHOP",
            "shipmentStatus": "CREATED",
            "refundAmount": 0,
            "amount": {
              "value": 0.5,
              "currencyId": "RUR"
            },
            "items": [
              {}
            ],
            "returnType": "UNREDEEMED",
            "fastReturn": true
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
  
  ### PickupAddressDTO {#entity-PickupAddressDTO}
  
  Адрес доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _city_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Город.
  
  _Example:_{.json-schema-reset .json-schema-example} `Москва`
  {.table-cell}
  ||
  ||
  
  _country_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Страна.
  
  _Example:_{.json-schema-reset .json-schema-example} `Россия`
  {.table-cell}
  ||
  ||
  
  _house_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер дома.
  
  _Example:_{.json-schema-reset .json-schema-example} `9к2`
  {.table-cell}
  ||
  ||
  
  _postcode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Почтовый индекс.
  
  _Example:_{.json-schema-reset .json-schema-example} `123518`
  {.table-cell}
  ||
  ||
  
  _street_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Улица.
  
  _Example:_{.json-schema-reset .json-schema-example} `Стрелецкая улица`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "country": "Россия",
    "city": "Москва",
    "street": "Стрелецкая улица",
    "house": "9к2",
    "postcode": "123518"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointType {#entity-LogisticPointType}
  
  Тип логистической точки:
  
    * `WAREHOUSE` — склад.
    * `PICKUP_POINT` — обычная точка выдачи заказов (ПВЗ).
    * `PICKUP_TERMINAL` — постамат.
    * `PICKUP_POST_OFFICE` — отделение почтовой связи (ОПС).
    * `PICKUP_MIXED` — торговый зал и пункт выдачи заказов.
    * `PICKUP_RETAIL` — торговый зал.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `WAREHOUSE`, `PICKUP_POINT`, `PICKUP_TERMINAL`, `PICKUP_POST_OFFICE`, `PICKUP_MIXED`, `PICKUP_RETAIL`
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPickupPointDTO {#entity-LogisticPickupPointDTO}
  
  Описание пункта вывоза для возврата.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PickupAddressDTO](#entity-PickupAddressDTO)
  
  Адрес пункта вывоза.
  
  Адрес доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "country": "Россия",
    "city": "Москва",
    "street": "Стрелецкая улица",
    "house": "9к2",
    "postcode": "123518"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор пункта вывоза.
  {.table-cell}
  ||
  ||
  
  _instruction_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Дополнительные инструкции к вывозу.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _logisticPartnerId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор логистического партнера, к которому относится логистическая точка.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название пункта вывоза.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [LogisticPointType](#entity-LogisticPointType)
  
  Тип логистической точки.
  
  Тип логистической точки:
  
    * `WAREHOUSE` — склад.
    * `PICKUP_POINT` — обычная точка выдачи заказов (ПВЗ).
    * `PICKUP_TERMINAL` — постамат.
    * `PICKUP_POST_OFFICE` — отделение почтовой связи (ОПС).
    * `PICKUP_MIXED` — торговый зал и пункт выдачи заказов.
    * `PICKUP_RETAIL` — торговый зал.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `WAREHOUSE`, `PICKUP_POINT`, `PICKUP_TERMINAL`, `PICKUP_POST_OFFICE`, `PICKUP_MIXED`, `PICKUP_RETAIL`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "address": {
      "country": "Россия",
      "city": "Москва",
      "street": "Стрелецкая улица",
      "house": "9к2",
      "postcode": "123518"
    },
    "instruction": "example",
    "type": "WAREHOUSE",
    "logisticPartnerId": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### RecipientType {#entity-RecipientType}
  
  Способ возврата товара покупателем:
  
  * `SHOP` — в точку возврата магазина.
  
  * `DELIVERY_SERVICE` — отправить курьером.
  
  * `POST` — почта.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SHOP`, `DELIVERY_SERVICE`, `POST`
  
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
  
  ### CurrencyValueDTO {#entity-CurrencyValueDTO}
  
  Валюта и ее значение.
  
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
  
  Значение.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### MarketSku {#entity-MarketSku}
  
  Идентификатор карточки товара на Маркете.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  ### ReturnDecisionReasonType {#entity-ReturnDecisionReasonType}
  
  Причины возврата:
  
  * `BAD_QUALITY` — бракованный товар (есть недостатки).
  
  * `DOES_NOT_FIT` — товар не подошел.
  
  * `WRONG_ITEM` — привезли не тот товар.
  
  * `DAMAGE_DELIVERY` — товар поврежден при доставке.
  
  * `LOYALTY_FAIL` — невозможно установить виновного в браке/пересорте.
  
  * `CONTENT_FAIL` — ошибочное описание товара по вине Маркета.
  
  * `DELIVERY_FAIL` — товар не привезли.
  
  * `UNKNOWN` — причина не известна.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `BAD_QUALITY`, `DOES_NOT_FIT`, `WRONG_ITEM`, `DAMAGE_DELIVERY`, `LOYALTY_FAIL`, `CONTENT_FAIL`, `DELIVERY_FAIL`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnDecisionSubreasonType {#entity-ReturnDecisionSubreasonType}
  
  Детали причин возврата:
    * `DOES_NOT_FIT`:
      * `USER_DID_NOT_LIKE` — товар не понравился.
      * `USER_CHANGED_MIND` — передумал покупать.
      * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки.
  
    * `BAD_QUALITY`:
      * `BAD_PACKAGE` — заводская упаковка повреждена.
      * `DAMAGED` — царапины, сколы.
      * `NOT_WORKING` — не включается, не работает.
      * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару).
      * `WRAPPING_DAMAGED` — транспортная упаковка повреждена.
      * `ITEM_WAS_USED` — следы использования на товаре.
      * `BROKEN` — товар разбит.
      * `BAD_FLOWERS` — некачественные цветы.
  
    * `WRONG_ITEM`:
      * `WRONG_ITEM` — не тот товар.
      * `WRONG_COLOR` — цвет не соответствует заявленному.
      * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным.
      * `WRONG_ORDER` — доставили чужой заказ.
      * `WRONG_AMOUNT_DELIVERED` — неверное количество товара.
      * `PARCEL_MISSING` — часть заказа отсутствует.
      * `INCOMPLETE` — заказ не привезли полностью.
  
    * `UNKNOWN` — детали причины не указаны.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER_DID_NOT_LIKE`, `USER_CHANGED_MIND`, `DELIVERED_TOO_LONG`, `BAD_PACKAGE`, `DAMAGED`, `NOT_WORKING`, `INCOMPLETENESS`, `WRONG_ITEM`, `WRONG_COLOR`, `DID_NOT_MATCH_DESCRIPTION`, `WRONG_ORDER`, `WRONG_AMOUNT_DELIVERED`, `WRAPPING_DAMAGED`, `ITEM_WAS_USED`, `BROKEN`, `BAD_FLOWERS`, `PARCEL_MISSING`, `INCOMPLETE`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnDecisionType {#entity-ReturnDecisionType}
  
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
  
  * `UNKNOWN` — не указано.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FAST_REFUND_MONEY`, `REFUND_MONEY`, `REFUND_MONEY_INCLUDING_SHIPMENT`, `REPAIR`, `REPLACE`, `SEND_TO_EXAMINATION`, `DECLINE_REFUND`, `PARTIAL_MONEY_REFUND`, `OTHER_DECISION`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnDecisionDTO {#entity-ReturnDecisionDTO}
  
  Решения по возвратам.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Сумма возврата.
  
  Валюта и ее значение.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _count_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара.
  {.table-cell}
  ||
  ||
  
  _decisionType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnDecisionType](#entity-ReturnDecisionType)
  
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
  
  * `UNKNOWN` — не указано.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FAST_REFUND_MONEY`, `REFUND_MONEY`, `REFUND_MONEY_INCLUDING_SHIPMENT`, `REPAIR`, `REPLACE`, `SEND_TO_EXAMINATION`, `DECLINE_REFUND`, `PARTIAL_MONEY_REFUND`, `OTHER_DECISION`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _images_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Список хеш-кодов фотографий товара от покупателя.
  
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
  ||
  
  _partnerCompensation_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `partnerCompensationAmount`.
  
  {% endnote %}
  
  Компенсация за обратную доставку в копейках.
  
  {.table-cell}
  ||
  ||
  
  _partnerCompensationAmount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Компенсация за обратную доставку.
  
  Валюта и ее значение.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _reasonType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnDecisionReasonType](#entity-ReturnDecisionReasonType)
  
  Причины возврата:
  
  * `BAD_QUALITY` — бракованный товар (есть недостатки).
  
  * `DOES_NOT_FIT` — товар не подошел.
  
  * `WRONG_ITEM` — привезли не тот товар.
  
  * `DAMAGE_DELIVERY` — товар поврежден при доставке.
  
  * `LOYALTY_FAIL` — невозможно установить виновного в браке/пересорте.
  
  * `CONTENT_FAIL` — ошибочное описание товара по вине Маркета.
  
  * `DELIVERY_FAIL` — товар не привезли.
  
  * `UNKNOWN` — причина не известна.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `BAD_QUALITY`, `DOES_NOT_FIT`, `WRONG_ITEM`, `DAMAGE_DELIVERY`, `LOYALTY_FAIL`, `CONTENT_FAIL`, `DELIVERY_FAIL`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _refundAmount_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `amount`.
  
  {% endnote %}
  
  Сумма возврата в копейках.
  
  {.table-cell}
  ||
  ||
  
  _returnItemId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в возврате.
  {.table-cell}
  ||
  ||
  
  _subreasonType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnDecisionSubreasonType](#entity-ReturnDecisionSubreasonType)
  
  Детали причин возврата:
    * `DOES_NOT_FIT`:
      * `USER_DID_NOT_LIKE` — товар не понравился.
      * `USER_CHANGED_MIND` — передумал покупать.
      * `DELIVERED_TOO_LONG` — передумал покупать из-за длительного срока доставки.
  
    * `BAD_QUALITY`:
      * `BAD_PACKAGE` — заводская упаковка повреждена.
      * `DAMAGED` — царапины, сколы.
      * `NOT_WORKING` — не включается, не работает.
      * `INCOMPLETENESS` — некомплект (не хватает детали в наборе, к товару).
      * `WRAPPING_DAMAGED` — транспортная упаковка повреждена.
      * `ITEM_WAS_USED` — следы использования на товаре.
      * `BROKEN` — товар разбит.
      * `BAD_FLOWERS` — некачественные цветы.
  
    * `WRONG_ITEM`:
      * `WRONG_ITEM` — не тот товар.
      * `WRONG_COLOR` — цвет не соответствует заявленному.
      * `DID_NOT_MATCH_DESCRIPTION` — описание или характеристики не соответствуют заявленным.
      * `WRONG_ORDER` — доставили чужой заказ.
      * `WRONG_AMOUNT_DELIVERED` — неверное количество товара.
      * `PARCEL_MISSING` — часть заказа отсутствует.
      * `INCOMPLETE` — заказ не привезли полностью.
  
    * `UNKNOWN` — детали причины не указаны.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER_DID_NOT_LIKE`, `USER_CHANGED_MIND`, `DELIVERED_TOO_LONG`, `BAD_PACKAGE`, `DAMAGED`, `NOT_WORKING`, `INCOMPLETENESS`, `WRONG_ITEM`, `WRONG_COLOR`, `DID_NOT_MATCH_DESCRIPTION`, `WRONG_ORDER`, `WRONG_AMOUNT_DELIVERED`, `WRAPPING_DAMAGED`, `ITEM_WAS_USED`, `BROKEN`, `BAD_FLOWERS`, `PARCEL_MISSING`, `INCOMPLETE`, `UNKNOWN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "returnItemId": 0,
    "count": 0,
    "comment": "example",
    "reasonType": "BAD_QUALITY",
    "subreasonType": "USER_DID_NOT_LIKE",
    "decisionType": "FAST_REFUND_MONEY",
    "refundAmount": 0,
    "amount": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "partnerCompensation": 0,
    "partnerCompensationAmount": null,
    "images": [
      "example"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnInstanceStockType {#entity-ReturnInstanceStockType}
  
  Тип остатка на складе:
  
  * `FIT` — годный.
  
  * `DEFECT` — бракованный.
  
  * `ANOMALY` — аномалия.
  
  * `SURPLUS` — лишний.
  
  * `EXPIRED` — просроченный.
  
  * `MISGRADING` — пересортица.
  
  * `UNDEFINED` — с неизвестным статусом.
  
  * `INCORRECT_IMEI` — товар с некорректным [IMEI](https://ru.wikipedia.org/wiki/IMEI).
  
  * `INCORRECT_SERIAL_NUMBER` — товар с некорректным серийным номером.
  
  * `INCORRECT_CIS` — товар с некорректным кодом идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  * `PART_MISSING` — недостача.
  
  * `NON_COMPLIENT` — товар с множественными несоответствиями.
  
  * `NOT_ACCEPTABLE` — товар, который Маркет не принимает.
  
  * `SERVICE` — сервисный сток.
  
  * `MARKDOWN` — уценка.
  
  * `DEMO` — демо.
  
  * `REPAIR` — ремонт.
  
  * `FIRMWARE` — прошивка.
  
  * `UNKNOWN` — неизвестный тип товара.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `DEFECT`, `ANOMALY`, `SURPLUS`, `EXPIRED`, `MISGRADING`, `UNDEFINED`, `INCORRECT_IMEI`, `INCORRECT_SERIAL_NUMBER`, `INCORRECT_CIS`, `PART_MISSING`, `NON_COMPLIENT`, `NOT_ACCEPTABLE`, `SERVICE`, `MARKDOWN`, `DEMO`, `REPAIR`, `FIRMWARE`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnInstanceStatusType {#entity-ReturnInstanceStatusType}
  
  Логистический статус конкретного товара:
  
  * `CREATED` — возврат создан.
  
  * `RECEIVED` — возврат принят у отправителя.
  
  * `IN_TRANSIT` — возврат в пути.
  
  * `READY_FOR_PICKUP` — возврат готов к выдаче магазину.
  
  * `PICKED` — возврат выдан магазину.
  
  * `RECEIVED_ON_FULFILLMENT` — возврат принят на складе Маркета.
  
  * `CANCELLED` — возврат отменен.
  
  * `LOST` — возврат утерян.
  
  * `UTILIZED` — возврат утилизирован.
  
  * `PREPARED_FOR_UTILIZATION` — возврат готов к утилизации.
  
  * `EXPROPRIATED` — товары в возврате направлены на перепродажу.
  
  * `NOT_IN_DEMAND` — возврат не забрали с почты.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `RECEIVED`, `IN_TRANSIT`, `READY_FOR_PICKUP`, `PICKED`, `RECEIVED_ON_FULFILLMENT`, `CANCELLED`, `LOST`, `UTILIZED`, `PREPARED_FOR_UTILIZATION`, `EXPROPRIATED`, `NOT_IN_DEMAND`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnInstanceDTO {#entity-ReturnInstanceDTO}
  
  Логистическая информация по возврату.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _cis_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Код идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _imei_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Международный идентификатор мобильного оборудования.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnInstanceStatusType](#entity-ReturnInstanceStatusType)
  
  Логистический статус конкретного товара.
  
  Логистический статус конкретного товара:
  
  * `CREATED` — возврат создан.
  
  * `RECEIVED` — возврат принят у отправителя.
  
  * `IN_TRANSIT` — возврат в пути.
  
  * `READY_FOR_PICKUP` — возврат готов к выдаче магазину.
  
  * `PICKED` — возврат выдан магазину.
  
  * `RECEIVED_ON_FULFILLMENT` — возврат принят на складе Маркета.
  
  * `CANCELLED` — возврат отменен.
  
  * `LOST` — возврат утерян.
  
  * `UTILIZED` — возврат утилизирован.
  
  * `PREPARED_FOR_UTILIZATION` — возврат готов к утилизации.
  
  * `EXPROPRIATED` — товары в возврате направлены на перепродажу.
  
  * `NOT_IN_DEMAND` — возврат не забрали с почты.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `RECEIVED`, `IN_TRANSIT`, `READY_FOR_PICKUP`, `PICKED`, `RECEIVED_ON_FULFILLMENT`, `CANCELLED`, `LOST`, `UTILIZED`, `PREPARED_FOR_UTILIZATION`, `EXPROPRIATED`, `NOT_IN_DEMAND`
  {.table-cell}
  ||
  ||
  
  _stockType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnInstanceStockType](#entity-ReturnInstanceStockType)
  
  Тип остатка на складе.
  
  Тип остатка на складе:
  
  * `FIT` — годный.
  
  * `DEFECT` — бракованный.
  
  * `ANOMALY` — аномалия.
  
  * `SURPLUS` — лишний.
  
  * `EXPIRED` — просроченный.
  
  * `MISGRADING` — пересортица.
  
  * `UNDEFINED` — с неизвестным статусом.
  
  * `INCORRECT_IMEI` — товар с некорректным [IMEI](https://ru.wikipedia.org/wiki/IMEI).
  
  * `INCORRECT_SERIAL_NUMBER` — товар с некорректным серийным номером.
  
  * `INCORRECT_CIS` — товар с некорректным кодом идентификации единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  * `PART_MISSING` — недостача.
  
  * `NON_COMPLIENT` — товар с множественными несоответствиями.
  
  * `NOT_ACCEPTABLE` — товар, который Маркет не принимает.
  
  * `SERVICE` — сервисный сток.
  
  * `MARKDOWN` — уценка.
  
  * `DEMO` — демо.
  
  * `REPAIR` — ремонт.
  
  * `FIRMWARE` — прошивка.
  
  * `UNKNOWN` — неизвестный тип товара.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FIT`, `DEFECT`, `ANOMALY`, `SURPLUS`, `EXPIRED`, `MISGRADING`, `UNDEFINED`, `INCORRECT_IMEI`, `INCORRECT_SERIAL_NUMBER`, `INCORRECT_CIS`, `PART_MISSING`, `NON_COMPLIENT`, `NOT_ACCEPTABLE`, `SERVICE`, `MARKDOWN`, `DEMO`, `REPAIR`, `FIRMWARE`, `UNKNOWN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "stockType": "FIT",
    "status": "CREATED",
    "cis": "example",
    "imei": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TrackDTO {#entity-TrackDTO}
  
  Информация о трек-номерах.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _trackCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Трек-код почтового отправления.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "trackCode": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnItemDTO {#entity-ReturnItemDTO}
  
  Список товаров в невыкупе или возврате.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара.
  {.table-cell}
  ||
  ||
  
  _shopSku_{.json-schema-reset .json-schema-property .json-schema-required}
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
  
  _decisions_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnDecisionDTO](#entity-ReturnDecisionDTO)[] &#124; null
  
  Список решений по возврату.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "returnItemId": 0,
      "count": 0,
      "comment": "example",
      "reasonType": "BAD_QUALITY",
      "subreasonType": "USER_DID_NOT_LIKE",
      "decisionType": "FAST_REFUND_MONEY",
      "refundAmount": 0,
      "amount": {
        "value": 0.5,
        "currencyId": "RUR"
      },
      "partnerCompensation": 0,
      "partnerCompensationAmount": null,
      "images": [
        "example"
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnInstanceDTO](#entity-ReturnInstanceDTO)[] &#124; null
  
  Список логистических позиций возврата.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "stockType": "FIT",
      "status": "CREATED",
      "cis": "example",
      "imei": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _marketSku_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MarketSku](#entity-MarketSku)
  
  Идентификатор карточки товара на Маркете.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _tracks_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TrackDTO](#entity-TrackDTO)[] &#124; null
  
  Список трек-кодов для почтовых отправлений.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "trackCode": "example"
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
    "marketSku": 1,
    "shopSku": "example",
    "count": 0,
    "decisions": [
      {
        "returnItemId": 0,
        "count": 0,
        "comment": "example",
        "reasonType": "BAD_QUALITY",
        "subreasonType": "USER_DID_NOT_LIKE",
        "decisionType": "FAST_REFUND_MONEY",
        "refundAmount": 0,
        "amount": {
          "value": 0.5,
          "currencyId": "RUR"
        },
        "partnerCompensation": 0,
        "partnerCompensationAmount": null,
        "images": [
          "example"
        ]
      }
    ],
    "instances": [
      {
        "stockType": "FIT",
        "status": "CREATED",
        "cis": "example",
        "imei": "example"
      }
    ],
    "tracks": [
      {
        "trackCode": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ReturnDTO {#entity-ReturnDTO}
  
  Невыкуп или возврат в заказе.
  
  Параметров `logisticPickupPoint`, `shipmentRecipientType` и `shipmentStatus` может не быть в случае возврата:
    * С опцией **Быстрый возврат денег за дешевый брак**, когда товар остается у покупателя (`fastReturn=true`).
    * По заказу от бизнеса, если:
      * статус возврата `STARTED_BY_USER` или `WAITING_FOR_DECISION`;
      * возврат отменен до передачи товара.
  
  Статус возврата денег `refundStatus` актуален только для `returnType=RETURN`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор невыкупа или возврата.
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ReturnItemDTO](#entity-ReturnItemDTO)[]
  
  Список товаров в невыкупе или возврате.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "marketSku": 1,
      "shopSku": "example",
      "count": 0,
      "decisions": [
        {
          "returnItemId": 0,
          "count": 0,
          "comment": "example",
          "reasonType": "BAD_QUALITY",
          "subreasonType": "USER_DID_NOT_LIKE",
          "decisionType": "FAST_REFUND_MONEY",
          "refundAmount": 0,
          "amount": {
            "value": 0.5,
            "currencyId": "RUR"
          },
          "partnerCompensation": 0,
          "partnerCompensationAmount": null,
          "images": [
            "example"
          ]
        }
      ],
      "instances": [
        {
          "stockType": "FIT",
          "status": "CREATED",
          "cis": "example",
          "imei": "example"
        }
      ],
      "tracks": [
        {
          "trackCode": "example"
        }
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _orderId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Номер заказа.
  {.table-cell}
  ||
  ||
  
  _returnType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ReturnType](#entity-ReturnType)
  
  Тип возврата.
  
  Тип фильтрации:
  
  * `UNREDEEMED` — невыкупы.
  
  * `RETURN` — возвраты.
  
  Если не указывать, в ответе будут и невыкупы, и возвраты.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`
  {.table-cell}
  ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Сумма возврата.
  
  Валюта и ее значение.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0.5,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _creationDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата создания невыкупа или возврата.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  ||
  
  _fastReturn_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Используется ли опция **Быстрый возврат денег за дешевый брак**.
  
  Актуально только для `returnType=RETURN`.
  
  {.table-cell}
  ||
  ||
  
  _logisticPickupPoint_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [LogisticPickupPointDTO](#entity-LogisticPickupPointDTO)
  
  Пункт вывоза.
  
  Описание пункта вывоза для возврата.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "address": {
      "country": "Россия",
      "city": "Москва",
      "street": "Стрелецкая улица",
      "house": "9к2",
      "postcode": "123518"
    },
    "instruction": "example",
    "type": "WAREHOUSE",
    "logisticPartnerId": 0
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pickupTillDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата, до которой можно забрать товар.
  
  Только для невыкупов и возвратов в логистическом статусе `READY_FOR_PICKUP`.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  ||
  
  _refundAmount_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `amount`.
  
  {% endnote %}
  
  Сумма возврата в копейках.
  
  {.table-cell}
  ||
  ||
  
  _refundStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RefundStatusType](#entity-RefundStatusType)
  
  Статус возврата денег:
  
  * `STARTED_BY_USER` — создан покупателем из личного кабинета.
  
  * `REFUND_IN_PROGRESS` — ждет решение о возврате денег (на рассмотрении).
  
  * `REFUNDED` — деньги возвращены.
  
  * `FAILED` — невозможно провести возврат покупателю.
  
  * `WAITING_FOR_DECISION` — ожидает решения (DBS).
  
  * `DECISION_MADE` — по возврату принято решение (DBS).
  
  * `REFUNDED_WITH_BONUSES` — возврат осуществлен баллами Плюса или промокодом.
  
  * `REFUNDED_BY_SHOP` — магазин сделал самостоятельно возврат денег.
  
  * `COMPLETE_WITHOUT_REFUND` — возврат денег не требуется.
  
  * `CANCELLED` — возврат отменен.
  
  * `REJECTED` — возврат отклонен модерацией или в ПВЗ.
  
  * `PREMODERATION_DISPUTE` — по возврату открыт спор (FBY, FBS и Экспресс).
  
  * `PREMODERATION_DECISION_WAITING` — ожидает решения (FBY, FBS и Экспресс).
  
  * `PREMODERATION_DECISION_MADE` — по возврату принято решение (FBY, FBS и Экспресс).
  
  * `PREMODERATION_SELECT_DELIVERY` — пользователь выбирает способ доставки (FBY, FBS и Экспресс).
  
  * `UNKNOWN` — неизвестный статус, обратитесь в поддержку.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `STARTED_BY_USER`, `REFUND_IN_PROGRESS`, `REFUNDED`, `FAILED`, `WAITING_FOR_DECISION`, `DECISION_MADE`, `REFUNDED_WITH_BONUSES`, `REFUNDED_BY_SHOP`, `CANCELLED`, `REJECTED`, `COMPLETE_WITHOUT_REFUND`, `PREMODERATION_DISPUTE`, `PREMODERATION_DECISION_WAITING`, `PREMODERATION_DECISION_MADE`, `PREMODERATION_SELECT_DELIVERY`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _shipmentRecipientType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RecipientType](#entity-RecipientType)
  
  Способ возврата товара покупателем.
  
  Способ возврата товара покупателем:
  
  * `SHOP` — в точку возврата магазина.
  
  * `DELIVERY_SERVICE` — отправить курьером.
  
  * `POST` — почта.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `SHOP`, `DELIVERY_SERVICE`, `POST`
  {.table-cell}
  ||
  ||
  
  _shipmentStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnShipmentStatusType](#entity-ReturnShipmentStatusType)
  
  Статус передачи возврата.
  
  Статус передачи возврата или невыкупа:
  
  * `CREATED` — возврат или невыкуп создан покупателем (оформлен).
  
  * `RECEIVED` — возврат подготовлен к отправке (принят у покупателя).
  
  * `IN_TRANSIT` — возврат или невыкуп в пути (отправлен).
  
  * `READY_FOR_PICKUP` — возврат или невыкуп готов к выдаче магазину.
  
  * `PICKED` — возврат или невыкуп выдан магазину.
  
  * `LOST` — возврат или невыкуп утерян (при транспортировке).
  
  * `EXPIRED` — покупатель не принес товар на возврат вовремя (возврат отменен).
  
  * `CANCELLED` — возврат или невыкуп отменен.
  
  * `FULFILMENT_RECEIVED` — возврат или невыкуп принят на складе Маркета.
  
  * `PREPARED_FOR_UTILIZATION` — возврат или невыкуп передан в очередь на утилизацию.
  
  * `NOT_IN_DEMAND` — возврат или невыкуп не забрали с почты.
  
  * `UTILIZED` — возврат или невыкуп утилизирован.
  
  * `READY_FOR_EXPROPRIATION` — товары в возврате или невыкупе направлены на перепродажу (проверка перед реализацией).
  
  * `RECEIVED_FOR_EXPROPRIATION` — товары в возврате или невыкупе приняты для перепродажи (реализация).
  
  * `UNKNOWN` — неизвестный статус, обратитесь в поддержку.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `RECEIVED`, `IN_TRANSIT`, `READY_FOR_PICKUP`, `PICKED`, `LOST`, `EXPIRED`, `CANCELLED`, `FULFILMENT_RECEIVED`, `PREPARED_FOR_UTILIZATION`, `NOT_IN_DEMAND`, `UTILIZED`, `READY_FOR_EXPROPRIATION`, `RECEIVED_FOR_EXPROPRIATION`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _updateDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата обновления невыкупа или возврата.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "orderId": 0,
    "creationDate": "2020-02-02T14:30:30+03:00",
    "updateDate": "2020-02-02T14:30:30+03:00",
    "refundStatus": "STARTED_BY_USER",
    "logisticPickupPoint": {
      "id": 0,
      "name": "example",
      "address": {
        "country": "Россия",
        "city": "Москва",
        "street": "Стрелецкая улица",
        "house": "9к2",
        "postcode": "123518"
      },
      "instruction": "example",
      "type": "WAREHOUSE",
      "logisticPartnerId": 0
    },
    "pickupTillDate": "2020-02-02T14:30:30+03:00",
    "shipmentRecipientType": "SHOP",
    "shipmentStatus": "CREATED",
    "refundAmount": 0,
    "amount": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "items": [
      {
        "marketSku": 1,
        "shopSku": "example",
        "count": 0,
        "decisions": [
          {
            "returnItemId": 0,
            "count": 0,
            "comment": "example",
            "reasonType": "BAD_QUALITY",
            "subreasonType": "USER_DID_NOT_LIKE",
            "decisionType": "FAST_REFUND_MONEY",
            "refundAmount": 0,
            "amount": null,
            "partnerCompensation": 0,
            "partnerCompensationAmount": null,
            "images": [
              null
            ]
          }
        ],
        "instances": [
          {
            "stockType": "FIT",
            "status": "CREATED",
            "cis": "example",
            "imei": "example"
          }
        ],
        "tracks": [
          {
            "trackCode": "example"
          }
        ]
      }
    ],
    "returnType": "UNREDEEMED",
    "fastReturn": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### PagedReturnsDTO {#entity-PagedReturnsDTO}
  
  Невыкупы или возвраты.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _returns_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ReturnDTO](#entity-ReturnDTO)[]
  
  Список невыкупов или возвратов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "orderId": 0,
      "creationDate": "2020-02-02T14:30:30+03:00",
      "updateDate": "2020-02-02T14:30:30+03:00",
      "refundStatus": "STARTED_BY_USER",
      "logisticPickupPoint": {
        "id": 0,
        "name": "example",
        "address": {
          "country": "Россия",
          "city": "Москва",
          "street": "Стрелецкая улица",
          "house": "9к2",
          "postcode": "123518"
        },
        "instruction": "example",
        "type": "WAREHOUSE",
        "logisticPartnerId": 0
      },
      "pickupTillDate": "2020-02-02T14:30:30+03:00",
      "shipmentRecipientType": "SHOP",
      "shipmentStatus": "CREATED",
      "refundAmount": 0,
      "amount": {
        "value": 0.5,
        "currencyId": "RUR"
      },
      "items": [
        {
          "marketSku": 1,
          "shopSku": "example",
          "count": 0,
          "decisions": [
            {}
          ],
          "instances": [
            {}
          ],
          "tracks": [
            {}
          ]
        }
      ],
      "returnType": "UNREDEEMED",
      "fastReturn": true
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
    "paging": {
      "nextPageToken": "example"
    },
    "returns": [
      {
        "id": 0,
        "orderId": 0,
        "creationDate": "2020-02-02T14:30:30+03:00",
        "updateDate": "2020-02-02T14:30:30+03:00",
        "refundStatus": "STARTED_BY_USER",
        "logisticPickupPoint": {
          "id": 0,
          "name": "example",
          "address": {
            "country": "Россия",
            "city": "Москва",
            "street": "Стрелецкая улица",
            "house": "9к2",
            "postcode": "123518"
          },
          "instruction": "example",
          "type": "WAREHOUSE",
          "logisticPartnerId": 0
        },
        "pickupTillDate": "2020-02-02T14:30:30+03:00",
        "shipmentRecipientType": "SHOP",
        "shipmentStatus": "CREATED",
        "refundAmount": 0,
        "amount": {
          "value": 0.5,
          "currencyId": "RUR"
        },
        "items": [
          {
            "marketSku": 1,
            "shopSku": "example",
            "count": 0,
            "decisions": [
              null
            ],
            "instances": [
              null
            ],
            "tracks": [
              null
            ]
          }
        ],
        "returnType": "UNREDEEMED",
        "fastReturn": true
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
    - description: |
        Идентификаторы заказов — для фильтрации результатов.
  
        Несколько идентификаторов перечисляются через запятую без пробела.
      in: query
      name: orderIds
      required: false
      schema:
        type: array
        maxItems: 50
        uniqueItems: true
        items:
          type: integer
          format: int64
          example: 123543
    - description: |
        Фильтр по статусам возврата денег за возвраты.
  
        Несколько статусов перечисляются через запятую.
      in: query
      name: statuses
      required: false
      example:
        - STARTED_BY_USER
        - WAITING_FOR_DECISION
      schema:
        type: array
        uniqueItems: true
        items:
          $ref: >-
            /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/RefundStatusType
    - description: |
        Фильтр по логистическим статусам невыкупов и возвратов.
  
        Несколько статусов перечисляются через запятую.
      in: query
      name: shipmentStatuses
      required: false
      example:
        - READY_FOR_PICKUP
        - IN_TRANSIT
      schema:
        type: array
        uniqueItems: true
        items:
          $ref: >-
            /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/ReturnShipmentStatusType
    - description: |
        Тип заказа для фильтрации:
  
        * `UNREDEEMED` — невыкуп.
  
        * `RETURN` — возврат.
  
        Если не указать, в ответе будут и невыкупы, и возвраты.
      in: query
      name: type
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/ReturnType
    - description: |
        Начальная дата для фильтрации невыкупов или возвратов по дате обновления.
  
        Формат: `ГГГГ-ММ-ДД`.
      in: query
      name: fromDate
      required: false
      example: '2022-10-31'
      schema:
        type: string
        format: date
    - description: |
        Конечная дата для фильтрации невыкупов или возвратов по дате обновления.
  
        Формат: `ГГГГ-ММ-ДД`.
      in: query
      name: toDate
      required: false
      example: '2022-11-30'
      schema:
        type: string
        format: date
    - description: |
        {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
        Вместо него используйте `fromDate`.
  
        {% endnote %}
  
        Начальная дата для фильтрации невыкупов или возвратов по дате обновления.
      deprecated: true
      x-deprecation-config:
        shutdown-date: '2026-10-12'
        replacement-field: fromDate
      in: query
      name: from_date
      required: false
      example: '2022-10-31'
      schema:
        type: string
        format: date
    - description: |
        {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
        Вместо него используйте `toDate`.
  
        {% endnote %}
  
        Конечная дата для фильтрации невыкупов или возвратов по дате обновления.
      deprecated: true
      x-deprecation-config:
        shutdown-date: '2026-10-12'
        replacement-field: toDate
      in: query
      name: to_date
      required: false
      example: '2022-11-30'
      schema:
        type: string
        format: date
  headers: []
  body: null
  schema: {}
  method: get
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
  path: v2/campaigns/{campaignId}/returns
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/returns/getReturns.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
