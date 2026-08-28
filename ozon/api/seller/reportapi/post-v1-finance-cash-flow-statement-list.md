---
title: Финансовый отчёт
api: ozon-seller
method: POST
path: /v1/finance/cash-flow-statement/list
operation_id: FinanceAPI_FinanceCashFlowStatementList
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b02d5d6af1672b9c
---

# Финансовый отчёт

`POST /v1/finance/cash-flow-statement/list`

Метод для получения финансового отчёта за периоды с 01 по 15 и с 16 по 31. 
Запросить отчёт за отдельные дни не получится. 
Соответствует разделу **Финансы → Баланс → Доходы и расходы** в личном кабинете.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date` — object **обязательный**. Период формирования отчёта.
  - `from` — string<date-time> **обязательный**. Дата, с ĸоторой рассчитывается отчёт.
  - `to` — string<date-time> **обязательный**. Дата, по ĸоторую рассчитывается отчёт.
- `page` — integer<int32> **обязательный**. Номер страницы, возвращаемой в запросе.
- `page_size` — integer<int32> **обязательный**. Количество элементов на странице.
- `with_details` — boolean. `true`, если нужно добавить дополнительные параметры в ответ.

## Ответы

**200** — Финансовый отчёт

- `result` — object. Результат работы метода.
  - `cash_flows` — ?. Список отчётов.
    - `commission_amount` — number<double>. Комиссия Ozon за реализацию товаров.
    - `currency_code` — string. Код валюты, в которой рассчитываются комиссии.
    - `item_delivery_and_return_amount` — number<double>. Сумма услуг логистики.
    - `orders_amount` — number<double>. Сумма цен реализованных товаров.
    - `period` — object. Период.
      - `begin` — string<date-time>. Начало периода.
      - `end` — string<date-time>. Конец периода.
      - `id` — integer<int64>. Идентификатор.
    - `returns_amount` — number<double>. Сумма цен возвращённых товаров.
    - `services_amount` — number<double>. Сумма дополнительных услуг.
  - `details` — object. Детализированная информация.
    - `begin_balance_amount` — number<double>. Баланс на начало периода.
    - `delivery` — object. Заказы.
      - `amount` — number<double>. Сумма, на которую выкуплено товаров с учётом комиссий.
      - `delivery_services` — object. Плата за обработку и доставку.
        - `items` — object. Детализация.
          - `name` — string. Название операции. Возможные значения: - `MarketplaceServiceItemDirectFlowLogisticSum` — логистика, - `MarketplaceServiceItemDirectFlowLogisticDC` — логистика РЦ, - `MarketplaceServiceItemDropoff` — обработка отправления Drop-off, - `MarketplaceServiceItemDirectFlowTrans` — магистраль, - `MarketplaceServiceDCFlowTrans` — магистраль РЦ, - `MarketplaceServiceItemFulfillment` — сборка заказа, - `MarketplaceServiceItemDelivToCustomer` — последняя миля.
          - `price` — number<double>. Сумма по операции.
        - `total` — number<double>. Общая сумма.
      - `total` — number<double>. Общая сумма.
    - `end_balance_amount` — number<double>. Баланс на конец периода.
    - `invoice_transfer` — number<double>. Сумма к выплате за период.
    - `loan` — number<double>. Перевод по договорам займа.
    - `others` — object. Компенсация и прочие начисления.
      - `items` — array[object]. Детализация.
        - `name` — string. Название операции. Возможные значения: - `MarketplaceRedistributionOfAcquiringOperation` — оплата эквайринга, - `MarketplaceSellerCompensationLossOfGoodsOperation` — компенсация за уничтоженный товар, - `MarketplaceSellerCorrectionOperation` — корректировка стоимости услуг, - `OperationCorrectionSeller` — инвентаризация взаиморасчётов, - `OperationMarketplaceWithHoldingForUndeliverableGoods` — компенсация за недовложение товаров, - `OperationClaim` — начисления по претензиям.
        - `price` — number<double>. Сумма по операции.
      - `total` — number<double>. Общая сумма.
    - `payments` — object. Выплачено за период.
      - `currency_code` — string. Валюта.
      - `payment` — number<double>. Сумма выплаты.
    - `period` — object. Период.
      - `begin` — string<date-time>. Начало периода.
      - `end` — string<date-time>. Конец периода.
      - `id` — integer<int64>. Идентификатор.
    - `return` — object. Возвраты и отмены.
      - `amount` — number<double>. Сумма, на которую получено возвратов с учётом комиссий.
      - `return_services` — object. Плата за возвраты и отмены.
        - `items` — object. Детализация.
          - `name` — string. Название операции. Возможные значения: - `MarketplaceServiceItemReturnAfterDelivToCustomer` — обработка возвратов, - `MarketplaceServiceItemReturnPartGoodsCustomer` — обработка частичного невыкупа, - `MarketplaceServiceItemReturnNotDelivToCustomer` — обработка отменённых и невостребованных товаров, - `MarketplaceServiceItemReturnFlowLogistic` — обратная логистика.
          - `price` — number<double>. Сумма по операции.
        - `total` — number<double>. Общая сумма.
      - `total` — number<double>. Общая сумма.
    - `rfbs` — object. Перечисления по схеме rFBS.
      - `compensation_delivery_return` — number<double>. Компенсация перечислений за доставку.
      - `partial_compensation` — number<double>. Перечисления частичных компенсаций покупателям.
      - `partial_compensation_return` — number<double>. Возврат частичных компенсаций.
      - `total` — number<double>. Общая сумма.
      - `transfer_delivery` — number<double>. Перечисления от покупателей.
      - `transfer_delivery_return` — number<double>. Возврат перечислений покупателям.
    - `services` — object. Услуги.
      - `items` — array[object]. Детализация.
        - `name` — string. Название операции: - `MarketplaceServiceItemElectronicServiceStencil` — услуга «Трафареты»; - `MarketplaceServiceItemElectronicServicesPromotionInSearch` — услуга «Продвижение в поиске»; - `MarketplaceServiceItemElectronicServicesBrandShelf` — услуга «Брендовая полка»; - `MarketplaceServiceBrandPromotion` и `MarketplaceServiceBrandCommission` — услуга «Продвижение бренда»; - `MarketplaceServiceItemMarketingServices` — маркетинговые услуги; - `MarketplaceServiceItemTechnicalServicesAndOtherServices` — технические и иные услуги; - `MarketplaceServiceItemOtherElectronicServices` — иные электронные услуги; - `ItemAgentServiceStarsMembership` — звёздные товары; - `MarketplaceReturnStorageServiceAtThePickupPointFbsItem` — краткосрочное размещение возврата FBS; - `MarketplaceSaleReviewsItem` — приобретение отзывов на платформе; - `MarketplaceServicePremiumCashbackIndividualPoints` — услуга продвижения «Бонусы продавца»; - `OperationMarketplaceServiceStorage` — услуга размещения товаров; - `MarketplaceServiceStockDisposal` — утилизация со стока; - `MarketplaceReturnDisposalServiceFbsItem` — утилизация FBS; - `MarketplaceServiceItemFlexiblePaymentSchedule` — услуга «Гибкий график выплат»; - `MarketplaceServiceProcessingSpoilage` — обработка брака; - `MarketplaceServiceProcessingIdentifiedSurplus` — обработка опознанных излишков; - `MarketplaceServiceProcessingIdentifiedDiscrepancies` — бронирование места для размещения на складе; - `MarketplaceServiceItemInternetSiteAdvertising` — реклама на сайте Ozon; - `MarketplaceServiceItemSubscribtionPremium` — премиум-подписка; - `MarketplaceAgencyFeeAggregator3PLGlobalItem` — агентское вознаграждение Ozon.
        - `price` — number<double>. Сумма по операции.
      - `total` — number<double>. Общая сумма.
  - `page_count` — integer<int64>. Количество страниц с отчётами.

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
