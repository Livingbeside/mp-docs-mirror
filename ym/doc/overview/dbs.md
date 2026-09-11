---
title: DBS
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md"
fetched_at: "2026-09-11T01:57:32Z"
content_sha: b41613446df3b0e5
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/dbs.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/dbs.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Список методов, используемых в модели DBS

При работе по модели DBS вы сами храните товары, собираете заказы и отвозите их покупателям. Подробнее о модели читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/introduction/models#dbs).

<!-- source: ru/_auto/methods_summary/dbs.md -->
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
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
{style="max-width: 400px"}
|
Передача кодов маркировки единиц товара
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)
{style="max-width: 400px"}
|
Удаление товаров из заказа или уменьшение их числа
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md)
{style="max-width: 400px"}
|
Передача трек‑номера посылки
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)
{style="max-width: 400px"}
|
Изменение даты доставки заказа
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md)
{style="max-width: 400px"}
|
Продление срока хранения заказа
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md)
{style="max-width: 400px"}
|
Информация о покупателе — физическом лице
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​cancellation/​accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md)
{style="max-width: 400px"}
|
Отмена заказа покупателем
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)
{style="max-width: 400px"}
|
Передача ключей цифровых товаров
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
|#

## DBS-доставка

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​campaigns/​{campaignId}/​outlets/​{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)
{style="max-width: 400px"}
|
Информация об одной точке продаж
||
||
[GET v2/​campaigns/​{campaignId}/​outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)
{style="max-width: 400px"}
|
Информация о нескольких точках продаж
||
||
[POST v2/​campaigns/​{campaignId}/​outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
{style="max-width: 400px"}
|
Создание точки продаж
||
||
[PUT v2/​campaigns/​{campaignId}/​outlets/​{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)
{style="max-width: 400px"}
|
Изменение информации о точке продаж
||
||
[DELETE v2/​campaigns/​{campaignId}/​outlets/​{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/deleteOutlet.md)
{style="max-width: 400px"}
|
Удаление точки продаж
||
||
[GET v2/​campaigns/​{campaignId}/​outlets/​licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md)
{style="max-width: 400px"}
|
Информация о лицензиях для точек продаж
||
||
[POST v2/​campaigns/​{campaignId}/​outlets/​licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/updateOutletLicenses.md)
{style="max-width: 400px"}
|
Создание и изменение лицензий для точек продаж
||
||
[DELETE v2/​campaigns/​{campaignId}/​outlets/​licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/deleteOutletLicenses.md)
{style="max-width: 400px"}
|
Удаление лицензий для точек продаж
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
<!-- endsource: ru/_auto/methods_summary/dbs.md -->
