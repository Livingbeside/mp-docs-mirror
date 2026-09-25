---
title: Отчёты — все методы
api: wb-reports
spec_version: reports
operations: 24
source: "https://dev.wildberries.ru/docs/openapi/reports"
content_sha: 0730c9da102a7fce
---

# Отчёты

Узнать больше об отчётах можно в [справочном центре](https://seller.wildberries.ru/instructions/subcategory/5f2162c5-069b-416d-a4e1-48da2a76e6b0)

С помощью этих методов вы можете получать [основные отчёты](./reports#tag/mainReports) и отчёты о:
 1. [Остатках на складах](./reports#tag/warehousesInventoryReport)
 2. [Товарах с обязательной маркировкой](./reports#tag/reportOnItemsWithMandatoryLabeling)
 3. [Удержаниях](./reports#tag/retentionReports)
 4. [Операциях при приёмке](./reports#tag/acceptanceExpenses)
 5. [Платном хранении](./reports#tag/paidStorage)
 6. [Продажах по регионам](./reports#tag/salesByRegions)
 7. [Доле бренда в продажах](./reports#tag/shareOfBrandInSales)
 8. [Заблокированных карточках](./reports#tag/blockedItems)
 9. [Возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport)

Версия спеки: `reports` · методов: **24** · разделов справки: **11**

Источник: https://dev.wildberries.ru/docs/openapi/reports

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/analytics/v1/deductions` | retentionReports | [Подмены и неверные вложения](retentionreports/get-api-analytics-v1-deductions.md) |
| `GET` | `/api/analytics/v1/item-returns` | returnsAndItemMovementReport | [Получить отчёт](returnsanditemmovementreport/get-api-analytics-v1-item-returns.md) |
| `GET` | `/api/analytics/v1/measurement-penalties` | retentionReports | [Удержания за занижение габаритов упаковки](retentionreports/get-api-analytics-v1-measurement-penalties.md) |
| `GET` | `/api/analytics/v1/warehouse-measurements` | retentionReports | [Замеры склада](retentionreports/get-api-analytics-v1-warehouse-measurements.md) |
| `GET` | `/api/v1/acceptance_report/tasks/{task_id}/download` | acceptanceExpenses | [Получить отчёт{{ /api/v1/acceptance_report/tasks/{task_id}/download }}](acceptanceexpenses/get-api-v1-acceptance-report-tasks-task-id-download.md) |
| `GET` | `/api/v1/acceptance_report/tasks/{task_id}/status` | acceptanceExpenses | [Проверить статус{{ /api/v1/acceptance_report/tasks/{task_id}/status }}](acceptanceexpenses/get-api-v1-acceptance-report-tasks-task-id-status.md) |
| `GET` | `/api/v1/acceptance_report` | acceptanceExpenses | [Создать отчёт](acceptanceexpenses/get-api-v1-acceptance-report.md) |
| `GET` | `/api/v1/analytics/antifraud-details` | retentionReports | [Самовыкупы](retentionreports/get-api-v1-analytics-antifraud-details.md) |
| `GET` | `/api/v1/analytics/banned-products/blocked` | blockedItems | [Получить отчёт](blockeditems/get-api-v1-analytics-banned-products-blocked.md) |
| `GET` | `/api/v1/analytics/brand-share/brands` | shareOfBrandInSales | [Бренды продавца](shareofbrandinsales/get-api-v1-analytics-brand-share-brands.md) |
| `GET` | `/api/v1/analytics/brand-share/parent-subjects` | shareOfBrandInSales | [Родительские категории бренда](shareofbrandinsales/get-api-v1-analytics-brand-share-parent-subjects.md) |
| `GET` | `/api/v1/analytics/brand-share` | shareOfBrandInSales | [Получить отчёт](shareofbrandinsales/get-api-v1-analytics-brand-share.md) |
| `GET` | `/api/v1/analytics/goods-labeling` | retentionReports | [Маркировка товара](retentionreports/get-api-v1-analytics-goods-labeling.md) |
| `GET` | `/api/v1/analytics/goods-return` | returnsAndItemMovementReport | [Получить отчёт](returnsanditemmovementreport/get-api-v1-analytics-goods-return.md) |
| `GET` | `/api/v1/analytics/region-sale` | salesByRegions | [Получить отчёт](salesbyregions/get-api-v1-analytics-region-sale.md) |
| `GET` | `/api/v1/paid_storage/tasks/{task_id}/download` | paidStorage | [Получить отчёт{{ /api/v1/paid_storage/tasks/{task_id}/download }}](paidstorage/get-api-v1-paid-storage-tasks-task-id-download.md) |
| `GET` | `/api/v1/paid_storage/tasks/{task_id}/status` | paidStorage | [Проверить статус{{ /api/v1/paid_storage/tasks/{task_id}/status }}](paidstorage/get-api-v1-paid-storage-tasks-task-id-status.md) |
| `GET` | `/api/v1/paid_storage` | paidStorage | [Создать отчёт](paidstorage/get-api-v1-paid-storage.md) |
| `GET` | `/api/v1/supplier/orders` | mainReports | [Заказы](mainreports/get-api-v1-supplier-orders.md) |
| `GET` | `/api/v1/supplier/sales` | mainReports | [Продажи](mainreports/get-api-v1-supplier-sales.md) |
| `GET` | `/api/v1/warehouse_remains/tasks/{task_id}/download` | warehousesInventoryReport | [Получить отчёт{{ /api/v1/warehouse_remains/tasks/{task_id}/download }}](warehousesinventoryreport/get-api-v1-warehouse-remains-tasks-task-id-download.md) |
| `GET` | `/api/v1/warehouse_remains/tasks/{task_id}/status` | warehousesInventoryReport | [Проверить статус{{ /api/v1/warehouse_remains/tasks/{task_id}/status }}](warehousesinventoryreport/get-api-v1-warehouse-remains-tasks-task-id-status.md) |
| `GET` | `/api/v1/warehouse_remains` | warehousesInventoryReport | [Создать отчёт](warehousesinventoryreport/get-api-v1-warehouse-remains.md) |
| `POST` | `/api/v1/analytics/excise-report` | reportOnItemsWithMandatoryLabeling | [Получить отчёт](reportonitemswithmandatorylabeling/post-api-v1-analytics-excise-report.md) |
