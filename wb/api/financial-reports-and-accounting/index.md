---
title: Документы и бухгалтерия — все методы
api: wb-financial-reports-and-accounting
spec_version: finances
operations: 11
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
content_sha: b798ed58577fcef1
---

# Документы и бухгалтерия

Узнать больше о документах и бухгалтерии можно в справочном центре Просмотр [баланса](./financial-reports-and-accounting#tag/balance), [финансовых отчётов](./financial-reports-and-accounting#tag/financialReports) и [документов](./financial-reports-and-accounting#tag/documents) продавца.

Версия спеки: `finances` · методов: **11**

Источник: https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v1/account/balance` | balance | [Получить баланс продавца{{ /api/v1/account/balance }}](balance/get-api-v1-account-balance.md) |
| `GET` | `/api/v1/documents/categories` | documents | [Категории документов{{ /api/v1/documents/categories }}](documents/get-api-v1-documents-categories.md) |
| `GET` | `/api/v1/documents/download` | documents | [Получить документ{{ /api/v1/documents/download }}](documents/get-api-v1-documents-download.md) |
| `GET` | `/api/v1/documents/list` | documents | [Список документов{{ /api/v1/documents/list }}](documents/get-api-v1-documents-list.md) |
| `POST` | `/api/finance/v1/acquiring/detailed/{reportId}` | financialReports | [Детализации к отчётам об издержках на приём платежей по ID отчётов{{ /api/finance/v1/acquiring/detailed/{reportId} }}](financialreports/post-api-finance-v1-acquiring-detailed-reportid.md) |
| `POST` | `/api/finance/v1/acquiring/detailed` | financialReports | [Детализации к отчётам об издержках на приём платежей за период{{ /api/finance/v1/acquiring/detailed }}](financialreports/post-api-finance-v1-acquiring-detailed.md) |
| `POST` | `/api/finance/v1/acquiring/list` | financialReports | [Список отчётов об издержках на приём платежей{{ /api/finance/v1/acquiring/list }}](financialreports/post-api-finance-v1-acquiring-list.md) |
| `POST` | `/api/finance/v1/sales-reports/detailed/{reportId}` | financialReports | [Детализации к отчётам реализации по ID отчётов{{ /api/finance/v1/sales-reports/detailed/{reportId} }}](financialreports/post-api-finance-v1-sales-reports-detailed-reportid.md) |
| `POST` | `/api/finance/v1/sales-reports/detailed` | financialReports | [Детализации к отчётам реализации за период{{ /api/finance/v1/sales-reports/detailed }}](financialreports/post-api-finance-v1-sales-reports-detailed.md) |
| `POST` | `/api/finance/v1/sales-reports/list` | financialReports | [Список отчётов реализации{{ /api/finance/v1/sales-reports/list }}](financialreports/post-api-finance-v1-sales-reports-list.md) |
| `POST` | `/api/v1/documents/download/all` | documents | [Получить документы{{ /api/v1/documents/download/all }}](documents/post-api-v1-documents-download-all.md) |
