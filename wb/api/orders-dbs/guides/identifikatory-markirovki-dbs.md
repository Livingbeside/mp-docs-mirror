---
title: Идентификаторы маркировки DBS
api: wb-orders-dbs
tag: dbsLabelIdentifiers
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
content_sha: bfef86a6beb7aa01
---

# Идентификаторы маркировки DBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a3-ff7d-70ba-a872-828430b24ea1/zakazy-dbs) по работе с заказами DBS

 Узнать больше об идентификаторах маркировки можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-305?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345)

С помощью этих методов вы можете [получать](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails), [удалять](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDelete) и редактировать идентификаторы маркировки [сборочных заданий](./orders-dbs#tag/dbsAssemblyOrders):
 - [Код маркировки Честного знака](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaSgtin)
 - [УИН](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaUin)
 - [IMEI](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei)
 - [GTIN](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaGtin)
 - [Номера ДТ и коды стран происхождения товара](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration)

Заполнять идентификаторы маркировки сборочных заданий в песочнице необязательно
