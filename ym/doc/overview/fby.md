---
title: FBY
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md"
fetched_at: "2026-08-28T11:51:39Z"
content_sha: 73e5337bfc0e1843
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/fby.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/fby.md
  - href: ru/overview/fby.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Список методов, используемых в модели FBY

Если вы работаете по модели FBY, Маркет берет на себя всю работу с заказами — от хранения до доставки. Вам останется только следить, чтобы ваши товары на складе Маркета не заканчивались, и поставлять новые партии. Подробнее о модели читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/introduction/models#fby).

<!-- source: ru/_auto/methods_summary/fby.md -->
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
[POST v1/​reports/​documents/​barcodes/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBarcodesReport.md)
{style="max-width: 400px"}
|
Получение файла со штрихкодами
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

## Заявки на поставку, вывоз и утилизацию (FBY, LaaS)

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​campaigns/​{campaignId}/​supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md)
{style="max-width: 400px"}
|
Получение информации о заявках на поставку, вывоз и утилизацию
||
||
[POST v2/​campaigns/​{campaignId}/​supply-requests/​items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestItems.md)
{style="max-width: 400px"}
|
Получение товаров в заявке на поставку, вывоз или утилизацию
||
||
[POST v2/​campaigns/​{campaignId}/​supply-requests/​documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md)
{style="max-width: 400px"}
|
Получение документов по заявке на поставку, вывоз или утилизацию
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
[POST v2/​reports/​goods-turnover/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)
{style="max-width: 400px"}
|
Отчет по оборачиваемости
||
||
[POST v2/​reports/​goods-movement/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)
{style="max-width: 400px"}
|
Отчет по движению товаров
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

## Склады

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)
{style="max-width: 400px"}
|
Идентификаторы фулфилмент-складов Маркета
||
|#
<!-- endsource: ru/_auto/methods_summary/fby.md -->
