---
title: Идентификаторы маркировки FBS
api: wb-orders-fbs
tag: fbsLabelIdentifiers
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: 96f9d3d444d24234
---

# Идентификаторы маркировки FBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать больше об идентификаторах маркировки можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-305?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345), а так же в [инструкции по работе с маркировкой](/knowledge-base/articles/019e9273-118b-7b69-a25a-ea1d756f05d9/rabota-s-markirovkoi-po-modeli-fbs).

С помощью этих методов вы можете [получить](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post), [удалить](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta/delete) и отредактировать идентификаторы маркировки [сборочных заданий](./orders-fbs#tag/Sborochnye-zadaniya-FBS):
 - [Код маркировки Честного знака](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1sgtin/put)
 - [УИН](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1uin/put)
 - [IMEI](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1imei/put)
 - [GTIN](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1gtin/put)
 - [Срок годности товара](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1expiration/put)
 - [Номер ДТ](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1%7BorderId%7D~1meta~1customs-declaration/put)

Заполнять идентификаторы маркировки сборочных заданий в песочнице необязательно
