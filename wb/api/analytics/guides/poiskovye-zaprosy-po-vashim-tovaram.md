---
title: Поисковые запросы по вашим товарам
api: wb-analytics
tag: searchQueriesForYourItems
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/analytics"
content_sha: f6f73a8508032b43
---

# Поисковые запросы по вашим товарам

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-0f6a-70bb-a87b-c1237a1a0714) по работе с Поисковыми запросами по вашим товарам

 Узнать больше об аналитике поисковых запросов можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/material/search-queries-report)

Методы получения [отчёта по поисковым запросам по вашим товарам](https://seller.wildberries.ru/search-analytics/my-search-queries), в частности:
 1. [Основной страницы](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportReport)
 2. Дополнительных данных к основной странице с [пагинацией по группам](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportTableGroups) или [пагинацией по товарам в группе](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportTableDetails)
 3. [Поисковых запросов по товару](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportProductSearchTexts)
 4. [Заказов и позиций по поисковым запросам товара](./analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportProductOrders)

 Вы можете использовать эти методы только с подпиской Джем
