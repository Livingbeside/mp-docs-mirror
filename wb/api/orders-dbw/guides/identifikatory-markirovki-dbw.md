---
title: Идентификаторы маркировки DBW
api: wb-orders-dbw
tag: dbwLabelIdentifiers
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
content_sha: a13d0ec192e3e9f2
---

# Идентификаторы маркировки DBW

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать больше об идентификаторах маркировки можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-305?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345)

С помощью этих методов вы можете [получать](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails), [удалять](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDelete) и редактировать идентификаторы маркировки [сборочных заданий](./orders-dbw#tag/dbwAssemblyOrders):
 - [Код маркировки Честного знака](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaSgtin)
 - [УИН](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaUin)
 - [IMEI](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei)
 - [GTIN](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaGtin)
