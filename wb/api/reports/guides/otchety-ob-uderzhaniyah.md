---
title: Отчёты об удержаниях
api: wb-reports
tag: retentionReports
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/reports"
content_sha: bae70ed88e6e9715
---

# Отчёты об удержаниях

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

 Узнать больше об отчётах об удержаниях можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-247?categoryId=5f2162c5-069b-416d-a4e1-48da2a76e6b0)

Методы загрузки отчётов об [удержаниях](https://seller.wildberries.ru/analytics-reports/dimensions-penalties):
 1. [Удержания за занижение габаритов упаковки](./reports#tag/retentionReports/operation/getV1MeasurementPenalties)
 2. [Замеры склада](./reports#tag/retentionReports/operation/getV1WarehouseMeasurements)
 2. [Подмены и неверные вложения](./reports#tag/retentionReports/operation/getV1Deductions)
 3. [Самовыкупы](./reports#tag/retentionReports/operation/getV1AnalyticsAntifraudDetails)
 4. [Маркировка товара](./reports#tag/retentionReports/operation/getV1AnalyticsGoodsLabeling)
