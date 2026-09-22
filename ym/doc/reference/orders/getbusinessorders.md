---
title: Информация о заказах
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md"
fetched_at: "2026-09-22T02:27:02Z"
content_sha: 4148797d4bd01dd9
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/getBusinessOrders.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/getBusinessOrders.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/getBusinessOrders.md -->
<div class="openapi">

# Информация о заказах в кабинете

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getBusinessOrders.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getBusinessOrders.md -->
  
  Возвращает информацию о заказах в кабинете. Запрос можно использовать для отслеживания заказов и их статусов.
  
  {% note tip "Вы также можете настроить API-уведомления" %}
  
  Маркет отправит вам [запрос](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый заказ или изменится его статус. А полную информацию можно получить с помощью этого метода.
  
  [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)
  
  {% endnote %}
  
  Доступна фильтрация по параметрам:
  
  * дата оформления заказа;
  
  * дата и время обновления заказа;
  
  * дата отгрузки;
  
  * статусы заказов (`statuses`);
  
  * этапы обработки или причины отмены (`substatuses`);
  
  * идентификаторы кампаний;
  
  * идентификаторы заказов;
  
  * внешние идентификаторы заказов;
  
  * тип заказа (настоящий или тестовый);
  
  * модели размещения;
  
  * наличие запросов от покупателей на отмену заказа.
  
  Максимальный диапазон дат за один запрос — 30 дней (передается в параметрах `fromDate` и `toDate`). Если их не передать, возвращается информация за последние 30 дней.
  
  Результаты возвращаются постранично. Для навигации используйте параметры `pageToken` и `limit`.
  
  Получить более подробную информацию о покупателе и его номере телефона можно с помощью запроса [GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md).
  
  <!-- source: ru/_auto/method_limits/getBusinessOrders.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getBusinessOrders.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v1/businesses/{businessId}/orders
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
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `50`
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
    "orderIds": [
      0
    ],
    "externalOrderIds": [
      "example"
    ],
    "programTypes": [
      "FBY"
    ],
    "campaignIds": [
      1
    ],
    "statuses": [
      "PLACING"
    ],
    "substatuses": [
      "RESERVATION_EXPIRED"
    ],
    "dates": {
      "creationDateFrom": "2025-01-01",
      "creationDateTo": "2025-01-01",
      "shipmentDateFrom": "2025-01-01",
      "shipmentDateTo": "2025-01-01",
      "updateDateFrom": "2025-01-01T00:00:00Z",
      "updateDateTo": "2025-01-01T00:00:00Z"
    },
    "fake": true,
    "waitingForCancellationApprove": true,
    "sourcePlatforms": [
      "MARKET"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)[] &#124; null
  
  Идентификаторы кампаний магазинов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
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
  
  _dates_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderDatesFilterDTO](#entity-OrderDatesFilterDTO)
  
  Даты заказов.
  
  Фильтр по датам заказов.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "creationDateFrom": "2025-01-01",
    "creationDateTo": "2025-01-01",
    "shipmentDateFrom": "2025-01-01",
    "shipmentDateTo": "2025-01-01",
    "updateDateFrom": "2025-01-01T00:00:00Z",
    "updateDateTo": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _externalOrderIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ExternalOrderId](#entity-ExternalOrderId)[] &#124; null
  
  Внешние идентификаторы заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
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
  
  _fake_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Тип заказа:
  
  * `false` — настоящий заказ покупателя.
  
  * `true` — [тестовый заказ](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md) Маркета.
  
  {.table-cell}
  ||
  ||
  
  _orderIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[] &#124; null
  
  Идентификаторы заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
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
  
  _programTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SellingProgramType](#entity-SellingProgramType)[] &#124; null
  
  Модели работы магазина на Маркете.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "FBY"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _sourcePlatforms_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderSourcePlatformType](#entity-OrderSourcePlatformType)[] &#124; null
  
  Площадки-источники заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "MARKET"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _statuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderStatusType](#entity-OrderStatusType)[] &#124; null
  
  Статусы заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "PLACING"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _substatuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderSubstatusType](#entity-OrderSubstatusType)[] &#124; null
  
  Этапы обработки или причины отмены заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "RESERVATION_EXPIRED"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _waitingForCancellationApprove_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  **Только для модели DBS**
  
  Фильтр для получения заказов, по которым есть запросы на отмену.
  
  При значении `true` возвращаются только те заказы, которые находятся в статусе `DELIVERY` или `PICKUP`, и пользователи решили их отменить.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ExternalOrderId {#entity-ExternalOrderId}
  
  Внешний идентификатор заказа, который вы передали в [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md).
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### SellingProgramType {#entity-SellingProgramType}
  
  Модель работы:
  
  * `FBY` — FBY.
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  * `LAAS` — LaaS.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBY`, `FBS`, `DBS`, `EXPRESS`, `LAAS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignId {#entity-CampaignId}
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderStatusType {#entity-OrderStatusType}
  
  Статус заказа:
  
  * `PLACING` — оформляется, подготовка к резервированию.
  
  * `RESERVED` — зарезервирован, но недооформлен (только для LaaS).
  
  * `UNPAID` — оформлен, но еще не оплачен (если выбрана оплата при оформлении).
  
  * `PROCESSING` — находится в обработке.
  
  * `DELIVERY` — передан в службу доставки.
  
  * `PICKUP` — доставлен в пункт выдачи.
  
  * `DELIVERED` — получен покупателем.
  
  * `CANCELLED` — отменен.
  
  * `PENDING` — ожидает обработки со стороны продавца.
  
  * `PARTIALLY_RETURNED` — возвращен частично.
  
  * `RETURNED` — возвращен полностью.
  
  * `UNKNOWN` — неизвестный статус.
  
  Также могут возвращаться другие значения. Обрабатывать их не нужно.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PLACING`, `RESERVED`, `UNPAID`, `PROCESSING`, `DELIVERY`, `PICKUP`, `DELIVERED`, `CANCELLED`, `PENDING`, `PARTIALLY_RETURNED`, `RETURNED`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderSubstatusType {#entity-OrderSubstatusType}
  
  Этап обработки заказа (статус `PROCESSING`) или причина отмены заказа (статус `CANCELLED`).
  
  * Значения для заказа в статусе `PROCESSING`:
  
      * `STARTED` — заказ подтвержден, его можно начать обрабатывать.
  
      * `READY_TO_SHIP` — заказ собран и готов к отправке.
  
  * Значения для заказа в статусе `CANCELLED`:
  
      * `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут.
  
      * `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут.
  
      * `USER_UNREACHABLE` — не удалось связаться с покупателем. Для отмены с этой причиной необходимо выполнить условия:
  
        * не менее 3 звонков с 8 до 21 в часовом поясе покупателя;
        * перерыв между первым и третьим звонком не менее 90 минут;
        * соединение не короче 5 секунд.
  
        Если хотя бы одно из этих условий не выполнено (кроме случая, когда номер недоступен), отменить заказ не получится. Вернется ответ с кодом ошибки 400.
  
      * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
  
      * `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки.
  
      * `USER_REFUSED_PRODUCT` — покупателю не подошел товар.
  
      * `SHOP_FAILED` — магазин не может выполнить заказ.
  
      * `USER_REFUSED_QUALITY` — покупателя не устроило качество товара.
  
      * `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе.
  
      * `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.
  
      * `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе.
  
      * `PROCESSING_EXPIRED` — значение более не используется.
  
      * `PICKUP_EXPIRED` — закончился срок хранения заказа в пункт выдачи.
  
      * `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз.
  
      * `TOO_LONG_DELIVERY` — заказ доставляется слишком долго.
  
      * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.
  
  * `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета. Обратитесь в поддержку.
  
  Также могут возвращаться другие значения. Обрабатывать их не нужно.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RESERVATION_EXPIRED`, `USER_NOT_PAID`, `USER_UNREACHABLE`, `USER_CHANGED_MIND`, `USER_REFUSED_DELIVERY`, `USER_REFUSED_PRODUCT`, `SHOP_FAILED`, `USER_REFUSED_QUALITY`, `REPLACING_ORDER`, `PROCESSING_EXPIRED`, `PENDING_EXPIRED`, `SHOP_PENDING_CANCELLED`, `PENDING_CANCELLED`, `USER_FRAUD`, `RESERVATION_FAILED`, `USER_PLACED_OTHER_ORDER`, `USER_BOUGHT_CHEAPER`, `MISSING_ITEM`, `BROKEN_ITEM`, `WRONG_ITEM`, `PICKUP_EXPIRED`, `DELIVERY_PROBLEMS`, `LATE_CONTACT`, `CUSTOM`, `DELIVERY_SERVICE_FAILED`, `WAREHOUSE_FAILED_TO_SHIP`, `DELIVERY_SERVICE_UNDELIVERED`, `PREORDER`, `AWAIT_CONFIRMATION`, `STARTED`, `PACKAGING`, `READY_TO_SHIP`, `SHIPPED`, `ASYNC_PROCESSING`, `WAITING_USER_INPUT`, `WAITING_BANK_DECISION`, `BANK_REJECT_CREDIT_OFFER`, `CUSTOMER_REJECT_CREDIT_OFFER`, `CREDIT_OFFER_FAILED`, `AWAIT_DELIVERY_DATES_CONFIRMATION`, `SERVICE_FAULT`, `DELIVERY_SERVICE_RECEIVED`, `USER_RECEIVED`, `WAITING_FOR_STOCKS`, `AS_PART_OF_MULTI_ORDER`, `READY_FOR_LAST_MILE`, `LAST_MILE_STARTED`, `ANTIFRAUD`, `DELIVERY_USER_NOT_RECEIVED`, `DELIVERY_SERVICE_DELIVERED`, `DELIVERED_USER_NOT_RECEIVED`, `USER_WANTED_ANOTHER_PAYMENT_METHOD`, `USER_RECEIVED_TECHNICAL_ERROR`, `USER_FORGOT_TO_USE_BONUS`, `DELIVERY_SERVICE_NOT_RECEIVED`, `DELIVERY_SERVICE_LOST`, `SHIPPED_TO_WRONG_DELIVERY_SERVICE`, `DELIVERED_USER_RECEIVED`, `WAITING_TINKOFF_DECISION`, `COURIER_SEARCH`, `COURIER_FOUND`, `COURIER_IN_TRANSIT_TO_SENDER`, `COURIER_ARRIVED_TO_SENDER`, `COURIER_RECEIVED`, `COURIER_NOT_FOUND`, `COURIER_NOT_DELIVER_ORDER`, `COURIER_RETURNS_ORDER`, `COURIER_RETURNED_ORDER`, `WAITING_USER_DELIVERY_INPUT`, `PICKUP_SERVICE_RECEIVED`, `PICKUP_USER_RECEIVED`, `CANCELLED_COURIER_NOT_FOUND`, `COURIER_NOT_COME_FOR_ORDER`, `DELIVERY_NOT_MANAGED_REGION`, `INCOMPLETE_CONTACT_INFORMATION`, `INCOMPLETE_MULTI_ORDER`, `INAPPROPRIATE_WEIGHT_SIZE`, `TECHNICAL_ERROR`, `SORTING_CENTER_LOST`, `COURIER_SEARCH_NOT_STARTED`, `LOST`, `AWAIT_PAYMENT`, `AWAIT_LAVKA_RESERVATION`, `USER_WANTS_TO_CHANGE_ADDRESS`, `FULL_NOT_RANSOM`, `PRESCRIPTION_MISMATCH`, `DROPOFF_LOST`, `DROPOFF_CLOSED`, `DELIVERY_TO_STORE_STARTED`, `USER_WANTS_TO_CHANGE_DELIVERY_DATE`, `WRONG_ITEM_DELIVERED`, `DAMAGED_BOX`, `AWAIT_DELIVERY_DATES`, `LAST_MILE_COURIER_SEARCH`, `PICKUP_POINT_CLOSED`, `LEGAL_INFO_CHANGED`, `USER_HAS_NO_TIME_TO_PICKUP_ORDER`, `DELIVERY_CUSTOMS_ARRIVED`, `DELIVERY_CUSTOMS_CLEARED`, `FIRST_MILE_DELIVERY_SERVICE_RECEIVED`, `AWAIT_AUTO_DELIVERY_DATES`, `AWAIT_USER_PERSONAL_DATA`, `NO_PERSONAL_DATA_EXPIRED`, `CUSTOMS_PROBLEMS`, `AWAIT_CASHIER`, `WAITING_POSTPAID_BUDGET_RESERVATION`, `AWAIT_SERVICEABLE_CONFIRMATION`, `POSTPAID_BUDGET_RESERVATION_FAILED`, `AWAIT_CUSTOM_PRICE_CONFIRMATION`, `READY_FOR_PICKUP`, `TOO_MANY_DELIVERY_DATE_CHANGES`, `TOO_LONG_DELIVERY`, `DEFERRED_PAYMENT`, `POSTPAID_FAILED`, `INCORRECT_PERSONAL_DATA`, `CUSTOMS_FAILED_MARKET`, `CUSTOMS_FAILED_USER_COMMERCIAL_ITEMS`, `CUSTOMS_FAILED_USER_DUTY_NOT_PAID`, `CUSTOMS_FAILED_USER_INVALID_PERSONAL_DATA`, `CUSTOMS_FAILED_USER_ADDITIONAL_DATA_NOT_PROVIDED`, `AWAIT_PAYMENT_AFTER_DELIVERY`, `AWAIT_USER_STEAM_FAST_URL`, `USER_IDENTIFICATION_MISMATCH`, `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderDatesFilterDTO {#entity-OrderDatesFilterDTO}
  
  Фильтр по датам заказов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _creationDateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начальная дата для фильтрации заказов по дате оформления.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  Между начальной и конечной датой (параметр `creationDateTo`) должно быть не больше 30 дней.
  
  Значение по умолчанию: 30 дней назад от текущей даты.
  
  Начальная дата включается в интервал для фильтрации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _creationDateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конечная дата для фильтрации заказов по дате оформления.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  Между начальной (параметр `creationDateFrom`) и конечной датой должно быть не больше 30 дней.
  
  Значение по умолчанию: текущая дата.
  
  Если промежуток времени между `creationDateTo` и `creationDateFrom` меньше суток, то `creationDateTo` равен `creationDateFrom` + сутки.
  
  Конечная дата не включается в интервал для фильтрации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _shipmentDateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Начальная дата для фильтрации заказов по дате отгрузки в службу доставки (параметр `shipmentDate`).
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  Между начальной и конечной датой (параметр `shipmentDateTo`) должно быть не больше 30 дней.
  
  Начальная дата включается в интервал для фильтрации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _shipmentDateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конечная дата для фильтрации заказов по дате отгрузки в службу доставки (параметр `shipmentDate`).
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  Между начальной (параметр `shipmentDateFrom`) и конечной датой должно быть не больше 30 дней.
  
  Если промежуток времени между `shipmentDateTo` и `shipmentDateFrom` меньше суток, то `shipmentDateTo` равен `shipmentDateFrom` + сутки.
  
  Конечная дата не включается в интервал для фильтрации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _updateDateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Начальная дата обновления заказа (ISO 8601).
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _updateDateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Конечная дата обновления заказа (ISO 8601).
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "creationDateFrom": "2025-01-01",
    "creationDateTo": "2025-01-01",
    "shipmentDateFrom": "2025-01-01",
    "shipmentDateTo": "2025-01-01",
    "updateDateFrom": "2025-01-01T00:00:00Z",
    "updateDateTo": "2025-01-01T00:00:00Z"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderSourcePlatformType {#entity-OrderSourcePlatformType}
  
  Площадка-источник заказа:
  
  * `MARKET` — заказ, оформленный на Маркете.
  
  * `OTHER` — LaaS-заказ, созданный продавцом.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MARKET`, `OZON`, `WILDBERRIES`, `OTHER`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Список заказов в кабинете.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "orders": [
      {
        "orderId": 0,
        "campaignId": 1,
        "programType": "FBY",
        "externalOrderId": "example",
        "status": "PLACING",
        "substatus": "RESERVATION_EXPIRED",
        "creationDate": "2020-02-02T14:30:30+03:00",
        "updateDate": "2020-02-02T14:30:30+03:00",
        "paymentType": "PREPAID",
        "paymentMethod": "CASH_ON_DELIVERY",
        "fake": true,
        "items": [
          {
            "id": 0,
            "offerId": "example",
            "offerName": "example",
            "count": 0,
            "prices": {},
            "instances": [
              null
            ],
            "requiredInstanceTypes": [
              null
            ],
            "itemStatuses": [
              null
            ],
            "tags": [
              null
            ]
          }
        ],
        "prices": {
          "payment": {
            "value": 0.5,
            "currencyId": "RUR"
          },
          "subsidy": null,
          "cashback": null,
          "delivery": {
            "payment": null,
            "subsidy": null,
            "vat": "NO_VAT"
          }
        },
        "delivery": {
          "type": "DELIVERY",
          "serviceName": "example",
          "deliveryServiceId": 0,
          "warehouseId": "example",
          "deliveryPartnerType": "SHOP",
          "dispatchType": "UNKNOWN",
          "dates": {
            "fromDate": "2025-01-01",
            "toDate": "2025-01-01",
            "fromTime": "12:00:00",
            "toTime": "12:00:00",
            "realDeliveryDate": "2025-01-01"
          },
          "shipment": {
            "id": 0,
            "shipmentDate": "2025-01-01",
            "shipmentTime": "12:00:00"
          },
          "courier": {
            "address": {},
            "region": {}
          },
          "pickup": {
            "address": null,
            "region": null,
            "logisticPointId": 1,
            "outletCode": "example",
            "outletStorageLimitDate": "2025-01-01"
          },
          "transfer": {
            "courier": {},
            "eac": {}
          },
          "boxesLayout": [
            {}
          ],
          "tracks": [
            {}
          ],
          "estimated": true,
          "receiveBarcode": "example",
          "receiveCode": "example",
          "digitalGoods": {
            "type": "EMAIL",
            "steamLink": "example"
          }
        },
        "services": {
          "liftType": "NOT_NEEDED"
        },
        "buyerType": "PERSON",
        "notes": "example",
        "cancelRequested": true,
        "sourcePlatform": "MARKET"
      }
    ],
    "paging": {
      "nextPageToken": "example"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _orders_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderDTO](#entity-BusinessOrderDTO)[]
  
  Список заказов в кабинете.
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "orderId": 0,
      "campaignId": 1,
      "programType": "FBY",
      "externalOrderId": "example",
      "status": "PLACING",
      "substatus": "RESERVATION_EXPIRED",
      "creationDate": "2020-02-02T14:30:30+03:00",
      "updateDate": "2020-02-02T14:30:30+03:00",
      "paymentType": "PREPAID",
      "paymentMethod": "CASH_ON_DELIVERY",
      "fake": true,
      "items": [
        {
          "id": 0,
          "offerId": "example",
          "offerName": "example",
          "count": 0,
          "prices": {
            "payment": {},
            "subsidy": null,
            "cashback": null,
            "vat": "NO_VAT"
          },
          "instances": [
            {}
          ],
          "requiredInstanceTypes": [
            "CIS"
          ],
          "itemStatuses": [
            {}
          ],
          "tags": [
            "ULTIMA"
          ]
        }
      ],
      "prices": {
        "payment": null,
        "subsidy": null,
        "cashback": null,
        "delivery": {
          "payment": null,
          "subsidy": null,
          "vat": null
        }
      },
      "delivery": {
        "type": "DELIVERY",
        "serviceName": "example",
        "deliveryServiceId": 0,
        "warehouseId": "example",
        "deliveryPartnerType": "SHOP",
        "dispatchType": "UNKNOWN",
        "dates": {
          "fromDate": "2025-01-01",
          "toDate": "2025-01-01",
          "fromTime": "12:00:00",
          "toTime": "12:00:00",
          "realDeliveryDate": "2025-01-01"
        },
        "shipment": {
          "id": 0,
          "shipmentDate": "2025-01-01",
          "shipmentTime": "12:00:00"
        },
        "courier": {
          "address": {
            "country": "example",
            "postcode": "example",
            "city": "example",
            "district": "example",
            "subway": "example",
            "street": "example",
            "house": "example",
            "block": "example",
            "entrance": "example",
            "entryphone": "example",
            "floor": "example",
            "apartment": "example",
            "gps": {}
          },
          "region": {
            "id": 0,
            "name": "example",
            "type": "OTHER",
            "parent": null
          }
        },
        "pickup": {
          "address": null,
          "region": null,
          "logisticPointId": 1,
          "outletCode": "example",
          "outletStorageLimitDate": "2025-01-01"
        },
        "transfer": {
          "courier": {
            "fullName": "example",
            "phone": "example",
            "phoneExtension": "example",
            "vehicleNumber": "example",
            "vehicleDescription": "example"
          },
          "eac": {
            "eacType": "MERCHANT_TO_COURIER",
            "eacCode": "example"
          }
        },
        "boxesLayout": [
          {
            "items": [
              null
            ],
            "boxId": 0,
            "barcode": "example"
          }
        ],
        "tracks": [
          {
            "trackCode": "example",
            "deliveryServiceId": 0
          }
        ],
        "estimated": true,
        "receiveBarcode": "example",
        "receiveCode": "example",
        "digitalGoods": {
          "type": "EMAIL",
          "steamLink": "example"
        }
      },
      "services": {
        "liftType": "NOT_NEEDED"
      },
      "buyerType": "PERSON",
      "notes": "example",
      "cancelRequested": true,
      "sourcePlatform": "MARKET"
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
  
  Информация о страницах результатов.
  
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
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderPaymentType {#entity-OrderPaymentType}
  
  Тип оплаты заказа:
  
  * `PREPAID` — оплата при оформлении заказа.
  
  * `POSTPAID` — оплата при получении заказа.
  
  * `UNKNOWN` — неизвестный тип.
  
  Если параметр отсутствует, заказ будет оплачен при получении.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREPAID`, `POSTPAID`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderPaymentMethodType {#entity-OrderPaymentMethodType}
  
  Способ оплаты заказа:
  
  * Значения, если выбрана оплата при оформлении заказа (`"paymentType": "PREPAID"`):
  
    * `YANDEX` — банковской картой.
  
    * `APPLE_PAY` — Apple Pay (не используется).
  
    * `GOOGLE_PAY` — Google Pay (не используется).
  
    * `CREDIT` — в кредит.
  
    * `TINKOFF_CREDIT` — в кредит в Тинькофф Банке.
  
    * `TINKOFF_INSTALLMENTS` — рассрочка в Тинькофф Банке.
  
    * `EXTERNAL_CERTIFICATE` — подарочным сертификатом (например, из приложения «Сбербанк Онлайн»).
  
    * `SBP` — через систему быстрых платежей.
  
    * `B2B_ACCOUNT_PREPAYMENT` — заказ оплачивает организация.
  
    * `MICROCREDIT` - Сплит на основе МКК (Микрокредитной компании).
  
    * `BNPL_TBC` - BNPL через внешний банк TBC.
  
    * `DIGITAL_RUBLE` - Цифровой рубль.
  
  
  * Значения, если выбрана оплата при получении заказа (`"paymentType": "POSTPAID"`):
  
    * `CARD_ON_DELIVERY` — банковской картой.
  
    * `BOUND_CARD_ON_DELIVERY` — привязанной картой при получении.
  
    * `BNPL_BANK_ON_DELIVERY` — супер Сплитом.
  
    * `BNPL_ON_DELIVERY` — Сплитом.
  
    * `BNPL_TBYB` - Оплата после доставки на основе Сплита.
  
    * `CASH_ON_DELIVERY` — наличными.
  
    * `B2B_ACCOUNT_POSTPAYMENT` — заказ оплачивает организация после доставки.
  
  * `UNKNOWN` — неизвестный тип.
  
  Значение по умолчанию: `CASH_ON_DELIVERY`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CASH_ON_DELIVERY`, `CARD_ON_DELIVERY`, `BOUND_CARD_ON_DELIVERY`, `BNPL_BANK_ON_DELIVERY`, `BNPL_ON_DELIVERY`, `YANDEX`, `APPLE_PAY`, `EXTERNAL_CERTIFICATE`, `CREDIT`, `GOOGLE_PAY`, `TINKOFF_CREDIT`, `SBP`, `TINKOFF_INSTALLMENTS`, `B2B_ACCOUNT_PREPAYMENT`, `B2B_ACCOUNT_POSTPAYMENT`, `MICROCREDIT`, `BNPL_TBYB`, `BNPL_TBC`, `DIGITAL_RUBLE`, `UNKNOWN`
  
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
  
  ### ItemPriceDTO {#entity-ItemPriceDTO}
  
  Информация о выплатах и вознаграждениях.
  
  {% note info "Как рассчитывается стоимость всех единиц товара и вознаграждение продавцу" %}
  
  * Стоимость всех единиц товара складывается из параметров `payment` и `cashback`.
  * Общая сумма вознаграждений продавцу возвращается в параметре `subsidy`.
  * Значение `payment`, `cashback` и `subsidy` может отличаться от стоимости в каталоге, потому что информация об акциях магазина не возвращается.
  * Если в заказе несколько единиц товаров, в параметрах возвращается суммарное значение.
  * Все суммы указаны в валюте магазина.
  
  {% endnote %}
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _cashback_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Сумма, которая оплачена баллами Плюса.
  
  
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
  
  _payment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Общая стоимость всех единиц товара.
  
  
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
  
  _subsidy_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Общая сумма вознаграждений продавцу.
  
  
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
  
  _vat_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderVatType](#entity-OrderVatType)
  
  НДС на товар.
  
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
    "payment": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "subsidy": null,
    "cashback": null,
    "vat": "NO_VAT"
  }
  ```
  
  {% endcut %}
  
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
  
  ### OrderItemInstanceType {#entity-OrderItemInstanceType}
  
  Вид маркировки товара:
  
  * `CIS` — КИЗ, идентификатор единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go). Обязателен для заполнения.
  
  * `CIS_OPTIONAL` — КИЗ, идентификатор единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/). Необязателен для заполнения, но в ближайшее время потребуется его передача.
  
  * `UIN` — УИН, уникальный идентификационный номер.
  
  * `RNPT` — РНПТ, регистрационный номер партии товара.
  
  * `GTD` — номер ГТД, грузовой таможенной декларации.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CIS`, `CIS_OPTIONAL`, `UIN`, `RNPT`, `GTD`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemUnitStatusType {#entity-OrderItemUnitStatusType}
  
  Статус единицы товара в заказе.
  
  * `CREATED` — создана.
  
  * `SHIPPED` — передана в доставку.
  
  * `CANCELLED` — отменена или удалена из заказа.
  
  * `DELIVERED_TO_BUYER` — передана покупателю.
  
  * `LOST` — утеряна.
  
  * `REJECTED` — невыкупленная.
  
  * `RETURNED` — возвращенная.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `SHIPPED`, `CANCELLED`, `DELIVERED_TO_BUYER`, `LOST`, `REJECTED`, `RETURNED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemUnitStatusDTO {#entity-OrderItemUnitStatusDTO}
  
  Количество единиц товара с определенным статусом.
  
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
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemUnitStatusType](#entity-OrderItemUnitStatusType)
  
  Статус единицы товара в заказе.
  
  * `CREATED` — создана.
  
  * `SHIPPED` — передана в доставку.
  
  * `CANCELLED` — отменена или удалена из заказа.
  
  * `DELIVERED_TO_BUYER` — передана покупателю.
  
  * `LOST` — утеряна.
  
  * `REJECTED` — невыкупленная.
  
  * `RETURNED` — возвращенная.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `SHIPPED`, `CANCELLED`, `DELIVERED_TO_BUYER`, `LOST`, `REJECTED`, `RETURNED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "CREATED",
    "count": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemTagType {#entity-OrderItemTagType}
  
  Признак товара:
  
  * `ULTIMA` — премиум-товар.
  * `SAFE_TAG` — товар с [защитной меткой](*safe-tag).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ULTIMA`, `SAFE_TAG`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderItemDTO {#entity-BusinessOrderItemDTO}
  
  Информация о товаре.
  
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
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в заказе.
  
  Позволяет идентифицировать товар в рамках заказа.
  
  {.table-cell}
  ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  Идентификатор товарного предложения.
  
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
  
  _offerName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название товара.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemInstanceDTO](#entity-OrderItemInstanceDTO)[] &#124; null
  
  Информация о маркировке единиц товара.
  
  Возвращаются данные для маркировки, переданные в запросе:
  
  * Для DBS — [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md) или [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
  * Для FBS и EXPRESS — [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
  
  Для FBY возвращаются коды маркировки, переданные во время поставки.
  
  Если магазин еще не передавал коды для этого заказа, `instances` отсутствует.
  
  
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
  
  _itemStatuses_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemUnitStatusDTO](#entity-OrderItemUnitStatusDTO)[] &#124; null
  
  Информация о статусах отдельных единиц товара в заказе.
  
  Если данных о статусах отдельных единиц товара нет, поле отсутствует.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "status": "CREATED",
      "count": 0
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _prices_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ItemPriceDTO](#entity-ItemPriceDTO)
  
  Информация о выплатах и вознаграждениях.
  
  
  Информация о выплатах и вознаграждениях.
  
  {% note info "Как рассчитывается стоимость всех единиц товара и вознаграждение продавцу" %}
  
  * Стоимость всех единиц товара складывается из параметров `payment` и `cashback`.
  * Общая сумма вознаграждений продавцу возвращается в параметре `subsidy`.
  * Значение `payment`, `cashback` и `subsidy` может отличаться от стоимости в каталоге, потому что информация об акциях магазина не возвращается.
  * Если в заказе несколько единиц товаров, в параметрах возвращается суммарное значение.
  * Все суммы указаны в валюте магазина.
  
  {% endnote %}
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "payment": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "subsidy": null,
    "cashback": null,
    "vat": "NO_VAT"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _requiredInstanceTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemInstanceType](#entity-OrderItemInstanceType)[] &#124; null
  
  Список необходимых маркировок товара.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "CIS"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _tags_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemTagType](#entity-OrderItemTagType)[] &#124; null
  
  Признаки товара.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "ULTIMA"
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
    "offerId": "example",
    "offerName": "example",
    "count": 0,
    "prices": {
      "payment": {
        "value": 0.5,
        "currencyId": "RUR"
      },
      "subsidy": null,
      "cashback": null,
      "vat": "NO_VAT"
    },
    "instances": [
      {
        "cis": "example",
        "cisFull": "example",
        "uin": "example",
        "rnpt": "example",
        "gtd": "example",
        "countryCode": "RU"
      }
    ],
    "requiredInstanceTypes": [
      "CIS"
    ],
    "itemStatuses": [
      {
        "status": "CREATED",
        "count": 0
      }
    ],
    "tags": [
      "ULTIMA"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeliveryPriceDTO {#entity-DeliveryPriceDTO}
  
  Информация о стоимости доставки, включая подъем на этаж.
  
  {% note info "Как рассчитывается стоимость доставки" %}
  
  * Стоимость доставки складывается из параметров `payment` и `subsidy`.
  * Все суммы указаны в валюте магазина.
  
  {% endnote %}
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _payment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Платеж покупателя за доставку.
  
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
  
  _subsidy_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Вознаграждение Маркета за доставку.
  
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
  
  _vat_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderVatType](#entity-OrderVatType)
  
  НДС на доставку.
  
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
    "payment": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "subsidy": null,
    "vat": "NO_VAT"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderPriceDTO {#entity-OrderPriceDTO}
  
  Информация о стоимости заказа.
  
  {% note info "Как рассчитывается стоимость заказа, доставки и вознаграждение продавцу" %}
  
  * Стоимость товаров в заказе складывается из параметров `payment` и `cashback`.
  * Общая сумма вознаграждений продавцу возвращается в параметре `subsidy`.
  * Значение `payment`, `cashback` и `subsidy` может отличаться от стоимости в каталоге, потому что информация об акциях магазина не возвращается.
  * Стоимость доставки складывается из параметров `payment` и `subsidy` в `delivery`.
  * Все суммы указаны в валюте магазина.
  
  {% endnote %}
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _cashback_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Сумма, которая оплачена баллами Плюса.
  
  Возвращается баллами.
  
  
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
  
  _delivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DeliveryPriceDTO](#entity-DeliveryPriceDTO)
  
  Информация о стоимости доставки, включая подъем на этаж.
  
  
  Информация о стоимости доставки, включая подъем на этаж.
  
  {% note info "Как рассчитывается стоимость доставки" %}
  
  * Стоимость доставки складывается из параметров `payment` и `subsidy`.
  * Все суммы указаны в валюте магазина.
  
  {% endnote %}
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "payment": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "subsidy": null,
    "vat": "NO_VAT"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _payment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Сумма платежа покупателя.
  
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
  
  _subsidy_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CurrencyValueDTO](#entity-CurrencyValueDTO)
  
  Общая сумма вознаграждений продавцу.
  
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "payment": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "subsidy": null,
    "cashback": null,
    "delivery": {
      "payment": null,
      "subsidy": null,
      "vat": "NO_VAT"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderDeliveryType {#entity-OrderDeliveryType}
  
  Способ доставки заказа:
  
  * `DELIVERY` — курьерская доставка.
  
  * `PICKUP` — самовывоз.
  
  * `POST` — почта.
  
  * `DIGITAL` — для цифровых товаров.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DELIVERY`, `PICKUP`, `POST`, `DIGITAL`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderDeliveryPartnerType {#entity-OrderDeliveryPartnerType}
  
  Тип сотрудничества со службой доставки в рамках конкретного заказа:
  
  * `SHOP` — магазин работает со службой доставки напрямую или доставляет заказы самостоятельно.
  
  * `YANDEX_MARKET` — магазин работает со службой доставки через Маркет.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `SHOP`, `YANDEX_MARKET`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderDeliveryDispatchType {#entity-OrderDeliveryDispatchType}
  
  Способ доставки:
  
  * `BUYER` — курьерская доставка покупателю.
  
  * `MARKET_BRANDED_OUTLET` — доставка в пункт выдачи заказов Маркета.
  
  * `SHOP_OUTLET` — доставка в пункт выдачи заказов магазина.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNKNOWN`, `BUYER`, `MARKET_BRANDED_OUTLET`, `SHOP_OUTLET`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderDeliveryDatesDTO {#entity-BusinessOrderDeliveryDatesDTO}
  
  Диапазон дат доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Ближайшая дата доставки.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _fromTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;time&gt;
  
  Начало интервала времени доставки.
  
  Передается только вместе с параметром `type=DELIVERY`.
  
  Формат времени: 24-часовой, `ЧЧ:ММ`. Вместо `ММ` всегда указывайте `00` (исключение — `23:59`).
  
  Минимальное значение: `00:00`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `12:00:00`
  {.table-cell}
  ||
  ||
  
  _realDeliveryDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата, когда товар доставлен до пункта выдачи заказа (в случае самовывоза) или до покупателя (если заказ доставляет курьер).
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _toDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Самая поздняя дата доставки.
  
  Если `toDate` не указан, считается дата в параметре `fromDate`.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _toTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;time&gt;
  
  Конец интервала времени доставки.
  
  Передается только вместе с параметром `type=DELIVERY`.
  
  Формат времени: 24-часовой, `ЧЧ:ММ`. Вместо `ММ` всегда указывайте `00` (исключение — `23:59`).
  
  Максимальное значение: `23:59`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `12:00:00`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01",
    "fromTime": "12:00:00",
    "toTime": "12:00:00",
    "realDeliveryDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderShipmentDTO {#entity-BusinessOrderShipmentDTO}
  
  Информация об отгрузке заказа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _shipmentDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата отгрузки.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer &#124; null
  
  Идентификатор отгрузки.
  {.table-cell}
  ||
  ||
  
  _shipmentTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;time&gt; &#124; null
  
  Время отгрузки.
  
  _Example:_{.json-schema-reset .json-schema-example} `12:00:00`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "shipmentDate": "2025-01-01",
    "shipmentTime": "12:00:00"
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
  
  ### BusinessOrderDeliveryAddressDTO {#entity-BusinessOrderDeliveryAddressDTO}
  
  Адрес доставки.
  
  Указывается, если параметр `type` принимает значение `DELIVERY`, `POST` или `PICKUP` (только для модели DBS). Если `type=PICKUP`, возвращается адрес пункта выдачи.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _apartment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер квартиры или офиса.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _block_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Корпус.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _city_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Город или населенный пункт.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _country_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Страна.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _district_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Район.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _entrance_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер подъезда.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _entryphone_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Код домофона.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _floor_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Этаж.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _gps_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [GpsDTO](#entity-GpsDTO)
  
  GPS-координаты.
  
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
  ||
  
  _house_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер дома.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _postcode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Почтовый индекс.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _street_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Улица.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _subway_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Станция метро.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "country": "example",
    "postcode": "example",
    "city": "example",
    "district": "example",
    "subway": "example",
    "street": "example",
    "house": "example",
    "block": "example",
    "entrance": "example",
    "entryphone": "example",
    "floor": "example",
    "apartment": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### RegionType {#entity-RegionType}
  
  Тип региона.
  
  Возможные значения:
  
  * `CITY_DISTRICT` — район города.
  
  * `CITY` — крупный город.
  
  * `CONTINENT` — континент.
  
  * `COUNTRY_DISTRICT` — область.
  
  * `COUNTRY` — страна.
  
  * `REGION` — регион.
  
  * `REPUBLIC_AREA` — район субъекта федерации.
  
  * `REPUBLIC` — субъект федерации.
  
  * `SUBWAY_STATION` — станция метро.
  
  * `VILLAGE` — город.
  
  * `OTHER` — неизвестный регион.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OTHER`, `CONTINENT`, `REGION`, `COUNTRY`, `COUNTRY_DISTRICT`, `REPUBLIC`, `CITY`, `VILLAGE`, `CITY_DISTRICT`, `SUBWAY_STATION`, `REPUBLIC_AREA`
  
  </div>
  
  <div class="openapi-entity">
  
  ### RegionDTO {#entity-RegionDTO}
  
  Регион доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название региона.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [RegionType](#entity-RegionType)
  
  Тип региона.
  
  Тип региона.
  
  Возможные значения:
  
  * `CITY_DISTRICT` — район города.
  
  * `CITY` — крупный город.
  
  * `CONTINENT` — континент.
  
  * `COUNTRY_DISTRICT` — область.
  
  * `COUNTRY` — страна.
  
  * `REGION` — регион.
  
  * `REPUBLIC_AREA` — район субъекта федерации.
  
  * `REPUBLIC` — субъект федерации.
  
  * `SUBWAY_STATION` — станция метро.
  
  * `VILLAGE` — город.
  
  * `OTHER` — неизвестный регион.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OTHER`, `CONTINENT`, `REGION`, `COUNTRY`, `COUNTRY_DISTRICT`, `REPUBLIC`, `CITY`, `VILLAGE`, `CITY_DISTRICT`, `SUBWAY_STATION`, `REPUBLIC_AREA`
  {.table-cell}
  ||
  ||
  
  _parent_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RegionDTO](#entity-RegionDTO)
  
  Информация о родительском регионе.
  
  Указываются родительские регионы до уровня страны.
  
  
  Регион доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "parent": null
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "parent": {
      "id": 0,
      "name": "example",
      "type": null,
      "parent": null
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderCourierDeliveryDTO {#entity-BusinessOrderCourierDeliveryDTO}
  
  Информация о курьерской доставке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderDeliveryAddressDTO](#entity-BusinessOrderDeliveryAddressDTO)
  
  Адрес доставки.
  
  Указывается, если параметр `type` принимает значение `DELIVERY`, `POST` или `PICKUP` (только для модели DBS). Если `type=PICKUP`, возвращается адрес пункта выдачи.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "country": "example",
    "postcode": "example",
    "city": "example",
    "district": "example",
    "subway": "example",
    "street": "example",
    "house": "example",
    "block": "example",
    "entrance": "example",
    "entryphone": "example",
    "floor": "example",
    "apartment": "example",
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
  
  _region_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RegionDTO](#entity-RegionDTO)
  
  Регион доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "parent": null
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "address": {
      "country": "example",
      "postcode": "example",
      "city": "example",
      "district": "example",
      "subway": "example",
      "street": "example",
      "house": "example",
      "block": "example",
      "entrance": "example",
      "entryphone": "example",
      "floor": "example",
      "apartment": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LogisticPointId {#entity-LogisticPointId}
  
  Идентификатор пункта выдачи.
  
  Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderPickupDeliveryDTO {#entity-BusinessOrderPickupDeliveryDTO}
  
  Информация о доставке в пункт выдачи.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderDeliveryAddressDTO](#entity-BusinessOrderDeliveryAddressDTO)
  
  Адрес доставки.
  
  Указывается, если параметр `type` принимает значение `DELIVERY`, `POST` или `PICKUP` (только для модели DBS). Если `type=PICKUP`, возвращается адрес пункта выдачи.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "country": "example",
    "postcode": "example",
    "city": "example",
    "district": "example",
    "subway": "example",
    "street": "example",
    "house": "example",
    "block": "example",
    "entrance": "example",
    "entryphone": "example",
    "floor": "example",
    "apartment": "example",
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
  
  _logisticPointId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [LogisticPointId](#entity-LogisticPointId)
  
  Идентификатор пункта выдачи.
  
  Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _outletCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор пункта самовывоза, присвоенный магазином.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _outletStorageLimitDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Дата, до которой заказ будет храниться в пункте выдачи. Возвращается, когда заказ переходит в статус `PICKUP`.
  
  Один раз дату можно поменять с помощью метода [PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md).
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _region_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RegionDTO](#entity-RegionDTO)
  
  Регион доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "parent": null
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "address": {
      "country": "example",
      "postcode": "example",
      "city": "example",
      "district": "example",
      "subway": "example",
      "street": "example",
      "house": "example",
      "block": "example",
      "entrance": "example",
      "entryphone": "example",
      "floor": "example",
      "apartment": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    },
    "logisticPointId": 1,
    "outletCode": "example",
    "outletStorageLimitDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderCourierDTO {#entity-OrderCourierDTO}
  
  Информация о курьере.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fullName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Полное имя.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _phone_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер телефона.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _phoneExtension_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Добавочный номер телефона.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _vehicleDescription_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание транспортного средства. Например, модель и цвет.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _vehicleNumber_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер транспортного средства.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullName": "example",
    "phone": "example",
    "phoneExtension": "example",
    "vehicleNumber": "example",
    "vehicleDescription": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderDeliveryEacType {#entity-OrderDeliveryEacType}
  
  Тип кода подтверждения ЭАПП:
  
  * `MERCHANT_TO_COURIER` (временно не возвращается) — продавец передает код курьеру для получения невыкупа.
  
  * `COURIER_TO_MERCHANT` — курьер передает код продавцу для получения заказа.
  
  * `CHECKING_BY_MERCHANT` — продавец проверяет код на своей стороне.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MERCHANT_TO_COURIER`, `COURIER_TO_MERCHANT`, `CHECKING_BY_MERCHANT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderEacDTO {#entity-BusinessOrderEacDTO}
  
  Информация о коде подтверждения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _eacType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderDeliveryEacType](#entity-OrderDeliveryEacType)
  
  Тип кода подтверждения ЭАПП.
  
  Тип кода подтверждения ЭАПП:
  
  * `MERCHANT_TO_COURIER` (временно не возвращается) — продавец передает код курьеру для получения невыкупа.
  
  * `COURIER_TO_MERCHANT` — курьер передает код продавцу для получения заказа.
  
  * `CHECKING_BY_MERCHANT` — продавец проверяет код на своей стороне.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MERCHANT_TO_COURIER`, `COURIER_TO_MERCHANT`, `CHECKING_BY_MERCHANT`
  {.table-cell}
  ||
  ||
  
  _eacCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Код подтверждения ЭАПП (для типа `MERCHANT_TO_COURIER`).
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "eacType": "MERCHANT_TO_COURIER",
    "eacCode": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderTransferDTO {#entity-BusinessOrderTransferDTO}
  
  Информация о курьере и код подтверждения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _courier_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderCourierDTO](#entity-OrderCourierDTO)
  
  Информация о курьере.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fullName": "example",
    "phone": "example",
    "phoneExtension": "example",
    "vehicleNumber": "example",
    "vehicleDescription": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _eac_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderEacDTO](#entity-BusinessOrderEacDTO)
  
  Информация о коде подтверждения.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "eacType": "MERCHANT_TO_COURIER",
    "eacCode": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "courier": {
      "fullName": "example",
      "phone": "example",
      "phoneExtension": "example",
      "vehicleNumber": "example",
      "vehicleDescription": "example"
    },
    "eac": {
      "eacType": "MERCHANT_TO_COURIER",
      "eacCode": "example"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderBoxLayoutPartialCountDTO {#entity-BusinessOrderBoxLayoutPartialCountDTO}
  
  Информация о части товара в коробке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _current_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Номер части, начиная с 1.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _total_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  На сколько всего частей разделен товар.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `2`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "current": 1,
    "total": 2
  }
  ```
  
  {% endcut %}
  
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
  
  ### BusinessOrderBoxLayoutItemDTO {#entity-BusinessOrderBoxLayoutItemDTO}
  
  Информация о товаре в коробке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в заказе.
  
  Параметр `id` в `items`.
  
  {.table-cell}
  ||
  ||
  
  _fullCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара в коробке.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BriefOrderItemInstanceDTO](#entity-BriefOrderItemInstanceDTO)[] &#124; null
  
  Переданные коды маркировки.
  
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
  ||
  
  _partialCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderBoxLayoutPartialCountDTO](#entity-BusinessOrderBoxLayoutPartialCountDTO)
  
  Информация о части товара в коробке.
  
  
  Информация о части товара в коробке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "current": 1,
    "total": 2
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "fullCount": 1,
    "partialCount": {
      "current": 1,
      "total": 2
    },
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
  
  ### BusinessOrderBoxLayoutDTO {#entity-BusinessOrderBoxLayoutDTO}
  
  Информация о коробке (для заказов в кабинете).
  
  #|
  || **Name** | **Description** ||
  ||
  
  _barcode_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор грузового места в системе магазина.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _boxId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор коробки.
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderBoxLayoutItemDTO](#entity-BusinessOrderBoxLayoutItemDTO)[]
  
  Список товаров в коробке.
  
  Если в коробке едет часть большого товара, в списке может быть только один пункт.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "fullCount": 1,
      "partialCount": {
        "current": 1,
        "total": 2
      },
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
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "items": [
      {
        "id": 0,
        "fullCount": 1,
        "partialCount": {
          "current": 1,
          "total": 2
        },
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
    "boxId": 0,
    "barcode": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderTrackDTO {#entity-OrderTrackDTO}
  
  Информация о трек-номере посылки (DBS).
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryServiceId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор службы доставки. Информацию о службе доставки можно получить с помощью запроса [GET delivery/services](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-services/getDeliveryServices.md).
  {.table-cell}
  ||
  ||
  
  _trackCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Трек‑номер посылки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "trackCode": "example",
    "deliveryServiceId": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DigitalGoodsDeliveryType {#entity-DigitalGoodsDeliveryType}
  
  Способ получения цифрового товара:
  
  * `EMAIL` — код активации по почте: покупатель получит письмо с кодом и инструкцией на почту.
  
  * `ACTIVATION_CODE` — код активации в заказе на Маркете: покупатель получит инструкцию и код в чате с магазином, а в списке заказов сможет скопировать код.
  
  * `STEAM_GIFT` — игры подарком в Steam: вы получите от покупателя ссылку формата https://s.team/p/m**-***/******** на добавление в друзья. Перейдите по ссылке, добавьте покупателя в друзья и отправьте ему игру. В течение трех часов передайте Маркету статус, что заказ доставлен — через API или на странице заказа.
  
  * `CHAT` — игры и товары в чате с покупателем на Маркете: покупатель получит сертификат в чате с магазином. Передайте Маркету статус, что заказ доставлен — через API или на странице заказа.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `EMAIL`, `ACTIVATION_CODE`, `STEAM_GIFT`, `CHAT`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DigitalGoodsDeliveryDetailsDTO {#entity-DigitalGoodsDeliveryDetailsDTO}
  
  Информация о доставке цифрового товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DigitalGoodsDeliveryType](#entity-DigitalGoodsDeliveryType)
  
  Тип цифрового товара.
  
  Способ получения цифрового товара:
  
  * `EMAIL` — код активации по почте: покупатель получит письмо с кодом и инструкцией на почту.
  
  * `ACTIVATION_CODE` — код активации в заказе на Маркете: покупатель получит инструкцию и код в чате с магазином, а в списке заказов сможет скопировать код.
  
  * `STEAM_GIFT` — игры подарком в Steam: вы получите от покупателя ссылку формата https://s.team/p/m**-***/******** на добавление в друзья. Перейдите по ссылке, добавьте покупателя в друзья и отправьте ему игру. В течение трех часов передайте Маркету статус, что заказ доставлен — через API или на странице заказа.
  
  * `CHAT` — игры и товары в чате с покупателем на Маркете: покупатель получит сертификат в чате с магазином. Передайте Маркету статус, что заказ доставлен — через API или на странице заказа.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `EMAIL`, `ACTIVATION_CODE`, `STEAM_GIFT`, `CHAT`
  {.table-cell}
  ||
  ||
  
  _steamLink_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Ссылка на Steam-аккаунт покупателя. Передается только для типа `STEAM_GIFT`.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "EMAIL",
    "steamLink": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderDeliveryDTO {#entity-BusinessOrderDeliveryDTO}
  
  Информация о доставке заказа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dates_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderDeliveryDatesDTO](#entity-BusinessOrderDeliveryDatesDTO)
  
  Диапазон дат доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "2025-01-01",
    "toDate": "2025-01-01",
    "fromTime": "12:00:00",
    "toTime": "12:00:00",
    "realDeliveryDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryPartnerType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderDeliveryPartnerType](#entity-OrderDeliveryPartnerType)
  
  Тип сотрудничества со службой доставки в рамках указанного заказа.
  
  Тип сотрудничества со службой доставки в рамках конкретного заказа:
  
  * `SHOP` — магазин работает со службой доставки напрямую или доставляет заказы самостоятельно.
  
  * `YANDEX_MARKET` — магазин работает со службой доставки через Маркет.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `SHOP`, `YANDEX_MARKET`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _deliveryServiceId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор службы доставки.
  {.table-cell}
  ||
  ||
  
  _serviceName_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название службы доставки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderDeliveryType](#entity-OrderDeliveryType)
  
  Способ доставки заказа.
  
  
  Способ доставки заказа:
  
  * `DELIVERY` — курьерская доставка.
  
  * `PICKUP` — самовывоз.
  
  * `POST` — почта.
  
  * `DIGITAL` — для цифровых товаров.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DELIVERY`, `PICKUP`, `POST`, `DIGITAL`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _boxesLayout_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderBoxLayoutDTO](#entity-BusinessOrderBoxLayoutDTO)[] &#124; null
  
  Раскладка товаров по коробкам.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "items": [
        {
          "id": 0,
          "fullCount": 1,
          "partialCount": {
            "current": 1,
            "total": 2
          },
          "instances": [
            {}
          ]
        }
      ],
      "boxId": 0,
      "barcode": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _courier_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderCourierDeliveryDTO](#entity-BusinessOrderCourierDeliveryDTO)
  
  Информация о курьерской доставке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "address": {
      "country": "example",
      "postcode": "example",
      "city": "example",
      "district": "example",
      "subway": "example",
      "street": "example",
      "house": "example",
      "block": "example",
      "entrance": "example",
      "entryphone": "example",
      "floor": "example",
      "apartment": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _digitalGoods_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DigitalGoodsDeliveryDetailsDTO](#entity-DigitalGoodsDeliveryDetailsDTO)
  
  Информация о доставке цифрового товара.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "EMAIL",
    "steamLink": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _dispatchType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderDeliveryDispatchType](#entity-OrderDeliveryDispatchType)
  
  Способ доставки:
  
  * `BUYER` — курьерская доставка покупателю.
  
  * `MARKET_BRANDED_OUTLET` — доставка в пункт выдачи заказов Маркета.
  
  * `SHOP_OUTLET` — доставка в пункт выдачи заказов магазина.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNKNOWN`, `BUYER`, `MARKET_BRANDED_OUTLET`, `SHOP_OUTLET`
  {.table-cell}
  ||
  ||
  
  _estimated_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Приблизительная ли дата доставки.
  {.table-cell}
  ||
  ||
  
  _pickup_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderPickupDeliveryDTO](#entity-BusinessOrderPickupDeliveryDTO)
  
  Информация о доставке в пункт выдачи.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "address": {
      "country": "example",
      "postcode": "example",
      "city": "example",
      "district": "example",
      "subway": "example",
      "street": "example",
      "house": "example",
      "block": "example",
      "entrance": "example",
      "entryphone": "example",
      "floor": "example",
      "apartment": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    },
    "logisticPointId": 1,
    "outletCode": "example",
    "outletStorageLimitDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _receiveBarcode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  **Только для модели LaaS**
  
  Штрихкод получения заказа на ПВЗ.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _receiveCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  **Только для модели LaaS**
  
  Код получения заказа на ПВЗ.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _shipment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderShipmentDTO](#entity-BusinessOrderShipmentDTO)
  
  Информация об отгрузке.
  
  Информация об отгрузке заказа.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "shipmentDate": "2025-01-01",
    "shipmentTime": "12:00:00"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _tracks_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderTrackDTO](#entity-OrderTrackDTO)[] &#124; null
  
  Информация для отслеживания посылки.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "trackCode": "example",
      "deliveryServiceId": 0
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _transfer_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderTransferDTO](#entity-BusinessOrderTransferDTO)
  
  Информация о курьере и код подтверждения.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "courier": {
      "fullName": "example",
      "phone": "example",
      "phoneExtension": "example",
      "vehicleNumber": "example",
      "vehicleDescription": "example"
    },
    "eac": {
      "eacType": "MERCHANT_TO_COURIER",
      "eacCode": "example"
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warehouseId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор склада в системе магазина, на который сформирован заказ.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "DELIVERY",
    "serviceName": "example",
    "deliveryServiceId": 0,
    "warehouseId": "example",
    "deliveryPartnerType": "SHOP",
    "dispatchType": "UNKNOWN",
    "dates": {
      "fromDate": "2025-01-01",
      "toDate": "2025-01-01",
      "fromTime": "12:00:00",
      "toTime": "12:00:00",
      "realDeliveryDate": "2025-01-01"
    },
    "shipment": {
      "id": 0,
      "shipmentDate": "2025-01-01",
      "shipmentTime": "12:00:00"
    },
    "courier": {
      "address": {
        "country": "example",
        "postcode": "example",
        "city": "example",
        "district": "example",
        "subway": "example",
        "street": "example",
        "house": "example",
        "block": "example",
        "entrance": "example",
        "entryphone": "example",
        "floor": "example",
        "apartment": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        }
      },
      "region": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "parent": null
      }
    },
    "pickup": {
      "address": null,
      "region": null,
      "logisticPointId": 1,
      "outletCode": "example",
      "outletStorageLimitDate": "2025-01-01"
    },
    "transfer": {
      "courier": {
        "fullName": "example",
        "phone": "example",
        "phoneExtension": "example",
        "vehicleNumber": "example",
        "vehicleDescription": "example"
      },
      "eac": {
        "eacType": "MERCHANT_TO_COURIER",
        "eacCode": "example"
      }
    },
    "boxesLayout": [
      {
        "items": [
          {
            "id": 0,
            "fullCount": 1,
            "partialCount": {},
            "instances": [
              null
            ]
          }
        ],
        "boxId": 0,
        "barcode": "example"
      }
    ],
    "tracks": [
      {
        "trackCode": "example",
        "deliveryServiceId": 0
      }
    ],
    "estimated": true,
    "receiveBarcode": "example",
    "receiveCode": "example",
    "digitalGoods": {
      "type": "EMAIL",
      "steamLink": "example"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderLiftType {#entity-OrderLiftType}
  
  Тип подъема заказа на этаж:
  
  * `NOT_NEEDED` — не требуется.
  
  * `MANUAL` — ручной.
  
  * `ELEVATOR` — лифт.
  
  * `CARGO_ELEVATOR` — грузовой лифт.
  
  * `FREE` — любой из перечисленных выше, если включена опция бесплатного подъема.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `NOT_NEEDED`, `MANUAL`, `ELEVATOR`, `CARGO_ELEVATOR`, `FREE`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderServicesDTO {#entity-BusinessOrderServicesDTO}
  
  Услуги, добавленные в заказ.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _liftType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderLiftType](#entity-OrderLiftType)
  
  Тип подъема заказа на этаж:
  
  * `NOT_NEEDED` — не требуется.
  
  * `MANUAL` — ручной.
  
  * `ELEVATOR` — лифт.
  
  * `CARGO_ELEVATOR` — грузовой лифт.
  
  * `FREE` — любой из перечисленных выше, если включена опция бесплатного подъема.
  
  * `UNKNOWN` — неизвестный тип.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `NOT_NEEDED`, `MANUAL`, `ELEVATOR`, `CARGO_ELEVATOR`, `FREE`, `UNKNOWN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "liftType": "NOT_NEEDED"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ItemId {#entity-ItemId}
  
  Идентификатор товара в заказе.
  
  Позволяет идентифицировать товар в рамках заказа.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderLineServiceArticle {#entity-BusinessOrderLineServiceArticle}
  
  Артикул услуги в системе продавца.
  
  Уникальный идентификатор, который продавец задаёт при создании услуги. Используется для всех изменений услуги в рамках заказа.
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderLineServiceStatusType {#entity-BusinessOrderLineServiceStatusType}
  
  Статус единицы услуги в заказе.
  
  * `CREATED` — создана.
  
  * `PROVIDED` — оказана.
  
  * `CANCELLED` — отменена.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `PROVIDED`, `CANCELLED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderLineServiceStatusDTO {#entity-BusinessOrderLineServiceStatusDTO}
  
  Количество единиц услуги с определенным статусом.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц услуги.
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderLineServiceStatusType](#entity-BusinessOrderLineServiceStatusType)
  
  Статус единицы услуги в заказе.
  
  * `CREATED` — создана.
  
  * `PROVIDED` — оказана.
  
  * `CANCELLED` — отменена.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CREATED`, `PROVIDED`, `CANCELLED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "CREATED",
    "count": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderLineServiceCancelReasonType {#entity-BusinessOrderLineServiceCancelReasonType}
  
  Причина отмены услуги.
  
  * `USER_REQUESTED` — покупатель отказался от услуги.
  
  * `SHOP_UNABLE_TO_RENDER` — продавец или его исполнитель не может оказать услугу.
  
  * `USER_UNREACHABLE` — не удалось связаться с покупателем по правилам DBS.
  
  * `UNKNOWN` — неизвестная причина.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER_REQUESTED`, `SHOP_UNABLE_TO_RENDER`, `USER_UNREACHABLE`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderLineServiceDTO {#entity-BusinessOrderLineServiceDTO}
  
  Услуга в составе заказа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _count_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц услуги на момент заказа.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _currency_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
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
  
  _itemId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ItemId](#entity-ItemId)
  
  Идентификатор товара в заказе.
  
  Позволяет идентифицировать товар в рамках заказа.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _serviceArticle_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderLineServiceArticle](#entity-BusinessOrderLineServiceArticle)
  
  Артикул услуги в системе продавца.
  
  Уникальный идентификатор, который продавец задаёт при создании услуги. Используется для всех изменений услуги в рамках заказа.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _shopSku_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  SKU товара услуги в системе продавца.
  
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
  
  _statuses_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderLineServiceStatusDTO](#entity-BusinessOrderLineServiceStatusDTO)[]
  
  Статусы единиц услуги.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "status": "CREATED",
      "count": 0
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _unitPrice_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Цена услуги за единицу на момент заказа.
  {.table-cell}
  ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время последнего обновления услуги.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2026-08-05T10:15:30+03:00`
  {.table-cell}
  ||
  ||
  
  _cancelReason_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderLineServiceCancelReasonType](#entity-BusinessOrderLineServiceCancelReasonType)
  
  Причина отмены услуги.
  
  Причина отмены услуги.
  
  * `USER_REQUESTED` — покупатель отказался от услуги.
  
  * `SHOP_UNABLE_TO_RENDER` — продавец или его исполнитель не может оказать услугу.
  
  * `USER_UNREACHABLE` — не удалось связаться с покупателем по правилам DBS.
  
  * `UNKNOWN` — неизвестная причина.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `USER_REQUESTED`, `SHOP_UNABLE_TO_RENDER`, `USER_UNREACHABLE`, `UNKNOWN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "itemId": 1,
    "serviceArticle": "example",
    "shopSku": "example",
    "count": 0,
    "unitPrice": 0.5,
    "currency": "RUR",
    "statuses": [
      {
        "status": "CREATED",
        "count": 0
      }
    ],
    "cancelReason": "USER_REQUESTED",
    "updatedAt": "2026-08-05T10:15:30+03:00"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBuyerType {#entity-OrderBuyerType}
  
  Тип покупателя:
  
  * `PERSON` — физическое лицо.
  
  * `BUSINESS` — организация.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERSON`, `BUSINESS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessOrderDTO {#entity-BusinessOrderDTO}
  
  Информация о заказе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _creationDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время оформления заказа.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  ||
  
  _delivery_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderDeliveryDTO](#entity-BusinessOrderDeliveryDTO)
  
  Информация о доставке заказа.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "DELIVERY",
    "serviceName": "example",
    "deliveryServiceId": 0,
    "warehouseId": "example",
    "deliveryPartnerType": "SHOP",
    "dispatchType": "UNKNOWN",
    "dates": {
      "fromDate": "2025-01-01",
      "toDate": "2025-01-01",
      "fromTime": "12:00:00",
      "toTime": "12:00:00",
      "realDeliveryDate": "2025-01-01"
    },
    "shipment": {
      "id": 0,
      "shipmentDate": "2025-01-01",
      "shipmentTime": "12:00:00"
    },
    "courier": {
      "address": {
        "country": "example",
        "postcode": "example",
        "city": "example",
        "district": "example",
        "subway": "example",
        "street": "example",
        "house": "example",
        "block": "example",
        "entrance": "example",
        "entryphone": "example",
        "floor": "example",
        "apartment": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        }
      },
      "region": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "parent": null
      }
    },
    "pickup": {
      "address": null,
      "region": null,
      "logisticPointId": 1,
      "outletCode": "example",
      "outletStorageLimitDate": "2025-01-01"
    },
    "transfer": {
      "courier": {
        "fullName": "example",
        "phone": "example",
        "phoneExtension": "example",
        "vehicleNumber": "example",
        "vehicleDescription": "example"
      },
      "eac": {
        "eacType": "MERCHANT_TO_COURIER",
        "eacCode": "example"
      }
    },
    "boxesLayout": [
      {
        "items": [
          {
            "id": 0,
            "fullCount": 1,
            "partialCount": {},
            "instances": [
              null
            ]
          }
        ],
        "boxId": 0,
        "barcode": "example"
      }
    ],
    "tracks": [
      {
        "trackCode": "example",
        "deliveryServiceId": 0
      }
    ],
    "estimated": true,
    "receiveBarcode": "example",
    "receiveCode": "example",
    "digitalGoods": {
      "type": "EMAIL",
      "steamLink": "example"
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _fake_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: boolean
  
  Тип заказа:
  
  * `false` — настоящий заказ покупателя.
  
  * `true` — [тестовый заказ](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md) Маркета.
  
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessOrderItemDTO](#entity-BusinessOrderItemDTO)[]
  
  Список товаров в заказе.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "offerId": "example",
      "offerName": "example",
      "count": 0,
      "prices": {
        "payment": {
          "value": 0.5,
          "currencyId": "RUR"
        },
        "subsidy": null,
        "cashback": null,
        "vat": "NO_VAT"
      },
      "instances": [
        {
          "cis": "example",
          "cisFull": "example",
          "uin": "example",
          "rnpt": "example",
          "gtd": "example",
          "countryCode": "RU"
        }
      ],
      "requiredInstanceTypes": [
        "CIS"
      ],
      "itemStatuses": [
        {
          "status": "CREATED",
          "count": 0
        }
      ],
      "tags": [
        "ULTIMA"
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
  
  Идентификатор заказа.
  {.table-cell}
  ||
  ||
  
  _paymentMethod_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderPaymentMethodType](#entity-OrderPaymentMethodType)
  
  Способ оплаты заказа:
  
  * Значения, если выбрана оплата при оформлении заказа (`"paymentType": "PREPAID"`):
  
    * `YANDEX` — банковской картой.
  
    * `APPLE_PAY` — Apple Pay (не используется).
  
    * `GOOGLE_PAY` — Google Pay (не используется).
  
    * `CREDIT` — в кредит.
  
    * `TINKOFF_CREDIT` — в кредит в Тинькофф Банке.
  
    * `TINKOFF_INSTALLMENTS` — рассрочка в Тинькофф Банке.
  
    * `EXTERNAL_CERTIFICATE` — подарочным сертификатом (например, из приложения «Сбербанк Онлайн»).
  
    * `SBP` — через систему быстрых платежей.
  
    * `B2B_ACCOUNT_PREPAYMENT` — заказ оплачивает организация.
  
    * `MICROCREDIT` - Сплит на основе МКК (Микрокредитной компании).
  
    * `BNPL_TBC` - BNPL через внешний банк TBC.
  
    * `DIGITAL_RUBLE` - Цифровой рубль.
  
  
  * Значения, если выбрана оплата при получении заказа (`"paymentType": "POSTPAID"`):
  
    * `CARD_ON_DELIVERY` — банковской картой.
  
    * `BOUND_CARD_ON_DELIVERY` — привязанной картой при получении.
  
    * `BNPL_BANK_ON_DELIVERY` — супер Сплитом.
  
    * `BNPL_ON_DELIVERY` — Сплитом.
  
    * `BNPL_TBYB` - Оплата после доставки на основе Сплита.
  
    * `CASH_ON_DELIVERY` — наличными.
  
    * `B2B_ACCOUNT_POSTPAYMENT` — заказ оплачивает организация после доставки.
  
  * `UNKNOWN` — неизвестный тип.
  
  Значение по умолчанию: `CASH_ON_DELIVERY`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CASH_ON_DELIVERY`, `CARD_ON_DELIVERY`, `BOUND_CARD_ON_DELIVERY`, `BNPL_BANK_ON_DELIVERY`, `BNPL_ON_DELIVERY`, `YANDEX`, `APPLE_PAY`, `EXTERNAL_CERTIFICATE`, `CREDIT`, `GOOGLE_PAY`, `TINKOFF_CREDIT`, `SBP`, `TINKOFF_INSTALLMENTS`, `B2B_ACCOUNT_PREPAYMENT`, `B2B_ACCOUNT_POSTPAYMENT`, `MICROCREDIT`, `BNPL_TBYB`, `BNPL_TBC`, `DIGITAL_RUBLE`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _paymentType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderPaymentType](#entity-OrderPaymentType)
  
  Тип оплаты заказа:
  
  * `PREPAID` — оплата при оформлении заказа.
  
  * `POSTPAID` — оплата при получении заказа.
  
  * `UNKNOWN` — неизвестный тип.
  
  Если параметр отсутствует, заказ будет оплачен при получении.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREPAID`, `POSTPAID`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderStatusType](#entity-OrderStatusType)
  
  Статус заказа:
  
  * `PLACING` — оформляется, подготовка к резервированию.
  
  * `RESERVED` — зарезервирован, но недооформлен (только для LaaS).
  
  * `UNPAID` — оформлен, но еще не оплачен (если выбрана оплата при оформлении).
  
  * `PROCESSING` — находится в обработке.
  
  * `DELIVERY` — передан в службу доставки.
  
  * `PICKUP` — доставлен в пункт выдачи.
  
  * `DELIVERED` — получен покупателем.
  
  * `CANCELLED` — отменен.
  
  * `PENDING` — ожидает обработки со стороны продавца.
  
  * `PARTIALLY_RETURNED` — возвращен частично.
  
  * `RETURNED` — возвращен полностью.
  
  * `UNKNOWN` — неизвестный статус.
  
  Также могут возвращаться другие значения. Обрабатывать их не нужно.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PLACING`, `RESERVED`, `UNPAID`, `PROCESSING`, `DELIVERY`, `PICKUP`, `DELIVERED`, `CANCELLED`, `PENDING`, `PARTIALLY_RETURNED`, `RETURNED`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _substatus_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderSubstatusType](#entity-OrderSubstatusType)
  
  Этап обработки заказа (статус `PROCESSING`) или причина отмены заказа (статус `CANCELLED`).
  
  * Значения для заказа в статусе `PROCESSING`:
  
      * `STARTED` — заказ подтвержден, его можно начать обрабатывать.
  
      * `READY_TO_SHIP` — заказ собран и готов к отправке.
  
  * Значения для заказа в статусе `CANCELLED`:
  
      * `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут.
  
      * `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут.
  
      * `USER_UNREACHABLE` — не удалось связаться с покупателем. Для отмены с этой причиной необходимо выполнить условия:
  
        * не менее 3 звонков с 8 до 21 в часовом поясе покупателя;
        * перерыв между первым и третьим звонком не менее 90 минут;
        * соединение не короче 5 секунд.
  
        Если хотя бы одно из этих условий не выполнено (кроме случая, когда номер недоступен), отменить заказ не получится. Вернется ответ с кодом ошибки 400.
  
      * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
  
      * `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки.
  
      * `USER_REFUSED_PRODUCT` — покупателю не подошел товар.
  
      * `SHOP_FAILED` — магазин не может выполнить заказ.
  
      * `USER_REFUSED_QUALITY` — покупателя не устроило качество товара.
  
      * `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе.
  
      * `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.
  
      * `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе.
  
      * `PROCESSING_EXPIRED` — значение более не используется.
  
      * `PICKUP_EXPIRED` — закончился срок хранения заказа в пункт выдачи.
  
      * `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз.
  
      * `TOO_LONG_DELIVERY` — заказ доставляется слишком долго.
  
      * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.
  
  * `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета. Обратитесь в поддержку.
  
  Также могут возвращаться другие значения. Обрабатывать их не нужно.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RESERVATION_EXPIRED`, `USER_NOT_PAID`, `USER_UNREACHABLE`, `USER_CHANGED_MIND`, `USER_REFUSED_DELIVERY`, `USER_REFUSED_PRODUCT`, `SHOP_FAILED`, `USER_REFUSED_QUALITY`, `REPLACING_ORDER`, `PROCESSING_EXPIRED`, `PENDING_EXPIRED`, `SHOP_PENDING_CANCELLED`, `PENDING_CANCELLED`, `USER_FRAUD`, `RESERVATION_FAILED`, `USER_PLACED_OTHER_ORDER`, `USER_BOUGHT_CHEAPER`, `MISSING_ITEM`, `BROKEN_ITEM`, `WRONG_ITEM`, `PICKUP_EXPIRED`, `DELIVERY_PROBLEMS`, `LATE_CONTACT`, `CUSTOM`, `DELIVERY_SERVICE_FAILED`, `WAREHOUSE_FAILED_TO_SHIP`, `DELIVERY_SERVICE_UNDELIVERED`, `PREORDER`, `AWAIT_CONFIRMATION`, `STARTED`, `PACKAGING`, `READY_TO_SHIP`, `SHIPPED`, `ASYNC_PROCESSING`, `WAITING_USER_INPUT`, `WAITING_BANK_DECISION`, `BANK_REJECT_CREDIT_OFFER`, `CUSTOMER_REJECT_CREDIT_OFFER`, `CREDIT_OFFER_FAILED`, `AWAIT_DELIVERY_DATES_CONFIRMATION`, `SERVICE_FAULT`, `DELIVERY_SERVICE_RECEIVED`, `USER_RECEIVED`, `WAITING_FOR_STOCKS`, `AS_PART_OF_MULTI_ORDER`, `READY_FOR_LAST_MILE`, `LAST_MILE_STARTED`, `ANTIFRAUD`, `DELIVERY_USER_NOT_RECEIVED`, `DELIVERY_SERVICE_DELIVERED`, `DELIVERED_USER_NOT_RECEIVED`, `USER_WANTED_ANOTHER_PAYMENT_METHOD`, `USER_RECEIVED_TECHNICAL_ERROR`, `USER_FORGOT_TO_USE_BONUS`, `DELIVERY_SERVICE_NOT_RECEIVED`, `DELIVERY_SERVICE_LOST`, `SHIPPED_TO_WRONG_DELIVERY_SERVICE`, `DELIVERED_USER_RECEIVED`, `WAITING_TINKOFF_DECISION`, `COURIER_SEARCH`, `COURIER_FOUND`, `COURIER_IN_TRANSIT_TO_SENDER`, `COURIER_ARRIVED_TO_SENDER`, `COURIER_RECEIVED`, `COURIER_NOT_FOUND`, `COURIER_NOT_DELIVER_ORDER`, `COURIER_RETURNS_ORDER`, `COURIER_RETURNED_ORDER`, `WAITING_USER_DELIVERY_INPUT`, `PICKUP_SERVICE_RECEIVED`, `PICKUP_USER_RECEIVED`, `CANCELLED_COURIER_NOT_FOUND`, `COURIER_NOT_COME_FOR_ORDER`, `DELIVERY_NOT_MANAGED_REGION`, `INCOMPLETE_CONTACT_INFORMATION`, `INCOMPLETE_MULTI_ORDER`, `INAPPROPRIATE_WEIGHT_SIZE`, `TECHNICAL_ERROR`, `SORTING_CENTER_LOST`, `COURIER_SEARCH_NOT_STARTED`, `LOST`, `AWAIT_PAYMENT`, `AWAIT_LAVKA_RESERVATION`, `USER_WANTS_TO_CHANGE_ADDRESS`, `FULL_NOT_RANSOM`, `PRESCRIPTION_MISMATCH`, `DROPOFF_LOST`, `DROPOFF_CLOSED`, `DELIVERY_TO_STORE_STARTED`, `USER_WANTS_TO_CHANGE_DELIVERY_DATE`, `WRONG_ITEM_DELIVERED`, `DAMAGED_BOX`, `AWAIT_DELIVERY_DATES`, `LAST_MILE_COURIER_SEARCH`, `PICKUP_POINT_CLOSED`, `LEGAL_INFO_CHANGED`, `USER_HAS_NO_TIME_TO_PICKUP_ORDER`, `DELIVERY_CUSTOMS_ARRIVED`, `DELIVERY_CUSTOMS_CLEARED`, `FIRST_MILE_DELIVERY_SERVICE_RECEIVED`, `AWAIT_AUTO_DELIVERY_DATES`, `AWAIT_USER_PERSONAL_DATA`, `NO_PERSONAL_DATA_EXPIRED`, `CUSTOMS_PROBLEMS`, `AWAIT_CASHIER`, `WAITING_POSTPAID_BUDGET_RESERVATION`, `AWAIT_SERVICEABLE_CONFIRMATION`, `POSTPAID_BUDGET_RESERVATION_FAILED`, `AWAIT_CUSTOM_PRICE_CONFIRMATION`, `READY_FOR_PICKUP`, `TOO_MANY_DELIVERY_DATE_CHANGES`, `TOO_LONG_DELIVERY`, `DEFERRED_PAYMENT`, `POSTPAID_FAILED`, `INCORRECT_PERSONAL_DATA`, `CUSTOMS_FAILED_MARKET`, `CUSTOMS_FAILED_USER_COMMERCIAL_ITEMS`, `CUSTOMS_FAILED_USER_DUTY_NOT_PAID`, `CUSTOMS_FAILED_USER_INVALID_PERSONAL_DATA`, `CUSTOMS_FAILED_USER_ADDITIONAL_DATA_NOT_PROVIDED`, `AWAIT_PAYMENT_AFTER_DELIVERY`, `AWAIT_USER_STEAM_FAST_URL`, `USER_IDENTIFICATION_MISMATCH`, `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _buyerType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderBuyerType](#entity-OrderBuyerType)
  
  Тип покупателя: физическое лицо или организация.
  
  Только для FBS- и FBY-магазинов, которые размещают товары на витрине [business.market.yandex.ru](https://business.market.yandex.ru).
  
  
  Тип покупателя:
  
  * `PERSON` — физическое лицо.
  
  * `BUSINESS` — организация.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERSON`, `BUSINESS`
  {.table-cell}
  ||
  ||
  
  _cancelRequested_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  **Только для модели DBS**
  
  Запрошена ли отмена.
  
  {.table-cell}
  ||
  ||
  
  _externalOrderId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ExternalOrderId](#entity-ExternalOrderId)
  
  Внешний идентификатор заказа, который вы передали в [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md).
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _notes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий к заказу.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _prices_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderPriceDTO](#entity-OrderPriceDTO)
  
  Информация о стоимости заказа, доставки и вознаграждениях.
  
  
  Информация о стоимости заказа.
  
  {% note info "Как рассчитывается стоимость заказа, доставки и вознаграждение продавцу" %}
  
  * Стоимость товаров в заказе складывается из параметров `payment` и `cashback`.
  * Общая сумма вознаграждений продавцу возвращается в параметре `subsidy`.
  * Значение `payment`, `cashback` и `subsidy` может отличаться от стоимости в каталоге, потому что информация об акциях магазина не возвращается.
  * Стоимость доставки складывается из параметров `payment` и `subsidy` в `delivery`.
  * Все суммы указаны в валюте магазина.
  
  {% endnote %}
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "payment": {
      "value": 0.5,
      "currencyId": "RUR"
    },
    "subsidy": null,
    "cashback": null,
    "delivery": {
      "payment": null,
      "subsidy": null,
      "vat": "NO_VAT"
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _programType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [SellingProgramType](#entity-SellingProgramType)
  
  Тип программы кампании магазина.
  
  Модель работы:
  
  * `FBY` — FBY.
  * `FBS` — FBS.
  * `DBS` — DBS.
  * `EXPRESS` — Экспресс.
  * `LAAS` — LaaS.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBY`, `FBS`, `DBS`, `EXPRESS`, `LAAS`
  {.table-cell}
  ||
  ||
  
  _services_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessOrderServicesDTO](#entity-BusinessOrderServicesDTO)
  
  Услуги, добавленные в заказ.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "liftType": "NOT_NEEDED"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _sourcePlatform_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderSourcePlatformType](#entity-OrderSourcePlatformType)
  
  Площадка-источник заказа:
  
  * `MARKET` — заказ, оформленный на Маркете.
  
  * `OTHER` — LaaS-заказ, созданный продавцом.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MARKET`, `OZON`, `WILDBERRIES`, `OTHER`
  {.table-cell}
  ||
  ||
  
  _updateDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата и время последнего обновления заказа.
  
  Формат даты: ISO 8601 со смещением относительно UTC.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2020-02-02T14:30:30+03:00`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "orderId": 0,
    "campaignId": 1,
    "programType": "FBY",
    "externalOrderId": "example",
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "creationDate": "2020-02-02T14:30:30+03:00",
    "updateDate": "2020-02-02T14:30:30+03:00",
    "paymentType": "PREPAID",
    "paymentMethod": "CASH_ON_DELIVERY",
    "fake": true,
    "items": [
      {
        "id": 0,
        "offerId": "example",
        "offerName": "example",
        "count": 0,
        "prices": {
          "payment": {
            "value": 0.5,
            "currencyId": "RUR"
          },
          "subsidy": null,
          "cashback": null,
          "vat": "NO_VAT"
        },
        "instances": [
          {
            "cis": "example",
            "cisFull": "example",
            "uin": "example",
            "rnpt": "example",
            "gtd": "example",
            "countryCode": "RU"
          }
        ],
        "requiredInstanceTypes": [
          "CIS"
        ],
        "itemStatuses": [
          {
            "status": "CREATED",
            "count": 0
          }
        ],
        "tags": [
          "ULTIMA"
        ]
      }
    ],
    "prices": {
      "payment": null,
      "subsidy": null,
      "cashback": null,
      "delivery": {
        "payment": null,
        "subsidy": null,
        "vat": null
      }
    },
    "delivery": {
      "type": "DELIVERY",
      "serviceName": "example",
      "deliveryServiceId": 0,
      "warehouseId": "example",
      "deliveryPartnerType": "SHOP",
      "dispatchType": "UNKNOWN",
      "dates": {
        "fromDate": "2025-01-01",
        "toDate": "2025-01-01",
        "fromTime": "12:00:00",
        "toTime": "12:00:00",
        "realDeliveryDate": "2025-01-01"
      },
      "shipment": {
        "id": 0,
        "shipmentDate": "2025-01-01",
        "shipmentTime": "12:00:00"
      },
      "courier": {
        "address": {
          "country": "example",
          "postcode": "example",
          "city": "example",
          "district": "example",
          "subway": "example",
          "street": "example",
          "house": "example",
          "block": "example",
          "entrance": "example",
          "entryphone": "example",
          "floor": "example",
          "apartment": "example",
          "gps": {
            "latitude": 0.5,
            "longitude": 0.5
          }
        },
        "region": {
          "id": 0,
          "name": "example",
          "type": "OTHER",
          "parent": null
        }
      },
      "pickup": {
        "address": null,
        "region": null,
        "logisticPointId": 1,
        "outletCode": "example",
        "outletStorageLimitDate": "2025-01-01"
      },
      "transfer": {
        "courier": {
          "fullName": "example",
          "phone": "example",
          "phoneExtension": "example",
          "vehicleNumber": "example",
          "vehicleDescription": "example"
        },
        "eac": {
          "eacType": "MERCHANT_TO_COURIER",
          "eacCode": "example"
        }
      },
      "boxesLayout": [
        {
          "items": [
            {}
          ],
          "boxId": 0,
          "barcode": "example"
        }
      ],
      "tracks": [
        {
          "trackCode": "example",
          "deliveryServiceId": 0
        }
      ],
      "estimated": true,
      "receiveBarcode": "example",
      "receiveCode": "example",
      "digitalGoods": {
        "type": "EMAIL",
        "steamLink": "example"
      }
    },
    "services": {
      "liftType": "NOT_NEEDED"
    },
    "buyerType": "PERSON",
    "notes": "example",
    "cancelRequested": true,
    "sourcePlatform": "MARKET"
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
    - description: "Идентификатор кабинета.\n\n{% if audience == \"partner\" %}\n\nЧтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n\n{% endif %}\n"
      name: businessId
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
        maximum: 50
  headers: []
  body: |-
    {
      "orderIds": [
        0
      ],
      "externalOrderIds": [
        "example"
      ],
      "programTypes": [
        "FBY"
      ],
      "campaignIds": [
        1
      ],
      "statuses": [
        "PLACING"
      ],
      "substatuses": [
        "RESERVATION_EXPIRED"
      ],
      "dates": {
        "creationDateFrom": "2025-01-01",
        "creationDateTo": "2025-01-01",
        "shipmentDateFrom": "2025-01-01",
        "shipmentDateTo": "2025-01-01",
        "updateDateFrom": "2025-01-01T00:00:00Z",
        "updateDateTo": "2025-01-01T00:00:00Z"
      },
      "fake": true,
      "waitingForCancellationApprove": true,
      "sourcePlatforms": [
        "MARKET"
      ]
    }
  schema:
    type: object
    description: Запрос на получение информации о заказах бизнеса.
    properties:
      orderIds:
        description: Идентификаторы заказов.
        nullable: true
        uniqueItems: true
        type: array
        items:
          type: integer
          format: int64
        minItems: 1
        maxItems: 50
      externalOrderIds:
        description: Внешние идентификаторы заказов.
        nullable: true
        uniqueItems: true
        type: array
        items:
          description: "Внешний идентификатор заказа, который вы передали в [POST\_v2/campaigns/{campaignId}/orders/{orderId}/external-id](../../reference/orders/updateExternalOrderId.md)."
          type: string
          minLength: 1
        minItems: 1
        maxItems: 50
      programTypes:
        description: Модели работы магазина на Маркете.
        nullable: true
        uniqueItems: true
        type: array
        items:
          description: |
            Модель работы:
  
            * `FBY` — FBY.
            * `FBS` — FBS.
            * `DBS` — DBS.
            * `EXPRESS` — Экспресс.
            * `LAAS` — LaaS.
          type: string
          enum:
            - FBY
            - FBS
            - DBS
            - EXPRESS
            - LAAS
        minItems: 1
      campaignIds:
        description: Идентификаторы кампаний магазинов.
        nullable: true
        uniqueItems: true
        type: array
        items:
          description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
          type: integer
          format: int64
          minimum: 1
        minItems: 1
        maxItems: 50
      statuses:
        description: Статусы заказов.
        nullable: true
        uniqueItems: true
        type: array
        items:
          description: >
            Статус заказа:
  
  
            * `PLACING` — оформляется, подготовка к резервированию.
  
  
            * `RESERVED` — зарезервирован, но недооформлен (только для LaaS).
  
  
            * `UNPAID` — оформлен, но еще не оплачен (если выбрана оплата при
            оформлении).
  
  
            * `PROCESSING` — находится в обработке.
  
  
            * `DELIVERY` — передан в службу доставки.
  
  
            * `PICKUP` — доставлен в пункт выдачи.
  
  
            * `DELIVERED` — получен покупателем.
  
  
            * `CANCELLED` — отменен.
  
  
            * `PENDING` — ожидает обработки со стороны продавца.
  
  
            * `PARTIALLY_RETURNED` — возвращен частично.
  
  
            * `RETURNED` — возвращен полностью.
  
  
            * `UNKNOWN` — неизвестный статус.
  
  
            Также могут возвращаться другие значения. Обрабатывать их не нужно.
          type: string
          enum:
            - PLACING
            - RESERVED
            - UNPAID
            - PROCESSING
            - DELIVERY
            - PICKUP
            - DELIVERED
            - CANCELLED
            - PENDING
            - PARTIALLY_RETURNED
            - RETURNED
            - UNKNOWN
        minItems: 1
      substatuses:
        description: Этапы обработки или причины отмены заказов.
        nullable: true
        uniqueItems: true
        type: array
        items:
          description: >
            Этап обработки заказа (статус `PROCESSING`) или причина отмены заказа
            (статус `CANCELLED`).
  
  
            * Значения для заказа в статусе `PROCESSING`:
  
                * `STARTED` — заказ подтвержден, его можно начать обрабатывать.
  
                * `READY_TO_SHIP` — заказ собран и готов к отправке.
  
            * Значения для заказа в статусе `CANCELLED`:
  
                * `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут.
  
                * `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут.
  
                * `USER_UNREACHABLE` — не удалось связаться с покупателем. Для отмены с этой причиной необходимо выполнить условия:
  
                  * не менее 3 звонков с 8 до 21 в часовом поясе покупателя;
                  * перерыв между первым и третьим звонком не менее 90 минут;
                  * соединение не короче 5 секунд.
  
                  Если хотя бы одно из этих условий не выполнено (кроме случая, когда номер недоступен), отменить заказ не получится. Вернется ответ с кодом ошибки 400.
  
                * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
  
                * `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки.
  
                * `USER_REFUSED_PRODUCT` — покупателю не подошел товар.
  
                * `SHOP_FAILED` — магазин не может выполнить заказ.
  
                * `USER_REFUSED_QUALITY` — покупателя не устроило качество товара.
  
                * `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе.
  
                * `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.
  
                * `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе.
  
                * `PROCESSING_EXPIRED` — значение более не используется.
  
                * `PICKUP_EXPIRED` — закончился срок хранения заказа в пункт выдачи.
  
                * `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз.
  
                * `TOO_LONG_DELIVERY` — заказ доставляется слишком долго.
  
                * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.
  
            * `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета.
            Обратитесь в поддержку.
  
  
            Также могут возвращаться другие значения. Обрабатывать их не нужно.
          type: string
          enum:
            - RESERVATION_EXPIRED
            - USER_NOT_PAID
            - USER_UNREACHABLE
            - USER_CHANGED_MIND
            - USER_REFUSED_DELIVERY
            - USER_REFUSED_PRODUCT
            - SHOP_FAILED
            - USER_REFUSED_QUALITY
            - REPLACING_ORDER
            - PROCESSING_EXPIRED
            - PENDING_EXPIRED
            - SHOP_PENDING_CANCELLED
            - PENDING_CANCELLED
            - USER_FRAUD
            - RESERVATION_FAILED
            - USER_PLACED_OTHER_ORDER
            - USER_BOUGHT_CHEAPER
            - MISSING_ITEM
            - BROKEN_ITEM
            - WRONG_ITEM
            - PICKUP_EXPIRED
            - DELIVERY_PROBLEMS
            - LATE_CONTACT
            - CUSTOM
            - DELIVERY_SERVICE_FAILED
            - WAREHOUSE_FAILED_TO_SHIP
            - DELIVERY_SERVICE_UNDELIVERED
            - PREORDER
            - AWAIT_CONFIRMATION
            - STARTED
            - PACKAGING
            - READY_TO_SHIP
            - SHIPPED
            - ASYNC_PROCESSING
            - WAITING_USER_INPUT
            - WAITING_BANK_DECISION
            - BANK_REJECT_CREDIT_OFFER
            - CUSTOMER_REJECT_CREDIT_OFFER
            - CREDIT_OFFER_FAILED
            - AWAIT_DELIVERY_DATES_CONFIRMATION
            - SERVICE_FAULT
            - DELIVERY_SERVICE_RECEIVED
            - USER_RECEIVED
            - WAITING_FOR_STOCKS
            - AS_PART_OF_MULTI_ORDER
            - READY_FOR_LAST_MILE
            - LAST_MILE_STARTED
            - ANTIFRAUD
            - DELIVERY_USER_NOT_RECEIVED
            - DELIVERY_SERVICE_DELIVERED
            - DELIVERED_USER_NOT_RECEIVED
            - USER_WANTED_ANOTHER_PAYMENT_METHOD
            - USER_RECEIVED_TECHNICAL_ERROR
            - USER_FORGOT_TO_USE_BONUS
            - DELIVERY_SERVICE_NOT_RECEIVED
            - DELIVERY_SERVICE_LOST
            - SHIPPED_TO_WRONG_DELIVERY_SERVICE
            - DELIVERED_USER_RECEIVED
            - WAITING_TINKOFF_DECISION
            - COURIER_SEARCH
            - COURIER_FOUND
            - COURIER_IN_TRANSIT_TO_SENDER
            - COURIER_ARRIVED_TO_SENDER
            - COURIER_RECEIVED
            - COURIER_NOT_FOUND
            - COURIER_NOT_DELIVER_ORDER
            - COURIER_RETURNS_ORDER
            - COURIER_RETURNED_ORDER
            - WAITING_USER_DELIVERY_INPUT
            - PICKUP_SERVICE_RECEIVED
            - PICKUP_USER_RECEIVED
            - CANCELLED_COURIER_NOT_FOUND
            - COURIER_NOT_COME_FOR_ORDER
            - DELIVERY_NOT_MANAGED_REGION
            - INCOMPLETE_CONTACT_INFORMATION
            - INCOMPLETE_MULTI_ORDER
            - INAPPROPRIATE_WEIGHT_SIZE
            - TECHNICAL_ERROR
            - SORTING_CENTER_LOST
            - COURIER_SEARCH_NOT_STARTED
            - LOST
            - AWAIT_PAYMENT
            - AWAIT_LAVKA_RESERVATION
            - USER_WANTS_TO_CHANGE_ADDRESS
            - FULL_NOT_RANSOM
            - PRESCRIPTION_MISMATCH
            - DROPOFF_LOST
            - DROPOFF_CLOSED
            - DELIVERY_TO_STORE_STARTED
            - USER_WANTS_TO_CHANGE_DELIVERY_DATE
            - WRONG_ITEM_DELIVERED
            - DAMAGED_BOX
            - AWAIT_DELIVERY_DATES
            - LAST_MILE_COURIER_SEARCH
            - PICKUP_POINT_CLOSED
            - LEGAL_INFO_CHANGED
            - USER_HAS_NO_TIME_TO_PICKUP_ORDER
            - DELIVERY_CUSTOMS_ARRIVED
            - DELIVERY_CUSTOMS_CLEARED
            - FIRST_MILE_DELIVERY_SERVICE_RECEIVED
            - AWAIT_AUTO_DELIVERY_DATES
            - AWAIT_USER_PERSONAL_DATA
            - NO_PERSONAL_DATA_EXPIRED
            - CUSTOMS_PROBLEMS
            - AWAIT_CASHIER
            - WAITING_POSTPAID_BUDGET_RESERVATION
            - AWAIT_SERVICEABLE_CONFIRMATION
            - POSTPAID_BUDGET_RESERVATION_FAILED
            - AWAIT_CUSTOM_PRICE_CONFIRMATION
            - READY_FOR_PICKUP
            - TOO_MANY_DELIVERY_DATE_CHANGES
            - TOO_LONG_DELIVERY
            - DEFERRED_PAYMENT
            - POSTPAID_FAILED
            - INCORRECT_PERSONAL_DATA
            - CUSTOMS_FAILED_MARKET
            - CUSTOMS_FAILED_USER_COMMERCIAL_ITEMS
            - CUSTOMS_FAILED_USER_DUTY_NOT_PAID
            - CUSTOMS_FAILED_USER_INVALID_PERSONAL_DATA
            - CUSTOMS_FAILED_USER_ADDITIONAL_DATA_NOT_PROVIDED
            - AWAIT_PAYMENT_AFTER_DELIVERY
            - AWAIT_USER_STEAM_FAST_URL
            - USER_IDENTIFICATION_MISMATCH
            - PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED
            - UNKNOWN
        minItems: 1
      dates:
        description: Даты заказов.
        $ref: '#/$defs/OrderDatesFilterDTO'
      fake:
        description: |
          Тип заказа:
  
          * `false` — настоящий заказ покупателя.
  
          * `true` — [тестовый заказ](../../concepts/sandbox.md) Маркета.
        type: boolean
      waitingForCancellationApprove:
        description: >
          **Только для модели DBS**
  
  
          Фильтр для получения заказов, по которым есть запросы на отмену.
  
  
          При значении `true` возвращаются только те заказы, которые находятся в
          статусе `DELIVERY` или `PICKUP`, и пользователи решили их отменить.
        type: boolean
      sourcePlatforms:
        description: Площадки-источники заказов.
        nullable: true
        uniqueItems: true
        type: array
        items:
          description: |
            Площадка-источник заказа:
  
            * `MARKET` — заказ, оформленный на Маркете.
  
            * `OTHER` — LaaS-заказ, созданный продавцом.
          type: string
          enum:
            - MARKET
            - OZON
            - WILDBERRIES
            - OTHER
        minItems: 1
    $defs:
      /home/sandbox/.ya/build/build_root/jc95/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/orders/api/getBusinessOrders.yaml#/OrderDatesFilterDTO:
        type: object
        description: Фильтр по датам заказов.
        properties:
          creationDateFrom:
            description: >
              Начальная дата для фильтрации заказов по дате оформления.
  
  
              Формат даты: `ГГГГ-ММ-ДД`.
  
  
              Между начальной и конечной датой (параметр `creationDateTo`) должно
              быть не больше 30 дней.
  
  
              Значение по умолчанию: 30 дней назад от текущей даты.
  
  
              Начальная дата включается в интервал для фильтрации.
            type: string
            format: date
          creationDateTo:
            description: >
              Конечная дата для фильтрации заказов по дате оформления.
  
  
              Формат даты: `ГГГГ-ММ-ДД`.
  
  
              Между начальной (параметр `creationDateFrom`) и конечной датой
              должно быть не больше 30 дней.
  
  
              Значение по умолчанию: текущая дата.
  
  
              Если промежуток времени между `creationDateTo` и `creationDateFrom`
              меньше суток, то `creationDateTo` равен `creationDateFrom` + сутки.
  
  
              Конечная дата не включается в интервал для фильтрации.
            type: string
            format: date
          shipmentDateFrom:
            description: >
              Начальная дата для фильтрации заказов по дате отгрузки в службу
              доставки (параметр `shipmentDate`).
  
  
              Формат даты: `ГГГГ-ММ-ДД`.
  
  
              Между начальной и конечной датой (параметр `shipmentDateTo`) должно
              быть не больше 30 дней.
  
  
              Начальная дата включается в интервал для фильтрации.
            type: string
            format: date
          shipmentDateTo:
            description: >
              Конечная дата для фильтрации заказов по дате отгрузки в службу
              доставки (параметр `shipmentDate`).
  
  
              Формат даты: `ГГГГ-ММ-ДД`.
  
  
              Между начальной (параметр `shipmentDateFrom`) и конечной датой
              должно быть не больше 30 дней.
  
  
              Если промежуток времени между `shipmentDateTo` и `shipmentDateFrom`
              меньше суток, то `shipmentDateTo` равен `shipmentDateFrom` + сутки.
  
  
              Конечная дата не включается в интервал для фильтрации.
            type: string
            format: date
          updateDateFrom:
            description: Начальная дата обновления заказа (ISO 8601).
            type: string
            format: date-time
          updateDateTo:
            description: Конечная дата обновления заказа (ISO 8601).
            type: string
            format: date-time
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
  path: v1/businesses/{businessId}/orders
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/getBusinessOrders.md -->

[*safe-tag]:
Защитная метка помогает исключить подмену товара при возврате. Вернуть товар без защитной метки, которая была при покупке, не получится.

[*cis-regular-value]:
Значение `cis` должно соответствовать регулярному выражению `^(?=.{1,256}$)\u001D?(\(?01\)?\d{14}\(?21\)?([!-~]{6,8}|[!-~]{13}|[!-~]{20})(\u001D\(?240\)?.{1,30})?\u001D\(?9[1,3]\)?.+)$`.<br><br>Без криптохвоста — `^(?=[!-~]{1,256}$)(\(?01\)?\d{14}\(?21\)?(.{6,8}|.{13}|.{20}))$`.

[*Deprecated]: No longer supported, please use an alternative and newer version.
