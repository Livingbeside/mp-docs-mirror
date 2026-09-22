---
title: FBS
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md"
fetched_at: "2026-09-22T02:26:35Z"
content_sha: 7b3a8cef0a200f05
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/fbs.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/fbs.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Список методов, используемых в модели FBS

Размещая товары по модели FBS, вы храните их на своем складе, а доставку заказов поручаете Маркету. Когда покупатель оформляет заказ, вы его собираете и упаковываете, а дальше либо сами отвозите Маркету, либо отгружаете в присланную Маркетом машину. Подробнее о модели читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/introduction/models#fbs).

<!-- source: ru/_auto/methods_summary/fbs.md -->
## Кабинеты и магазины

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​campaigns/​{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md)
{style="max-width: 400px"}
|
Информация о магазине
||
||
[GET v2/​campaigns/​{campaignId}/​settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md)
{style="max-width: 400px"}
|
Настройки магазина
||
|#

## Товары

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​campaigns/​{campaignId}/​offers/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)
{style="max-width: 400px"}
|
Изменение условий продажи товаров в магазине
||
||
[POST v2/​campaigns/​{campaignId}/​offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
{style="max-width: 400px"}
|
Информация о товарах, которые размещены в заданном магазине
||
||
[POST v2/​campaigns/​{campaignId}/​offers/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/deleteCampaignOffers.md)
{style="max-width: 400px"}
|
Удаление товаров из ассортимента магазина
||
||
[GET v2/​campaigns/​{campaignId}/​hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)
{style="max-width: 400px"}
|
Информация о скрытых вами товарах
||
||
[POST v2/​campaigns/​{campaignId}/​hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)
{style="max-width: 400px"}
|
Скрытие товаров и настройки скрытия
||
||
[POST v2/​campaigns/​{campaignId}/​hidden-offers/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md)
{style="max-width: 400px"}
|
Возобновление показа товаров
||
|#

## Остатки и оборачиваемость

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​campaigns/​{campaignId}/​offers/​stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)
{style="max-width: 400px"}
|
Информация об остатках и оборачиваемости
||
||
[PUT v2/​campaigns/​{campaignId}/​offers/​stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)
{style="max-width: 400px"}
|
Передача информации об остатках
||
|#

## Цены

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​tariffs/​calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)
{style="max-width: 400px"}
|
Калькулятор стоимости услуг
||
||
[POST v2/​campaigns/​{campaignId}/​offer-prices/​updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)
{style="max-width: 400px"}
|
Установка цен на товары в конкретном магазине
||
||
[POST v2/​campaigns/​{campaignId}/​offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)
{style="max-width: 400px"}
|
Просмотр цен на указанные товары в конкретном магазине
||
||
[POST v2/​campaigns/​{campaignId}/​price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md)
{style="max-width: 400px"}
|
Список товаров, находящихся в карантине по цене в магазине
||
||
[POST v2/​campaigns/​{campaignId}/​price-quarantine/​confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmCampaignPrices.md)
{style="max-width: 400px"}
|
Удаление товара из карантина по цене в магазине
||
|#

## Заказы

#|
|| **Метод** | **Описание метода** ||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)
{style="max-width: 400px"}
|
Подготовка заказа
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)
{style="max-width: 400px"}
|
Передача внешнего идентификатора заказа
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
{style="max-width: 400px"}
|
Изменение статуса одного заказа
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)
{style="max-width: 400px"}
|
Изменение статусов нескольких заказов
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​identifiers/​status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)
{style="max-width: 400px"}
|
Статусы проверки кодов маркировки
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)
{style="max-width: 400px"}
|
Информация о покупателе — юридическом лице
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)
{style="max-width: 400px"}
|
Информация о документах
||
|#

## Отгрузки FBS

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)
{style="max-width: 400px"}
|
Получение информации об одной отгрузке
||
||
[PUT v2/​campaigns/​{campaignId}/​first-mile/​shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)
{style="max-width: 400px"}
|
Получение информации о нескольких отгрузках
||
||
[POST v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md)
{style="max-width: 400px"}
|
Подтверждение отгрузки
||
||
[GET v2/​campaigns/​{campaignId}/​shipments/​reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)
{style="max-width: 400px"}
|
Подтверждение ближайшей отгрузки и получение акта приема-передачи для нее
||
||
[POST v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​orders/​transfer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/transferOrdersFromShipment.md)
{style="max-width: 400px"}
|
Перенос заказов в следующую отгрузку
||
||
[PUT v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​pallets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/setShipmentPalletsCount.md)
{style="max-width: 400px"}
|
Передача количества упаковок для доверительной приемки
||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md)
{style="max-width: 400px"}
|
Получение акта приема-передачи
||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​discrepancy-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentDiscrepancyAct.md)
{style="max-width: 400px"}
|
Получение акта расхождений
||
||
[POST v2/​reports/​documents/​shipment-list/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShipmentListDocumentReport.md)
{style="max-width: 400px"}
|
Получение листа сборки
||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​transportation-waybill](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentTransportationWaybill.md)
{style="max-width: 400px"}
|
Получение транспортной накладной
||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​inbound-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentInboundAct.md)
{style="max-width: 400px"}
|
Получение фактического акта приема-передачи
||
|#

## Ярлыки FBS и DBS

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​shipments/​{shipmentId}/​boxes/​{boxId}/​label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)
{style="max-width: 400px"}
|
Готовый ярлык‑наклейка для коробки в заказе
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)
{style="max-width: 400px"}
|
Готовые ярлыки‑наклейки на все коробки в одном заказе
||
||
[POST v2/​reports/​documents/​labels/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)
{style="max-width: 400px"}
|
Готовые ярлыки‑наклейки на все коробки в нескольких заказах
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​labels/​data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)
{style="max-width: 400px"}
|
Данные для самостоятельного изготовления ярлыков
||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​orders/​info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipmentOrdersInfo.md)
{style="max-width: 400px"}
|
Получение информации о возможности печати ярлыков
||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​pallet/​labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentPalletLabels.md)
{style="max-width: 400px"}
|
Ярлыки для доверительной приемки
||
|#

## Невыкупы и возвраты

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​campaigns/​{campaignId}/​returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)
{style="max-width: 400px"}
|
Список невыкупов и возвратов
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
{style="max-width: 400px"}
|
Информация о невыкупе или возврате
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}/​application](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnApplication.md)
{style="max-width: 400px"}
|
Получение заявления на возврат
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}/​decision/​{itemId}/​image/​{imageHash}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnPhoto.md)
{style="max-width: 400px"}
|
Получение фотографий товаров в возврате
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}/​decision/​submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md)
{style="max-width: 400px"}
|
Передача решения по возврату
||
|#

## Отчеты и документы

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​reports/​shows-sales/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)
{style="max-width: 400px"}
|
Отчет «Аналитика продаж»
||
||
[POST v2/​reports/​sales-geography/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateSalesGeographyReport.md)
{style="max-width: 400px"}
|
Отчет по географии продаж
||
||
[POST v2/​reports/​key-indicators/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md)
{style="max-width: 400px"}
|
Отчет по ключевым показателям
||
||
[POST v2/​reports/​competitors-position/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateCompetitorsPositionReport.md)
{style="max-width: 400px"}
|
Отчет «Конкурентная позиция»
||
||
[POST v2/​campaigns/​{campaignId}/​stats/​orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)
{style="max-width: 400px"}
|
Детальная информация по заказам
||
||
[POST v2/​reports/​united-orders/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)
{style="max-width: 400px"}
|
Отчет по заказам
||
||
[POST v2/​campaigns/​{campaignId}/​stats/​skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)
{style="max-width: 400px"}
|
Отчет по товарам
||
||
[POST v2/​reports/​goods-prices/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md)
{style="max-width: 400px"}
|
Отчет «Цены»
||
||
[POST v2/​reports/​goods-feedback/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md)
{style="max-width: 400px"}
|
Отчет по отзывам о товарах
||
||
[POST v2/​reports/​jewelry-fiscal/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateJewelryFiscalReport.md)
{style="max-width: 400px"}
|
Отчет по заказам с ювелирными изделиями
||
||
[POST v2/​reports/​goods-realization/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)
{style="max-width: 400px"}
|
Отчет по реализации
||
||
[POST v2/​reports/​united-netting/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)
{style="max-width: 400px"}
|
Отчет по платежам
||
||
[POST v2/​reports/​shows-boost/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md)
{style="max-width: 400px"}
|
Отчет по бусту показов
||
||
[POST v2/​reports/​boost-consolidated/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBoostConsolidatedReport.md)
{style="max-width: 400px"}
|
Отчет по бусту продаж
||
||
[POST v2/​reports/​shelf-statistics/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)
{style="max-width: 400px"}
|
Отчет по полкам
||
||
[POST v2/​reports/​banners-statistics/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md)
{style="max-width: 400px"}
|
Отчет по охватному продвижению
||
|#

## Индекс качества

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​campaigns/​{campaignId}/​ratings/​quality/​details](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatingDetails.md)
{style="max-width: 400px"}
|
Заказы, которые повлияли на индекс качества
||
|#

## Справочники

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​delivery/​services](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-services/getDeliveryServices.md)
{style="max-width: 400px"}
|
Справочник служб доставки
||
|#
<!-- endsource: ru/_auto/methods_summary/fbs.md -->
