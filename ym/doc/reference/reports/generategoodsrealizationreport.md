---
title: Отчет по реализации
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md"
fetched_at: "2026-08-28T11:52:56Z"
content_sha: 724e5826b796ee63
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateGoodsRealizationReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateGoodsRealizationReport.md
  - href: ru/reference/reports/generateGoodsRealizationReport.md
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

<!-- source: ru/api/reports/generateGoodsRealizationReport.md -->
<div class="openapi">

# Отчет по реализации

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateGoodsRealizationReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateGoodsRealizationReport.md -->
  
  Запускает генерацию отчета по реализации за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/accounting/transactions#sales-report)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  {% list tabs %}
  
  - FBY, FBS, Экспресс
  
    <!-- source: ru/_auto/reports/united/statistics/generator/united_statistics_v2.md -->
    Пояснение к колонкам отчета:

    {% cut "Лист **Товары, переданные в доставку** (файл **transferred_to_delivery**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название товара | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    transferredToDeliveryPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех переданных в доставку штук с НДС без учёта скидок
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_DISCOUNT_SUM
    |
    transferredToDeliveryDiscountSum
    |
    Заказы/Сумма всех скидок для переданных в доставку штук
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    transferredToDeliveryPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех переданных в доставку штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Документы/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Документы/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Документы/Номер УКД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    |#

    {% endcut %}

    {% cut "Лист **Доставленные товары** (файл **delivered**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название товара | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || DELIVERED_COUNT | deliveredCount | Заказы/Доставлено, шт. | integer ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    DELIVERED_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    deliveredPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех доставленных штук с НДС без учёта скидок
    |
    number
    ||
    || DELIVERED_DISCOUNT_SUM | deliveredDiscountSum | Заказы/Сумма всех скидок для доставленных штук | number ||
    ||
    DELIVERED_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    deliveredPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех доставленных штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    |#

    {% endcut %}

    {% cut "Лист **Невыкупленные товары** (файл **unredeemed**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название товара | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || UNREDEEMED_COUNT | unredeemedCount | Заказы/Не выкуплено, шт. | integer ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    ||
    UNREDEEMED_WAREHOUSE_OR_SC_ACCEPT_DATE
    |
    unredeemedWarehouseOrScAcceptDate
    |
    Заказы/Дата приёма невыкупа складом или сортировочным центром
    |
    string
    ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    UNREDEEMED_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    unredeemedPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех невыкупленных штук с НДС без учёта скидок
    |
    number
    ||
    || UNREDEEMED_DISCOUNT_SUM | unredeemedDiscountSum | Заказы/Сумма всех скидок для невыкупленных штук | number ||
    ||
    UNREDEEMED_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    unredeemedPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех невыкупленных штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Электронный документооборот/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Электронный документооборот/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Электронный документооборот/Номер УКД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    ||
    ADJUSTMENT_INVOICE_DATE
    |
    adjustmentInvoiceDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата корректировочного счёта-фактуры
    |
    string
    ||
    ||
    ADJUSTMENT_INVOICE_NUMBER
    |
    adjustmentInvoiceNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер корректировочного счёта фактуры
    |
    string
    ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Стоимость выкупленного товара | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Документы/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Документы/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Документы/Номер УКД | string ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Документы/Стоимость выкупленного товара | string ||
    |#

    {% endcut %}

    {% cut "Лист **Возвращенные товары** (файл **returned**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название товара | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    || DELIVERED_COUNT | deliveredCount | Заказы/Количество доставленных, шт. | integer ||
    || RETURNED_COUNT | returnedCount | Заказы/Возвращено, шт. | integer ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    ||
    RETURN_WAREHOUSE_OR_SC_ACCEPT_DATE
    |
    returnWarehouseOrScAcceptDate
    |
    Заказы/Дата приёма возврата складом или сортировочным центром
    |
    string
    ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    RETURN_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    returnPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех возвращённых штук с НДС без учёта скидок
    |
    number
    ||
    || RETURN_DISCOUNT_SUM | returnDiscountSum | Заказы/Сумма всех скидок для возвращённых штук | number ||
    ||
    RETURN_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    returnPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех возвращённых штук с НДС с учётом всех скидок
    |
    number
    ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Документы/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Документы/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Документы/Номер УКД | string ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Документы/Стоимость выкупленного товара | number ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Электронный документооборот/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Электронный документооборот/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Электронный документооборот/Номер УКД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    ||
    ADJUSTMENT_INVOICE_DATE
    |
    adjustmentInvoiceDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата корректировочного счёта-фактуры
    |
    string
    ||
    ||
    ADJUSTMENT_INVOICE_NUMBER
    |
    adjustmentInvoiceNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер корректировочного счёта фактуры
    |
    string
    ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Стоимость выкупленного товара | number ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    |#

    {% endcut %}

    {% cut "Лист **Товары, утраченные в доставке** (файл **lost_items**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название товара | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    transferredToDeliveryPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех переданных в доставку штук с НДС без учёта скидок
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_DISCOUNT_SUM
    |
    transferredToDeliveryDiscountSum
    |
    Заказы/Сумма всех скидок для переданных в доставку штук
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    transferredToDeliveryPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех переданных в доставку штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || COMPENSATION_DATE | compensationDate | Компенсации/Дата автокомпенсации  | string ||
    || COMPENSATION_AMOUNT | compensationAmount | Компенсации/Сумма автокомпенсации | number ||
    ||
    LOST_RETURN_RECEIVED_DATE
    |
    lostReturnReceivedDate
    |
    Компенсации/Дата приёма заказа складом Маркета или выдачи продавцу с СЦ 
    |
    string
    ||
    || DECOMPENSATION_DATE | decompensationDate | Компенсации/Дата декомпенсации  | string ||
    || DECOMPENSATION_AMOUNT | decompensationAmount | Компенсации/Сумма декомпенсации | number ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Электронный документооборот/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Электронный документооборот/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Электронный документооборот/Номер УКД | string ||
    ||
    ADJUSTMENT_INVOICE_DATE
    |
    adjustmentInvoiceDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата корректировочного счёта-фактуры
    |
    string
    ||
    ||
    ADJUSTMENT_INVOICE_NUMBER
    |
    adjustmentInvoiceNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер корректировочного счёта фактуры
    |
    string
    ||
    |#

    {% endcut %}
    <!-- endsource: ru/_auto/reports/united/statistics/generator/united_statistics_v2.md -->
  
  - DBS
  
    <!-- source: ru/_auto/reports/united/statistics/generator/united_statistics_v2_dbs.md -->
    Пояснение к колонкам отчета:

    {% cut "Лист **Передано в доставку** (файл **transferred_to_delivery**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    transferredToDeliveryPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех переданных в доставку штук с НДС без учёта скидок
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_DISCOUNT_SUM
    |
    transferredToDeliveryDiscountSum
    |
    Заказы/Сумма всех скидок для переданных в доставку штук
    |
    number
    ||
    ||
    TRANSFERRED_TO_DELIVERY_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    transferredToDeliveryPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех переданных в доставку штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Документы/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Документы/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Документы/Номер УКД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    |#

    {% endcut %}

    {% cut "Лист **Доставлено** (файл **delivered**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || DELIVERED_COUNT | deliveredCount | Заказы/Доставлено, шт. | integer ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    DELIVERED_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    deliveredPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех доставленных штук с НДС без учёта скидок
    |
    number
    ||
    || DELIVERED_DISCOUNT_SUM | deliveredDiscountSum | Заказы/Сумма всех скидок для доставленных штук | number ||
    ||
    DELIVERED_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    deliveredPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех доставленных штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    |#

    {% endcut %}

    {% cut "Лист **Невыкуплено** (файл **unredeemed**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    ||
    TRANSFERRED_TO_DELIVERY_COUNT
    |
    transferredToDeliveryCount
    |
    Заказы/Количество переданных в доставку, шт.
    |
    integer
    ||
    || UNREDEEMED_COUNT | unredeemedCount | Заказы/Невыкуплено, шт. | integer ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    ||
    UNREDEEMED_WAREHOUSE_OR_SC_ACCEPT_DATE
    |
    unredeemedWarehouseOrScAcceptDate
    |
    Заказы/Дата приёма невыкупа складом или сортировочным центром
    |
    string
    ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    UNREDEEMED_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    unredeemedPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех невыкупленных штук с НДС без учёта скидок
    |
    number
    ||
    || UNREDEEMED_DISCOUNT_SUM | unredeemedDiscountSum | Заказы/Сумма всех скидок для невыкупленных штук | number ||
    ||
    UNREDEEMED_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    unredeemedPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех невыкупленных штук с НДС с учётом всех скидок
    |
    number
    ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Электронный документооборот/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Электронный документооборот/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Электронный документооборот/Номер УКД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    ||
    ADJUSTMENT_INVOICE_DATE
    |
    adjustmentInvoiceDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата корректировочного счёта-фактуры
    |
    string
    ||
    ||
    ADJUSTMENT_INVOICE_NUMBER
    |
    adjustmentInvoiceNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер корректировочного счёта фактуры
    |
    string
    ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Стоимость выкупленного товара | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Документы/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Документы/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Документы/Номер УКД | string ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Документы/Стоимость выкупленного товара | string ||
    |#

    {% endcut %}

    {% cut "Лист **Возвращено** (файл **returned**)" %}

    #|
    || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
    || ORDER_ID | orderId | Заказы/Номер заказа | integer ||
    || YOUR_ORDER_ID | yourOrderId | Заказы/Ваш номер заказа | string ||
    || ORDER_TYPE | orderType | Заказы/Тип заказа | string ||
    || OFFER_NAME | offerName | Заказы/Название | string ||
    || YOUR_SKU | yourSku | Заказы/Ваш SKU | string ||
    || SHOP_SKU | shopSku | Заказы/${mbi.reports.statistics:mbi.reports.statistics.column.shop.sku} | string ||
    || DELIVERED_COUNT | deliveredCount | Заказы/Количество доставленных, шт. | integer ||
    || RETURNED_COUNT | returnedCount | Заказы/Возвращено, шт. | integer ||
    || ORDER_CREATION_DATE | orderCreationDate | Заказы/Дата оформления заказа | string ||
    || TRANSFERRED_TO_DELIVERY_DATE | transferredToDeliveryDate | Заказы/Дата передачи товара в доставку | string ||
    || DELIVERY_DATE | deliveryDate | Заказы/Дата доставки товара | string ||
    ||
    RETURN_WAREHOUSE_OR_SC_ACCEPT_DATE
    |
    returnWarehouseOrScAcceptDate
    |
    Заказы/Дата выдачи возврата вам
    |
    string
    ||
    || PAYMENT_TYPE | paymentType | Заказы/Способ оплаты | string ||
    || VAT | vat | Заказы/Ставка НДС | string ||
    ||
    PRICE_WITH_VAT_AND_NO_DISCOUNT
    |
    priceWithVatAndNoDiscount
    |
    Заказы/Цена c НДС без учёта скидок за шт.
    |
    number
    ||
    ||
    SHOP_MARKETPLACE_DISCOUNT
    |
    shopMarketplaceDiscount
    |
    Заказы/Ваша скидка по акции маркетплейса на 1 шт.
    |
    number
    ||
    || SPASIBO_DISCOUNT | spasiboDiscount | Заказы/Ваша скидка по бонусам СберСпасибо (за шт.) на 1 шт. | number ||
    || YANDEX_PLUS_DISCOUNT | yandexPlusDiscount | Заказы/Ваша скидка по баллам Яндекс.Плюса на 1 шт. | number ||
    ||
    PRICE_WITH_VAT_AND_ALL_DISCOUNTS
    |
    priceWithVatAndAllDiscounts
    |
    Заказы/Цена с НДС с учётом всех скидок за шт.
    |
    number
    ||
    ||
    RETURN_PRICE_SUM_WITH_VAT_AND_NO_DISCOUNTS
    |
    returnPriceSumWithVatAndNoDiscounts
    |
    Заказы/Стоимость всех возвращённых штук с НДС без учёта скидок
    |
    number
    ||
    || RETURN_DISCOUNT_SUM | returnDiscountSum | Заказы/Сумма всех скидок для возвращённых штук | number ||
    ||
    RETURN_PRICE_SUM_WITH_VAT_AND_DISCOUNTS
    |
    returnPriceSumWithVatAndDiscounts
    |
    Заказы/Стоимость всех возвращённых штук с НДС с учётом всех скидок
    |
    number
    ||
    || ORGANIZATION | organization | Продажи бизнесу/Информация о покупателе/Наименование организации | string ||
    || INN | inn | Продажи бизнесу/Информация о покупателе/ИНН | string ||
    || KPP | kpp | Продажи бизнесу/Информация о покупателе/КПП | string ||
    ||
    ORGANIZATION_JUR_ADDRESS
    |
    organizationJurAddress
    |
    Продажи бизнесу/Информация о покупателе/Юридический адрес
    |
    string
    ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Документы/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Документы/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Документы/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Документы/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Документы/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Документы/Номер УКД | string ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Документы/Стоимость выкупленного товара | number ||
    || UPD_STATUS | updStatus | Продажи бизнесу/Электронный документооборот/Статус УПД | string ||
    || UPD_DATE | updDate | Продажи бизнесу/Электронный документооборот/Дата УПД | string ||
    || UPD_NUMBER | updNumber | Продажи бизнесу/Электронный документооборот/Номер УПД | string ||
    || UKD_STATUS | ukdStatus | Продажи бизнесу/Электронный документооборот/Статус УКД | string ||
    || UKD_DATE | ukdDate | Продажи бизнесу/Электронный документооборот/Дата УКД | string ||
    || UKD_NUMBER | ukdNumber | Продажи бизнесу/Электронный документооборот/Номер УКД | string ||
    ||
    CONSIGNMENT_NOTE_DATE
    |
    consignmentNoteDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата товарной накладной
    |
    string
    ||
    ||
    CONSIGNMENT_NOTE_NUMBER
    |
    consignmentNoteNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер товарной накладной
    |
    string
    ||
    || INVOICE_DATE | invoiceDate | Продажи бизнесу/Бумажный документооборот/Дата счёта-фактуры | string ||
    || INVOICE_NUMBER | invoiceNumber | Продажи бизнесу/Бумажный документооборот/Номер счёта фактуры | string ||
    ||
    ADJUSTMENT_INVOICE_DATE
    |
    adjustmentInvoiceDate
    |
    Продажи бизнесу/Бумажный документооборот/Дата корректировочного счёта-фактуры
    |
    string
    ||
    ||
    ADJUSTMENT_INVOICE_NUMBER
    |
    adjustmentInvoiceNumber
    |
    Продажи бизнесу/Бумажный документооборот/Номер корректировочного счёта фактуры
    |
    string
    ||
    || REDEEMED_PRICE | redeemedPrice | Продажи бизнесу/Стоимость выкупленного товара | number ||
    ||
    RNPT
    |
    rnpt
    |
    Заказы/Регистрационный номер таможенной декларации или Регистрационный номер партии товара, подлежащего прослеживаемости (РНПТ)
    |
    string
    ||
    || RECEIPT_ID | receiptId | Заказы/Номер чека | string ||
    || RECEIPT_LINK | receiptLink | Заказы/Ссылка на чек | string ||
    || RECEIPT_DATETIME | receiptDatetime | Заказы/Дата печати чека | string ||
    |#

    {% endcut %}
    <!-- endsource: ru/_auto/reports/united/statistics/generator/united_statistics_v2_dbs.md -->
  
  {% endlist %}
  
  <!-- source: ru/_auto/method_limits/generateGoodsRealizationReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateGoodsRealizationReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/goods-realization/generate
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
    "campaignId": 1,
    "year": 2025,
    "month": 12
  }
  ```
  
  {% endcut %}
  
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
  
  _month_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Month](#entity-Month)
  
  Номер месяца.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `12`
  
  _Example:_{.json-schema-reset .json-schema-example} `12`
  {.table-cell}
  ||
  ||
  
  _year_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Year](#entity-Year)
  
  Год.
  
  _Example:_{.json-schema-reset .json-schema-example} `2025`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  headers: []
  body: |-
    {
      "campaignId": 1,
      "year": 2025,
      "month": 12
    }
  schema:
    description: >
      Данные, необходимые для генерации отчета: идентификатор кампании и период,
      за который нужен отчет.
    type: object
    required:
      - campaignId
      - year
      - month
    properties:
      campaignId:
        description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
        type: integer
        format: int64
        minimum: 1
      year:
        description: Год.
        type: integer
        format: int32
        example: 2025
      month:
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
  path: v2/reports/goods-realization/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateGoodsRealizationReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
