---
title: История остатков
api: wb-analytics
tag: stocksReport
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/analytics"
content_sha: 58620033a36bca1a
---

# История остатков

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019ef14c-c72d-717a-9fc2-b0b2f361dc80) по работе с Историей остатков

 Узнать больше об аналитике остатков можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/material/stock-history-report)

Это информация из детализированной таблицы товаров и виджета детализации по регионам.

Остатки в ответах данных методов — на текущий день.

 Чтобы получать остатки по дням за период до 3 месяцев от текущей даты, используйте методы Аналитика продавца CSV — тип отчёта STOCK_HISTORY_DAILY_CSV

Методы получения [отчёта по статистике остатков](https://seller.wildberries.ru/content-analytics/history-remains):
 1. Текущих [остатков на складах WB](./analytics#tag/stocksReport/operation/postV1StocksReportWbWarehouses) по размерам
 2. Данных по таблице товаров с агрегацией по [группам](./analytics#tag/stocksReport/operation/postV2StocksReportProductsGroups), [товарам](./analytics#tag/stocksReport/operation/postV2StocksReportProductsProducts), [размерам](./analytics#tag/stocksReport/operation/postV2StocksReportProductsSizes)
 3. Данных виджета **Статистика по регионам отгрузки** с детализацией по [складам](./analytics#tag/stocksReport/operation/postV2StocksReportOffices)
