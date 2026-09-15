---
title: Идентификаторы маркировки DBS
api: wb-dbs
tag: dbsLabelIdentifiers
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/dbs"
content_sha: f3e33dfad7a197f2
---

# Идентификаторы маркировки DBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a3-ff7d-70ba-a872-828430b24ea1/zakazy-dbs) по работе с заказами DBS

 Узнать больше об идентификаторах маркировки можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-305?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345)

С помощью этих методов вы можете [получать](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails), [удалять](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDelete) и редактировать идентификаторы маркировки [сборочных заданий](./dbs#tag/dbsAssemblyOrders):
 - [Код маркировки Честного знака](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaSgtin)
 - [УИН](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaUin)
 - [IMEI](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei)
 - [GTIN](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaGtin)
 - [Номера ДТ и коды стран происхождения товара](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration)

Заполнять идентификаторы маркировки сборочных заданий в песочнице необязательно
