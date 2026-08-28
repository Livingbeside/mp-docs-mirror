---
title: Отчет по невыкупам и возвратам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedReturnsReport.md"
fetched_at: "2026-08-28T11:52:50Z"
content_sha: fa59f5d2413c9065
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateUnitedReturnsReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedReturnsReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateUnitedReturnsReport.md
  - href: ru/reference/reports/generateUnitedReturnsReport.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateUnitedReturnsReport.md -->
<div class="openapi">

# Отчет по невыкупам и возвратам

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateUnitedReturnsReport.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateUnitedReturnsReport.md -->
  
  Запускает генерацию сводного отчета по невыкупам и возвратам за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/orders/returns/logistic#rejected-orders)
  
  Отчет содержит информацию о невыкупах и возвратах за указанный период, а также о тех, которые готовы к выдаче.
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/united/returns/generator/united_returns.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Готовы к выдаче** (файл **returns_ready_for_pickup**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказах/Номер заказа или отгрузки | integer ||
  || PARTNER_ORDER_ID | partnerOrderId | Информация о заказах/Ваш номер заказа | string ||
  || PLACEMENT_DATE | placementDate | Информация о заказах/Дата оформления заказа | string ||
  || SHOP_SKU | shopSku | Информация о заказах/Ваш SKU | string ||
  || PRODUCT_NAME | productName | Информация о заказах/Название товара | string ||
  || COUNT | count | Информация о заказах/Количество, шт. | integer ||
  || PRICE | price | Информация о заказах/Ваша цена (за шт.) | number ||
  || MARKETPLACE_DISCOUNT | marketplaceDiscount | Информация о заказах/Скидка маркетплейса (за шт.) | number ||
  || SPASIBO_DISCOUNT | spasiboDiscount | Информация о заказах/Оплата бонусами СберСпасибо (за шт.) | number ||
  || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Информация о заказах/Оплата баллами Яндекс Плюса | number ||
  || DELIVERY_SERVICE | deliveryService | Информация о заказах/Служба доставки товара | string ||
  || TYPE | type | Информация о возвратах или невыкупах/Тип | string ||
  || RETURN_NUMBER | returnNumber | Информация о возвратах или невыкупах/Номер возврата | integer ||
  || STATUS | status | Информация о возвратах или невыкупах/Статус | string ||
  || BOX_BARCODES | boxBarcodes | Информация о возвратах или невыкупах/Штрихкоды коробок | string ||
  ||
  DATE_OF_RETURN_CREATION
  |
  dateOfReturnCreation
  |
  Информация о возвратах или невыкупах/Дата возврата или невыкупа
  |
  string
  ||
  ||
  DATE_READY_FOR_ISSUANCE
  |
  dateReadyForIssuance
  |
  Информация о возвратах или невыкупах/Дата готовности к выдаче
  |
  string
  ||
  ||
  CHARGEABLE_STORAGE_DAYS_NUMBER
  |
  chargeableStorageDaysNumber
  |
  Информация о возвратах или невыкупах/Сколько дней хранится платно
  |
  integer
  ||
  ||
  DAYS_BEFORE_RECYCLING_QUEUE
  |
  daysBeforeRecyclingQueue
  |
  Информация о возвратах или невыкупах/Дней до постановки в очередь на утилизацию
  |
  integer
  ||
  ||
  DISPOSAL_TRANSFER_DATE
  |
  disposalTransferDate
  |
  Информация о возвратах или невыкупах/Дата передачи в утилизацию
  |
  string
  ||
  || DISPENSING_PLACE | dispensingPlace | Информация о возвратах или невыкупах/Место выдачи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Возвраты и невыкупы** (файл **returns_for_selected_range**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказах/Номер заказа или отгрузки | integer ||
  || PARTNER_ORDER_ID | partnerOrderId | Информация о заказах/Ваш номер заказа | string ||
  || PLACEMENT_DATE | placementDate | Информация о заказах/Дата оформления заказа | string ||
  || SHOP_SKU | shopSku | Информация о заказах/Ваш SKU | string ||
  || PRODUCT_NAME | productName | Информация о заказах/Название товара | string ||
  || PRICE | price | Информация о заказах/Ваша цена (за шт.) | number ||
  || MARKETPLACE_DISCOUNT | marketplaceDiscount | Информация о заказах/Скидка маркетплейса (за шт.) | number ||
  || SPASIBO_DISCOUNT | spasiboDiscount | Информация о заказах/Оплата бонусами СберСпасибо (за шт.) | number ||
  || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Информация о заказах/Оплата баллами Яндекс Плюса | number ||
  || DELIVERY_SERVICE | deliveryService | Информация о заказах/Служба доставки товара | string ||
  || TYPE | type | Информация о возвратах или невыкупах/Тип | string ||
  || COUNT | count | Информация о возвратах или невыкупах/Количество, шт. | integer ||
  || COUNT_OF_FIT | countOfFit | Информация о возвратах или невыкупах/Количество годных, шт. | integer ||
  || RETURN_NUMBER | returnNumber | Информация о возвратах или невыкупах/Номер возврата | integer ||
  || STATUS | status | Информация о возвратах или невыкупах/Статус | string ||
  || BOX_BARCODES | boxBarcodes | Информация о возвратах или невыкупах/Штрихкоды коробок | string ||
  ||
  DATE_OF_RETURN_CREATION
  |
  dateOfReturnCreation
  |
  Информация о возвратах или невыкупах/Дата возврата или невыкупа
  |
  string
  ||
  ||
  DATE_READY_FOR_ISSUANCE
  |
  dateReadyForIssuance
  |
  Информация о возвратах или невыкупах/Дата готовности к выдаче
  |
  string
  ||
  ||
  CHARGEABLE_STORAGE_DAYS_NUMBER
  |
  chargeableStorageDaysNumber
  |
  Информация о возвратах или невыкупах/Сколько дней хранится платно
  |
  integer
  ||
  ||
  DAYS_BEFORE_RECYCLING_QUEUE
  |
  daysBeforeRecyclingQueue
  |
  Информация о возвратах или невыкупах/Дней до постановки в очередь на утилизацию
  |
  integer
  ||
  ||
  DISPOSAL_TRANSFER_DATE
  |
  disposalTransferDate
  |
  Информация о возвратах или невыкупах/Дата передачи в утилизацию
  |
  string
  ||
  || DISPENSING_PLACE | dispensingPlace | Информация о возвратах или невыкупах/Место выдачи | string ||
  ||
  RETURN_PICKED_DATE
  |
  returnPickedDate
  |
  Информация о возвратах или невыкупах/Дата выдачи вам или возврата в продажу
  |
  string
  ||
  || RETURN_LOST_DATE | returnLostDate | Информация о возвратах или невыкупах/Дата утери | string ||
  || RETURN_REASON | returnReason | Информация о возвратах или невыкупах/Причина возврата | string ||
  || BUYER_COMMENT | buyerComment | Информация о возвратах или невыкупах/Комментарий покупателя | string ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/united/returns/generator/united_returns.md -->
  
  <!-- source: ru/_includes/common/report-data-period-unchanged.md -->
  {% note warning "Ограничения по тарифному плану" %}

  Период выгрузки данных и количество одновременно генерирующихся отчетов зависят от вашего тарифного плана:
  * **Без подписки или тариф «Лайт»** — доступны данные за последние 90 дней, одновременно может генерироваться 1 отчет
  * **Тариф «Медиум»** — одновременно может генерироваться до 10 отчетов

  Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).

  {% endnote %}
  <!-- endsource: ru/_includes/common/report-data-period-unchanged.md -->
  
  <!-- source: ru/_auto/method_limits/generateUnitedReturnsReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateUnitedReturnsReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/united-returns/generate
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _format_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReportFormatType](#entity-ReportFormatType)
  
  Формат отчета или документа.
  
  Формат отчета:
  
  * `FILE` — файл с электронной таблицей (XLSX).
  * `CSV` — ZIP-архив с CSV-файлами на каждый лист отчета.
  * `JSON` — ZIP-архив с JSON-файлами на каждый лист отчета.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `FILE`
  
  _Enum:_{.json-schema-reset .json-schema-value} `FILE`, `CSV`, `JSON`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### ReportFormatType {#entity-ReportFormatType}
  
  Формат отчета:
  
  * `FILE` — файл с электронной таблицей (XLSX).
  * `CSV` — ZIP-архив с CSV-файлами на каждый лист отчета.
  * `JSON` — ZIP-архив с JSON-файлами на каждый лист отчета.
  
  
  **Type**: string
  
  _Default:_{.json-schema-reset .json-schema-value} `FILE`
  
  _Enum:_{.json-schema-reset .json-schema-value} `FILE`, `CSV`, `JSON`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "businessId": 1,
    "dateFrom": "2025-08-22",
    "dateTo": "2025-09-22",
    "campaignIds": [
      1
    ],
    "returnType": "UNREDEEMED",
    "returnStatusTypes": [
      "CREATED"
    ]
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [BusinessId](#entity-BusinessId)
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _dateFrom_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PeriodDateFrom](#entity-PeriodDateFrom)
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [PeriodDateTo](#entity-PeriodDateTo)
  
  Конец периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-09-22`
  {.table-cell}
  ||
  ||
  
  _campaignIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignId](#entity-CampaignId)[] &#124; null
  
  Список идентификаторов кампании тех магазинов, которые нужны в отчете.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  _returnStatusTypes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnShipmentStatusType](#entity-ReturnShipmentStatusType)[] &#124; null
  
  Статусы передачи возвратов, которые нужны в отчете.
  
  Если их не указать, вернется информация по всем возвратам.
  
  
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
  
  _returnType_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReturnType](#entity-ReturnType) &#124; null
  
  Тип фильтрации:
  
  * `UNREDEEMED` — невыкупы.
  
  * `RETURN` — возвраты.
  
  Если не указывать, в ответе будут и невыкупы, и возвраты.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BusinessId {#entity-BusinessId}
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PeriodDateFrom {#entity-PeriodDateFrom}
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  **Type**: string&lt;date&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PeriodDateTo {#entity-PeriodDateTo}
  
  Конец периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  **Type**: string&lt;date&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-09-22`
  
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
  
  ### ReturnType {#entity-ReturnType}
  
  Тип фильтрации:
  
  * `UNREDEEMED` — невыкупы.
  
  * `RETURN` — возвраты.
  
  Если не указывать, в ответе будут и невыкупы, и возвраты.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNREDEEMED`, `RETURN`
  
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
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  В ответ приходит идентификатор, который позволяет узнавать статус генерации и скачать готовый отчет.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "reportId": "example",
      "estimatedGenerationTime": 0
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
    **Type**: [GenerateReportDTO](#entity-GenerateReportDTO)
  
    Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "reportId": "example",
      "estimatedGenerationTime": 0
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
        "reportId": "example",
        "estimatedGenerationTime": 0
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
  
  ### GenerateReportDTO {#entity-GenerateReportDTO}
  
  Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _estimatedGenerationTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Ожидаемая продолжительность генерации в миллисекундах.
  {.table-cell}
  ||
  ||
  
  _reportId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "reportId": "example",
    "estimatedGenerationTime": 0
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
  pathParams: []
  searchParams:
    - description: Формат отчета или документа.
      name: format
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
  headers: []
  body: |-
    {
      "businessId": 1,
      "dateFrom": "2025-08-22",
      "dateTo": "2025-09-22",
      "campaignIds": [
        1
      ],
      "returnType": "UNREDEEMED",
      "returnStatusTypes": [
        "CREATED"
      ]
    }
  schema:
    description: |
      Данные, необходимые для генерации отчета.
    type: object
    required:
      - businessId
      - dateFrom
      - dateTo
    properties:
      businessId:
        description: "Идентификатор кабинета. {% if audience == \"partner\" %}Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n{% endif %}\n"
        type: integer
        format: int64
        minimum: 1
      dateFrom:
        type: string
        format: date
        description: |
          Начало периода, включительно.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        example: '2025-08-22'
      dateTo:
        type: string
        format: date
        description: |
          Конец периода, включительно.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        example: '2025-09-22'
      campaignIds:
        description: |
          Список идентификаторов кампании тех магазинов, которые нужны в отчете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
          type: integer
          format: int64
          minimum: 1
      returnType:
        $ref: '#/$defs/ReturnType'
        nullable: true
      returnStatusTypes:
        description: |
          Статусы передачи возвратов, которые нужны в отчете.
  
          Если их не указать, вернется информация по всем возвратам.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: >
            Статус передачи возврата или невыкупа:
  
  
            * `CREATED` — возврат или невыкуп создан покупателем (оформлен).
  
  
            * `RECEIVED` — возврат подготовлен к отправке (принят у покупателя).
  
  
            * `IN_TRANSIT` — возврат или невыкуп в пути (отправлен).
  
  
            * `READY_FOR_PICKUP` — возврат или невыкуп готов к выдаче магазину.
  
  
            * `PICKED` — возврат или невыкуп выдан магазину.
  
  
            * `LOST` — возврат или невыкуп утерян (при транспортировке).
  
  
            * `EXPIRED` — покупатель не принес товар на возврат вовремя (возврат
            отменен).
  
  
            * `CANCELLED` — возврат или невыкуп отменен.
  
  
            * `FULFILMENT_RECEIVED` — возврат или невыкуп принят на складе
            Маркета.
  
  
            * `PREPARED_FOR_UTILIZATION` — возврат или невыкуп передан в очередь
            на утилизацию.
  
  
            * `NOT_IN_DEMAND` — возврат или невыкуп не забрали с почты.
  
  
            * `UTILIZED` — возврат или невыкуп утилизирован.
  
  
            * `READY_FOR_EXPROPRIATION` — товары в возврате или невыкупе
            направлены на перепродажу (проверка перед реализацией).
  
  
            * `RECEIVED_FOR_EXPROPRIATION` — товары в возврате или невыкупе
            приняты для перепродажи (реализация).
  
  
            * `UNKNOWN` — неизвестный статус, обратитесь в поддержку.
          type: string
          enum:
            - CREATED
            - RECEIVED
            - IN_TRANSIT
            - READY_FOR_PICKUP
            - PICKED
            - LOST
            - EXPIRED
            - CANCELLED
            - FULFILMENT_RECEIVED
            - PREPARED_FOR_UTILIZATION
            - NOT_IN_DEMAND
            - UTILIZED
            - READY_FOR_EXPROPRIATION
            - RECEIVED_FOR_EXPROPRIATION
            - UNKNOWN
    $defs:
      /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/ReturnType:
        description: |
          Тип фильтрации:
  
          * `UNREDEEMED` — невыкупы.
  
          * `RETURN` — возвраты.
  
          Если не указывать, в ответе будут и невыкупы, и возвраты.
        type: string
        enum:
          - UNREDEEMED
          - RETURN
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
  path: v2/reports/united-returns/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateUnitedReturnsReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
