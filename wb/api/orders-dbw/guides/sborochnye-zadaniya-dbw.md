---
title: Сборочные задания DBW
api: wb-orders-dbw
tag: dbwAssemblyOrders
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
content_sha: 92067542346eca98
---

# Сборочные задания DBW

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

Для работы со сборочными заданиями DBW:
1. [Получите новое сборочное задание](./orders-dbw#tag/dbwAssemblyOrders/operation/getV3DbwOrdersNew).
2. [Переведите его на сборку](./orders-dbw#tag/dbwAssemblyOrders/operation/patchV3DbwOrdersOrderIdConfirm).
3. После перевода на сборку для заказа становится доступной [информация о курьере](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersCourier) (телефон, номер автомобиля).

Чтобы курьер мог связаться с вами [привяжите](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1dbw~1warehouses~1%7BwarehouseId%7D~1contacts/put) свои контакты к складу. Вы так же можете [получить](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1dbw~1warehouses~1%7BwarehouseId%7D~1contacts/get) текущий список своих контактов.
4. [Получите](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStickers), распечатайте и прикрепите стикеры.
5. [Переведите сборочное задание в доставку](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatusDeliver).
6. Дождитесь курьера.
7. Курьер забирает заказ и отвозит клиенту.
8. Клиент принимает заказ или отказывается от него.
9. Если клиент принимает заказ, курьер переводит сборочное задание в статус `receive`. Если отказывается — в `reject`.

 
 Узнать больше о сборочных заданиях DBW можно в [справочном центре](https://seller.wildberries.ru/help-center/category/01956ff5-e134-74f3-a798-24b6b49a403b)
