---
title: Обработка заказов и учёт товаров
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md"
fetched_at: "2026-09-24T02:13:02Z"
content_sha: acac65ab5d73f840
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/inventory-and-order-processing.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/inventory-and-order-processing.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Обработка заказов и учёт товаров

Название доступа в OpenAPI-спецификации: inventory-and-order-processing.

## Товары

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/reports/documents/barcodes/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBarcodesReport.md)
|
Получение файла со штрихкодами
||
|#

## Заказы

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)
|
Информация о заказах в кабинете
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)
|
Подготовка заказа
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)
|
Передача внешнего идентификатора заказа
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|
Изменение статуса одного заказа
||
||
[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)
|
Изменение статусов нескольких заказов
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
|
Передача кодов маркировки единиц товара
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)
|
Статусы проверки кодов маркировки
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md)
|
Передача кода подтверждения
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)
|
Удаление товаров из заказа или уменьшение их числа
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/delivery/track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md)
|
Передача трек‑номера посылки
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)
|
Изменение даты доставки заказа
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md)
|
Продление срока хранения заказа
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md)
|
Информация о покупателе — физическом лице
||
||
[PUT v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md)
|
Отмена заказа покупателем
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)
|
Передача ключей цифровых товаров
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)
|
Информация о покупателе — юридическом лице
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)
|
Информация о документах
||
||
[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
|
Создание заказа
||
||
[POST v1/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md)
|
Получение доступных вариантов доставки заказов
||
||
[POST v1/campaigns/{campaignId}/orders/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md)
|
Изменение заказа
||
||
[POST v1/campaigns/{campaignId}/orders/update-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderUpdateOptions.md)
|
Получение временных интервалов для изменения заказа
||
|#

## Отгрузки FBS

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)
|
Получение информации об одной отгрузке
||
||
[PUT v2/campaigns/{campaignId}/first-mile/shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)
|
Получение информации о нескольких отгрузках
||
||
[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md)
|
Подтверждение отгрузки
||
||
[GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)
|
Подтверждение ближайшей отгрузки и получение акта приема-передачи для нее
||
||
[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/transfer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/transferOrdersFromShipment.md)
|
Перенос заказов в следующую отгрузку
||
||
[PUT v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/setShipmentPalletsCount.md)
|
Передача количества упаковок для доверительной приемки
||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md)
|
Получение акта приема-передачи
||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/discrepancy-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentDiscrepancyAct.md)
|
Получение акта расхождений
||
||
[POST v2/reports/documents/shipment-list/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShipmentListDocumentReport.md)
|
Получение листа сборки
||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/transportation-waybill](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentTransportationWaybill.md)
|
Получение транспортной накладной
||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/inbound-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentInboundAct.md)
|
Получение фактического акта приема-передачи
||
|#

## Ярлыки FBS и DBS

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)
|
Готовый ярлык‑наклейка для коробки в заказе
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)
|
Готовые ярлыки‑наклейки на все коробки в одном заказе
||
||
[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)
|
Готовые ярлыки‑наклейки на все коробки в нескольких заказах
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)
|
Данные для самостоятельного изготовления ярлыков
||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipmentOrdersInfo.md)
|
Получение информации о возможности печати ярлыков
||
||
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallet/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentPalletLabels.md)
|
Ярлыки для доверительной приемки
||
|#

## Невыкупы и возвраты

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)
|
Список невыкупов и возвратов
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|
Информация о невыкупе или возврате
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/application](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnApplication.md)
|
Получение заявления на возврат
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/{itemId}/image/{imageHash}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnPhoto.md)
|
Получение фотографий товаров в возврате
||
||
[POST v1/businesses/{businessId}/returns/decisions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnAvailableDecisions.md)
|
Получение возможных решений по возврату
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md)
|
Передача решения по возврату
||
||
[POST v1/campaigns/{campaignId}/returns/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md)
|
Создание возврата
||
||
[POST v1/campaigns/{campaignId}/return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md)
|
Получение подходящих для возврата пунктов выдачи
||
||
[POST v1/campaigns/{campaignId}/returns/cancel](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/cancelReturn.md)
|
Отмена возврата
||
|#

## Отчеты и документы

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)
|
Детальная информация по заказам
||
||
[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)
|
Отчет по заказам
||
||
[POST v2/reports/united-returns/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedReturnsReport.md)
|
Отчет по невыкупам и возвратам
||
||
[POST v2/reports/goods-movement/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)
|
Отчет по движению товаров
||
||
[POST v2/reports/jewelry-fiscal/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateJewelryFiscalReport.md)
|
Отчет по заказам с ювелирными изделиями
||
|#

## Индекс качества

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/businesses/{businessId}/ratings/quality](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatings.md)
|
Индекс качества магазинов
||
||
[POST v2/campaigns/{campaignId}/ratings/quality/details](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatingDetails.md)
|
Заказы, которые повлияли на индекс качества
||
|#

## Склады

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md)
|
Список складов
||
||
[POST v3/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md)
|
Список складов
||
||
[POST v3/businesses/{businessId}/warehouse/models/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseModelStatus.md)
|
Включение/выключение модели работы склада
||
|#

## Просмотр дополнительной информации {#common}

#|
|| **Метод** | **Описание метода** ||
|| [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) | Список магазинов пользователя ||
|| [GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md) | Информация о магазине ||
||
[POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md)
|
Настройки кабинета
||
||
[GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md)
|
Настройки магазина
||
|| [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md) | Дерево категорий ||
||
[POST v1/businesses/{businessId}/operations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/operations/getOperations.md)
|
Получение статусов операций
||
||
[GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md)
|
Получение заданного отчета или документа
||
||
[GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)
|
Идентификаторы фулфилмент-складов Маркета
||
||
[POST v2/auth/token](https://yandex.ru/dev/market/partner-api/doc/ru/reference/auth/getAuthTokenInfo.md)
|
Получение информации о токене авторизации
||
||
[GET v2/delivery/services](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-services/getDeliveryServices.md)
|
Справочник служб доставки
||
||
[POST v1/businesses/{businessId}/logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md)
|
Получение точек ПВЗ Маркета
||
||
[POST v2/regions/countries](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
|
Список допустимых кодов стран
||
|| [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md) | Поиск регионов по их имени ||
|| [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md) | Информация о регионе ||
||
[GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md)
|
Информация о дочерних регионах
||
|#
