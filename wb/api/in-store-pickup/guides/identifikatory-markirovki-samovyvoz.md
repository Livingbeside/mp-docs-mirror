---
title: Идентификаторы маркировки Самовывоз
api: wb-in-store-pickup
tag: inStorePickupLabelIdentifiers
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
content_sha: 1386a17b3bfccafe
---

# Идентификаторы маркировки Самовывоз

Для доступа к методам используйте [токен](/openapi/api-information#tag/authorization) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-16d3-7b8c-b42a-026b566a8e29/samovyvoz) по работе с заказами Самовывоз

С помощью этих методов вы можете [получать](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails), [удалять](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDelete) и редактировать идентификаторы маркировки сборочных заданий:
 - [Код маркировки Честного знака](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaSgtin)
 - [УИН](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaUin)
 - [IMEI](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaImei)
 - [GTIN](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaGtin)
 - [Номера ДТ и коды стран происхождения товара](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration)

Заполнять идентификаторы маркировки сборочных заданий в песочнице необязательно
