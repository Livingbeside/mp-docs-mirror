---
title: Идентификаторы маркировки FBS
api: wb-orders-fbs
tag: fbsLabelIdentifiers
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: 78df2bf44e44e43e
---

# Идентификаторы маркировки FBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать больше об идентификаторах маркировки можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-305?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345), а так же в [инструкции по работе с маркировкой](/knowledge-base/articles/019e9273-118b-7b69-a25a-ea1d756f05d9/rabota-s-markirovkoi-po-modeli-fbs).

С помощью этих методов вы можете [получить](./orders-fbs#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta), [удалить](./orders-fbs#tag/fbsLabelIdentifiers/operation/deleteV3OrdersOrderIdMeta) и отредактировать идентификаторы маркировки [сборочных заданий](./orders-fbs#tag/fbsAssemblyOrders):
 - [Код маркировки Честного знака](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaSgtin)
 - [УИН](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaUin)
 - [IMEI](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaImei)
 - [GTIN](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaGtin)
 - [Срок годности товара](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaExpiration)
 - [Номер ДТ](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaCustomsDeclaration)

Заполнять идентификаторы маркировки сборочных заданий в песочнице необязательно
