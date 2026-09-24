---
title: Получение информации по FBY-заявкам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md"
fetched_at: "2026-09-24T02:13:07Z"
content_sha: 3f5eb2ebbd051cd9
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/_auto/scopes_summary/pages/supplies-management_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/_auto/scopes_summary/pages/supplies-management_read-only.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Получение информации по FBY-заявкам

Название доступа в OpenAPI-спецификации: supplies-management:read-only.

## Заявки на поставку, вывоз и утилизацию (FBY, LaaS)

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md)
|
Получение информации о заявках на поставку, вывоз и утилизацию
||
||
[POST v2/campaigns/{campaignId}/supply-requests/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestItems.md)
|
Получение товаров в заявке на поставку, вывоз или утилизацию
||
||
[POST v2/campaigns/{campaignId}/supply-requests/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md)
|
Получение документов по заявке на поставку, вывоз или утилизацию
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
