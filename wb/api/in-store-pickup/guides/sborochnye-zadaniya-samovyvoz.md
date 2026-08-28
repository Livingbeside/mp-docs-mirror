---
title: Сборочные задания Самовывоз
api: wb-in-store-pickup
tag: inStorePickupAssemblyOrders
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
content_sha: dd150814e7a19ea7
---

# Сборочные задания Самовывоз

Для доступа к методам используйте [токен](/openapi/api-information#tag/authorization) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-16d3-7b8c-b42a-026b566a8e29/samovyvoz) по работе с заказами Самовывоз

Порядок работы:
1. [Получите новое сборочное задание](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/getV3ClickCollectOrdersNew)
2. [Переведите его на сборку](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusConfirm)
3. После этого для задания становится доступной [информация по покупателю](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersClient) (имя, телефон)
4. После сборки [сообщите, что сборочное задание готово к выдаче](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusPrepare)
5. После того как сборочное задание получит статус `Готово к выдаче`, вы можете проверить, [принадлежит ли это сборочное задание покупателю](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersClientIdentity).
6. После доставки задания покупателю вам необходимо сообщить на наш сервер, что [заказ принят покупателем](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusReceive) или что [покупатель отказался от заказа](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusReject)
