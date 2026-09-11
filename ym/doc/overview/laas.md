---
title: LaaS
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md"
fetched_at: "2026-09-11T01:57:33Z"
content_sha: 2bd7f13a9f3527eb
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/laas.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/laas.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Список методов, используемых в модели LaaS

При работе по модели LaaS вы храните товары на складе Маркета, но не размещаете их на его витрине. Маркет берет на себя всю работу с заказами — от хранения до доставки. Вам останется только:

* сообщать о новых заказах с внешних площадок;
* следить, чтобы ваши товары на складе Маркета не заканчивались, и поставлять новые партии.

Подробнее о модели читайте в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/tools/laas).

<!-- source: ru/_auto/methods_summary/laas.md -->
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
|#

## Заказы

#|
|| **Метод** | **Описание метода** ||
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
[POST v1/​campaigns/​{campaignId}/​orders/​create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
{style="max-width: 400px"}
|
Создание заказа
||
||
[POST v1/​campaigns/​{campaignId}/​delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md)
{style="max-width: 400px"}
|
Получение доступных вариантов доставки заказов
||
||
[POST v1/​campaigns/​{campaignId}/​orders/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md)
{style="max-width: 400px"}
|
Изменение заказа
||
||
[POST v1/​campaigns/​{campaignId}/​orders/​update-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderUpdateOptions.md)
{style="max-width: 400px"}
|
Получение временных интервалов для изменения заказа
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
[POST v1/​campaigns/​{campaignId}/​returns/​create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md)
{style="max-width: 400px"}
|
Создание возврата
||
||
[POST v1/​campaigns/​{campaignId}/​return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md)
{style="max-width: 400px"}
|
Получение подходящих для возврата пунктов выдачи
||
||
[POST v1/​campaigns/​{campaignId}/​returns/​cancel](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/cancelReturn.md)
{style="max-width: 400px"}
|
Отмена возврата
||
|#

## Отчеты и документы

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​reports/​goods-movement/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)
{style="max-width: 400px"}
|
Отчет по движению товаров
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
<!-- endsource: ru/_auto/methods_summary/laas.md -->
