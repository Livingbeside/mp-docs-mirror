---
title: Изменение статуса одного заказа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md"
fetched_at: "2026-09-22T02:27:04Z"
content_sha: c1878b6f9a06e190
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/updateOrderStatus.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/updateOrderStatus.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/updateOrderStatus.md -->
<div class="openapi">

# Изменение статуса одного заказа

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateOrderStatus.md -->
  **Метод доступен для моделей: [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md), [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md) и [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateOrderStatus.md -->
  
  Изменяет статус заказа. Возможные изменения статусов:
  
  * Если магазин подтвердил и подготовил заказ к отправке, то заказ из статуса `"status": "PROCESSING"` и этапа обработки `"substatus": "STARTED"` нужно перевести в статус `"status": "PROCESSING"` и этап обработки `"substatus": "READY_TO_SHIP"`.
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
  
  <!-- source: ru/_auto/method_limits/updateOrderStatus.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateOrderStatus.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-put);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  PUT {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/status
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
    "order": {
      "status": "PLACING",
      "substatus": "RESERVATION_EXPIRED",
      "delivery": {
        "dates": {
          "realDeliveryDate": "2025-01-01"
        }
      }
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _order_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderStatusChangeDTO](#entity-OrderStatusChangeDTO)
  
  Заказ.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "delivery": {
      "dates": {
        "realDeliveryDate": "2025-01-01"
      }
    }
  }
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
  
  ### OrderStatusChangeDeliveryDatesDTO {#entity-OrderStatusChangeDeliveryDatesDTO}
  
  Диапазон дат доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _realDeliveryDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  **Только для модели DBS**
  
  Фактическая дата доставки.
  <br><br>
  Когда передавать параметр `realDeliveryDate`:
  
  * Не передавайте параметр, если:
    * переводите заказ в любой статус, кроме `PICKUP` или `DELIVERED`;
    * меняете статус заказа на `PICKUP` или `DELIVERED` в день доставки — будет указана дата выполнения запроса.
  * Передавайте дату доставки, если переводите заказ в статус `PICKUP` или `DELIVERED` не в день доставки. Нельзя указывать дату доставки в будущем.
  
    {% note warning "Передача статуса после установленного срока снижает индекс качества" %}
  
    О сроках читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/quality/tech#dbs).
  
    {% endnote %}
  
     
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "realDeliveryDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderStatusChangeDeliveryDTO {#entity-OrderStatusChangeDeliveryDTO}
  
  Информация о доставке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dates_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderStatusChangeDeliveryDatesDTO](#entity-OrderStatusChangeDeliveryDatesDTO)
  
  Диапазон дат доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "realDeliveryDate": "2025-01-01"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "dates": {
      "realDeliveryDate": "2025-01-01"
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderStatusChangeDTO {#entity-OrderStatusChangeDTO}
  
  Заказ.
  
  #|
  || **Name** | **Description** ||
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
  
  _delivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderStatusChangeDeliveryDTO](#entity-OrderStatusChangeDeliveryDTO)
  
  Информация о доставке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "dates": {
      "realDeliveryDate": "2025-01-01"
    }
  }
  ```
  
  {% endcut %}
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
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "delivery": {
      "dates": {
        "realDeliveryDate": "2025-01-01"
      }
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  В случае успешного изменения статуса заказа возвращается обновленная информация о заказе.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "order": {
      "id": 0,
      "externalOrderId": "example",
      "status": "PLACING",
      "substatus": "RESERVATION_EXPIRED",
      "creationDate": "23-09-2022 09:12:41",
      "updatedAt": null,
      "currency": "RUR",
      "itemsTotal": 0.5,
      "deliveryTotal": 0.5,
      "buyerItemsTotal": 0.5,
      "buyerTotal": 0.5,
      "buyerItemsTotalBeforeDiscount": 0.5,
      "buyerTotalBeforeDiscount": 0.5,
      "paymentType": "PREPAID",
      "paymentMethod": "CASH_ON_DELIVERY",
      "fake": true,
      "items": [
        {
          "id": 0,
          "offerId": "example",
          "offerName": "example",
          "price": 0.5,
          "buyerPrice": 0.5,
          "buyerPriceBeforeDiscount": 0.5,
          "priceBeforeDiscount": 0.5,
          "count": 0,
          "vat": "NO_VAT",
          "shopSku": null,
          "subsidy": 0.5,
          "partnerWarehouseId": "example",
          "promos": [
            {}
          ],
          "instances": [
            {}
          ],
          "details": [
            {}
          ],
          "subsidies": [
            {}
          ],
          "requiredInstanceTypes": [
            "CIS"
          ],
          "tags": [
            "ULTIMA"
          ]
        }
      ],
      "subsidies": [
        {
          "type": "YANDEX_CASHBACK",
          "amount": 0.5
        }
      ],
      "delivery": {
        "id": "example",
        "type": "DELIVERY",
        "serviceName": "example",
        "price": 0.5,
        "deliveryPartnerType": "SHOP",
        "courier": {
          "fullName": "example",
          "phone": "example",
          "phoneExtension": "example",
          "vehicleNumber": "example",
          "vehicleDescription": "example"
        },
        "dates": {
          "fromDate": "23-09-2022",
          "toDate": null,
          "fromTime": "12:00:00",
          "toTime": "12:00:00",
          "realDeliveryDate": null
        },
        "region": {
          "id": 0,
          "name": "example",
          "type": "OTHER",
          "parent": null
        },
        "address": {
          "country": "example",
          "postcode": "example",
          "city": "example",
          "district": "example",
          "subway": "example",
          "street": "example",
          "house": "example",
          "estate": "example",
          "block": "example",
          "building": "example",
          "entrance": "example",
          "entryphone": "example",
          "floor": "example",
          "apartment": "example",
          "phone": "example",
          "recipient": "example",
          "gps": {
            "latitude": 0.5,
            "longitude": 0.5
          }
        },
        "vat": null,
        "deliveryServiceId": 0,
        "liftType": "NOT_NEEDED",
        "liftPrice": 0.5,
        "outletCode": "example",
        "outletStorageLimitDate": null,
        "dispatchType": "UNKNOWN",
        "tracks": [
          {
            "trackCode": "example",
            "deliveryServiceId": 0
          }
        ],
        "shipments": [
          {
            "id": 0,
            "shipmentDate": null,
            "shipmentTime": "example",
            "tracks": [
              null
            ],
            "boxes": [
              null
            ]
          }
        ],
        "estimated": true,
        "eacType": "MERCHANT_TO_COURIER",
        "eacCode": "example",
        "receiveCode": "example"
      },
      "buyer": {
        "id": "example",
        "lastName": "example",
        "firstName": "example",
        "middleName": "example",
        "type": "PERSON"
      },
      "notes": "example",
      "taxSystem": "OSN",
      "cancelRequested": true,
      "expiryDate": null
    },
    "operation": {
      "id": "example",
      "type": "ORDER_RECIPIENT_UPDATE"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
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
  
  _order_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderDTO](#entity-OrderDTO)
  
  Заказ.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "externalOrderId": "example",
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "creationDate": "23-09-2022 09:12:41",
    "updatedAt": null,
    "currency": "RUR",
    "itemsTotal": 0.5,
    "deliveryTotal": 0.5,
    "buyerItemsTotal": 0.5,
    "buyerTotal": 0.5,
    "buyerItemsTotalBeforeDiscount": 0.5,
    "buyerTotalBeforeDiscount": 0.5,
    "paymentType": "PREPAID",
    "paymentMethod": "CASH_ON_DELIVERY",
    "fake": true,
    "items": [
      {
        "id": 0,
        "offerId": "example",
        "offerName": "example",
        "price": 0.5,
        "buyerPrice": 0.5,
        "buyerPriceBeforeDiscount": 0.5,
        "priceBeforeDiscount": 0.5,
        "count": 0,
        "vat": "NO_VAT",
        "shopSku": null,
        "subsidy": 0.5,
        "partnerWarehouseId": "example",
        "promos": [
          {
            "type": "DIRECT_DISCOUNT",
            "discount": 0.5,
            "subsidy": 0.5,
            "shopPromoId": "example",
            "marketPromoId": "example"
          }
        ],
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
        "details": [
          {
            "itemCount": 0,
            "itemStatus": "REJECTED",
            "updateDate": "23-09-2022"
          }
        ],
        "subsidies": [
          {
            "type": "YANDEX_CASHBACK",
            "amount": 0.5
          }
        ],
        "requiredInstanceTypes": [
          "CIS"
        ],
        "tags": [
          "ULTIMA"
        ]
      }
    ],
    "subsidies": [
      {
        "type": "YANDEX_CASHBACK",
        "amount": 0.5
      }
    ],
    "delivery": {
      "id": "example",
      "type": "DELIVERY",
      "serviceName": "example",
      "price": 0.5,
      "deliveryPartnerType": "SHOP",
      "courier": {
        "fullName": "example",
        "phone": "example",
        "phoneExtension": "example",
        "vehicleNumber": "example",
        "vehicleDescription": "example"
      },
      "dates": {
        "fromDate": null,
        "toDate": null,
        "fromTime": "12:00:00",
        "toTime": "12:00:00",
        "realDeliveryDate": null
      },
      "region": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "parent": null
      },
      "address": {
        "country": "example",
        "postcode": "example",
        "city": "example",
        "district": "example",
        "subway": "example",
        "street": "example",
        "house": "example",
        "estate": "example",
        "block": "example",
        "building": "example",
        "entrance": "example",
        "entryphone": "example",
        "floor": "example",
        "apartment": "example",
        "phone": "example",
        "recipient": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        }
      },
      "vat": null,
      "deliveryServiceId": 0,
      "liftType": "NOT_NEEDED",
      "liftPrice": 0.5,
      "outletCode": "example",
      "outletStorageLimitDate": null,
      "dispatchType": "UNKNOWN",
      "tracks": [
        {
          "trackCode": "example",
          "deliveryServiceId": 0
        }
      ],
      "shipments": [
        {
          "id": 0,
          "shipmentDate": null,
          "shipmentTime": "example",
          "tracks": [
            null
          ],
          "boxes": [
            {}
          ]
        }
      ],
      "estimated": true,
      "eacType": "MERCHANT_TO_COURIER",
      "eacCode": "example",
      "receiveCode": "example"
    },
    "buyer": {
      "id": "example",
      "lastName": "example",
      "firstName": "example",
      "middleName": "example",
      "type": "PERSON"
    },
    "notes": "example",
    "taxSystem": "OSN",
    "cancelRequested": true,
    "expiryDate": null
  }
  ```
  
  {% endcut %}
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
  
  ### DateDdMmYyyyHhMmSs {#entity-DateDdMmYyyyHhMmSs}
  
  **Type**: string&lt;date-dd-MM-yyyy-HH-mm-ss&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022 09:12:41`
  
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
  
  ### OrderPromoType {#entity-OrderPromoType}
  
  Тип скидки:
  
  * `DIRECT_DISCOUNT` — прямая скидка, которую устанавливает продавец или Маркет.
  
  * `BLUE_SET` — комплекты.
  
  * `BLUE_FLASH` — флеш-акция.
  
  * `MARKET_COUPON` — скидка по промокоду Маркета.
  
  * `MARKET_PROMOCODE` — скидка по промокоду магазина.
  
  * `MARKET_BLUE` — скидка на Маркете.
  
  * `CHEAPEST_AS_GIFT` — самый дешевый товар в подарок.
  
  * `CASHBACK` — кешбэк.
  
  * `SPREAD_DISCOUNT_COUNT` — скидка за количество одинаковых товаров.
  
  * `SPREAD_DISCOUNT_RECEIPT` — скидка от суммы чека.
  
  * `DISCOUNT_BY_PAYMENT_TYPE` — прямая скидка при оплате картой Плюса.
  
  * `PERCENT_DISCOUNT` — прямая скидка в процентах.
  
  * `DCO_EXTRA_DISCOUNT` — дополнительная скидка, необходимая для расчета субсидии от Маркета.
  
  * `UNKNOWN` — неизвестный тип.
  
  Устаревшие типы:
  
  * `GENERIC_BUNDLE`.
  
  * `MARKET_COIN`.
  
  * `PRICE_DROP_AS_YOU_SHOP`.
  
  * `SECRET_SALE`.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DIRECT_DISCOUNT`, `BLUE_SET`, `BLUE_FLASH`, `GENERIC_BUNDLE`, `MARKET_COUPON`, `MARKET_PROMOCODE`, `MARKET_BLUE`, `MARKET_COIN`, `PRICE_DROP_AS_YOU_SHOP`, `SECRET_SALE`, `CHEAPEST_AS_GIFT`, `CASHBACK`, `SPREAD_DISCOUNT_COUNT`, `SPREAD_DISCOUNT_RECEIPT`, `DISCOUNT_BY_PAYMENT_TYPE`, `PERCENT_DISCOUNT`, `DCO_EXTRA_DISCOUNT`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemPromoDTO {#entity-OrderItemPromoDTO}
  
  Информация о вознаграждении продавцу за скидки на товар по промокодам, купонам и акциям.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _subsidy_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Вознаграждение продавцу от Маркета за товар, проданный в рамках акции.
  
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderPromoType](#entity-OrderPromoType)
  
  Тип скидки.
  
  
  Тип скидки:
  
  * `DIRECT_DISCOUNT` — прямая скидка, которую устанавливает продавец или Маркет.
  
  * `BLUE_SET` — комплекты.
  
  * `BLUE_FLASH` — флеш-акция.
  
  * `MARKET_COUPON` — скидка по промокоду Маркета.
  
  * `MARKET_PROMOCODE` — скидка по промокоду магазина.
  
  * `MARKET_BLUE` — скидка на Маркете.
  
  * `CHEAPEST_AS_GIFT` — самый дешевый товар в подарок.
  
  * `CASHBACK` — кешбэк.
  
  * `SPREAD_DISCOUNT_COUNT` — скидка за количество одинаковых товаров.
  
  * `SPREAD_DISCOUNT_RECEIPT` — скидка от суммы чека.
  
  * `DISCOUNT_BY_PAYMENT_TYPE` — прямая скидка при оплате картой Плюса.
  
  * `PERCENT_DISCOUNT` — прямая скидка в процентах.
  
  * `DCO_EXTRA_DISCOUNT` — дополнительная скидка, необходимая для расчета субсидии от Маркета.
  
  * `UNKNOWN` — неизвестный тип.
  
  Устаревшие типы:
  
  * `GENERIC_BUNDLE`.
  
  * `MARKET_COIN`.
  
  * `PRICE_DROP_AS_YOU_SHOP`.
  
  * `SECRET_SALE`.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DIRECT_DISCOUNT`, `BLUE_SET`, `BLUE_FLASH`, `GENERIC_BUNDLE`, `MARKET_COUPON`, `MARKET_PROMOCODE`, `MARKET_BLUE`, `MARKET_COIN`, `PRICE_DROP_AS_YOU_SHOP`, `SECRET_SALE`, `CHEAPEST_AS_GIFT`, `CASHBACK`, `SPREAD_DISCOUNT_COUNT`, `SPREAD_DISCOUNT_RECEIPT`, `DISCOUNT_BY_PAYMENT_TYPE`, `PERCENT_DISCOUNT`, `DCO_EXTRA_DISCOUNT`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _discount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Размер пользовательской скидки в валюте покупателя.
  
  {.table-cell}
  ||
  ||
  
  _marketPromoId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор акции в рамках соглашения на оказание услуг по продвижению сервиса между Маркетом и продавцом.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _shopPromoId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор акции поставщика.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "DIRECT_DISCOUNT",
    "discount": 0.5,
    "subsidy": 0.5,
    "shopPromoId": "example",
    "marketPromoId": "example"
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
  
  ### OrderItemStatusType {#entity-OrderItemStatusType}
  
  Невыкупленный или возвращенный товар:
  
  * `REJECTED` — невыкупленный.
  
  * `RETURNED` — возвращенный.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `REJECTED`, `RETURNED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DateDdMmYyyy {#entity-DateDdMmYyyy}
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  **Type**: string&lt;date-dd-MM-yyyy&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemDetailDTO {#entity-OrderItemDetailDTO}
  
  Детали по товару в заказе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _itemCount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара.
  {.table-cell}
  ||
  ||
  
  _itemStatus_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemStatusType](#entity-OrderItemStatusType)
  
  Невыкупленный или возвращенный товар:
  
  * `REJECTED` — невыкупленный.
  
  * `RETURNED` — возвращенный.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `REJECTED`, `RETURNED`
  {.table-cell}
  ||
  ||
  
  _updateDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "itemCount": 0,
    "itemStatus": "REJECTED",
    "updateDate": "23-09-2022"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemSubsidyType {#entity-OrderItemSubsidyType}
  
  Тип субсидии:
  
  * `YANDEX_CASHBACK` — скидка по подписке Яндекс Плюс.
  
  * `SUBSIDY` — скидка Маркета (по акциям, промокодам, купонам и т. д.).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `YANDEX_CASHBACK`, `SUBSIDY`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemSubsidyDTO {#entity-OrderItemSubsidyDTO}
  
  Общее вознаграждение продавцу за все скидки на товар:
  
  * по промокодам, купонам и акциям;
  * по баллам Плюса.
  
  Включает НДС.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Сумма субсидии.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemSubsidyType](#entity-OrderItemSubsidyType)
  
  Тип субсидии:
  
  * `YANDEX_CASHBACK` — скидка по подписке Яндекс Плюс.
  
  * `SUBSIDY` — скидка Маркета (по акциям, промокодам, купонам и т. д.).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `YANDEX_CASHBACK`, `SUBSIDY`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "YANDEX_CASHBACK",
    "amount": 0.5
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
  
  ### OrderItemTagType {#entity-OrderItemTagType}
  
  Признак товара:
  
  * `ULTIMA` — премиум-товар.
  * `SAFE_TAG` — товар с [защитной меткой](*safe-tag).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ULTIMA`, `SAFE_TAG`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderItemDTO {#entity-OrderItemDTO}
  
  Список товаров в заказе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _buyerPrice_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Цена товара в валюте покупателя. В цене уже учтены скидки по:
  
  * акциям;
  * купонам;
  * промокодам.
  
  {.table-cell}
  ||
  ||
  
  _buyerPriceBeforeDiscount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Стоимость товара в валюте покупателя до применения скидок по:
  
  * акциям;
  * купонам;
  * промокодам.
  
  Это зачеркнутая цена, которая отображается покупателю на карточке товара до применения скидок.
  
  {.table-cell}
  ||
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
  
  Идентификатор вашего товарного предложения для определенного товара. [Описание поля в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/assortment/fields/index.html#sku)
  
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
  
  _price_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Цена товара в валюте заказа без учета вознаграждения продавцу за скидки по промокодам, купонам и акциям (параметр `subsidies`).
  
  Включает НДС.
  
  {.table-cell}
  ||
  ||
  
  _details_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [OrderItemDetailDTO](#entity-OrderItemDetailDTO)[] &#124; null
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
  Для получения информации о невыкупах и возвратах используйте [GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md).
  
  {% endnote %}
  
  Информация о невыкупленных или возвращенных товарах в заказе.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "itemCount": 0,
      "itemStatus": "REJECTED",
      "updateDate": "23-09-2022"
    }
  ]
  ```
  
  {% endcut %}
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
  
  _partnerWarehouseId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  **Только для моделей FBY и LaaS**
  
  Идентификатор склада, на который сформирован заказ.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _priceBeforeDiscount_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
   
  
  {% endnote %}
  
  Стоимость товара в валюте магазина до применения скидок.
  
  {.table-cell}
  ||
  ||
  
  _promos_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemPromoDTO](#entity-OrderItemPromoDTO)[] &#124; null
  
  Информация о вознаграждении продавцу за скидки на товар по промокодам, купонам и акциям.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "DIRECT_DISCOUNT",
      "discount": 0.5,
      "subsidy": 0.5,
      "shopPromoId": "example",
      "marketPromoId": "example"
    }
  ]
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
  
  _shopSku_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
  Вместо него используйте `offerId`.
  
  {% endnote %}
  
  Ваш SKU — идентификатор товара в вашей системе.
  
  
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
  
  _subsidies_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderItemSubsidyDTO](#entity-OrderItemSubsidyDTO)[] &#124; null
  
  Список субсидий по типам.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "YANDEX_CASHBACK",
      "amount": 0.5
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _subsidy_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
  Вместо него используйте `subsidies`.
  
  {% endnote %}
  
  Общее вознаграждение продавцу за DBS-доставку и все скидки на товар:
  
  * по промокодам;
  * по купонам;
  * по баллам Плюса;
  * по акциям.
  
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
    "id": 0,
    "offerId": "example",
    "offerName": "example",
    "price": 0.5,
    "buyerPrice": 0.5,
    "buyerPriceBeforeDiscount": 0.5,
    "priceBeforeDiscount": 0.5,
    "count": 0,
    "vat": "NO_VAT",
    "shopSku": null,
    "subsidy": 0.5,
    "partnerWarehouseId": "example",
    "promos": [
      {
        "type": "DIRECT_DISCOUNT",
        "discount": 0.5,
        "subsidy": 0.5,
        "shopPromoId": "example",
        "marketPromoId": "example"
      }
    ],
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
    "details": [
      {
        "itemCount": 0,
        "itemStatus": "REJECTED",
        "updateDate": "23-09-2022"
      }
    ],
    "subsidies": [
      {
        "type": "YANDEX_CASHBACK",
        "amount": 0.5
      }
    ],
    "requiredInstanceTypes": [
      "CIS"
    ],
    "tags": [
      "ULTIMA"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderSubsidyType {#entity-OrderSubsidyType}
  
  Тип субсидии:
  
  * `YANDEX_CASHBACK` — скидка по подписке Яндекс Плюс.
  
  * `SUBSIDY` — скидка Маркета (по акциям, промокодам, купонам и т. д.)
  
  * `DELIVERY` — скидка за доставку (DBS).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `YANDEX_CASHBACK`, `SUBSIDY`, `DELIVERY`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderSubsidyDTO {#entity-OrderSubsidyDTO}
  
  Общее вознаграждение продавцу за DBS-доставку и все скидки на товар:
  
  * по промокодам, купонам и акциям;
  * по баллам Плюса;
  * по доставке (DBS).
  
  Включает НДС.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _amount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Сумма субсидии.
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderSubsidyType](#entity-OrderSubsidyType)
  
  Тип субсидии:
  
  * `YANDEX_CASHBACK` — скидка по подписке Яндекс Плюс.
  
  * `SUBSIDY` — скидка Маркета (по акциям, промокодам, купонам и т. д.)
  
  * `DELIVERY` — скидка за доставку (DBS).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `YANDEX_CASHBACK`, `SUBSIDY`, `DELIVERY`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "YANDEX_CASHBACK",
    "amount": 0.5
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
  
  ### OrderDeliveryDatesDTO {#entity-OrderDeliveryDatesDTO}
  
  Диапазон дат доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Ближайшая дата доставки.
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
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
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Дата, когда товар доставлен до пункта выдачи (в случае самовывоза) или до покупателя (если заказ доставляет курьер).
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  {.table-cell}
  ||
  ||
  
  _toDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Самая поздняя дата доставки.
  
  Если `toDate` не указан, считается дата в параметре `fromDate`.
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
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
    "fromDate": "23-09-2022",
    "toDate": null,
    "fromTime": "12:00:00",
    "toTime": "12:00:00",
    "realDeliveryDate": null
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
  
  ### OrderDeliveryAddressDTO {#entity-OrderDeliveryAddressDTO}
  
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
  
  _building_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Строение.
  
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
  
  _estate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер владения.
  
  
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
  
  _phone_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Телефон получателя заказа.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _postcode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Почтовый индекс.
  
  Указывается, если выбрана доставка почтой (`delivery type=POST`).
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _recipient_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Фамилия, имя и отчество получателя заказа.
  
  
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
    "estate": "example",
    "block": "example",
    "building": "example",
    "entrance": "example",
    "entryphone": "example",
    "floor": "example",
    "apartment": "example",
    "phone": "example",
    "recipient": "example",
    "gps": {
      "latitude": 0.5,
      "longitude": 0.5
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
  
  ### OrderParcelBoxDTO {#entity-OrderParcelBoxDTO}
  
  Информация о грузоместе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fulfilmentId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор грузового места в системе магазина.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор грузового места.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "fulfilmentId": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderShipmentDTO {#entity-OrderShipmentDTO}
  
  Список посылок.
  
  В параметре может указываться несколько посылок.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _boxes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderParcelBoxDTO](#entity-OrderParcelBoxDTO)[] &#124; null
  
  Список грузовых мест.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "fulfilmentId": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
   
  
  {% endnote %}
  
  Идентификатор посылки, присвоенный Маркетом.
  
  {.table-cell}
  ||
  ||
  
  _shipmentDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  День, в который нужно отгрузить заказ службе доставки.
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  Если заказ сделан организацией, параметр не возвращается до согласования даты доставки.
  
  {% cut "Иногда Маркет может перенести дату отгрузки" %}
  
  У таких заказов обновится параметр `updatedAt`. Чтобы найти их, в запросе [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) укажите параметры `updateDateFrom` и `updateDateTo`.
  
  {% endcut %}
  
   
  
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  {.table-cell}
  ||
  ||
  
  _shipmentTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  **Только для модели Экспресс**
  
  Время, к которому магазин должен упаковать заказ и перевести его в статус `READY_TO_SHIP`. После смены статуса за заказом приедет курьер.
  
  Поле может появиться не сразу. Запрашивайте информацию о заказе в течении 5–10 минут, пока оно не вернется.
  
  Формат времени: 24-часовой, `ЧЧ:ММ`.
  
  Если заказ сделан организацией, параметр не возвращается до согласования даты доставки.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _tracks_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderTrackDTO](#entity-OrderTrackDTO)[] &#124; null
  
  **Только для модели DBS**
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "shipmentDate": "23-09-2022",
    "shipmentTime": "example",
    "tracks": [
      {
        "trackCode": "example",
        "deliveryServiceId": 0
      }
    ],
    "boxes": [
      {
        "id": 0,
        "fulfilmentId": "example"
      }
    ]
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
  
  ### OrderDeliveryDTO {#entity-OrderDeliveryDTO}
  
  Информация о доставке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dates_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderDeliveryDatesDTO](#entity-OrderDeliveryDatesDTO)
  
  Диапазон дат доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "23-09-2022",
    "toDate": null,
    "fromTime": "12:00:00",
    "toTime": "12:00:00",
    "realDeliveryDate": null
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
  
  _address_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderDeliveryAddressDTO](#entity-OrderDeliveryAddressDTO)
  
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
    "estate": "example",
    "block": "example",
    "building": "example",
    "entrance": "example",
    "entryphone": "example",
    "floor": "example",
    "apartment": "example",
    "phone": "example",
    "recipient": "example",
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
  
  _eacCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Код подтверждения ЭАПП (для типа `MERCHANT_TO_COURIER`).
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _eacType_{.json-schema-reset .json-schema-property}
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
  
  _estimated_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Приблизительная ли дата доставки.
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
   
  
  {% endnote %}
  
  Идентификатор доставки, присвоенный магазином.
  
  Указывается, только если магазин передал данный идентификатор в ответе на запрос методом `POST cart`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _liftPrice_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Стоимость подъема на этаж.
  {.table-cell}
  ||
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
  ||
  
  _outletCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор пункта выдачи, присвоенный магазином.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _outletStorageLimitDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Дата, до которой заказ будет храниться в пункте выдачи. Возвращается, когда заказ переходит в статус `PICKUP`.
  
  Один раз дату можно поменять с помощью метода [PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md).
  
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  {.table-cell}
  ||
  ||
  
  _price_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
  Стоимость доставки смотрите в параметре `deliveryTotal`.
  
  {% endnote %}
  
  Стоимость доставки в валюте заказа.
  
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
  ||
  
  _shipments_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderShipmentDTO](#entity-OrderShipmentDTO)[] &#124; null
  
  Информация о посылках.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "shipmentDate": "23-09-2022",
      "shipmentTime": "example",
      "tracks": [
        {
          "trackCode": "example",
          "deliveryServiceId": 0
        }
      ],
      "boxes": [
        {
          "id": 0,
          "fulfilmentId": "example"
        }
      ]
    }
  ]
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
  
  _vat_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderVatType](#entity-OrderVatType)
  
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
    "id": "example",
    "type": "DELIVERY",
    "serviceName": "example",
    "price": 0.5,
    "deliveryPartnerType": "SHOP",
    "courier": {
      "fullName": "example",
      "phone": "example",
      "phoneExtension": "example",
      "vehicleNumber": "example",
      "vehicleDescription": "example"
    },
    "dates": {
      "fromDate": "23-09-2022",
      "toDate": null,
      "fromTime": "12:00:00",
      "toTime": "12:00:00",
      "realDeliveryDate": null
    },
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    },
    "address": {
      "country": "example",
      "postcode": "example",
      "city": "example",
      "district": "example",
      "subway": "example",
      "street": "example",
      "house": "example",
      "estate": "example",
      "block": "example",
      "building": "example",
      "entrance": "example",
      "entryphone": "example",
      "floor": "example",
      "apartment": "example",
      "phone": "example",
      "recipient": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "vat": "NO_VAT",
    "deliveryServiceId": 0,
    "liftType": "NOT_NEEDED",
    "liftPrice": 0.5,
    "outletCode": "example",
    "outletStorageLimitDate": null,
    "dispatchType": "UNKNOWN",
    "tracks": [
      {
        "trackCode": "example",
        "deliveryServiceId": 0
      }
    ],
    "shipments": [
      {
        "id": 0,
        "shipmentDate": null,
        "shipmentTime": "example",
        "tracks": [
          null
        ],
        "boxes": [
          {
            "id": 0,
            "fulfilmentId": "example"
          }
        ]
      }
    ],
    "estimated": true,
    "eacType": "MERCHANT_TO_COURIER",
    "eacCode": "example",
    "receiveCode": "example"
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
  
  ### OrderBuyerBasicInfoDTO {#entity-OrderBuyerBasicInfoDTO}
  
  Информация о покупателе с базовыми полями.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
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
  
  _firstName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Имя.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор покупателя.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _lastName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Фамилия.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _middleName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Отчество.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "lastName": "example",
    "firstName": "example",
    "middleName": "example",
    "type": "PERSON"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBuyerDTO {#entity-OrderBuyerDTO}
  
  Информация о покупателе.
  
  Параметры `id`, `lastName`, `firstName` и `middleName` возвращаются, только если вы работаете по модели DBS.
  
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [OrderBuyerBasicInfoDTO](#entity-OrderBuyerBasicInfoDTO)
  
    Информация о покупателе с базовыми полями.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": "example",
      "lastName": "example",
      "firstName": "example",
      "middleName": "example",
      "type": "PERSON"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {}
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "lastName": "example",
    "firstName": "example",
    "middleName": "example",
    "type": "PERSON"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderTaxSystemType {#entity-OrderTaxSystemType}
  
  Система налогообложения (СНО) магазина на момент оформления заказа:
  
  * `ECHN` — единый сельскохозяйственный налог (ЕСХН).
  
  * `ENVD` — единый налог на вмененный доход (ЕНВД).
  
  * `OSN` — общая система налогообложения (ОСН).
  
  * `PSN` — патентная система налогообложения (ПСН).
  
  * `USN` — упрощенная система налогообложения (УСН).
  
  * `USN_MINUS_COST` — упрощенная система налогообложения, доходы, уменьшенные на величину расходов (УСН «Доходы минус расходы»).
  
  * `NPD` — налог на профессиональный доход (НПД).
  
  * `AUSN` — автоматизированная упрощенная система налогообложения (АУСН).
  
  * `AUSN_MINUS_COST` — автоматизированная упрощенная система налогообложения, доходы, уменьшенные на величину расходов (АУСН «Доходы минус расходы»).
  
  * `UNKNOWN_VALUE` — неизвестное значение.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OSN`, `USN`, `USN_MINUS_COST`, `ENVD`, `ECHN`, `PSN`, `NPD`, `AUSN`, `AUSN_MINUS_COST`, `UNKNOWN_VALUE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderSourcePlatformType {#entity-OrderSourcePlatformType}
  
  Площадка-источник заказа:
  
  * `MARKET` — заказ, оформленный на Маркете.
  
  * `OTHER` — LaaS-заказ, созданный продавцом.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MARKET`, `OZON`, `WILDBERRIES`, `OTHER`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderDTO {#entity-OrderDTO}
  
  Заказ.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _buyer_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderBuyerDTO](#entity-OrderBuyerDTO)
  
  Информация о покупателе.
  
  Параметры `id`, `lastName`, `firstName` и `middleName` возвращаются, только если вы работаете по модели DBS.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "lastName": "example",
    "firstName": "example",
    "middleName": "example",
    "type": "PERSON"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _buyerItemsTotalBeforeDiscount_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Стоимость всех товаров в заказе в валюте покупателя без учета стоимости доставки и до применения скидок по:
  
  * акциям;
  * купонам;
  * промокодам.
  
  {.table-cell}
  ||
  ||
  
  _creationDate_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DateDdMmYyyyHhMmSs](#entity-DateDdMmYyyyHhMmSs)
  
  Дата и время оформления заказа.
  
  Формат даты и времени: `ДД-ММ-ГГГГ ЧЧ:ММ:СС`. Часовой пояс — UTC+03:00 (Москва).
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022 09:12:41`
  {.table-cell}
  ||
  ||
  
  _currency_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта, в которой указаны цены на товары в заказе.
  
  
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
  
  _delivery_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderDeliveryDTO](#entity-OrderDeliveryDTO)
  
  Информация о доставке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": "example",
    "type": "DELIVERY",
    "serviceName": "example",
    "price": 0.5,
    "deliveryPartnerType": "SHOP",
    "courier": {
      "fullName": "example",
      "phone": "example",
      "phoneExtension": "example",
      "vehicleNumber": "example",
      "vehicleDescription": "example"
    },
    "dates": {
      "fromDate": "23-09-2022",
      "toDate": null,
      "fromTime": "12:00:00",
      "toTime": "12:00:00",
      "realDeliveryDate": null
    },
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    },
    "address": {
      "country": "example",
      "postcode": "example",
      "city": "example",
      "district": "example",
      "subway": "example",
      "street": "example",
      "house": "example",
      "estate": "example",
      "block": "example",
      "building": "example",
      "entrance": "example",
      "entryphone": "example",
      "floor": "example",
      "apartment": "example",
      "phone": "example",
      "recipient": "example",
      "gps": {
        "latitude": 0.5,
        "longitude": 0.5
      }
    },
    "vat": "NO_VAT",
    "deliveryServiceId": 0,
    "liftType": "NOT_NEEDED",
    "liftPrice": 0.5,
    "outletCode": "example",
    "outletStorageLimitDate": null,
    "dispatchType": "UNKNOWN",
    "tracks": [
      {
        "trackCode": "example",
        "deliveryServiceId": 0
      }
    ],
    "shipments": [
      {
        "id": 0,
        "shipmentDate": null,
        "shipmentTime": "example",
        "tracks": [
          null
        ],
        "boxes": [
          {
            "id": 0,
            "fulfilmentId": "example"
          }
        ]
      }
    ],
    "estimated": true,
    "eacType": "MERCHANT_TO_COURIER",
    "eacCode": "example",
    "receiveCode": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryTotal_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Стоимость доставки.
  
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
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderItemDTO](#entity-OrderItemDTO)[]
  
  Список товаров в заказе.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "offerId": "example",
      "offerName": "example",
      "price": 0.5,
      "buyerPrice": 0.5,
      "buyerPriceBeforeDiscount": 0.5,
      "priceBeforeDiscount": 0.5,
      "count": 0,
      "vat": "NO_VAT",
      "shopSku": null,
      "subsidy": 0.5,
      "partnerWarehouseId": "example",
      "promos": [
        {
          "type": "DIRECT_DISCOUNT",
          "discount": 0.5,
          "subsidy": 0.5,
          "shopPromoId": "example",
          "marketPromoId": "example"
        }
      ],
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
      "details": [
        {
          "itemCount": 0,
          "itemStatus": "REJECTED",
          "updateDate": "23-09-2022"
        }
      ],
      "subsidies": [
        {
          "type": "YANDEX_CASHBACK",
          "amount": 0.5
        }
      ],
      "requiredInstanceTypes": [
        "CIS"
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
  
  _itemsTotal_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Платеж покупателя.
  
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
  
  _taxSystem_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderTaxSystemType](#entity-OrderTaxSystemType)
  
  Система налогообложения (СНО) магазина на момент оформления заказа:
  
  * `ECHN` — единый сельскохозяйственный налог (ЕСХН).
  
  * `ENVD` — единый налог на вмененный доход (ЕНВД).
  
  * `OSN` — общая система налогообложения (ОСН).
  
  * `PSN` — патентная система налогообложения (ПСН).
  
  * `USN` — упрощенная система налогообложения (УСН).
  
  * `USN_MINUS_COST` — упрощенная система налогообложения, доходы, уменьшенные на величину расходов (УСН «Доходы минус расходы»).
  
  * `NPD` — налог на профессиональный доход (НПД).
  
  * `AUSN` — автоматизированная упрощенная система налогообложения (АУСН).
  
  * `AUSN_MINUS_COST` — автоматизированная упрощенная система налогообложения, доходы, уменьшенные на величину расходов (АУСН «Доходы минус расходы»).
  
  * `UNKNOWN_VALUE` — неизвестное значение.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OSN`, `USN`, `USN_MINUS_COST`, `ENVD`, `ECHN`, `PSN`, `NPD`, `AUSN`, `AUSN_MINUS_COST`, `UNKNOWN_VALUE`
  {.table-cell}
  ||
  ||
  
  _buyerItemsTotal_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
  Вместо него используйте `itemsTotal`.
  
  {% endnote %}
  
  Стоимость всех товаров в заказе в валюте покупателя после применения скидок и без учета стоимости доставки.
  
  {.table-cell}
  ||
  ||
  
  _buyerTotal_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
   
  
  {% endnote %}
  
  Стоимость всех товаров в заказе в валюте покупателя после применения скидок и с учетом стоимости доставки.
  
  {.table-cell}
  ||
  ||
  
  _buyerTotalBeforeDiscount_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: number
  
  {% note warning "Параметр устарел и будет отключен 05.10.2026." %}
  
   
  
  {% endnote %}
  
  Стоимость всех товаров в заказе в валюте покупателя до применения скидок и с учетом стоимости доставки (`buyerItemsTotalBeforeDiscount` + стоимость доставки).
  
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
  
  _expiryDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyyHhMmSs](#entity-DateDdMmYyyyHhMmSs)
  
  Дата, после которой заказ будет отменен, если не сменит статус.
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022 09:12:41`
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
  
  _subsidies_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderSubsidyDTO](#entity-OrderSubsidyDTO)[] &#124; null
  
  Список субсидий по типам.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "YANDEX_CASHBACK",
      "amount": 0.5
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _updatedAt_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyyHhMmSs](#entity-DateDdMmYyyyHhMmSs)
  
  Дата и время последнего обновления заказа.
  
  Формат даты и времени: `ДД-ММ-ГГГГ ЧЧ:ММ:СС`. Часовой пояс — UTC+03:00 (Москва).
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022 09:12:41`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "externalOrderId": "example",
    "status": "PLACING",
    "substatus": "RESERVATION_EXPIRED",
    "creationDate": "23-09-2022 09:12:41",
    "updatedAt": null,
    "currency": "RUR",
    "itemsTotal": 0.5,
    "deliveryTotal": 0.5,
    "buyerItemsTotal": 0.5,
    "buyerTotal": 0.5,
    "buyerItemsTotalBeforeDiscount": 0.5,
    "buyerTotalBeforeDiscount": 0.5,
    "paymentType": "PREPAID",
    "paymentMethod": "CASH_ON_DELIVERY",
    "fake": true,
    "items": [
      {
        "id": 0,
        "offerId": "example",
        "offerName": "example",
        "price": 0.5,
        "buyerPrice": 0.5,
        "buyerPriceBeforeDiscount": 0.5,
        "priceBeforeDiscount": 0.5,
        "count": 0,
        "vat": "NO_VAT",
        "shopSku": null,
        "subsidy": 0.5,
        "partnerWarehouseId": "example",
        "promos": [
          {
            "type": "DIRECT_DISCOUNT",
            "discount": 0.5,
            "subsidy": 0.5,
            "shopPromoId": "example",
            "marketPromoId": "example"
          }
        ],
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
        "details": [
          {
            "itemCount": 0,
            "itemStatus": "REJECTED",
            "updateDate": "23-09-2022"
          }
        ],
        "subsidies": [
          {
            "type": "YANDEX_CASHBACK",
            "amount": 0.5
          }
        ],
        "requiredInstanceTypes": [
          "CIS"
        ],
        "tags": [
          "ULTIMA"
        ]
      }
    ],
    "subsidies": [
      {
        "type": "YANDEX_CASHBACK",
        "amount": 0.5
      }
    ],
    "delivery": {
      "id": "example",
      "type": "DELIVERY",
      "serviceName": "example",
      "price": 0.5,
      "deliveryPartnerType": "SHOP",
      "courier": {
        "fullName": "example",
        "phone": "example",
        "phoneExtension": "example",
        "vehicleNumber": "example",
        "vehicleDescription": "example"
      },
      "dates": {
        "fromDate": null,
        "toDate": null,
        "fromTime": "12:00:00",
        "toTime": "12:00:00",
        "realDeliveryDate": null
      },
      "region": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "parent": null
      },
      "address": {
        "country": "example",
        "postcode": "example",
        "city": "example",
        "district": "example",
        "subway": "example",
        "street": "example",
        "house": "example",
        "estate": "example",
        "block": "example",
        "building": "example",
        "entrance": "example",
        "entryphone": "example",
        "floor": "example",
        "apartment": "example",
        "phone": "example",
        "recipient": "example",
        "gps": {
          "latitude": 0.5,
          "longitude": 0.5
        }
      },
      "vat": null,
      "deliveryServiceId": 0,
      "liftType": "NOT_NEEDED",
      "liftPrice": 0.5,
      "outletCode": "example",
      "outletStorageLimitDate": null,
      "dispatchType": "UNKNOWN",
      "tracks": [
        {
          "trackCode": "example",
          "deliveryServiceId": 0
        }
      ],
      "shipments": [
        {
          "id": 0,
          "shipmentDate": null,
          "shipmentTime": "example",
          "tracks": [
            null
          ],
          "boxes": [
            {}
          ]
        }
      ],
      "estimated": true,
      "eacType": "MERCHANT_TO_COURIER",
      "eacCode": "example",
      "receiveCode": "example"
    },
    "buyer": {
      "id": "example",
      "lastName": "example",
      "firstName": "example",
      "middleName": "example",
      "type": "PERSON"
    },
    "notes": "example",
    "taxSystem": "OSN",
    "cancelRequested": true,
    "expiryDate": null
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
      "order": {
        "status": "PLACING",
        "substatus": "RESERVATION_EXPIRED",
        "delivery": {
          "dates": {
            "realDeliveryDate": "2025-01-01"
          }
        }
      }
    }
  schema:
    type: object
    required:
      - order
    properties:
      order:
        description: Заказ.
        type: object
        required:
          - status
        properties:
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
          delivery:
            description: Информация о доставке.
            type: object
            properties:
              dates:
                description: Диапазон дат доставки.
                type: object
                properties:
                  realDeliveryDate:
                    description: "**Только для модели DBS**\n\nФактическая дата доставки.\n<br><br>\nКогда передавать параметр `realDeliveryDate`:\n\n* Не передавайте параметр, если:\n  * переводите заказ в любой статус, кроме `PICKUP` или `DELIVERED`;\n  * меняете статус заказа на `PICKUP` или `DELIVERED` в день доставки — будет указана дата выполнения запроса.\n* Передавайте дату доставки, если переводите заказ в статус `PICKUP` или `DELIVERED` не в день доставки. Нельзя указывать дату доставки в будущем.\n\n  {% note warning \"Передача статуса после установленного срока снижает индекс качества\" %}\n\n  О сроках читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/quality/tech#dbs).\n\n  {% endnote %}\n\n  \_\nФормат даты: `ГГГГ-ММ-ДД`.\n"
                    type: string
                    format: date
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
  path: v2/campaigns/{campaignId}/orders/{orderId}/status
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/updateOrderStatus.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
