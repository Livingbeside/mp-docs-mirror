---
title: Финансовые отчёты
api: wb-documents-and-accounting
tag: financialReports
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
content_sha: de98b473cd957cfb
---

# Финансовые отчёты

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Финансы

 Узнать больше о финансовых отчётах можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/subcategory/financial-reports)

Методы получения:
 1. [Списка](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsList) отчётов реализации и детализаций к отчётам по [ID](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) и за [период](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed)
 2. [Списка](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringList) отчётов об издержках на приём платежей и детализаций к отчётам по [ID](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) и за [период](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed). Доступно только для продавцов из России

 Вы можете выгрузить данные в [Google Таблицы](/knowledge-base/articles/019d49a4-650c-7b04-9596-ba441936f9d3)
