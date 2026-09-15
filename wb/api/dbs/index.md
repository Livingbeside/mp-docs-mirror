---
title: DBS — все методы
api: wb-dbs
spec_version: dbs
operations: 21
source: "https://dev.wildberries.ru/docs/openapi/dbs"
content_sha: 1cb1a47ca46f8dbf
---

# DBS

Узнать больше о модели DBS можно в [справочном центре](https://seller.wildberries.ru/instructions/category/6572e024-7428-4db1-86a8-a4c7dbebbfcf?goBackOption=prevRoute&categoryId=5a8e1202-0865-45b7-acae-5d0afc7add56)

Управление [сборочными заданиями](./dbs#tag/dbsAssemblyOrders) и [идентификаторами маркировки](./dbs#tag/dbsLabelIdentifiers) DBS (Delivery by Seller).

Вы можете протестировать методы DBS в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Marketplejs-DBS) для эмуляции действий пользователя

Версия спеки: `dbs` · методов: **21** · разделов справки: **3**

Источник: https://dev.wildberries.ru/docs/openapi/dbs

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v3/dbs/orders/new` | dbsAssemblyOrders | [Получить список новых сборочных заданий](dbsassemblyorders/get-api-v3-dbs-orders-new.md) |
| `GET` | `/api/v3/dbs/orders` | dbsAssemblyOrders | [Получить информацию о завершенных сборочных заданиях](dbsassemblyorders/get-api-v3-dbs-orders.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/b2b/info` | dbsAssemblyOrders | [Информация о покупателе B2B](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-b2b-info.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/final-price` | dbsAssemblyOrders | [Получить цены продавца и суммы к оплате](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-final-price.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/customs-declaration` | dbsLabelIdentifiers | [Закрепить номера ДТ за сборочными заданиями](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-customs-declaration.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/delete` | dbsLabelIdentifiers | [Удалить идентификаторы маркировки сборочных заданий](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-delete.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/details` | dbsLabelIdentifiers | [Получить идентификаторы маркировки сборочных заданий](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-details.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/gtin` | dbsLabelIdentifiers | [Закрепить GTIN за сборочными заданиями](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-gtin.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/imei` | dbsLabelIdentifiers | [Закрепить IMEI за сборочными заданиями](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-imei.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/sgtin` | dbsLabelIdentifiers | [Закрепить коды маркировки Честного знака за сборочными заданиями](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-sgtin.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/uin` | dbsLabelIdentifiers | [Закрепить УИН за сборочными заданиями](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-uin.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/cancel` | dbsAssemblyOrders | [Отменить сборочные задания](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-cancel.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/confirm` | dbsAssemblyOrders | [Перевести сборочные задания на сборку](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-confirm.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/deliver` | dbsAssemblyOrders | [Перевести сборочные задания в доставку](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-deliver.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/info` | dbsAssemblyOrders | [Получить статусы сборочных заданий](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-info.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/receive` | dbsAssemblyOrders | [Сообщить о получении заказов](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-receive.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/reject` | dbsAssemblyOrders | [Сообщить об отказе от заказов](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-reject.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/stickers` | dbsAssemblyOrders | [Получить стикеры для сборочных заданий с доставкой в ПВЗ](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-stickers.md) |
| `POST` | `/api/v3/dbs/groups/info` | dbsAssemblyOrders | [Получить информацию о платной доставке](dbsassemblyorders/post-api-v3-dbs-groups-info.md) |
| `POST` | `/api/v3/dbs/orders/client` | dbsAssemblyOrders | [Информация о покупателе](dbsassemblyorders/post-api-v3-dbs-orders-client.md) |
| `POST` | `/api/v3/dbs/orders/delivery-date` | dbsAssemblyOrders | [Получить дату и время доставки](dbsassemblyorders/post-api-v3-dbs-orders-delivery-date.md) |
