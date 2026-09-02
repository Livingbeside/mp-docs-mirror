---
title: Документы и бухгалтерия — все методы
api: wb-documents-and-accounting
spec_version: finances
operations: 11
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
content_sha: d48385f0e1748c1e
---

# Документы и бухгалтерия

Узнать больше о документах и бухгалтерии можно в [справочном центре](https://seller.wildberries.ru/instructions/category/ba929b64-1f89-4426-82d7-ce998ee552bd?goBackOption=prevRoute&categoryId=3c971375-9939-45e8-ab82-376019be8942)

Просмотр [баланса](./financial-reports-and-accounting#tag/balance), [финансовых отчётов](./financial-reports-and-accounting#tag/financialReports) и [документов](./financial-reports-and-accounting#tag/documents) продавца.

Версия спеки: `finances` · методов: **11** · разделов справки: **4**

Источник: https://dev.wildberries.ru/docs/openapi/documents-and-accounting

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v1/account/balance` | balance | [Получить баланс продавца](balance/get-api-v1-account-balance.md) |
| `GET` | `/api/v1/documents/categories` | documents | [Категории документов](documents/get-api-v1-documents-categories.md) |
| `GET` | `/api/v1/documents/download` | documents | [Получить документ](documents/get-api-v1-documents-download.md) |
| `GET` | `/api/v1/documents/list` | documents | [Список документов](documents/get-api-v1-documents-list.md) |
| `POST` | `/api/finance/v1/acquiring/detailed/{reportId}` | financialReports | [Детализации к отчётам об издержках на приём платежей по ID отчётов{{ /api/finance/v1/acquiring/detailed/{reportId} }}](financialreports/post-api-finance-v1-acquiring-detailed-reportid.md) |
| `POST` | `/api/finance/v1/acquiring/detailed` | financialReports | [Детализации к отчётам об издержках на приём платежей за период](financialreports/post-api-finance-v1-acquiring-detailed.md) |
| `POST` | `/api/finance/v1/acquiring/list` | financialReports | [Список отчётов об издержках на приём платежей](financialreports/post-api-finance-v1-acquiring-list.md) |
| `POST` | `/api/finance/v1/sales-reports/detailed/{reportId}` | financialReports | [Детализации к отчётам реализации по ID отчётов{{ /api/finance/v1/sales-reports/detailed/{reportId} }}](financialreports/post-api-finance-v1-sales-reports-detailed-reportid.md) |
| `POST` | `/api/finance/v1/sales-reports/detailed` | financialReports | [Детализации к отчётам реализации за период](financialreports/post-api-finance-v1-sales-reports-detailed.md) |
| `POST` | `/api/finance/v1/sales-reports/list` | financialReports | [Список отчётов реализации](financialreports/post-api-finance-v1-sales-reports-list.md) |
| `POST` | `/api/v1/documents/download/all` | documents | [Получить документы](documents/post-api-v1-documents-download-all.md) |
