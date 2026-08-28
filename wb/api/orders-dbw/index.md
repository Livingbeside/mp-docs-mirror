---
title: Заказы DBW — все методы
api: wb-orders-dbw
spec_version: ordersdbw
operations: 16
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
content_sha: 602effd475b646e8
---

# Заказы DBW

С помощью методов Заказы DBW (Доставка курьером WB) вы можете:
 - получать информацию о [сборочных заданиях](./orders-dbw#tag/dbwAssemblyOrders), управлять статусами и отменять сборочные задания
 - получать, добавлять, редактировать и удалять [метаданные](./orders-dbw#tag/dbwLabelIdentifiers) сборочных заданий

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-036a-7721-98e8-bed5f1a4f72d/zakazy-dbw) по работе с заказами DBW

Версия спеки: `ordersdbw` · методов: **16** · разделов справки: **3**

Источник: https://dev.wildberries.ru/docs/openapi/orders-dbw

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v3/dbw/orders/new` | dbwAssemblyOrders | [Получить список новых сборочных заданий](dbwassemblyorders/get-api-v3-dbw-orders-new.md) |
| `GET` | `/api/v3/dbw/orders` | dbwAssemblyOrders | [Получить информацию о завершенных сборочных заданиях](dbwassemblyorders/get-api-v3-dbw-orders.md) |
| `PATCH` | `/api/v3/dbw/orders/{orderId}/cancel` | dbwAssemblyOrders | [Отменить сборочное задание{{ /api/v3/dbw/orders/{orderId}/cancel }}](dbwassemblyorders/patch-api-v3-dbw-orders-orderid-cancel.md) |
| `PATCH` | `/api/v3/dbw/orders/{orderId}/confirm` | dbwAssemblyOrders | [Перевести на сборку{{ /api/v3/dbw/orders/{orderId}/confirm }}](dbwassemblyorders/patch-api-v3-dbw-orders-orderid-confirm.md) |
| `POST` | `/api/marketplace/v3/dbw/orders/client` | dbwAssemblyOrders | [Информация о покупателе](dbwassemblyorders/post-api-marketplace-v3-dbw-orders-client.md) |
| `POST` | `/api/marketplace/v3/dbw/orders/meta/delete` | dbwLabelIdentifiers | [Удалить идентификаторы маркировки сборочных заданий](dbwlabelidentifiers/post-api-marketplace-v3-dbw-orders-meta-delete.md) |
| `POST` | `/api/marketplace/v3/dbw/orders/meta/details` | dbwLabelIdentifiers | [Получить идентификаторы маркировки сборочных заданий](dbwlabelidentifiers/post-api-marketplace-v3-dbw-orders-meta-details.md) |
| `POST` | `/api/marketplace/v3/dbw/orders/meta/sgtin` | dbwLabelIdentifiers | [Закрепить коды маркировки Честного знака за сборочными заданиями](dbwlabelidentifiers/post-api-marketplace-v3-dbw-orders-meta-sgtin.md) |
| `POST` | `/api/marketplace/v3/dbw/orders/status/deliver` | dbwAssemblyOrders | [Перевести сборочные задания в доставку](dbwassemblyorders/post-api-marketplace-v3-dbw-orders-status-deliver.md) |
| `POST` | `/api/v3/dbw/orders/courier` | dbwAssemblyOrders | [Информация о курьере](dbwassemblyorders/post-api-v3-dbw-orders-courier.md) |
| `POST` | `/api/v3/dbw/orders/delivery-date` | dbwAssemblyOrders | [Получить дату и время доставки](dbwassemblyorders/post-api-v3-dbw-orders-delivery-date.md) |
| `POST` | `/api/v3/dbw/orders/status` | dbwAssemblyOrders | [Получить статусы сборочных заданий](dbwassemblyorders/post-api-v3-dbw-orders-status.md) |
| `POST` | `/api/v3/dbw/orders/stickers` | dbwAssemblyOrders | [Получить стикеры сборочных заданий](dbwassemblyorders/post-api-v3-dbw-orders-stickers.md) |
| `PUT` | `/api/v3/dbw/orders/{orderId}/meta/gtin` | dbwLabelIdentifiers | [Закрепить GTIN за сборочным заданием{{ /api/v3/dbw/orders/{orderId}/meta/gtin }}](dbwlabelidentifiers/put-api-v3-dbw-orders-orderid-meta-gtin.md) |
| `PUT` | `/api/v3/dbw/orders/{orderId}/meta/imei` | dbwLabelIdentifiers | [Закрепить IMEI за сборочным заданием{{ /api/v3/dbw/orders/{orderId}/meta/imei }}](dbwlabelidentifiers/put-api-v3-dbw-orders-orderid-meta-imei.md) |
| `PUT` | `/api/v3/dbw/orders/{orderId}/meta/uin` | dbwLabelIdentifiers | [Закрепить УИН за сборочным заданием{{ /api/v3/dbw/orders/{orderId}/meta/uin }}](dbwlabelidentifiers/put-api-v3-dbw-orders-orderid-meta-uin.md) |
