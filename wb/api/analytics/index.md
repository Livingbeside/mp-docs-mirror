---
title: Аналитика и данные — все методы
api: wb-analytics
spec_version: analytics
operations: 20
source: "https://dev.wildberries.ru/docs/openapi/analytics"
content_sha: 86c75293bdef6ed3
---

# Аналитика и данные

Узнать больше об аналитике и данных можно в справочном центре В разделе описаны методы получения: 1. [Воронки продаж](./analytics#tag/salesFunnel) 2. [Ленты заказов](./analytics#tag/orderFeed) 3. [Поисковых запросов по вашим товарам](./analytics#tag/searchQueriesForYourItems) 4. [Истории остатков](./analytics#tag/stocksReport) 5. [Оценки товара](./analytics#tag/itemRating) 6. [Аналитики продавца в формате CSV](./analytics#tag/sellerAnalyticsCsv)

Версия спеки: `analytics` · методов: **20**

Источник: https://dev.wildberries.ru/docs/openapi/analytics

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v2/nm-report/downloads/file/{downloadId}` | sellerAnalyticsCsv | [Получить отчёт{{ /api/v2/nm-report/downloads/file/{downloadId} }}](selleranalyticscsv/get-api-v2-nm-report-downloads-file-downloadid.md) |
| `GET` | `/api/v2/nm-report/downloads` | sellerAnalyticsCsv | [Получить список отчётов{{ /api/v2/nm-report/downloads }}](selleranalyticscsv/get-api-v2-nm-report-downloads.md) |
| `POST` | `/api/analytics/v1/order-feed` | orderFeed | [Получить отчёт{{ /api/analytics/v1/order-feed }}](orderfeed/post-api-analytics-v1-order-feed.md) |
| `POST` | `/api/analytics/v1/stocks-report/seller-warehouses` | stocksReport | [Остатки на складах продавца{{ /api/analytics/v1/stocks-report/seller-warehouses }}](stocksreport/post-api-analytics-v1-stocks-report-seller-warehouses.md) |
| `POST` | `/api/analytics/v1/stocks-report/wb-warehouses` | stocksReport | [Остатки на складах WB{{ /api/analytics/v1/stocks-report/wb-warehouses }}](stocksreport/post-api-analytics-v1-stocks-report-wb-warehouses.md) |
| `POST` | `/api/analytics/v2/item-rating` | itemRating | [Получить отчёт{{ /api/analytics/v2/item-rating }}](itemrating/post-api-analytics-v2-item-rating.md) |
| `POST` | `/api/analytics/v3/sales-funnel/grouped/history` | salesFunnel | [Статистика групп карточек товаров по дням{{ /api/analytics/v3/sales-funnel/grouped/history }}](salesfunnel/post-api-analytics-v3-sales-funnel-grouped-history.md) |
| `POST` | `/api/analytics/v3/sales-funnel/products/history` | salesFunnel | [Статистика карточек товаров по дням{{ /api/analytics/v3/sales-funnel/products/history }}](salesfunnel/post-api-analytics-v3-sales-funnel-products-history.md) |
| `POST` | `/api/analytics/v3/sales-funnel/products` | salesFunnel | [Статистика карточек товаров за период{{ /api/analytics/v3/sales-funnel/products }}](salesfunnel/post-api-analytics-v3-sales-funnel-products.md) |
| `POST` | `/api/v2/nm-report/downloads/retry` | sellerAnalyticsCsv | [Сгенерировать отчёт повторно{{ /api/v2/nm-report/downloads/retry }}](selleranalyticscsv/post-api-v2-nm-report-downloads-retry.md) |
| `POST` | `/api/v2/nm-report/downloads` | sellerAnalyticsCsv | [Создать отчёт{{ /api/v2/nm-report/downloads }}](selleranalyticscsv/post-api-v2-nm-report-downloads.md) |
| `POST` | `/api/v2/search-report/product/orders` | searchQueriesForYourItems | [Заказы и позиции по поисковым запросам товара{{ /api/v2/search-report/product/orders }}](searchqueriesforyouritems/post-api-v2-search-report-product-orders.md) |
| `POST` | `/api/v2/search-report/product/search-texts` | searchQueriesForYourItems | [Поисковые запросы по товару{{ /api/v2/search-report/product/search-texts }}](searchqueriesforyouritems/post-api-v2-search-report-product-search-texts.md) |
| `POST` | `/api/v2/search-report/report` | searchQueriesForYourItems | [Основная страница{{ /api/v2/search-report/report }}](searchqueriesforyouritems/post-api-v2-search-report-report.md) |
| `POST` | `/api/v2/search-report/table/details` | searchQueriesForYourItems | [Пагинация по товарам в группе{{ /api/v2/search-report/table/details }}](searchqueriesforyouritems/post-api-v2-search-report-table-details.md) |
| `POST` | `/api/v2/search-report/table/groups` | searchQueriesForYourItems | [Пагинация по группам{{ /api/v2/search-report/table/groups }}](searchqueriesforyouritems/post-api-v2-search-report-table-groups.md) |
| `POST` | `/api/v2/stocks-report/offices` | stocksReport | [Данные по складам{{ /api/v2/stocks-report/offices }}](stocksreport/post-api-v2-stocks-report-offices.md) |
| `POST` | `/api/v2/stocks-report/products/groups` | stocksReport | [Данные по группам{{ /api/v2/stocks-report/products/groups }}](stocksreport/post-api-v2-stocks-report-products-groups.md) |
| `POST` | `/api/v2/stocks-report/products/products` | stocksReport | [Данные по товарам{{ /api/v2/stocks-report/products/products }}](stocksreport/post-api-v2-stocks-report-products-products.md) |
| `POST` | `/api/v2/stocks-report/products/sizes` | stocksReport | [Данные по размерам{{ /api/v2/stocks-report/products/sizes }}](stocksreport/post-api-v2-stocks-report-products-sizes.md) |
