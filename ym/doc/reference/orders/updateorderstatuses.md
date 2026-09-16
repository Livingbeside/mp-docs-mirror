---
title: Массовое изменение статусов заказов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md"
fetched_at: "2026-09-16T02:27:28Z"
content_sha: 5d404d1910fa3c11
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/updateOrderStatuses.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/updateOrderStatuses.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/updateOrderStatuses.md -->
<div class="openapi">

# Изменение статусов нескольких заказов

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateOrderStatuses.md -->
  **Метод доступен для моделей: [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md), [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md) и [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateOrderStatuses.md -->
  
  Изменяет статусы нескольких заказов.
  
  Возможные изменения статусов:
  
  * Если магазин подтвердил и подготовил заказ к отправке, то заказ из статуса `"status": "PROCESSING"`и этапа обработки `"substatus": "STARTED"` нужно перевести в статус `"status": "PROCESSING"` и этап обработки `"substatus": "READY_TO_SHIP"`.
  * Если магазин подтвердил заказ, но не может его выполнить (например, товар числится в базе, но отсутствует на складе или нет нужного цвета), то заказ из статуса `"status": "PROCESSING"` и этапа обработки `"substatus": "STARTED"` нужно перевести в статус `"status": "CANCELLED"` с причиной отмены заказа `"substatus": "SHOP_FAILED"`.
  * Если магазин подготовил заказ к отгрузке, но не может его выполнить (например, последний товар был поврежден или оказался с браком), то заказ из статуса `"status": "PROCESSING"` и этапа обработки `"substatus": "READY_TO_SHIP"` нужно перевести в статус `"status": "CANCELLED"` с причиной отмены заказа `"substatus": "SHOP_FAILED"`.
  
  Полная информация о статусной модели DBS-заказов: [Как изменяются статусы заказов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md).
  
  {% cut "**Как подтвердить LaaS-заказ**" %}
  
  Для подтверждения черновика заказа передайте статус `"status": "PROCESSING"` с подстатусом `"substatus": "STARTED"`.
  
  Подтверждение заказа, созданного с параметром `draft` равным `false`, не требуется.
  
  {% endcut %}
  
  {% cut "**Как отменить LaaS-заказ**" %}
  
  Передайте статус `"status": "CANCELLED"` с причиной отмены заказа `"substatus": "SHOP_FAILED"`.
  
  При успешном выполнении запроса отмена произойдет через некоторое время. [Как проверить статус операции](https://yandex.ru/dev/market/partner-api/doc/ru/reference/operations/getOperations.md)
  
  {% endcut %}
  
  <!-- source: ru/_auto/method_limits/updateOrderStatuses.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 заказов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateOrderStatuses.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/status-update
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
    "orders": [
      {
        "id": 0,
        "status": "PLACING",
        "substatus": "RESERVATION_EXPIRED"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _orders_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderStateDTO](#entity-OrderStateDTO)[]
  
  Список заказов.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `30`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "status": "PLACING",
      "substatus": "RESERVATION_EXPIRED"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  ### OrderStateDTO {#entity-OrderStateDTO}
  
  Информация по заказу.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
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
  
  _substatus_{.json-schema-reset .json-schema-property}
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Возвращается информация об обновленных статусах заказов.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "orders": [
        {
          "id": 0,
          "status": "PLACING",
          "substatus": "RESERVATION_EXPIRED",
          "updateStatus": "OK",
          "errorDetails": "example",
          "operation": {}
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
    **Type**: [UpdateOrderStatusesDTO](#entity-UpdateOrderStatusesDTO)
  
    Список заказов, статус которых обновился.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "orders": [
        {
          "id": 0,
          "status": "PLACING",
          "substatus": "RESERVATION_EXPIRED",
          "updateStatus": "OK",
          "errorDetails": "example",
          "operation": {
            "id": "example",
            "type": "ORDER_RECIPIENT_UPDATE"
          }
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
        "orders": [
          {
            "id": 0,
            "status": "PLACING",
            "substatus": "RESERVATION_EXPIRED",
            "updateStatus": "OK",
            "errorDetails": "example",
            "operation": {
              "id": "example",
              "type": "ORDER_RECIPIENT_UPDATE"
            }
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
  
  ### OrderUpdateStatusType {#entity-OrderUpdateStatusType}
  
  Изменился ли статус заказа:
  
  * `OK` — статус изменен.
  
  * `ERROR` — статус не изменен. В этом случае появится сообщение об ошибке в параметре `errorDetails`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  
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
  
  ### UpdateOrderStatusDTO {#entity-UpdateOrderStatusDTO}
  
  Список заказов.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _errorDetails_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Ошибка при изменении статуса заказа. Содержит описание ошибки и идентификатор заказа.
  
  Возвращается, если параметр `updateStatus` принимает значение `ERROR`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  ||
  
  _operation_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OperationDTO](#entity-OperationDTO)
  
  **Только для модели LaaS**
  
  Информация о запущенной операции по обновлению статуса.
  
  
  Информация об операции.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "type": "ORDER_RECIPIENT_UPDATE"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _status_{.json-schema-reset .json-schema-property}
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
  
  _substatus_{.json-schema-reset .json-schema-property}
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
  
  _updateStatus_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderUpdateStatusType](#entity-OrderUpdateStatusType)
  
  Статус обновления.
  
  Изменился ли статус заказа:
  
  * `OK` — статус изменен.
  
  * `ERROR` — статус не изменен. В этом случае появится сообщение об ошибке в параметре `errorDetails`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "updateStatus": "OK",
    "errorDetails": "example",
    "operation": {
      "id": "example",
      "type": "ORDER_RECIPIENT_UPDATE"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOrderStatusesDTO {#entity-UpdateOrderStatusesDTO}
  
  Список заказов, статус которых обновился.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _orders_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateOrderStatusDTO](#entity-UpdateOrderStatusDTO)[]
  
  Список с обновленными заказами.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "status": "PLACING",
      "substatus": "RESERVATION_EXPIRED",
      "updateStatus": "OK",
      "errorDetails": "example",
      "operation": {
        "id": "example",
        "type": "ORDER_RECIPIENT_UPDATE"
      }
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
    "orders": [
      {
        "id": 0,
        "status": "PLACING",
        "substatus": "RESERVATION_EXPIRED",
        "updateStatus": "OK",
        "errorDetails": "example",
        "operation": {
          "id": "example",
          "type": "ORDER_RECIPIENT_UPDATE"
        }
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
  searchParams: []
  headers: []
  body: |-
    {
      "orders": [
        {
          "id": 0,
          "status": "PLACING",
          "substatus": "RESERVATION_EXPIRED"
        }
      ]
    }
  schema:
    description: Список заказов.
    type: object
    required:
      - orders
    properties:
      orders:
        description: Список заказов.
        type: array
        minItems: 1
        maxItems: 30
        items:
          description: Информация по заказу.
          type: object
          required:
            - id
            - status
          properties:
            id:
              description: Идентификатор заказа.
              type: integer
              format: int64
            status:
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
  
  
                Также могут возвращаться другие значения. Обрабатывать их не
                нужно.
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
            substatus:
              description: >
                Этап обработки заказа (статус `PROCESSING`) или причина отмены
                заказа (статус `CANCELLED`).
  
  
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
  
  
                Также могут возвращаться другие значения. Обрабатывать их не
                нужно.
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
  path: v2/campaigns/{campaignId}/orders/status-update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/updateOrderStatuses.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
