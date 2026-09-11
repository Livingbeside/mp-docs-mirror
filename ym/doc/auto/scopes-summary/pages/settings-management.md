---
title: Настройка магазинов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md"
fetched_at: "2026-09-11T01:57:11Z"
content_sha: 3bc0a7f43b407b75
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/settings-management.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/settings-management.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Настройка магазинов

Название доступа в OpenAPI-спецификации: settings-management.

## DBS-доставка

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)
|
Информация об одной точке продаж
||
||
[GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)
|
Информация о нескольких точках продаж
||
||
[POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
|
Создание точки продаж
||
||
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)
|
Изменение информации о точке продаж
||
||
[DELETE v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/deleteOutlet.md)
|
Удаление точки продаж
||
||
[GET v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md)
|
Информация о лицензиях для точек продаж
||
||
[POST v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/updateOutletLicenses.md)
|
Создание и изменение лицензий для точек продаж
||
||
[DELETE v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/deleteOutletLicenses.md)
|
Удаление лицензий для точек продаж
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
