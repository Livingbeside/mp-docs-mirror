---
title: Просмотр товаров и карточек
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md"
fetched_at: "2026-09-24T02:13:05Z"
content_sha: 5bf6b0d2c1c9cce6
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Просмотр товаров и карточек

Название доступа в OpenAPI-спецификации: offers-and-cards-management:read-only.

## Товары

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)
|
Списки характеристик товаров по категориям
||
||
[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)
|
Получение информации о заполненности карточек магазина
||
||
[POST v1/businesses/{businessId}/offers/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/getDocuments.md)
|
Получение документов
||
||
[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|
Информация о товарах в каталоге
||
||
[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
|
Информация о товарах, которые размещены в заданном магазине
||
||
[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)
|
Информация о скрытых вами товарах
||
|#

## Остатки и оборачиваемость

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)
|
Информация об остатках и оборачиваемости
||
||
[POST v3/businesses/{businessId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md)
|
Информация об остатках
||
|#

## Отчеты и документы

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)
|
Отчет по товарам
||
||
[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)
|
Отчет по остаткам на складах
||
||
[POST v3/businesses/{businessId}/reports/stocks/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksReport.md)
|
Отчет по остаткам на складах партнера
||
||
[POST v2/reports/goods-turnover/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)
|
Отчет по оборачиваемости
||
||
[POST v2/reports/goods-movement/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)
|
Отчет по движению товаров
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
