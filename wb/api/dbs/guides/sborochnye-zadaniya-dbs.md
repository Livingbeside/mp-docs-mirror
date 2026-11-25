---
title: Сборочные задания DBS
api: wb-dbs
tag: dbsAssemblyOrders
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/dbs"
content_sha: 2af3663069fa3dc6
---

# Сборочные задания DBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a3-ff7d-70ba-a872-828430b24ea1/zakazy-dbs) по работе с заказами DBS

 Узнать больше о сборочных заданиях DBS можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-108?goBackOption=prevRoute&categoryId=0fc94a39-22b1-4a54-8ef2-06dac1d8137b)

Порядок работы со сборочными заданиями DBS:
1. [Получите новое сборочное задание](./dbs#tag/dbsAssemblyOrders/operation/getV3DbsOrdersNew) и сохраните информацию о нём до перевода на сборку. Если вы не сохраните данные, вы сможете получить их только после отмены или продажи заказа. Проверяйте [дату и время доставки](./dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersDeliveryDate).
2. [Переведите сборочное задание на сборку](./dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusConfirm).
3. Получите [информацию о покупателе](./dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersClient).
3. [Переведите сборочное задание в доставку](./dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusDeliver).
4. Сообщите, что покупатель [принял заказ](./dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusReceive) или [отказался от заказа](./dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusReject).
