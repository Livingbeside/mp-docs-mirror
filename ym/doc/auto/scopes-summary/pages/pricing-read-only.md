---
title: Просмотр цен
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md"
fetched_at: "2026-09-22T02:26:12Z"
content_sha: 098818b2e01ae975
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/pricing_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/pricing_read-only.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Просмотр цен

Название доступа в OpenAPI-спецификации: pricing:read-only.

## Цены

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)
|
Калькулятор стоимости услуг
||
||
[POST v2/businesses/{businessId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getDefaultPrices.md)
|
Просмотр цен на указанные товары во всех магазинах
||
||
[POST v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)
|
Просмотр цен на указанные товары в конкретном магазине
||
||
[POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md)
|
Рекомендации Маркета, касающиеся цен
||
||
[POST v2/businesses/{businessId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getBusinessQuarantineOffers.md)
|
Список товаров, находящихся в карантине по цене в кабинете
||
||
[POST v2/campaigns/{campaignId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md)
|
Список товаров, находящихся в карантине по цене в магазине
||
|#

## Акции

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md)
|
Получение списка акций
||
||
[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)
|
Получение списка товаров, которые участвуют или могут участвовать в акции
||
|#

## Заказы

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md)
|
Получение доступных вариантов доставки заказов
||
|#

## Невыкупы и возвраты

#|
|| **Метод** | **Описание метода** ||
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
[POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md)
|
Отчет «Цены»
||
|#

## Буст продаж

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/businesses/{businessId}/bids/info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsInfoForBusiness.md)
|
Информация об установленных ставках
||
||
[POST v2/businesses/{businessId}/bids/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)
|
Рекомендованные ставки для заданных товаров
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
