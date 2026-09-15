---
title: Сборочные задания DBW
api: wb-orders-dbw
tag: dbwAssemblyOrders
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
content_sha: 4afb89c56b62006d
---

# Сборочные задания DBW

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

Для работы со сборочными заданиями DBW:
1. [Получите новое сборочное задание](./orders-dbw#tag/dbwAssemblyOrders/operation/getV3DbwOrdersNew).
2. [Переведите его на сборку](./orders-dbw#tag/dbwAssemblyOrders/operation/patchV3DbwOrdersOrderIdConfirm).
3. После перевода на сборку для заказа становится доступной [информация о курьере](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersCourier) (телефон, номер автомобиля).

Чтобы курьер мог связаться с вами [привяжите](./item-management#tag/sellerWarehouses/operation/putV3DbwWarehousesWarehouseIdContacts) свои контакты к складу. Вы так же можете [получить](./item-management#tag/sellerWarehouses/operation/getV3DbwWarehousesWarehouseIdContacts) текущий список своих контактов.
4. [Получите](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStickers), распечатайте и прикрепите стикеры.
5. [Переведите сборочное задание в доставку](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatusDeliver).
6. Дождитесь курьера.
7. Курьер забирает заказ и отвозит клиенту.
8. Клиент принимает заказ или отказывается от него.
9. Если клиент принимает заказ, курьер переводит сборочное задание в статус `receive`. Если отказывается — в `reject`.

 
 Узнать больше о сборочных заданиях DBW можно в [справочном центре](https://seller.wildberries.ru/help-center/category/01956ff5-e134-74f3-a798-24b6b49a403b)
