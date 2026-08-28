---
title: Список транзакций
api: ozon-seller
method: POST
path: /v3/finance/transaction/list
operation_id: FinanceAPI_FinanceTransactionListV3
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f0be76cf5a2811c2
---

# Список транзакций

`POST /v3/finance/transaction/list`

Метод устаревает и будет отключён 8 сентября 2026 года. Переключитесь на [/v1/finance/accrual/postings](#operation/GetFinanceAccrualPostings), [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes), [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay).

Используйте метод с последовательной отправкой запросов.

Данные могут не соответствовать информации в личном кабинете.

Возвращает подробную информацию по всем начислениям. Максимальный период, за который можно получить информацию в одном запросе — 1 месяц.

Если в запросе не указывать `posting_number`, то в ответе будут все отправления за указанный период или отправления определённого типа.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр.
- `page` — integer<int64> **обязательный**. Номер страницы, возвращаемой в запросе.
- `page_size` — integer<int64> **обязательный**. Количество элементов на странице.

## Ответы

**200** — Список транзакций

- `result` — object. Результаты запроса.
  - `operations` — array[object]. Информация об операциях.
    - `accruals_for_sale` — number<double>. Стоимость товаров с учётом скидок продавца.
    - `amount` — number<double>. Итоговая сумма операции.
    - `delivery_charge` — number<double>. Стоимость доставки для начислений по тарифам, которые действовали до 1 февраля 2021 года, а также начислений для крупногабаритных товаров.
    - `items` — array[object]. Информация о товаре.
      - `name` — string. Название товара.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `operation_date` — string. Дата операции.
    - `operation_id` — integer<int64>. Идентификатор операции.
    - `operation_type` — string. Тип операции.
    - `operation_type_name` — string. Название типа операции.
    - `posting` — object. Информация об отправлении.
      - `delivery_schema` — string. Схема доставки: - `FBO` — доставка со склада Ozon, - `FBS` — доставка со своего склада, - `CROSSBORDER` — доставка из-за рубежа, - `RFBS` — доставка по выбору продавца, - `FBP` — доставка с партнёрских складов Ozon, - `FBOECONOMY` — доставка эконом-товаров со склада Ozon, - `FBSECONOMY` — доставка эконом-товаров со своего склада.
      - `order_date` — string. Дата принятия отправления в обработку.
      - `posting_number` — string. Номер отправления.
      - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `return_delivery_charge` — number<double>. Плата за возвраты и отмены для начислений по тарифам, которые действовали до 1 февраля 2021 года, а также начислений для крупногабаритных товаров.
    - `sale_commission` — number<double>. Комиссия за продажу или возврат комиссии за продажу.
    - `services` — array[object]. Название услуги.
      - `name` — string. Название услуги: - `MarketplaceNotDeliveredCostItem` — возврат невостребованного товара от покупателя на склад. - `MarketplaceReturnAfterDeliveryCostItem` — возврат от покупателя на склад после доставки. - `MarketplaceDeliveryCostItem` — доставка товара до покупателя. - `MarketplaceSaleReviewsItem` — приобретение отзывов на платформе. - `ItemAdvertisementForSupplierLogistic` — доставка товаров на склад Ozon — кросс-докинг. - `OperationMarketplaceServiceStorage` — размещения товаров. - `MarketplaceMarketingActionCostItem` — продвижение товаров. - `MarketplaceServiceItemInstallment` — продвижениe и продажа в рассрочку. - `MarketplaceServiceItemMarkingItems` — обязательная маркировка товаров. - `MarketplaceServiceItemFlexiblePaymentSchedule` — гибкий график выплат. - `MarketplaceServiceItemReturnFromStock` — комплектация товаров для вывоза продавцом. - `ItemAdvertisementForSupplierLogisticSeller` — транспортно-экспедиционные услуги. - `ItemAgentServiceStarsMembership` — вознаграждение за услугу [«Звёздные товары»](https://s.ozon.ru/e7NlR6b). - `MarketplaceServiceItemDelivToCustomer` — последняя миля. - `MarketplaceServiceItemDirectFlowTrans` — магистраль. - `MarketplaceServiceItemDropoffFF` — обработка отправления. - `MarketplaceServiceItemDropoffPVZ` — обработка отправления. - `MarketplaceServiceItemDropoffSC` — обработка отправления. - `MarketplaceServiceItemFulfillment` — сборка заказа. - `MarketplaceServiceItemPickup` — выезд транспортного средства по адресу продавца для забора отправлений — Pick-up. - `MarketplaceServiceItemReturnAfterDelivToCustomer` — обработка возврата. - `MarketplaceServiceItemReturnFlowTrans` — обратная магистраль. - `MarketplaceServiceItemReturnNotDelivToCustomer` — обработка отмен. - `MarketplaceServiceItemReturnPartGoodsCustomer` — обработка невыкупа. - `MarketplaceRedistributionOfAcquiringOperation` — оплата эквайринга. - `MarketplaceReturnStorageServiceAtThePickupPointFbsItem` — краткосрочное размещение возврата FBS. - `MarketplaceReturnStorageServiceInTheWarehouseFbsItem` — долгосрочное размещение возврата FBS. - `MarketplaceServiceItemDeliveryKGT` — доставка крупногабаритного товара (КГТ). - `MarketplaceServiceItemDirectFlowLogistic` — логистика. - `MarketplaceServiceItemReturnFlowLogistic` — обратная логистика. - `MarketplaceServicePremiumCashbackIndividualPoints` — услуга продвижения «Бонусы продавца». - `MarketplaceServicePremiumPromotion` — услуга продвижение Premium, фиксированная комиссия. - `OperationMarketplaceWithHoldingForUndeliverableGoods` — удержание за недовложение товара. - `MarketplaceServiceItemDropoffPPZ` — услуга drop-off в пункте приёма заказов. - `MarketplaceServiceItemRedistributionReturnsPVZ` — перевыставление возвратов на ПВЗ. - `OperationMarketplaceAgencyFeeAggregator3PLGlobal` — тарификация агентской услуги Agregator 3PL Global. - `MarketplaceServiceItemDirectFlowLogisticVDC` — логистика вРЦ.
      - `price` — number<double>. Цена.
    - `type` — string. Тип начисления: - `all` — все, - `orders` — заказы, - `returns` — возвраты и отмены, - `services` — сервисные сборы, - `compensation` — компенсация, - `transferDelivery` — стоимость доставки, - `other` — прочее.
  - `page_count` — integer<int64>. Количество страниц. Если 0, страниц больше нет.
  - `row_count` — integer<int64>. Количество транзакций на всех страницах. Если 0, транзакций больше нет.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
