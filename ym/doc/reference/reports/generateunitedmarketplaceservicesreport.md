---
title: Отчет по стоимости услуг
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md"
fetched_at: "2026-08-28T11:52:57Z"
content_sha: cd1afd695df32c03
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateUnitedMarketplaceServicesReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateUnitedMarketplaceServicesReport.md
  - href: ru/reference/reports/generateUnitedMarketplaceServicesReport.md
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

<!-- source: ru/api/reports/generateUnitedMarketplaceServicesReport.md -->
<div class="openapi">

# Отчет по стоимости услуг

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateUnitedMarketplaceServicesReport.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateUnitedMarketplaceServicesReport.md -->
  
  Запускает генерацию отчета по стоимости услуг за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/accounting/transactions#reports)
  
  Тип отчета зависит от того, какие поля заполнены в запросе:
  
  |**Тип отчета**               |**Какие поля нужны**             |
  |-----------------------------|---------------------------------|
  |По дате начисления услуги    |`dateFrom` и `dateTo`            |
  |По дате формирования акта    |`year` и `month`                 |
  
  Заказать отчеты обоих типов одним запросом нельзя.
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/united/services/generator/united_marketplace_services.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Размещение товаров и услуг** (файл **placement**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/Дата создания заказа
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара или услуги | string ||
  || TURBO_GOODS | turboGoods | Информация о заказе и товаре/Тип товара | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за товар или услугу | number ||
  ||
  DECOUPLING_MARKUP
  |
  decouplingMarkup
  |
  Информация о заказе и товаре/Разница между вашей ценой и ценой продажи
  |
  number
  ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || BATCH_SIZE | batchSize | Информация о заказе и товаре/Квант продажи | integer ||
  || BATCH_COUNT | batchCount | Информация о заказе и товаре/Квантов в заказе | integer ||
  || BATCH_PRICE | batchPrice | Информация о заказе и товаре/Цена за квант | number ||
  || WEIGHT | weight | Информация о заказе и товаре/Вес, кг | number ||
  || VOLUME | volume | Информация о заказе и товаре/Объем, л | number ||
  || LENGTH | length | Информация о заказе и товаре/Длина, см | number ||
  || WIDTH | width | Информация о заказе и товаре/Ширина, см | number ||
  || HEIGHT | height | Информация о заказе и товаре/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация о заказе и товаре/Сумма трёх измерений, см | number ||
  || PAYMENT_TYPE | paymentType | Информация о заказе и товаре/Способ приёма оплаты | string ||
  || QUALITY_INDEX | qualityIndex | Информация о заказе и товаре/Значение индекса качества | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF_TERMS | tariffTerms | Информация об услуге/Условия тарифа | string ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || MAX_TARIFF | maxTariff | Информация об услуге/Максимальный тариф за шт. | number ||
  || SERVICE_BEFORE_TARIFF | serviceBeforeTariff | Информация об услуге/Стоимость услуги до мин. тарифа | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  ||
  AMOUNT_WITHOUT_BONUSES
  |
  amountWithoutBonuses
  |
  Информация об услуге/Стоимость услуги без скидок и наценок
  |
  number
  ||
  ||
  FEE_BENEFIT_TARIFF
  |
  feeBenefitTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Тариф, %
  |
  number
  ||
  ||
  FEE_BENEFIT_DISCOUNT
  |
  feeBenefitDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Скидка с учётом минимального тарифа
  |
  number
  ||
  ||
  DAYS_OF_DELAY
  |
  daysOfDelay
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Опоздание при отгрузке или доставке, дни
  |
  integer
  ||
  ||
  LATE_ORDER_EXECUTION_FEE_TARIFF
  |
  lateOrderExecutionFeeTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Тариф при несвоевременной отгрузке или доставке, % от тарифа на размещение
  |
  number
  ||
  ||
  CANCELLATION_ORDER_FEE_TARIFF
  |
  cancellationOrderFeeTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Тариф при отмене по вине продавца, % от тарифа на размещение
  |
  number
  ||
  ||
  QUALITY_INDEX_MIN_TARIFF
  |
  qualityIndexMinTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Минимальная стоимость за шт.
  |
  number
  ||
  ||
  QUALITY_INDEX_MAX_TARIFF
  |
  qualityIndexMaxTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Максимальная стоимость за шт.
  |
  number
  ||
  ||
  QUALITY_INDEX_AMOUNT
  |
  qualityIndexAmount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Изменение стоимости услуги
  |
  number
  ||
  ||
  DECOUPLING_TARIFF
  |
  decouplingTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Умное предложение/Тариф, %
  |
  number
  ||
  ||
  DECOUPLING_PRICE_CHANGE
  |
  decouplingPriceChange
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Умное предложение/Изменение стоимости услуги
  |
  number
  ||
  ||
  INDIVIDUAL_DISCOUNT
  |
  individualDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Индивидуальная скидка на услугу
  |
  number
  ||
  ||
  LOYALTY_DISCOUNT
  |
  loyaltyDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Скидка за лояльность
  |
  number
  ||
  ||
  NETTING
  |
  netting
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Скидка за участие в совместных акциях
  |
  number
  ||
  || TOTAL_AMOUNT | totalAmount | Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Поручение на продажу** (файл **sale_commission**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/Дата создания заказа
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за шт. | number ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || PAYMENT_TYPE | paymentType | Информация о заказе и товаре/Способ приёма оплаты | string ||
  || QUALITY_INDEX | qualityIndex | Информация о заказе и товаре/Значение индекса качества | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  ||
  AMOUNT_WITHOUT_BONUSES
  |
  amountWithoutBonuses
  |
  Информация об услуге/Стоимость услуги без скидок и наценок
  |
  number
  ||
  ||
  FEE_BENEFIT_TARIFF
  |
  feeBenefitTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Тариф, %
  |
  number
  ||
  ||
  FEE_BENEFIT_DISCOUNT
  |
  feeBenefitDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Скидка с учётом минимального тарифа
  |
  number
  ||
  ||
  DAYS_OF_DELAY
  |
  daysOfDelay
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Опоздание при отгрузке или доставке, дни
  |
  integer
  ||
  ||
  LATE_ORDER_EXECUTION_FEE_TARIFF
  |
  lateOrderExecutionFeeTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Тариф при несвоевременной отгрузке или доставке, % от тарифа на размещение
  |
  number
  ||
  ||
  CANCELLATION_ORDER_FEE_TARIFF
  |
  cancellationOrderFeeTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Тариф при отмене по вине продавца, % от тарифа на размещение
  |
  number
  ||
  ||
  QUALITY_INDEX_MIN_TARIFF
  |
  qualityIndexMinTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Минимальная стоимость за шт.
  |
  number
  ||
  ||
  QUALITY_INDEX_MAX_TARIFF
  |
  qualityIndexMaxTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Максимальная стоимость за шт.
  |
  number
  ||
  ||
  QUALITY_INDEX_AMOUNT
  |
  qualityIndexAmount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Изменение стоимости услуги
  |
  number
  ||
  ||
  INDIVIDUAL_DISCOUNT
  |
  individualDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Индивидуальная скидка на услугу
  |
  number
  ||
  ||
  LOYALTY_DISCOUNT
  |
  loyaltyDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Скидка за лояльность
  |
  number
  ||
  || TOTAL_AMOUNT | totalAmount | Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Складская обработка** (файл **warehouse_processing**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/Дата создания заказа
  |
  string
  ||
  || WAREHOUSE | warehouse | Информация о заказе и товаре/Склад | string ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за шт. | number ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || BATCH_SIZE | batchSize | Информация о заказе и товаре/Квант продажи | integer ||
  || BATCH_COUNT | batchCount | Информация о заказе и товаре/Квантов в заказе | integer ||
  || BATCH_PRICE | batchPrice | Информация о заказе и товаре/Цена за квант | number ||
  || WEIGHT | weight | Информация о заказе и товаре/Вес, кг | number ||
  || LENGTH | length | Информация о заказе и товаре/Длина, см | number ||
  || WIDTH | width | Информация о заказе и товаре/Ширина, см | number ||
  || HEIGHT | height | Информация о заказе и товаре/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация о заказе и товаре/Сумма трёх измерений, см | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || MAX_TARIFF | maxTariff | Информация об услуге/Максимальный тариф за шт. | number ||
  ||
  SERVICE_PRICE_BEFORE_TARIFF
  |
  servicePriceBeforeTariff
  |
  Информация об услуге/Стоимость услуги без учёта ограничений тарифа
  |
  number
  ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Приемка поставки** (файл **goods_acceptance**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || FF_REEQUEST_ID | ffReequestId | Информация об услуге/Номер поставки на Маркете | string ||
  || WMS_ID | wmsId | Информация об услуге/Номер поставки на складе | string ||
  || WAREHOUSE | warehouse | Информация об услуге/Склад | string ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || WEIGHT | weight | Информация об услуге/Вес, кг | number ||
  || LENGTH | length | Информация об услуге/Длина, см | number ||
  || WIDTH | width | Информация об услуге/Ширина, см | number ||
  || HEIGHT | height | Информация об услуге/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация об услуге/Сумма трёх измерений, см | number ||
  || CARGO_PLACE_TYPE | cargoPlaceType | Информация об услуге/Тип грузоместа или товара | string ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || ACCEPTANCE_STAGE | acceptanceStage | Информация об услуге/Этап | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Программа лояльности и отзывы** (файл **loyalty_and_reviews**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || PRICE | price | Информация об услуге/Ваша цена за шт. | number ||
  || CLIENT_PRICE | clientPrice | Информация об услуге/Покупатель заплатил | number ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || REVIEW_ID | reviewId | Информация об услуге/ID отзыва | string ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  ||
  TARIFF_OR_BET_FOR_REVIEW
  |
  tariffOrBetForReview
  |
  Информация об услуге/Тариф за шт. или ставка продавца за отзыв
  |
  number
  ||
  || PROMO_AMOUNT | promoAmount | Информация об услуге/Ставка по условиям акции | number ||
  || CUSTOMER_BONUS_AMOUNT | customerBonusAmount | Информация об услуге/Количество баллов покупателю | number ||
  || DISCOUNT | discount | Информация об услуге/Скидка | number ||
  || PAYMENT_WITH_BONUSES | paymentWithBonuses | Информация об услуге/Оплата бонусами | number ||
  |#

  {% endcut %}

  {% cut "Лист **Буст продаж, оплата за продажи** (файл **boost**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || CATEGORY | category | Информация об услуге/Категория | string ||
  || PRICE | price | Информация об услуге/Ваша цена за шт. | number ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || BET | bet | Информация об услуге/Сработавшая ставка, % от цены продажи | number ||
  || PREPAID | prepaid | Информация об услуге/Предоплата | number ||
  || POSTPAID | postpaid | Информация об услуге/Постоплата | number ||
  || BONUS_PAID | bonusPaid | Информация об услуге/Оплата бонусами | number ||
  || NETTING | netting | Информация об услуге/Скидка за участие в совместных акциях | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Рассрочка** (файл **installment_plan**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || PRICE | price | Информация об услуге/Ваша цена за шт. | number ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. (применяется к цене товара до скидок) | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || TYPE | type | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Полки** (файл **shelf**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | string ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || PAYMENT | payment | Информация об услуге/Оплата | number ||
  || BONUS_PAID | bonusPaid | Информация об услуге/Оплата бонусами | number ||
  || NETTING | netting | Информация об услуге/Скидка за участие в совместных акциях | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Буст продаж, оплата за показы** (файл **cpm-boost**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || PAYMENT | payment | Информация об услуге/Оплата | number ||
  || BONUS_PAID | bonusPaid | Информация об услуге/Оплата бонусами | number ||
  || NETTING | netting | Информация об услуге/Скидка за участие в совместных акциях | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Товарные баннеры** (файл **product-banners**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || PAYMENT | payment | Информация об услуге/Оплата | number ||
  || BONUS_PAID | bonusPaid | Информация об услуге/Оплата бонусами | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Баннеры** (файл **banners**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Пуш-уведомления** (файл **pushes**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Поп-ап уведомления** (файл **popups**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Доставка покупателю** (файл **delivery**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/Дата создания заказа
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара или тип грузоместа | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за шт. | number ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || BATCH_SIZE | batchSize | Информация о заказе и товаре/Квант продажи | integer ||
  || BATCH_COUNT | batchCount | Информация о заказе и товаре/Квантов в заказе | integer ||
  || BATCH_PRICE | batchPrice | Информация о заказе и товаре/Цена за квант | number ||
  || WEIGHT | weight | Информация о заказе и товаре/Вес, кг | number ||
  || DIMENSIONAL_WEIGHT | dimensionalWeight | Информация о заказе и товаре/Объёмный вес, кг | number ||
  || VOLUME | volume | Информация о заказе и товаре/Объем, л | number ||
  || LENGTH | length | Информация о заказе и товаре/Длина, см | number ||
  || WIDTH | width | Информация о заказе и товаре/Ширина, см | number ||
  || HEIGHT | height | Информация о заказе и товаре/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация о заказе и товаре/Сумма трёх измерений, см | number ||
  || LOCALITY_INDEX | localityIndex | Информация о заказе и товаре/Доля локальных продаж, % | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || FROM | from | Информация об услуге/Откуда | string ||
  || TO | to | Информация об услуге/Куда | string ||
  || DELIVERY_TYPE | deliveryType | Информация об услуге/Способ доставки | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || MAX_TARIFF | maxTariff | Информация об услуге/Максимальный тариф за шт. | number ||
  ||
  SERVICE_PRICE_BEFORE_TARIFF
  |
  servicePriceBeforeTariff
  |
  Информация об услуге/Стоимость услуги без учёта ограничений тарифа
  |
  number
  ||
  || LOCALITY_COEFFICIENT | localityCoefficient | Информация об услуге/Коэффициент локальности | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Доставка (средняя миля)** (файл **crossregional_delivery**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/${mbi.reports.united.services:column.order.or.return.creation.time}
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за шт. | number ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || WEIGHT | weight | Информация о заказе и товаре/Вес, кг | number ||
  || DIMENSIONAL_WEIGHT | dimensionalWeight | Информация о заказе и товаре/Объёмный вес, кг | number ||
  || VOLUME | volume | Информация о заказе и товаре/Объем, л | number ||
  || LENGTH | length | Информация о заказе и товаре/Длина, см | number ||
  || WIDTH | width | Информация о заказе и товаре/Ширина, см | number ||
  || HEIGHT | height | Информация о заказе и товаре/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация о заказе и товаре/Сумма трёх измерений, см | number ||
  || LOCALITY_INDEX | localityIndex | Информация о заказе и товаре/Доля локальных продаж, % | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || FROM | from | Информация об услуге/Откуда | string ||
  || TO | to | Информация об услуге/Куда | string ||
  || DELIVERY_TYPE | deliveryType | Информация об услуге/Способ доставки | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || MAX_TARIFF | maxTariff | Информация об услуге/Максимальный тариф за шт. | number ||
  ||
  SERVICE_PRICE_BEFORE_TARIFF
  |
  servicePriceBeforeTariff
  |
  Информация об услуге/Стоимость услуги без учёта ограничений тарифа
  |
  number
  ||
  || LOCALITY_COEFFICIENT | localityCoefficient | Информация об услуге/Коэффициент локальности | number ||
  || NETTING | netting | Информация об услуге/Скидка за участие в совместных акциях | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Экспресс-доставка покупателю** (файл **express_delivery**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/Дата создания заказа
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за шт. | number ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || BATCH_SIZE | batchSize | Информация о заказе и товаре/Квант продажи | integer ||
  || BATCH_COUNT | batchCount | Информация о заказе и товаре/Квантов в заказе | integer ||
  || BATCH_PRICE | batchPrice | Информация о заказе и товаре/Цена за квант | number ||
  || WEIGHT | weight | Информация о заказе и товаре/Вес, кг | number ||
  || LENGTH | length | Информация о заказе и товаре/Длина, см | number ||
  || WIDTH | width | Информация о заказе и товаре/Ширина, см | number ||
  || HEIGHT | height | Информация о заказе и товаре/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация о заказе и товаре/Сумма трёх измерений, см | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за заказ/шт. | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || MAX_TARIFF | maxTariff | Информация об услуге/Максимальный тариф за шт. | number ||
  ||
  SERVICE_PRICE_BEFORE_TARIFF
  |
  servicePriceBeforeTariff
  |
  Информация об услуге/Стоимость услуги без учёта ограничений тарифа
  |
  number
  ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Доставка из-за рубежа** (файл **delivery_from_abroad**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация о заказе/Дата создания заказа | string ||
  || PARCELS_COUNT | parcelsCount | Информация о заказе/Количество отправлений в заказе, шт. | integer ||
  || WEIGHT | weight | Информация о заказе/Вес всех отправлений в заказе, кг | number ||
  || WEIGHT_ROUNDED | weightRounded | Информация о заказе/Вес после округления, кг | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || FROM | from | Информация об услуге/Откуда | string ||
  || TO | to | Информация об услуге/Куда | string ||
  || SHIPPING_TARIFF | shippingTariff | Информация об услуге/Тариф за отправление | number ||
  || TARIFF_FOR_WEIGHT | tariffForWeight | Информация об услуге/Тариф за 1 кг | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Приём платежа** (файл **payment_accepting**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация об услуге/Дата создания заказа | string ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара или услуги | string ||
  || BUYER_PAID | buyerPaid | Информация об услуге/Покупатель заплатил | number ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || RECORD_TYPE | recordType | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Перевод платежа** (файл **payment_transfer**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация об услуге/Дата создания заказа | string ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара или услуги | string ||
  || MERCHANT_PRICE | merchantPrice | Информация об услуге/Ваша цена | number ||
  || BUYER_PAID | buyerPaid | Информация об услуге/Покупатель заплатил | number ||
  || PAYMENT_AMOUNT | paymentAmount | Информация об услуге/Сумма досрочной выплаты | number ||
  ||
  TARIFF_FOR_TRANSFER
  |
  tariffForTransfer
  |
  Информация об услуге/Тариф, до 28.02.26 — % от платежа покупателя,
   с 1.03.2026 — % от цены товара или услуги

  |
  number
  ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || RECORD_TYPE | recordType | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Поручение на перевод платежа** (файл **money_withdraw**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация об услуге/Дата создания заказа | string ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || ITEM_PRICE | itemPrice | Информация об услуге/Ваша цена за шт. | number ||
  ||
  TARIFF_FOR_TRANSFER
  |
  tariffForTransfer
  |
  Информация об услуге/Тариф, до 28.02.26 — % от платежа покупателя,
   с 1.03.2026 — % от цены товара
  |
  number
  ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || RECORD_TYPE | recordType | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Бронирование товара** (файл **item_booking**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  ||
  ORDER_CREATION_DATE_TIME
  |
  orderCreationDateTime
  |
  Информация о заказе и товаре/Дата создания заказа
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация о заказе и товаре/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказе и товаре/Название товара | string ||
  || PRICE | price | Информация о заказе и товаре/Ваша цена за шт. | number ||
  || COUNT | count | Информация о заказе и товаре/Количество, шт. | integer ||
  || PAYMENT_TYPE | paymentType | Информация о заказе и товаре/Способ приёма оплаты | string ||
  || QUALITY_INDEX | qualityIndex | Информация о заказе и товаре/Значение индекса качества | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || UNIT | unit | Информация об услуге/Единица измерения | string ||
  || MIN_TARIFF | minTariff | Информация об услуге/Минимальный тариф за шт. | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  ||
  AMOUNT_WITHOUT_BONUSES
  |
  amountWithoutBonuses
  |
  Информация об услуге/Стоимость услуги без скидок и наценок
  |
  number
  ||
  ||
  FEE_BENEFIT_TARIFF
  |
  feeBenefitTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Тариф, %
  |
  number
  ||
  ||
  FEE_BENEFIT_DISCOUNT
  |
  feeBenefitDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Скидка с учётом минимального тарифа
  |
  number
  ||
  ||
  DAYS_OF_DELAY
  |
  daysOfDelay
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Опоздание при отгрузке или доставке, дни
  |
  integer
  ||
  ||
  LATE_ORDER_EXECUTION_FEE_TARIFF
  |
  lateOrderExecutionFeeTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Тариф при несвоевременной отгрузке или доставке, % от тарифа на размещение
  |
  number
  ||
  ||
  CANCELLATION_ORDER_FEE_TARIFF
  |
  cancellationOrderFeeTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Тариф при отмене по вине продавца, % от тарифа на размещение
  |
  number
  ||
  ||
  QUALITY_INDEX_MIN_TARIFF
  |
  qualityIndexMinTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Минимальная стоимость за шт.
  |
  number
  ||
  ||
  QUALITY_INDEX_MAX_TARIFF
  |
  qualityIndexMaxTariff
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Максимальная стоимость за шт.
  |
  number
  ||
  ||
  QUALITY_INDEX_AMOUNT
  |
  qualityIndexAmount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Отмены по вине продавца, отгрузка или доставка не вовремя/Изменение стоимости услуги
  |
  number
  ||
  ||
  INDIVIDUAL_DISCOUNT
  |
  individualDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Индивидуальная скидка на услугу
  |
  number
  ||
  ||
  LOYALTY_DISCOUNT
  |
  loyaltyDiscount
  |
  Уменьшение (скидка) и увеличение  стоимости услуги/Прочие скидки/Скидка за лояльность
  |
  number
  ||
  || TOTAL_AMOUNT | totalAmount | Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Платное хранение до 31.05.22** (файл **paid_storage_before_31-05-22**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || MARKET_SKU | marketSku | Информация об услуге/SKU на Яндексе | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || WEIGHT | weight | Информация об услуге/Вес, кг | number ||
  || LENGTH | length | Информация об услуге/Длина, см | number ||
  || WIDTH | width | Информация об услуге/Ширина, см | number ||
  || HEIGHT | height | Информация об услуге/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация об услуге/Сумма трёх измерений, см | number ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Платное хранение с 01.06.22** (файл **paid_storage_after_01-06-22**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || CATEGORY | category | Информация об услуге/Категория | string ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || WAREHOUSE | warehouse | Информация об услуге/Склад или кластер | string ||
  || AVG_STOCK_LITERS | avgStockLiters | Информация об услуге/Среднесуточный объём товаров на складе, л | number ||
  || AVG_SOLD_LITERS | avgSoldLiters | Информация об услуге/Среднесуточный объём проданных товаров, л | number ||
  || TURNOVER_DAYS | turnoverDays | Информация об услуге/Оборачиваемость, дни | string ||
  || LENGTH_PRODUCT_M | lengthProductM | Информация об услуге/Длина единицы товара, м | string ||
  || WIDTH_PRODUCT_M | widthProductM | Информация об услуге/Ширина единицы товара, м | string ||
  || HEIGHT_PRODUCT_M | heightProductM | Информация об услуге/Высота единицы товара, м | string ||
  || COUNT_PRODUCT_UNIT | countProductUnit | Информация об услуге/Количество единиц товара, шт. | string ||
  ||
  VOLUME_UNITS_OF_GOODS
  |
  volumeUnitsOfGoods
  |
  Информация об услуге/Объём всех единиц товара, кубометры
  |
  string
  ||
  || MEASUREMENT_UNIT | measurementUnit | Информация об услуге/Единица измерения | string ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || TRANSACTION_TYPE | transactionType | Информация об услуге/Тип транзакции | string ||
  || STORAGE_PERIOD | storagePeriod | Информация об услуге/Количество дней хранения по тарифу | integer ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || PAID_STORAGE | paidStorage | Информация об услуге/Стоимость платного хранения | number ||
  |#

  {% endcut %}

  {% cut "Лист **Поставка через транзитный склад** (файл **delivery_via_transit_warehouse**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || MARKET_DELIVERY_ID | marketDeliveryId | Информация об услуге/Номер поставки на Маркете | string ||
  || WAREHOUSE_DELIVERY_ID | warehouseDeliveryId | Информация об услуге/Номер поставки на складе | integer ||
  || ACCEPTANCE_POINT | acceptancePoint | Информация об услуге/Точка отгрузки | string ||
  ||
  SERVICES_COLUMN_MANY_WAREHOUSES_SUPPLY
  |
  servicesColumnManyWarehousesSupply
  |
  Информация об услуге/Поставка для нескольких складов
  |
  string
  ||
  || XDOC_FROM | xdocFrom | Информация об услуге/Откуда | string ||
  || XDOC_TO | xdocTo | Информация об услуге/Куда | string ||
  ||
  SERVICES_COLUMN_VDC_DIRECTIONS_COUNT
  |
  servicesColumnVdcDirectionsCount
  |
  Информация об услуге/Количество доехавших направлений в поставке
  |
  integer
  ||
  || IS_BOX | isBox | Информация об услуге/Палета или коробка | string ||
  || CARGO_PLACE_TYPE | cargoPlaceType | Информация об услуге/Тип грузоместа или товара | string ||
  || VOLUME_LITERS | volumeLiters | Информация об услуге/Объём поставки, л. | integer ||
  || TURBO_PERCENTAGE | turboPercentage | Информация об услуге/Доля турбо в поставке, % | number ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || MEASUREMENT_UNIT | measurementUnit | Информация об услуге/Единица измерения | string ||
  || MINIMUM_TARIFF_LIMIT | minimumTariffLimit | Информация об услуге/Минимальное ограничение тарифа | number ||
  || MINIMUM_TARIFF_CONDITION | minimumTariffCondition | Информация об услуге/Условие ограничения | string ||
  || BOX_COUNT | boxCount | Информация об услуге/Количество палет или коробок, шт. | integer ||
  || DISCOUNT_PERCENT | discountPercent | Информация об услуге/Скидка, % | number ||
  || DISCOUNT_AMOUNT | discountAmount | Информация об услуге/Скидка | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Приём излишков на складе** (файл **reception_of_surplus**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || MARKET_DELIVERY_ID | marketDeliveryId | Информация об услуге/Номер поставки на Маркете | string ||
  || WAREHOUSE_DELIVERY_ID | warehouseDeliveryId | Информация об услуге/Номер поставки на складе | integer ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || PAYMENT_TYPE | paymentType | Информация об услуге/Тип начисления | string ||
  |#

  {% endcut %}

  {% cut "Лист **Нанесение знака маркировки** (файл **product_marking**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || MARKET_DELIVERY_ID | marketDeliveryId | Информация об услуге/Номер поставки на Маркете | integer ||
  || WAREHOUSE_DELIVERY_ID | warehouseDeliveryId | Информация об услуге/Номер поставки на складе | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за шт. | number ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Вывоз со склада, СЦ, ПВЗ** (файл **export_from_warehouse**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || MARKET_REQUEST_ID | marketRequestId | Информация об услуге/Номер заявки на Маркете | string ||
  || WAREHOUSE_REQUEST_ID | warehouseRequestId | Информация об услуге/Номер заявки на складе | string ||
  || WAREHOUSE | warehouse | Информация об услуге/Склад | string ||
  || XDOC_FROM | xdocFrom | Информация об услуге/Откуда | string ||
  || XDOC_TO | xdocTo | Информация об услуге/Куда | string ||
  || CARGO_PLACE_TYPE | cargoPlaceType | Информация об услуге/Тип грузоместа или товара | string ||
  || VOLUME_LITERS | volumeLiters | Информация об услуге/Объём поставки, л. | integer ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || STOCK | stock | Информация об услуге/Сток | string ||
  || ESTIMATED_COST | estimatedCost | Информация об услуге/Оценочная стоимость | number ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || WEIGHT | weight | Информация об услуге/Вес, кг | number ||
  || LENGTH | length | Информация об услуге/Длина, см | number ||
  || WIDTH | width | Информация об услуге/Ширина, см | number ||
  || HEIGHT | height | Информация об услуге/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация об услуге/Сумма трёх измерений, см | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || MEASUREMENT_UNIT | measurementUnit | Информация об услуге/Единица измерения | string ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Организация забора заказов** (файл **intake_logistics**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация об услуге/Дата создания заказа | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || GOODS_COUNT | goodsCount | Информация об услуге/Количество товаров, шт. | integer ||
  || CARGO_TYPE | cargoType | Информация об услуге/Тип товара | string ||
  || WEIGHT | weight | Информация об услуге/Вес, кг | number ||
  || DIMENSIONAL_WEIGHT | dimensionalWeight | Информация об услуге/Объёмный вес, кг | number ||
  || LENGTH | length | Информация об услуге/Длина, см | number ||
  || WIDTH | width | Информация об услуге/Ширина, см | number ||
  || HEIGHT | height | Информация об услуге/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация об услуге/Сумма трёх измерений, см | number ||
  || ORDER_COUNT | orderCount | Информация об услуге/Количество заказов | integer ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || UNIT_NAME | unitName | Информация об услуге/За что начисляется тариф | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за заказ/шт. | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || RECORD_TYPE | recordType | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Обработка заказов в СЦ или ПВЗ** (файл **order_processing**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация об услуге/Дата создания заказа | string ||
  ||
  BOX_EXTERNAL_ID
  |
  boxExternalId
  |
  Информация об услуге/Номер возвратного отправления (штрихкод коробки)
  |
  string
  ||
  || LOCATION | location | Информация об услуге/Место отгрузки заказов | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф за заказ или отправление | number ||
  || MIN_AMOUNT | minAmount | Информация об услуге/Минимальная сумма | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || RECORD_TYPE | recordType | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Обработка заказов на складе** (файл **order_processing_on_warehouse**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || ORDER_CREATION_DATE_TIME | orderCreationDateTime | Информация об услуге/Дата создания заказа | string ||
  ||
  BOX_EXTERNAL_ID
  |
  boxExternalId
  |
  Информация об услуге/Номер возвратного отправления (штрихкод коробки)
  |
  string
  ||
  || TARIFF | tariff | Информация об услуге/Тариф за отправление | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Хранение невыкупов и возвратов** (файл **storage_of_returns**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || RESUPPLY_TYPE | resupplyType | Информация об услуге/Возврат или невыкуп | string ||
  || ORDER_ID | orderId | Информация об услуге/Номер заказа или отгрузки | integer ||
  || RETURN_ID | returnId | Информация об услуге/Номер возврата | integer ||
  || RETURN_COUNT | returnCount | Информация об услуге/Количество возвращенных товаров шт. | integer ||
  ||
  UNREDEEMED_ORDER_TARIFF
  |
  unredeemedOrderTariff
  |
  Информация об услуге/Тариф за хранение невыкупленного заказа
  |
  number
  ||
  || RETURN_TARIFF | returnTariff | Информация об услуге/Тариф за хранение возврата | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || RECORD_TYPE | recordType | Информация об услуге/Тип записи | string ||
  |#

  {% endcut %}

  {% cut "Лист **Вознаграждение за продажу** (файл **expropriation**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_NUMBER | orderNumber | Информация о заказе и товаре/Номер заказа или отгрузки | integer ||
  || SKU | sku | Информация о заказе и товаре/Ваш SKU | string ||
  || PRODUCT_NAME | productName | Информация о заказе и товаре/Название товара | string ||
  || MERCHANT_PRICE | merchantPrice | Информация о заказе и товаре/Ваша цена | number ||
  || SELL_PRICE | sellPrice | Информация о заказе и товаре/Цена продажи | number ||
  || SERVICE | service | Информация об услуге/Услуга | string ||
  || TARIFF_PER_ITEM | tariffPerItem | Информация об услуге/Тариф за шт. | number ||
  || MEASUREMENT_UNIT | measurementUnit | Информация об услуге/Единица измерения | string ||
  || DATE_TIME | dateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || FULL_PRICE | fullPrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Организация утилизации** (файл **utilization**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || UTILIZATION_REQUEST_ID | utilizationRequestId | Информация об услуге/Номер заявки на утилизацию | string ||
  ||
  UTILIZATION_REQUEST_DATE_TIME
  |
  utilizationRequestDateTime
  |
  Информация об услуге/Дата и время создания заявки на утилизацию
  |
  string
  ||
  || SHOP_SKU | shopSku | Информация об услуге/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация об услуге/Название товара | string ||
  || COUNT | count | Информация об услуге/Количество, шт. | integer ||
  || WEIGHT | weight | Информация об услуге/Вес, кг | number ||
  || LENGTH | length | Информация об услуге/Длина, см | number ||
  || WIDTH | width | Информация об услуге/Ширина, см | number ||
  || HEIGHT | height | Информация об услуге/Высота, см | number ||
  || DIMENSIONS_SUM | dimensionsSum | Информация об услуге/Сумма трёх измерений, см | number ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || SERVICE_DATE_TIME | serviceDateTime | Информация об услуге/Дата и время оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Расширенный доступ к сервисам** (файл **extended_service_access**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || SECURITY_PAYMENT_ID | securityPaymentId | Информация об услуге/Номер обеспечительного платежа | string ||
  || SECURITY_PAYMENT_DATE | securityPaymentDate | Информация об услуге/Дата обеспечительного платежа | string ||
  ||
  SECURITY_PAYMENT_AMOUNT
  |
  securityPaymentAmount
  |
  Информация об услуге/Сумма обеспечительного платежа
  |
  number
  ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Подписки** (файл **business_subscription**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф в месяц | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || COMMENTARY | commentary | Информация об услуге/Комментарий | string ||
  |#

  {% endcut %}

  {% cut "Лист **Персональный менеджер** (файл **personal_manager**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || TARIFF | tariff | Информация об услуге/Тариф в месяц | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  || COMMENTARY | commentary | Информация об услуге/Комментарий | string ||
  |#

  {% endcut %}

  {% cut "Лист **Рассылки** (файл **mailing**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Реклама на внешних площадках** (файл **web**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **ТВ реклама** (файл **tv**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Реклама на Маркете** (файл **yandex-market**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}

  {% cut "Лист **Видеобаннеры в такси** (файл **pads**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || PLACEMENT_MODEL | placementModel | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || PARTNER_NAME | partnerName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ADVERTISER_ID | advertiserId | Информация об услуге/ID рекламодателя | integer ||
  || CAMPAIGN_ID | campaignId | Информация об услуге/Номер кампании | integer ||
  || CAMPAIGN_NAME | campaignName | Информация об услуге/Название кампании | string ||
  || SERVICE_NAME | serviceName | Информация об услуге/Услуга | string ||
  || EVENTS_COUNT | eventsCount | Информация об услуге/Показы, шт. | integer ||
  || SURFACE_TYPE | surfaceType | Информация об услуге/Площадка | string ||
  || DAILY_LIMIT | dailyLimit | Информация об услуге/Бюджет | number ||
  || SERVICE_DATE | serviceDate | Информация об услуге/Дата оказания услуги | string ||
  || ACT_DATE | actDate | Информация об услуге/Дата формирования акта | string ||
  || LIMIT_TYPE | limitType | Информация об услуге/Тип бюджета | string ||
  || SERVICE_PRICE | servicePrice | Информация об услуге/Стоимость услуги | number ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/united/services/generator/united_marketplace_services.md -->
  
  <!-- source: ru/_auto/method_limits/generateUnitedMarketplaceServicesReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateUnitedMarketplaceServicesReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/united-marketplace-services/generate
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
  ||
  
  _language_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [ReportLanguageType](#entity-ReportLanguageType)
  
  Язык отчета или документа.
  
  Язык отчета:
  
  * `RU` — русский язык.
  * `EN` — английский язык.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `EN`
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
  
  ### ReportLanguageType {#entity-ReportLanguageType}
  
  Язык отчета:
  
  * `RU` — русский язык.
  * `EN` — английский язык.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `EN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "businessId": 1,
    "dateTimeFrom": "2025-01-01T00:00:00Z",
    "dateTimeTo": "2025-01-01T00:00:00Z",
    "dateFrom": "2025-08-22",
    "dateTo": "2025-01-01",
    "yearFrom": 2025,
    "monthFrom": 12,
    "yearTo": null,
    "monthTo": null,
    "placementPrograms": [
      "FBS"
    ],
    "inns": [
      "example"
    ],
    "campaignIds": [
      1
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
  
  _dateFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PeriodDateFrom](#entity-PeriodDateFrom)
  
  Начало периода, включительно.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-08-22`
  {.table-cell}
  ||
  ||
  
  _dateTimeFrom_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `dateFrom`.
  
  {% endnote %}
  
  Начало периода, включительно.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _dateTimeTo_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `dateTo`.
  
  {% endnote %}
  
  Конец периода, включительно. Максимальный период — 3 месяца.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01T00:00:00Z`
  {.table-cell}
  ||
  ||
  
  _dateTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string&lt;date&gt;
  
  Конец периода, включительно. Максимальный период — 3 месяца.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
  {.table-cell}
  ||
  ||
  
  _inns_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Список ИНН, которые нужны в отчете.
  
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
  
  _monthFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Month](#entity-Month)
  
  Начальный номер месяца формирования акта.
  
  Номер месяца.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  _Example:_{.json-schema-reset .json-schema-example} `12`
  {.table-cell}
  ||
  ||
  
  _monthTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Month](#entity-Month)
  
  Конечный номер месяца формирования акта.
  
  Номер месяца.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  _Example:_{.json-schema-reset .json-schema-example} `12`
  {.table-cell}
  ||
  ||
  
  _placementPrograms_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PlacementType](#entity-PlacementType)[] &#124; null
  
  Список моделей, которые нужны в отчете.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "FBS"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _yearFrom_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Year](#entity-Year)
  
  Начальный год формирования акта.
  
  Год.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025`
  {.table-cell}
  ||
  ||
  
  _yearTo_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Year](#entity-Year)
  
  Конечный год формирования акта.
  
  Год.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025`
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
  
  ### Year {#entity-Year}
  
  Год.
  
  **Type**: integer
  
  </div>
  
  <div class="openapi-entity">
  
  ### Month {#entity-Month}
  
  Номер месяца.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PlacementType {#entity-PlacementType}
  
  Модель, по которой работает магазин:
  
  * `FBS` — FBS или Экспресс.
  * `FBY` — FBY.
  * `DBS` — DBS.
  * `LAAS` — LaaS.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `FBS`, `FBY`, `DBS`, `LAAS`
  
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
  pathParams: []
  searchParams:
    - description: Формат отчета или документа.
      name: format
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
    - description: Язык отчета или документа.
      name: language
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportLanguageType
  headers: []
  body: |-
    {
      "businessId": 1,
      "dateTimeFrom": "2025-01-01T00:00:00Z",
      "dateTimeTo": "2025-01-01T00:00:00Z",
      "dateFrom": "2025-08-22",
      "dateTo": "2025-01-01",
      "yearFrom": 2025,
      "monthFrom": 12,
      "yearTo": null,
      "monthTo": null,
      "placementPrograms": [
        "FBS"
      ],
      "inns": [
        "example"
      ],
      "campaignIds": [
        1
      ]
    }
  schema:
    description: >
      Данные, необходимые для генерации отчета: идентификатор кампании, период, за
      который нужен отчет, а также фильтры.
    type: object
    required:
      - businessId
    properties:
      businessId:
        description: "Идентификатор кабинета. {% if audience == \"partner\" %}Чтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n{% endif %}\n"
        type: integer
        format: int64
        minimum: 1
      dateTimeFrom:
        description: |
          {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
          Вместо него используйте `dateFrom`.
  
          {% endnote %}
  
          Начало периода, включительно.
        format: date-time
        type: string
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-12'
          replacement-field: dateFrom
      dateTimeTo:
        description: |
          {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
          Вместо него используйте `dateTo`.
  
          {% endnote %}
  
          Конец периода, включительно. Максимальный период — 3 месяца.
        format: date-time
        type: string
        deprecated: true
        x-deprecation-config:
          shutdown-date: '2026-10-12'
          replacement-field: dateTo
      dateFrom:
        type: string
        format: date
        description: |
          Начало периода, включительно.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        example: '2025-08-22'
      dateTo:
        description: |
          Конец периода, включительно. Максимальный период — 3 месяца.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        format: date
        type: string
      yearFrom:
        description: Начальный год формирования акта.
        $ref: '#/$defs/Year'
      monthFrom:
        description: Начальный номер месяца формирования акта.
        $ref: '#/$defs/Month'
      yearTo:
        description: Конечный год формирования акта.
        $ref: '#/$defs/Year'
      monthTo:
        description: Конечный номер месяца формирования акта.
        $ref: '#/$defs/Month'
      placementPrograms:
        description: |
          Список моделей, которые нужны в отчете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          description: |
            Модель, по которой работает магазин:
  
            * `FBS` — FBS или Экспресс.
            * `FBY` — FBY.
            * `DBS` — DBS.
            * `LAAS` — LaaS.
          type: string
          enum:
            - FBS
            - FBY
            - DBS
            - LAAS
      inns:
        description: Список ИНН, которые нужны в отчете.
        type: array
        nullable: true
        minItems: 1
        uniqueItems: true
        items:
          type: string
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
    $defs:
      /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/Year:
        description: Год.
        type: integer
        format: int32
        example: 2025
      /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/Month:
        description: Номер месяца.
        type: integer
        format: int32
        minimum: 1
        maximum: 12
        example: 12
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
  path: v2/reports/united-marketplace-services/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateUnitedMarketplaceServicesReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
