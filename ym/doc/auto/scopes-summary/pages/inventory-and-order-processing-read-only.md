---
title: Просмотр информации о заказах
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md"
fetched_at: "2026-08-28T11:51:10Z"
content_sha: 5bb620badfc64cdb
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md
  - href: ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md
    type: text/markdown
    title: Markdown version
  - href: ../../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Просмотр информации о заказах

Название доступа в OpenAPI-спецификации: inventory-and-order-processing:read-only.

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
[POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)
|
Статусы проверки кодов маркировки
||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md)
|
Информация о покупателе — физическом лице
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
[POST v1/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md)
|
Получение доступных вариантов доставки заказов
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
[POST v2/reports/documents/shipment-list/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShipmentListDocumentReport.md)
|
Получение листа сборки
||
|#

## Ярлыки FBS и DBS

#|
|| **Метод** | **Описание метода** ||
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
[POST v1/campaigns/{campaignId}/return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md)
|
Получение подходящих для возврата пунктов выдачи
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
