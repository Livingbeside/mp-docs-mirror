---
title: Сборочные задания DBS
api: wb-orders-dbs
tag: dbsAssemblyOrders
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
content_sha: d3290e1012901426
---

# Сборочные задания DBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a3-ff7d-70ba-a872-828430b24ea1/zakazy-dbs) по работе с заказами DBS

 Узнать больше о сборочных заданиях DBS можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-108?goBackOption=prevRoute&categoryId=0fc94a39-22b1-4a54-8ef2-06dac1d8137b)

Для работы со сборочными заданиями DBS:
1. [Получите новое сборочное задание](./orders-dbs#tag/dbsAssemblyOrders/operation/getV3DbsOrdersNew) и сохраните его до перевода на сборку. Если вы не сохраните информацию о сборочном задании заранее, вы сможете получить ее только после завершения задания (отмены или продажи). Проверяйте [дату и время доставки](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersDeliveryDate).
2. [Переведите его на сборку](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusConfirm).
3. После перевода на сборку для заказа становится доступной [информация о покупателе](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersClient) (имя, телефон).
4. [Переведите в доставку](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusDeliver).
5. После доставки задания покупателю вам необходимо сообщить на наш сервер, что [сборочное задание принято](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusReceive) покупателем или, что [покупатель отказался от сборочного задания](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusReject).
