---
title: Аналитика продавца CSV
api: wb-analytics
tag: sellerAnalyticsCsv
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/analytics"
content_sha: eb2ba529170dc7cf
---

# Аналитика продавца CSV

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

s

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a3-f76b-7f22-82f3-54930b8f59e8) по работе с Аналитикой продавца CSV

Чтобы получить отчёт:
 1. Сгенерируйте его с помощью метода [создания отчёта](./analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads).
 2. Дождитесь, когда отчёт будет готов. Вы можете проверить статус готовности через [получение списка отчётов](./analytics#tag/sellerAnalyticsCsv/operation/getV2NmReportDownloads). Готовый отчёт хранится 48 часов.

 Если вы получили статус `FAILED`, [сгенерируйте отчёт повторно](./analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloadsRetry).
 3. [Получите отчёт](./analytics#tag/sellerAnalyticsCsv/operation/getV2NmReportDownloadsFileDownloadId).

Можно получить отчёт максимум за год. Отчёты по остаткам — за 3 месяца.

Максимальное количество отчётов, генерируемых в сутки — 20.

 Вы можете использовать эти методы — за исключением отчётов по остаткам — только с подпиской Джем
