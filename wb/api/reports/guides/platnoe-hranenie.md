---
title: Платное хранение
api: wb-reports
tag: paidStorage
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/reports"
content_sha: 08066f3d0e589ce6
---

# Платное хранение

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

 Узнать больше об отчётах о платном хранении можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-242?categoryId=5f2162c5-069b-416d-a4e1-48da2a76e6b0)

Чтобы получить отчёт о [платном хранении](https://seller.wildberries.ru/analytics-reports/paid-storage/storage):
 1. [Создайте отчёт](./reports#tag/paidStorage/operation/getV1PaidStorage).
 2. Дождитесь, когда отчёт будет готов. Вы можете [проверить статус](./reports#tag/paidStorage/operation/getV1PaidStorageTasksTaskIdStatus) готовности отчёта. Готовый отчёт хранится 2 часа, после чего его нельзя будет получить.
 3. [Получите отчёт](./reports#tag/paidStorage/operation/getV1PaidStorageTasksTaskIdDownload).
