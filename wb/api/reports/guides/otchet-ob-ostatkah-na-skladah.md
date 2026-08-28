---
title: Отчёт об остатках на складах
api: wb-reports
tag: warehousesInventoryReport
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/reports"
content_sha: b8fe43d41dde980f
---

# Отчёт об остатках на складах

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

 Узнать больше об отчётах по остаткам на складах можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-244?categoryId=5f2162c5-069b-416d-a4e1-48da2a76e6b0)

Чтобы получить отчёт об [остатках на складах WB](https://seller.wildberries.ru/analytics-reports/warehouse-remains):
 1. [Создайте отчёт](./reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemains).
 2. Дождитесь, когда отчёт будет готов. Вы можете [проверить статус](./reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemainsTasksTaskIdStatus) готовности отчёта. Готовый отчёт хранится 2 часа.
 3. [Получите отчёт](./reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemainsTasksTaskIdDownload).
