---
title: Отчет по ключевым показателям
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md"
fetched_at: "2026-09-15T02:22:28Z"
content_sha: 1cf54355ea3922ce
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateKeyIndicatorsReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateKeyIndicatorsReport.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Структура и содержание отчетов могут изменяться без предварительного уведомления" %}

Например, может добавиться новая колонка или поменяться название листа.

{% endnote %}

<!-- source: ru/api/reports/generateKeyIndicatorsReport.md -->
<div class="openapi">

# Отчет по ключевым показателям

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateKeyIndicatorsReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * promotion:read-only — [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateKeyIndicatorsReport.md -->
  
  Запускает генерацию отчета по ключевым показателям. [Что это за отчет](https://yandex.ru/support/marketplace/ru/analytics/key-metrics)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/key_indicators/key_indicators.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Основные** (файл **key_indicators_summary**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || PERIOD | period | Период | string ||
  || GMV | gmv | Выручка, ₽ | number ||
  || ORDERS_DELIVERED | ordersDelivered | Доставленные заказы, шт. | integer ||
  || ORDERS_AVG_PRICE | ordersAvgPrice | Средний чек заказа, ₽ | number ||
  || TOTAL_SUBSIDY | totalSubsidy | Все платежи за скидки, ₽ | number ||
  ||
  SERVICES_WITHOUT_PROMOTION
  |
  servicesWithoutPromotion
  |
  Стоимость всех услуг Маркета без продвижения, ₽
  |
  number
  ||
  || PROMOTION_SERVICES | promotionServices | Стоимость услуг продвижения, ₽ | number ||
  |#

  {% endcut %}

  {% cut "Лист **Выручка** (файл **key_indicators_revenue**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || PERIOD | period | Период | string ||
  || GMV | gmv | Выручка, ₽ | number ||
  || TOTAL_SUBSIDY | totalSubsidy | Все платежи за скидки, ₽ | number ||
  || YANDEX_PLUS | yandexPlus | Платежи за скидки по баллам Яндекс Плюса, ₽ | number ||
  || SUBSIDY | subsidy | Платежи за скидки маркетплейса, ₽ | number ||
  |#

  {% endcut %}

  {% cut "Лист **Показатели продаж** (файл **key_indicators_sales**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || PERIOD | period | Период | string ||
  ||
  SHOWS
  |
  shows
  |
  Показы товаров

  |
  integer
  ||
  ||
  TO_CART_CONVERSION
  |
  toCartConversion
  |
  Конверсия 
  добавления 
  в корзину, %
  |
  number
  ||
  ||
  TO_ORDER_CONVERSION
  |
  toOrderConversion
  |
  Конверсия 
  из корзины 
  в заказ, %
  |
  number
  ||
  || ORDERS_DELIVERED | ordersDelivered | Доставленные заказы, шт. | integer ||
  || GMV | gmv | Выручка, ₽ | number ||
  ||
  ORDERS_AVG_PRICE
  |
  ordersAvgPrice
  |
  Средний чек 
  заказа, ₽
  |
  number
  ||
  ||
  ORDER_ITEMS_DELIVERED
  |
  orderItemsDelivered
  |
  Доставленные 
  товары, шт
  |
  integer
  ||
  ||
  ORDER_ITEM_AVG_PRICE
  |
  orderItemAvgPrice
  |
  Средняя стоимость 
  доставленного 
  товара, ₽
  |
  number
  ||
  |#

  {% endcut %}

  {% cut "Лист **Расходы** (файл **key_indicators_expenses**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || PERIOD | period | Период | string ||
  ||
  SERVICES_WITHOUT_PROMOTION
  |
  servicesWithoutPromotion
  |
  Стоимость всех 
  услуг Маркета 
  без продвижения, ₽
  |
  number
  ||
  ||
  FEE
  |
  fee
  |
  Стоимость размещения 
  товаров на витрине, ₽
  |
  number
  ||
  ||
  PAYMENT_ACCEPTANCE_AND_TRANSFER
  |
  paymentAcceptanceAndTransfer
  |
  Приём и 
  перевод платежа 
  покупателя, ₽
  |
  number
  ||
  ||
  LOGISTIC_SERVICES
  |
  logisticServices
  |
  Стоимость услуг 
  логистики, ₽
  |
  number
  ||
  ||
  WAREHOUSE_SERVICES
  |
  warehouseServices
  |
  Стоимость услуг 
  склада, ₽
  |
  number
  ||
  ||
  PROMOTION_SERVICES
  |
  promotionServices
  |
  Стоимость услуг 
  продвижения, ₽
  |
  number
  ||
  ||
  BOOST
  |
  boost
  |
  Расходы на 
  буст 
  продаж, ₽
  |
  number
  ||
  ||
  PROMOTION_WITH_SHOWS
  |
  promotionWithShows
  |
  Расходы на продвижение 
  с оплатой за показы, ₽
  |
  number
  ||
  ||
  LOYALTY_PARTICIPATION_FEE
  |
  loyaltyParticipationFee
  |
  Участие в программе 
  лояльности и отзывы, ₽
  |
  number
  ||
  || EXTENDED_ACCESS_PAYMENT | extendedAccessPayment | Расширенный доступ к сервисам Маркетплейса, ₽ | number ||
  |#

  {% endcut %}

  {% cut "Лист **Все** (файл **key_indicators_full**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || PERIOD | period | Период | string ||
  || SHOWS | shows | Показы товаров | integer ||
  ||
  TO_CART_CONVERSION
  |
  toCartConversion
  |
  Конверсия 
  добавления 
  в корзину, %
  |
  number
  ||
  ||
  TO_ORDER_CONVERSION
  |
  toOrderConversion
  |
  Конверсия 
  из корзины 
  в заказ, %
  |
  number
  ||
  ||
  ORDERS_DELIVERED
  |
  ordersDelivered
  |
  Доставленные 
  заказы, шт.
  |
  integer
  ||
  || GMV | gmv | Выручка, ₽ | number ||
  ||
  ORDERS_AVG_PRICE
  |
  ordersAvgPrice
  |
  Средний чек 
  заказа, ₽
  |
  number
  ||
  ||
  ORDER_ITEMS_DELIVERED
  |
  orderItemsDelivered
  |
  Доставленные 
  товары, шт
  |
  integer
  ||
  ||
  ORDER_ITEM_AVG_PRICE
  |
  orderItemAvgPrice
  |
  Средняя стоимость 
  доставленного 
  товара, ₽
  |
  number
  ||
  ||
  TOTAL_SUBSIDY
  |
  totalSubsidy
  |
  Все платежи 
  за скидки, ₽
  |
  number
  ||
  ||
  YANDEX_PLUS
  |
  yandexPlus
  |
  Платежи за скидки 
  по баллам Яндекс 
  Плюса, ₽
  |
  number
  ||
  ||
  SUBSIDY
  |
  subsidy
  |
  Платежи за скидки 
  маркетплейса, ₽
  |
  number
  ||
  ||
  SERVICES_WITHOUT_PROMOTION
  |
  servicesWithoutPromotion
  |
  Стоимость всех 
  услуг Маркета 
  без продвижения, ₽
  |
  number
  ||
  ||
  FEE
  |
  fee
  |
  Стоимость размещения 
  товаров на витрине, ₽
  |
  number
  ||
  ||
  PAYMENT_ACCEPTANCE_AND_TRANSFER
  |
  paymentAcceptanceAndTransfer
  |
  Приём и 
  перевод платежа 
  покупателя, ₽
  |
  number
  ||
  ||
  LOGISTIC_SERVICES
  |
  logisticServices
  |
  Стоимость услуг 
  логистики, ₽
  |
  number
  ||
  ||
  WAREHOUSE_SERVICES
  |
  warehouseServices
  |
  Стоимость услуг 
  склада, ₽
  |
  number
  ||
  ||
  PROMOTION_SERVICES
  |
  promotionServices
  |
  Стоимость услуг 
  продвижения, ₽
  |
  number
  ||
  ||
  BOOST
  |
  boost
  |
  Расходы на 
  буст 
  продаж, ₽
  |
  number
  ||
  ||
  PROMOTION_WITH_SHOWS
  |
  promotionWithShows
  |
  Расходы на продвижение 
  с оплатой за показы, ₽
  |
  number
  ||
  ||
  LOYALTY_PARTICIPATION_FEE
  |
  loyaltyParticipationFee
  |
  Участие в программе 
  лояльности и отзывы, ₽
  |
  number
  ||
  || EXTENDED_ACCESS_PAYMENT | extendedAccessPayment | Расширенный доступ к сервисам Маркетплейса, ₽ | number ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/key_indicators/key_indicators.md -->
  
  <!-- source: ru/_includes/common/report-data-period-400-days.md -->
  {% note warning "Ограничения по тарифному плану" %}

  Период выгрузки данных и количество одновременно генерирующихся отчетов зависят от вашего тарифного плана:
  * **Без подписки или тариф «Лайт»** — доступны данные за последние 90 дней, одновременно может генерироваться 1 отчет
  * **Тариф «Медиум»** — доступны данные за последние 400 дней, одновременно может генерироваться до 10 отчетов

  Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).

  {% endnote %}
  <!-- endsource: ru/_includes/common/report-data-period-400-days.md -->
  
  <!-- source: ru/_auto/method_limits/generateKeyIndicatorsReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateKeyIndicatorsReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/key-indicators/generate
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
    "campaignId": 1,
    "detalizationLevel": "WEEK"
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _detalizationLevel_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [KeyIndicatorsReportDetalizationLevelType](#entity-KeyIndicatorsReportDetalizationLevelType)
  
  За какой период нужна детализация.
  
  За какой период нужна детализация:
  
  * `WEEK` — по неделям.
  
  * `MONTH` — по месяцам.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `WEEK`, `MONTH`
  {.table-cell}
  ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BusinessId](#entity-BusinessId)
  
  Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property}
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
  
  ### KeyIndicatorsReportDetalizationLevelType {#entity-KeyIndicatorsReportDetalizationLevelType}
  
  За какой период нужна детализация:
  
  * `WEEK` — по неделям.
  
  * `MONTH` — по месяцам.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `WEEK`, `MONTH`
  
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
          /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
  headers: []
  body: |-
    {
      "businessId": 1,
      "campaignId": 1,
      "detalizationLevel": "WEEK"
    }
  schema:
    description: >
      Данные, необходимые для генерации отчета.
  
  
      В запросе обязательно должен быть либо `businessId`, либо `campaignId`, но
      не оба сразу.
    type: object
    required:
      - detalizationLevel
    properties:
      businessId:
        description: "Идентификатор кабинета. {% if audience == \"partner\" %}Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n{% endif %}\n"
        type: integer
        format: int64
        minimum: 1
      campaignId:
        description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
        type: integer
        format: int64
        minimum: 1
      detalizationLevel:
        description: За какой период нужна детализация.
        $ref: '#/$defs/KeyIndicatorsReportDetalizationLevelType'
    $defs:
      /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/api/generateKeyIndicatorsReport.yaml#/KeyIndicatorsReportDetalizationLevelType:
        description: |
          За какой период нужна детализация:
  
          * `WEEK` — по неделям.
  
          * `MONTH` — по месяцам.
        type: string
        enum:
          - WEEK
          - MONTH
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
  path: v2/reports/key-indicators/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateKeyIndicatorsReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
