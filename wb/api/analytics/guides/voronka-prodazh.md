---
title: Воронка продаж
api: wb-analytics
tag: salesFunnel
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/analytics"
content_sha: 430c0ed3427fd5bf
---

# Воронка продаж

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Аналитика

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a3-fb9a-7c0c-9372-17d880f74ff9) по работе с Воронкой продаж

 Узнать больше об аналитике воронки продаж можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/material/sales-funnel-report)

Методы получения [статистики](https://seller.wildberries.ru/content-analytics/interactive-report/main):
 1. [Карточек товаров за период](./analytics#tag/salesFunnel/operation/postV3SalesFunnelProducts)
 2. [Карточек товаров по дням](./analytics#tag/salesFunnel/operation/postV3SalesFunnelProductsHistory)
 3. [Групп карточек товаров по дням](./analytics#tag/salesFunnel/operation/postV3SalesFunnelGroupedHistory)

 Таймзоны представлены в формате IANA, актуальный список можно посмотреть [здесь](https://nodatime.org/TimeZones)
