---
title: Сравнение методов по моделям
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md"
fetched_at: "2026-08-28T11:51:42Z"
content_sha: 13277769f53adef1
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/comparison.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/comparison.md
  - href: ru/overview/comparison.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Сравнение методов по моделям

<!-- source: ru/_auto/methods_summary/comparison.md -->
## Кабинеты и магазины

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​campaigns/​{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md)
{width=310px}
|
Информация о магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[GET v2/​campaigns/​{campaignId}/​settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md)
{width=310px}
|
Настройки магазина
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
|#

## Товары

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[POST v2/​campaigns/​{campaignId}/​offers/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)
{width=310px}
|
Изменение условий продажи товаров в магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[POST v1/​reports/​documents/​barcodes/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBarcodesReport.md)
{width=310px}
|
Получение файла со штрихкодами
{width=240px}
|
✔️
|

|

|

|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
{width=310px}
|
Информация о товарах, которые размещены в заданном магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​offers/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/deleteCampaignOffers.md)
{width=310px}
|
Удаление товаров из ассортимента магазина
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[GET v2/​campaigns/​{campaignId}/​hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)
{width=310px}
|
Информация о скрытых вами товарах
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)
{width=310px}
|
Скрытие товаров и настройки скрытия
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​hidden-offers/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md)
{width=310px}
|
Возобновление показа товаров
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
|#

## Остатки и оборачиваемость

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[POST v2/​campaigns/​{campaignId}/​offers/​stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)
{width=310px}
|
Информация об остатках и оборачиваемости
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[PUT v2/​campaigns/​{campaignId}/​offers/​stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)
{width=310px}
|
Передача информации об остатках
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
|#

## Цены

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[POST v2/​tariffs/​calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)
{width=310px}
|
Калькулятор стоимости услуг
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​offer-prices/​updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)
{width=310px}
|
Установка цен на товары в конкретном магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)
{width=310px}
|
Просмотр цен на указанные товары в конкретном магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md)
{width=310px}
|
Список товаров, находящихся в карантине по цене в магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​price-quarantine/​confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmCampaignPrices.md)
{width=310px}
|
Удаление товара из карантина по цене в магазине
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
|#

## Заказы

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)
{width=310px}
|
Подготовка заказа
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)
{width=310px}
|
Передача внешнего идентификатора заказа
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
{width=310px}
|
Изменение статуса одного заказа
{width=240px}
|

|
✔️
|
✔️
|
✔️
|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​orders/​status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)
{width=310px}
|
Изменение статусов нескольких заказов
{width=240px}
|

|
✔️
|
✔️
|
✔️
|
✔️
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
{width=310px}
|
Передача кодов маркировки единиц товара
{width=240px}
|

|

|

|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​identifiers/​status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)
{width=310px}
|
Статусы проверки кодов маркировки
{width=240px}
|

|
✔️
|
✔️
|

|
✔️
||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md)
{width=310px}
|
Передача кода подтверждения
{width=240px}
|

|

|
✔️
|

|

||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)
{width=310px}
|
Удаление товаров из заказа или уменьшение их числа
{width=240px}
|

|

|

|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md)
{width=310px}
|
Передача трек‑номера посылки
{width=240px}
|

|

|

|
✔️
|

||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)
{width=310px}
|
Изменение даты доставки заказа
{width=240px}
|

|

|

|
✔️
|

||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md)
{width=310px}
|
Продление срока хранения заказа
{width=240px}
|

|

|

|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md)
{width=310px}
|
Информация о покупателе — физическом лице
{width=240px}
|

|

|

|
✔️
|

||
||
[PUT v2/​campaigns/​{campaignId}/​orders/​{orderId}/​cancellation/​accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md)
{width=310px}
|
Отмена заказа покупателем
{width=240px}
|

|

|

|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)
{width=310px}
|
Передача ключей цифровых товаров
{width=240px}
|

|

|

|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)
{width=310px}
|
Информация о покупателе — юридическом лице
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)
{width=310px}
|
Информация о документах
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v1/​campaigns/​{campaignId}/​orders/​create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
{width=310px}
|
Создание заказа
{width=240px}
|

|

|

|

|
✔️
||
||
[POST v1/​campaigns/​{campaignId}/​delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md)
{width=310px}
|
Получение доступных вариантов доставки заказов
{width=240px}
|

|

|

|

|
✔️
||
||
[POST v1/​campaigns/​{campaignId}/​orders/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md)
{width=310px}
|
Изменение заказа
{width=240px}
|

|

|

|

|
✔️
||
||
[POST v1/​campaigns/​{campaignId}/​orders/​update-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderUpdateOptions.md)
{width=310px}
|
Получение временных интервалов для изменения заказа
{width=240px}
|

|

|

|

|
✔️
||
|#

## Отгрузки FBS

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)
{width=310px}
|
Получение информации об одной отгрузке
{width=240px}
|

|
✔️
|

|

|

||
||
[PUT v2/​campaigns/​{campaignId}/​first-mile/​shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)
{width=310px}
|
Получение информации о нескольких отгрузках
{width=240px}
|

|
✔️
|

|

|

||
||
[POST v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md)
{width=310px}
|
Подтверждение отгрузки
{width=240px}
|

|
✔️
|

|

|

||
||
[GET v2/​campaigns/​{campaignId}/​shipments/​reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)
{width=310px}
|
Подтверждение ближайшей отгрузки и получение акта приема-передачи для нее
{width=240px}
|

|
✔️
|

|

|

||
||
[POST v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​orders/​transfer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/transferOrdersFromShipment.md)
{width=310px}
|
Перенос заказов в следующую отгрузку
{width=240px}
|

|
✔️
|

|

|

||
||
[PUT v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​pallets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/setShipmentPalletsCount.md)
{width=310px}
|
Передача количества упаковок для доверительной приемки
{width=240px}
|

|
✔️
|

|

|

||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md)
{width=310px}
|
Получение акта приема-передачи
{width=240px}
|

|
✔️
|

|

|

||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​discrepancy-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentDiscrepancyAct.md)
{width=310px}
|
Получение акта расхождений
{width=240px}
|

|
✔️
|

|

|

||
||
[POST v2/​reports/​documents/​shipment-list/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShipmentListDocumentReport.md)
{width=310px}
|
Получение листа сборки
{width=240px}
|

|
✔️
|

|

|

||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​transportation-waybill](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentTransportationWaybill.md)
{width=310px}
|
Получение транспортной накладной
{width=240px}
|

|
✔️
|

|

|

||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​inbound-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentInboundAct.md)
{width=310px}
|
Получение фактического акта приема-передачи
{width=240px}
|

|
✔️
|

|

|

||
|#

## Ярлыки FBS и DBS

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​shipments/​{shipmentId}/​boxes/​{boxId}/​label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)
{width=310px}
|
Готовый ярлык‑наклейка для коробки в заказе
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)
{width=310px}
|
Готовые ярлыки‑наклейки на все коробки в одном заказе
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​documents/​labels/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)
{width=310px}
|
Готовые ярлыки‑наклейки на все коробки в нескольких заказах
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​delivery/​labels/​data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)
{width=310px}
|
Данные для самостоятельного изготовления ярлыков
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​orders/​info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipmentOrdersInfo.md)
{width=310px}
|
Получение информации о возможности печати ярлыков
{width=240px}
|

|
✔️
|

|

|

||
||
[GET v2/​campaigns/​{campaignId}/​first-mile/​shipments/​{shipmentId}/​pallet/​labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentPalletLabels.md)
{width=310px}
|
Ярлыки для доверительной приемки
{width=240px}
|

|
✔️
|

|

|

||
|#

## Заявки на поставку, вывоз и утилизацию (FBY, LaaS)

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[POST v2/​campaigns/​{campaignId}/​supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md)
{width=310px}
|
Получение информации о заявках на поставку, вывоз и утилизацию
{width=240px}
|
✔️
|

|

|

|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​supply-requests/​items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestItems.md)
{width=310px}
|
Получение товаров в заявке на поставку, вывоз или утилизацию
{width=240px}
|
✔️
|

|

|

|
✔️
||
||
[POST v2/​campaigns/​{campaignId}/​supply-requests/​documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md)
{width=310px}
|
Получение документов по заявке на поставку, вывоз или утилизацию
{width=240px}
|
✔️
|

|

|

|
✔️
||
|#

## DBS-доставка

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​campaigns/​{campaignId}/​outlets/​{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)
{width=310px}
|
Информация об одной точке продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)
{width=310px}
|
Информация о нескольких точках продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
{width=310px}
|
Создание точки продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[PUT v2/​campaigns/​{campaignId}/​outlets/​{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)
{width=310px}
|
Изменение информации о точке продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[DELETE v2/​campaigns/​{campaignId}/​outlets/​{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/deleteOutlet.md)
{width=310px}
|
Удаление точки продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​outlets/​licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md)
{width=310px}
|
Информация о лицензиях для точек продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​outlets/​licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/updateOutletLicenses.md)
{width=310px}
|
Создание и изменение лицензий для точек продаж
{width=240px}
|

|

|

|
✔️
|

||
||
[DELETE v2/​campaigns/​{campaignId}/​outlets/​licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/deleteOutletLicenses.md)
{width=310px}
|
Удаление лицензий для точек продаж
{width=240px}
|

|

|

|
✔️
|

||
|#

## Невыкупы и возвраты

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​campaigns/​{campaignId}/​returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)
{width=310px}
|
Список невыкупов и возвратов
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
{width=310px}
|
Информация о невыкупе или возврате
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|
✔️
||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}/​application](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnApplication.md)
{width=310px}
|
Получение заявления на возврат
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[GET v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}/​decision/​{itemId}/​image/​{imageHash}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnPhoto.md)
{width=310px}
|
Получение фотографий товаров в возврате
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​orders/​{orderId}/​returns/​{returnId}/​decision/​submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md)
{width=310px}
|
Передача решения по возврату
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v1/​campaigns/​{campaignId}/​returns/​create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md)
{width=310px}
|
Создание возврата
{width=240px}
|

|

|

|

|
✔️
||
||
[POST v1/​campaigns/​{campaignId}/​return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md)
{width=310px}
|
Получение подходящих для возврата пунктов выдачи
{width=240px}
|

|

|

|

|
✔️
||
||
[POST v1/​campaigns/​{campaignId}/​returns/​cancel](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/cancelReturn.md)
{width=310px}
|
Отмена возврата
{width=240px}
|

|

|

|

|
✔️
||
|#

## Отчеты и документы

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[POST v2/​reports/​shows-sales/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)
{width=310px}
|
Отчет «Аналитика продаж»
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​sales-geography/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateSalesGeographyReport.md)
{width=310px}
|
Отчет по географии продаж
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​key-indicators/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md)
{width=310px}
|
Отчет по ключевым показателям
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​competitors-position/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateCompetitorsPositionReport.md)
{width=310px}
|
Отчет «Конкурентная позиция»
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​stats/​orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)
{width=310px}
|
Детальная информация по заказам
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​united-orders/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)
{width=310px}
|
Отчет по заказам
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​campaigns/​{campaignId}/​stats/​skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)
{width=310px}
|
Отчет по товарам
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​goods-prices/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md)
{width=310px}
|
Отчет «Цены»
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​goods-feedback/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md)
{width=310px}
|
Отчет по отзывам о товарах
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​goods-turnover/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)
{width=310px}
|
Отчет по оборачиваемости
{width=240px}
|
✔️
|

|

|

|

||
||
[POST v2/​reports/​goods-movement/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)
{width=310px}
|
Отчет по движению товаров
{width=240px}
|
✔️
|

|

|

|
✔️
||
||
[POST v2/​reports/​jewelry-fiscal/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateJewelryFiscalReport.md)
{width=310px}
|
Отчет по заказам с ювелирными изделиями
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​goods-realization/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)
{width=310px}
|
Отчет по реализации
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​united-netting/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)
{width=310px}
|
Отчет по платежам
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​shows-boost/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md)
{width=310px}
|
Отчет по бусту показов
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​boost-consolidated/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBoostConsolidatedReport.md)
{width=310px}
|
Отчет по бусту продаж
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​shelf-statistics/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)
{width=310px}
|
Отчет по полкам
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
||
[POST v2/​reports/​banners-statistics/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md)
{width=310px}
|
Отчет по охватному продвижению
{width=240px}
|
✔️
|
✔️
|
✔️
|
✔️
|

||
|#

## Индекс качества

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[POST v2/​campaigns/​{campaignId}/​ratings/​quality/​details](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatingDetails.md)
{width=310px}
|
Заказы, которые повлияли на индекс качества
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
|#

## Склады

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)
{width=310px}
|
Идентификаторы фулфилмент-складов Маркета
{width=240px}
|
✔️
|

|

|

|
✔️
||
|#

## Справочники

#|
|| **Метод** | **Описание метода** | **FBY** | **FBS** | **Экспресс** | **DBS** | **LaaS** ||
||
[GET v2/​delivery/​services](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-services/getDeliveryServices.md)
{width=310px}
|
Справочник служб доставки
{width=240px}
|

|
✔️
|
✔️
|
✔️
|

||
|#
<!-- endsource: ru/_auto/methods_summary/comparison.md -->
