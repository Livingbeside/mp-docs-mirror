---
title: Операции при приёмке
api: wb-reports
tag: acceptanceExpenses
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/reports"
content_sha: eaf709d0568ee484
---

# Операции при приёмке

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

Чтобы получить отчёт об [операциях при приёмке](https://seller.wildberries.ru/analytics-reports/acceptance-report):
 1. [Создайте отчёт](./reports#tag/acceptanceExpenses/operation/getV1AcceptanceReport).
 2. Дождитесь, когда отчёт будет готов. Вы можете [проверить статус](./reports#tag/acceptanceExpenses/operation/getV1AcceptanceReportTasksTaskIdStatus) готовности отчёта. Готовый отчёт хранится 2 часа.
 3. [Получите отчёт](./reports#tag/acceptanceExpenses/operation/getV1AcceptanceReportTasksTaskIdDownload).
