---
title: Отчет по заказам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md"
fetched_at: "2026-09-15T02:22:30Z"
content_sha: 172713de3f3a7f8e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/reports/generateUnitedOrdersReport.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/reports/generateUnitedOrdersReport.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md
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

<!-- source: ru/api/reports/generateUnitedOrdersReport.md -->
<div class="openapi">

# Отчет по заказам

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateUnitedOrdersReport.md -->
  **Метод доступен для моделей: [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md), [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * promotion:read-only — [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateUnitedOrdersReport.md -->
  
  Запускает генерацию отчета по заказам за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/accounting/transactions#get-report)
  
  Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md).
  
  <!-- source: ru/_auto/reports/united/orders/generator/united_orders.md -->
  Пояснение к колонкам отчета:

  {% cut "Лист **Транзакции по заказам и товарам** (файл **orders_and_offers_transactions**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказах/Номер заказа | integer ||
  || PARTNER_ORDER_ID | partnerOrderId | Информация о заказах/Ваш номер заказа | string ||
  || CREATION_DATE | creationDate | Информация о заказах/Дата оформления | string ||
  || ORDER_TYPE | orderType | Информация о заказах/Тип заказа | string ||
  || SHOP_SKU | shopSku | Информация о заказах/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказах/Название товара | string ||
  || PARTNER_PRICE_FOR_DELIVERY | partnerPriceForDelivery | Информация о заказах/Ваша цена (за шт.) | number ||
  || BILLING_PRICE | billingPrice | Информация о заказах/Цена продажи (за шт.) | number ||
  ||
  COFINANCE_TRESHOLD
  |
  cofinanceTreshold
  |
  Информация о заказах/Ваш порог снижения цены для участия в софинансировании на момент оформления заказа (за шт.)
  |
  number
  ||
  ||
  COFINANCE_VALUE
  |
  cofinanceValue
  |
  Информация о заказах/Ваша скидка, если товар участвовал в софинансировании (за шт.)
  |
  number
  ||
  ||
  COFINANCE_SUBSIDY
  |
  cofinanceSubsidy
  |
  Информация о заказах/Скидка Маркета, если товар участвовал в софинансировании
  |
  number
  ||
  || MARKETPLACE_SUBSIDY | marketplaceSubsidy | Информация о заказах/Другие скидки Маркета (за шт.) | number ||
  || SPASIBO | spasibo | Информация о заказах/Оплата бонусами СберСпасибо (за шт.) | number ||
  || YANDEX_PLUS | yandexPlus | Информация о заказах/Оплата баллами Яндекс Плюса (за шт.) | number ||
  || TRANSFERRED_FOR_DELIVERY | transferredForDelivery | Информация о заказах/Передано в доставку | integer ||
  || DELIVERED_OR_RETURNED | deliveredOrReturned | Информация о заказах/Доставлено или возвращено | integer ||
  || DELIVERY_DATE | deliveryDate | Информация о заказах/Дата доставки заказа | string ||
  || OFFER_STATUS | offerStatus | Информация о заказах/Статус товара | string ||
  || STATUS_CHANGED | statusChanged | Информация о заказах/Статус изменен | string ||
  || PAYMENT_TYPE | paymentType | Информация о заказах/Способ оплаты | string ||
  || SHIPMENT_WAREHOUSE | shipmentWarehouse | Информация о заказах/Склад отгрузки | string ||
  || SHIPMENT_DATE | shipmentDate | Информация о заказах/Дата отгрузки | string ||
  || DELIVERY_REGION | deliveryRegion | Информация о заказах/Регион доставки | string ||
  || BUYER_PAYMENT_AMOUNT | buyerPaymentAmount | Платёж покупателя/Сумма платежа | number ||
  ||
  BUYER_PAYMENT_BANK_ORDER_ID
  |
  buyerPaymentBankOrderId
  |
  Платёж покупателя/Номер платежного поручения
  |
  string
  ||
  ||
  BUYER_PAYMENT_BANK_ORDER_DATE
  |
  buyerPaymentBankOrderDate
  |
  Платёж покупателя/Дата платежного поручения
  |
  string
  ||
  || BUYER_PAYMENT_ID | buyerPaymentId | Платёж покупателя/Идентификатор платежа | string ||
  || BUYER_PAYMENT_HANDLING_TIME | buyerPaymentHandlingTime | Платёж покупателя/Дата реестра платежей | string ||
  ||
  MARKETPLACE_DISCOUNT_PAYMENT_AMOUNT
  |
  marketplaceDiscountPaymentAmount
  |
  Платёж за скидку Маркета/Сумма платежа
  |
  number
  ||
  ||
  MARKETPLACE_DISCOUNT_PAYMENT_BANK_ORDER_ID
  |
  marketplaceDiscountPaymentBankOrderId
  |
  Платёж за скидку Маркета/Номер платежного поручения
  |
  string
  ||
  ||
  MARKETPLACE_DISCOUNT_PAYMENT_BANK_ORDER_DATE
  |
  marketplaceDiscountPaymentBankOrderDate
  |
  Платёж за скидку Маркета/Дата платежного поручения
  |
  string
  ||
  ||
  MARKETPLACE_DISCOUNT_PAYMENT_ID
  |
  marketplaceDiscountPaymentId
  |
  Платёж за скидку Маркета/Идентификатор платежа
  |
  string
  ||
  ||
  MARKETPLACE_DISCOUNT_PAYMENT_HANDLING_TIME
  |
  marketplaceDiscountPaymentHandlingTime
  |
  Платёж за скидку Маркета/Дата реестра платежей
  |
  string
  ||
  ||
  SPASIBO_PAYMENT_AMOUNT
  |
  spasiboPaymentAmount
  |
  Платёж за скидку по бонусам СберСпасибо/Сумма платежа
  |
  number
  ||
  ||
  SPASIBO_PAYMENT_BANK_ORDER_ID
  |
  spasiboPaymentBankOrderId
  |
  Платёж за скидку по бонусам СберСпасибо/Номер платежного поручения
  |
  string
  ||
  ||
  SPASIBO_PAYMENT_BANK_ORDER_DATE
  |
  spasiboPaymentBankOrderDate
  |
  Платёж за скидку по бонусам СберСпасибо/Дата платежного поручения
  |
  string
  ||
  ||
  SPASIBO_PAYMENT_ID
  |
  spasiboPaymentId
  |
  Платёж за скидку по бонусам СберСпасибо/Идентификатор платежа
  |
  string
  ||
  ||
  SPASIBO_PAYMENT_HANDLING_TIME
  |
  spasiboPaymentHandlingTime
  |
  Платёж за скидку по бонусам СберСпасибо/Дата реестра платежей
  |
  string
  ||
  || YANDEX_PLUS_PAYMENT_AMOUNT | yandexPlusPaymentAmount | Платёж за скидку Яндекс Плюс/Сумма платежа | number ||
  ||
  YANDEX_PLUS_PAYMENT_BANK_ORDER_ID
  |
  yandexPlusPaymentBankOrderId
  |
  Платёж за скидку Яндекс Плюс/Номер платежного поручения
  |
  string
  ||
  ||
  YANDEX_PLUS_PAYMENT_BANK_ORDER_DATE
  |
  yandexPlusPaymentBankOrderDate
  |
  Платёж за скидку Яндекс Плюс/Дата платежного поручения
  |
  string
  ||
  || YANDEX_PLUS_PAYMENT_ID | yandexPlusPaymentId | Платёж за скидку Яндекс Плюс/Идентификатор платежа | string ||
  ||
  YANDEX_PLUS_PAYMENT_HANDLING_TIME
  |
  yandexPlusPaymentHandlingTime
  |
  Платёж за скидку Яндекс Плюс/Дата реестра платежей
  |
  string
  ||
  || REFUND_BUYER_PAYMENT_AMOUNT | refundBuyerPaymentAmount | Возврат платежа покупателя/Сумма возврата | number ||
  ||
  REFUND_BUYER_PAYMENT_BANK_ORDER_ID
  |
  refundBuyerPaymentBankOrderId
  |
  Возврат платежа покупателя/Номер платежного поручения
  |
  string
  ||
  ||
  REFUND_BUYER_PAYMENT_BANK_ORDER_DATE
  |
  refundBuyerPaymentBankOrderDate
  |
  Возврат платежа покупателя/Дата платежного поручения
  |
  string
  ||
  || REFUND_BUYER_PAYMENT_ID | refundBuyerPaymentId | Возврат платежа покупателя/Идентификатор платежа | string ||
  ||
  REFUND_BUYER_PAYMENT_HANDLING_TIME
  |
  refundBuyerPaymentHandlingTime
  |
  Возврат платежа покупателя/Дата реестра платежей
  |
  string
  ||
  ||
  REFUND_MARKETPLACE_DISCOUNT_PAYMENT_AMOUNT
  |
  refundMarketplaceDiscountPaymentAmount
  |
  Возврат платежа за скидку Маркета/Сумма возврата
  |
  number
  ||
  ||
  REFUND_MARKETPLACE_DISCOUNT_PAYMENT_BANK_ORDER_ID
  |
  refundMarketplaceDiscountPaymentBankOrderId
  |
  Возврат платежа за скидку Маркета/Номер платежного поручения
  |
  string
  ||
  ||
  REFUND_MARKETPLACE_DISCOUNT_PAYMENT_BANK_ORDER_DATE
  |
  refundMarketplaceDiscountPaymentBankOrderDate
  |
  Возврат платежа за скидку Маркета/Дата платежного поручения
  |
  string
  ||
  ||
  REFUND_MARKETPLACE_DISCOUNT_PAYMENT_ID
  |
  refundMarketplaceDiscountPaymentId
  |
  Возврат платежа за скидку Маркета/Идентификатор платежа
  |
  string
  ||
  ||
  REFUND_MARKETPLACE_DISCOUNT_PAYMENT_HANDLING_TIME
  |
  refundMarketplaceDiscountPaymentHandlingTime
  |
  Возврат платежа за скидку Маркета/Дата реестра платежей
  |
  string
  ||
  ||
  REFUND_SPASIBO_PAYMENT_AMOUNT
  |
  refundSpasiboPaymentAmount
  |
  Возврат платежа за скидку по бонусам СберСпасибо/Сумма возврата
  |
  number
  ||
  ||
  REFUND_SPASIBO_PAYMENT_BANK_ORDER_ID
  |
  refundSpasiboPaymentBankOrderId
  |
  Возврат платежа за скидку по бонусам СберСпасибо/Номер платежного поручения
  |
  string
  ||
  ||
  REFUND_SPASIBO_PAYMENT_BANK_ORDER_DATE
  |
  refundSpasiboPaymentBankOrderDate
  |
  Возврат платежа за скидку по бонусам СберСпасибо/Дата платежного поручения
  |
  string
  ||
  ||
  REFUND_SPASIBO_PAYMENT_ID
  |
  refundSpasiboPaymentId
  |
  Возврат платежа за скидку по бонусам СберСпасибо/Идентификатор платежа
  |
  string
  ||
  ||
  REFUND_SPASIBO_PAYMENT_HANDLING_TIME
  |
  refundSpasiboPaymentHandlingTime
  |
  Возврат платежа за скидку по бонусам СберСпасибо/Дата реестра платежей
  |
  string
  ||
  ||
  REFUND_YANDEX_PLUS_PAYMENT_AMOUNT
  |
  refundYandexPlusPaymentAmount
  |
  Возврат платежа за скидку Яндекс Плюс/Сумма возврата
  |
  number
  ||
  ||
  REFUND_YANDEX_PLUS_PAYMENT_BANK_ORDER_ID
  |
  refundYandexPlusPaymentBankOrderId
  |
  Возврат платежа за скидку Яндекс Плюс/Номер платежного поручения
  |
  string
  ||
  ||
  REFUND_YANDEX_PLUS_PAYMENT_BANK_ORDER_DATE
  |
  refundYandexPlusPaymentBankOrderDate
  |
  Возврат платежа за скидку Яндекс Плюс/Дата платежного поручения
  |
  string
  ||
  ||
  REFUND_YANDEX_PLUS_PAYMENT_ID
  |
  refundYandexPlusPaymentId
  |
  Возврат платежа за скидку Яндекс Плюс/Идентификатор платежа
  |
  string
  ||
  ||
  REFUND_YANDEX_PLUS_PAYMENT_HANDLING_TIME
  |
  refundYandexPlusPaymentHandlingTime
  |
  Возврат платежа за скидку Яндекс Плюс/Дата реестра платежей
  |
  string
  ||
  ||
  DEFECT_REFUND_PAYMENT_AMOUNT
  |
  defectRefundPaymentAmount
  |
  Выплата расходов покупателю при возврате товара ненадлежащего качества/Удержанная сумма
  |
  number
  ||
  ||
  DEFECT_REFUND_PAYMENT_BANK_ORDER_ID
  |
  defectRefundPaymentBankOrderId
  |
  Выплата расходов покупателю при возврате товара ненадлежащего качества/Номер платежного поручения
  |
  string
  ||
  ||
  DEFECT_REFUND_PAYMENT_BANK_ORDER_DATE
  |
  defectRefundPaymentBankOrderDate
  |
  Выплата расходов покупателю при возврате товара ненадлежащего качества/Дата платежного поручения
  |
  string
  ||
  ||
  DEFECT_REFUND_PAYMENT_ID
  |
  defectRefundPaymentId
  |
  Выплата расходов покупателю при возврате товара ненадлежащего качества/Идентификатор платежа
  |
  string
  ||
  ||
  DEFECT_REFUND_PAYMENT_HANDLING_TIME
  |
  defectRefundPaymentHandlingTime
  |
  Выплата расходов покупателю при возврате товара ненадлежащего качества/Дата реестра платежей
  |
  string
  ||
  || NETTING_AMOUNT | nettingAmount | Баллы за скидки Маркета и скидки Яндекс Плюс/Сумма баллов | number ||
  ||
  NETTING_TRANSACTION_STATUS
  |
  nettingTransactionStatus
  |
  Баллы за скидки Маркета и скидки Яндекс Плюс/Статус (справочно)
  |
  string
  ||
  |#

  {% endcut %}

  {% cut "Лист **Услуги и маржа по заказам** (файл **services_and_orders_margin**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказах/Номер заказа | integer ||
  || PARTNER_ORDER_ID | partnerOrderId | Информация о заказах/Ваш номер заказа | string ||
  || ORDER_STATUS | orderStatus | Информация о заказах/Статус заказа | string ||
  || CREATION_DATE | creationDate | Информация о заказах/Дата оформления | string ||
  || ORDER_TYPE | orderType | Информация о заказах/Тип заказа | string ||
  ||
  SUMMARY_COMMISSION
  |
  summaryCommission
  |
  Информация по денежным средствам/Все услуги Маркета за заказы
  |
  number
  ||
  ||
  SUM_BILLING_PRICE_OF_ITEMS
  |
  sumBillingPriceOfItems
  |
  Информация по денежным средствам/Цена продажи (за шт.)
  |
  number
  ||
  ||
  INCOME_WITHOUT_SERVICES
  |
  incomeWithoutServices
  |
  Информация по денежным средствам/Доход за вычетом услуг Маркета
  |
  number
  ||
  ||
  BUYER_PAYMENT
  |
  buyerPayment
  |
  Информация по денежным средствам/Платёж покупателя, не включает скидки Маркета и баллы Плюса
  |
  number
  ||
  ||
  BUYER_PAYMENT_STATUS
  |
  buyerPaymentStatus
  |
  Информация по денежным средствам/Статус платежа покупателя
  |
  string
  ||
  || BANK_ORDER_ID | bankOrderId | Информация по денежным средствам/Номер платежного поручения | string ||
  || SALE_COMMISSION | saleCommission | Информация по услугам/Размещение товаров на витрине | number ||
  || WAREHOUSE_PROCESSING | warehouseProcessing | Информация по услугам/Складская обработка | number ||
  || LOYALTY_PROGRAM | loyaltyProgram | Информация по услугам/Программа лояльности и отзывы | number ||
  || BOOST | boost | Информация по услугам/Буст продаж | number ||
  || INSTALLMENT | installment | Информация по услугам/Рассрочка | number ||
  || BUYER_DELIVERY | buyerDelivery | Информация по услугам/Доставка покупателю | number ||
  || CROSSREGIONAL_DELIVERY | crossregionalDelivery | Информация по услугам/Доставка (средняя миля) | number ||
  || BUYER_EXPRESS_DELIVERY | buyerExpressDelivery | Информация по услугам/Экспресс-доставка покупателю | number ||
  || CROSSBORDER_DELIVERY | crossborderDelivery | Информация по услугам/Доставка из-за рубежа | number ||
  || BUYER_PAYMENT_ACCEPT | buyerPaymentAccept | Информация по услугам/Приём платежа покупателя | number ||
  || BUYER_PAYMENT_TRANSFER | buyerPaymentTransfer | Информация по услугам/Перевод платежа покупателя | number ||
  || ORDER_INTAKE | orderIntake | Информация по услугам/Организация забора заказов | number ||
  || ORDER_PROCESSING | orderProcessing | Информация по услугам/Обработка заказов в СЦ или ПВЗ | number ||
  || RESUPPLY_HANDLING | resupplyHandling | Информация по услугам/Хранение невыкупов и возвратов | number ||
  || RETURN_RESUPPLY | returnResupply | Информация по услугам/Обработка заказов на складе | number ||
  || EXPROPRIATION_RESALE | expropriationResale | Информация по услугам/Вознаграждение за продажу товара | number ||
  |#

  {% endcut %}

  {% cut "Лист **Заказы с умн.ценообразованием** (файл **services_with_decoupling**)" %}

  #|
  || **Название колонки в CSV** | **Название колонки в JSON** | **Название колонки в XLSX** | **Тип значения** ||
  || BUSINESS_ID | businessId | Информация о бизнесе/ID бизнес-аккаунта | integer ||
  || MODEL | model | Информация о бизнесе/Модели работы | string ||
  || PARTNER_ID | partnerId | Информация о бизнесе/ID магазинов | integer ||
  || SHOP_NAME | shopName | Информация о бизнесе/Названия магазинов | string ||
  || INN | inn | Информация о бизнесе/ИНН | string ||
  || PLACEMENT_CONTRACT | placementContract | Информация о бизнесе/Номера договоров на размещение | string ||
  || PROMOTION_CONTRACT | promotionContract | Информация о бизнесе/Номера договоров на продвижение | string ||
  || ORDER_ID | orderId | Информация о заказах/Номер заказа | integer ||
  || SHOP_ORDER_ID | shopOrderId | Информация о заказах/Ваш номер заказа | string ||
  || ORDER_STATUS | orderStatus | Информация о заказах/Статус заказа | string ||
  || CREATION_DATE | creationDate | Информация о заказах/Дата оформления | string ||
  || ORDER_TYPE | orderType | Информация о заказах/Тип заказа | string ||
  || SHOP_SKU | shopSku | Информация о заказах/Ваш SKU | string ||
  || OFFER_NAME | offerName | Информация о заказах/Название товара | string ||
  || COUNT | count | Информация о заказах/Количество | integer ||
  || SHOP_PRICE | shopPrice | Информация по денежным средствам/Ваша цена (за шт.) | number ||
  || SELLING_PRICE | sellingPrice | Информация по денежным средствам/Цена продажи (за шт.) | number ||
  ||
  BUYER_PAYMENT
  |
  buyerPayment
  |
  Информация по денежным средствам/Платёж покупателя, не включает скидки Маркета и баллы Плюса
  |
  number
  ||
  ||
  EXTRA_INCOME
  |
  extraIncome
  |
  Информация по денежным средствам/Разница между вашей ценой и ценой продажи
  |
  number
  ||
  ||
  SUMMARY_COMMISSION
  |
  summaryCommission
  |
  Информация по денежным средствам/Все услуги Маркета за заказы
  |
  number
  ||
  ||
  INCOME_WITHOUT_SERVICES
  |
  incomeWithoutServices
  |
  Информация по денежным средствам/Доход за вычетом услуг Маркета
  |
  number
  ||
  ||
  EXTRA_DECOUPLING_MARGIN
  |
  extraDecouplingMargin
  |
  Информация по денежным средствам/Доп.выручка от умного предложения
  |
  number
  ||
  ||
  NET_DECOUPLING_GAIN
  |
  netDecouplingGain
  |
  Информация по денежным средствам/Доп. доход от умного предложения
  |
  number
  ||
  || SALE_COMMISSION | saleCommission | Информация по услугам/Размещение товаров на витрине | number ||
  ||
  EXTRA_DECOUPLING_SALE_COMMISSION
  |
  extraDecouplingSaleCommission
  |
  Информация по услугам/Умное предложение (доп.тариф на размещение)
  |
  number
  ||
  || WAREHOUSE_HANDLING | warehouseHandling | Информация по услугам/Складская обработка | number ||
  || LOYALTY_PROGRAM | loyaltyProgram | Информация по услугам/Программа лояльности и отзывы | number ||
  || BOOST | boost | Информация по услугам/Буст продаж | number ||
  || INSTALLMENT | installment | Информация по услугам/Рассрочка | number ||
  || DELIVERY | delivery | Информация по услугам/Доставка покупателю | number ||
  || EXPRESS_DELIVERY | expressDelivery | Информация по услугам/Экспресс-доставка покупателю | number ||
  || PAYMENT_ACCEPTING | paymentAccepting | Информация по услугам/Приём платежа покупателя | number ||
  || PAYMENT_TRANSFER | paymentTransfer | Информация по услугам/Перевод платежа покупателя | number ||
  || ORDER_PROCESSING | orderProcessing | Информация по услугам/Обработка заказов в СЦ или ПВЗ | number ||
  || RESUPPLY_STORAGE | resupplyStorage | Информация по услугам/Хранение невыкупов и возвратов | number ||
  || RESUPPLY_RETURN | resupplyReturn | Информация по услугам/Обработка заказов на складе | number ||
  || ORDER_INTAKE | orderIntake | Информация по услугам/Организация забора заказов | number ||
  |#

  {% endcut %}
  <!-- endsource: ru/_auto/reports/united/orders/generator/united_orders.md -->
  
  <!-- source: ru/_includes/common/report-data-period-unchanged.md -->
  {% note warning "Ограничения по тарифному плану" %}

  Период выгрузки данных и количество одновременно генерирующихся отчетов зависят от вашего тарифного плана:
  * **Без подписки или тариф «Лайт»** — доступны данные за последние 90 дней, одновременно может генерироваться 1 отчет
  * **Тариф «Медиум»** — одновременно может генерироваться до 10 отчетов

  Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).

  {% endnote %}
  <!-- endsource: ru/_includes/common/report-data-period-unchanged.md -->
  
  <!-- source: ru/_auto/method_limits/generateUnitedOrdersReport.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 1 запрос в 2 минуты<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 1 запрос в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateUnitedOrdersReport.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/reports/united-orders/generate
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
    "dateFrom": "2025-08-22",
    "dateTo": "2025-01-01",
    "campaignIds": [
      1
    ],
    "promoId": "example"
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
  **Type**: string&lt;date&gt;
  
  Конец периода, включительно. Максимальный период — 1 год.
  
  Формат даты: `ГГГГ-ММ-ДД`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2025-01-01`
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
  
  _promoId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор акции, товары из которой нужны в отчете.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
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
          /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportFormatType
    - description: Язык отчета или документа.
      name: language
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/reports/schemas.yaml#/ReportLanguageType
  headers: []
  body: |-
    {
      "businessId": 1,
      "dateFrom": "2025-08-22",
      "dateTo": "2025-01-01",
      "campaignIds": [
        1
      ],
      "promoId": "example"
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
        description: |
          Конец периода, включительно. Максимальный период — 1 год.
  
          Формат даты: `ГГГГ-ММ-ДД`.
        format: date
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
      promoId:
        description: Идентификатор акции, товары из которой нужны в отчете.
        type: string
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
  path: v2/reports/united-orders/generate
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/reports/generateUnitedOrdersReport.md -->


[*Deprecated]: No longer supported, please use an alternative and newer version.
