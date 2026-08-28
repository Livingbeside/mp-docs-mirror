---
title: DBS — все методы
api: wb-orders-dbs
spec_version: dbs
operations: 21
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
content_sha: 1f2b3d2a1d156580
---

# DBS

Узнать больше о модели DBS можно в справочном центре Управление [сборочными заданиями](./orders-dbs#tag/dbsAssemblyOrders) и [идентификаторами маркировки](./orders-dbs#tag/dbsLabelIdentifiers) DBS (Delivery by Seller). Вы можете протестировать методы DBS в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Marketplejs-DBS) для эмуляции действий пользователя

Версия спеки: `dbs` · методов: **21**

Источник: https://dev.wildberries.ru/docs/openapi/orders-dbs

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v3/dbs/orders/new` | dbsAssemblyOrders | [Получить список новых сборочных заданий{{ /api/v3/dbs/orders/new }}](dbsassemblyorders/get-api-v3-dbs-orders-new.md) |
| `GET` | `/api/v3/dbs/orders` | dbsAssemblyOrders | [Получить информацию о завершенных сборочных заданиях{{ /api/v3/dbs/orders }}](dbsassemblyorders/get-api-v3-dbs-orders.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/b2b/info` | dbsAssemblyOrders | [Информация о покупателе B2B{{ /api/marketplace/v3/dbs/orders/b2b/info }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-b2b-info.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/final-price` | dbsAssemblyOrders | [Получить цены продавца и суммы к оплате{{ /api/marketplace/v3/dbs/orders/final-price }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-final-price.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/customs-declaration` | dbsLabelIdentifiers | [Закрепить номера ДТ за сборочными заданиями{{ /api/marketplace/v3/dbs/orders/meta/customs-declaration }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-customs-declaration.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/delete` | dbsLabelIdentifiers | [Удалить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/dbs/orders/meta/delete }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-delete.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/details` | dbsLabelIdentifiers | [Получить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/dbs/orders/meta/details }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-details.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/gtin` | dbsLabelIdentifiers | [Закрепить GTIN за сборочными заданиями{{ /api/marketplace/v3/dbs/orders/meta/gtin }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-gtin.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/imei` | dbsLabelIdentifiers | [Закрепить IMEI за сборочными заданиями{{ /api/marketplace/v3/dbs/orders/meta/imei }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-imei.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/sgtin` | dbsLabelIdentifiers | [Закрепить коды маркировки Честного знака за сборочными заданиями{{ /api/marketplace/v3/dbs/orders/meta/sgtin }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-sgtin.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/meta/uin` | dbsLabelIdentifiers | [Закрепить УИН за сборочными заданиями{{ /api/marketplace/v3/dbs/orders/meta/uin }}](dbslabelidentifiers/post-api-marketplace-v3-dbs-orders-meta-uin.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/cancel` | dbsAssemblyOrders | [Отменить сборочные задания{{ /api/marketplace/v3/dbs/orders/status/cancel }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-cancel.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/confirm` | dbsAssemblyOrders | [Перевести сборочные задания на сборку{{ /api/marketplace/v3/dbs/orders/status/confirm }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-confirm.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/deliver` | dbsAssemblyOrders | [Перевести сборочные задания в доставку{{ /api/marketplace/v3/dbs/orders/status/deliver }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-deliver.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/info` | dbsAssemblyOrders | [Получить статусы сборочных заданий{{ /api/marketplace/v3/dbs/orders/status/info }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-info.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/receive` | dbsAssemblyOrders | [Сообщить о получении заказов{{ /api/marketplace/v3/dbs/orders/status/receive }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-receive.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/status/reject` | dbsAssemblyOrders | [Сообщить об отказе от заказов{{ /api/marketplace/v3/dbs/orders/status/reject }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-status-reject.md) |
| `POST` | `/api/marketplace/v3/dbs/orders/stickers` | dbsAssemblyOrders | [Получить стикеры для сборочных заданий с доставкой в ПВЗ{{ /api/marketplace/v3/dbs/orders/stickers }}](dbsassemblyorders/post-api-marketplace-v3-dbs-orders-stickers.md) |
| `POST` | `/api/v3/dbs/groups/info` | dbsAssemblyOrders | [Получить информацию о платной доставке{{ /api/v3/dbs/groups/info }}](dbsassemblyorders/post-api-v3-dbs-groups-info.md) |
| `POST` | `/api/v3/dbs/orders/client` | dbsAssemblyOrders | [Информация о покупателе{{ /api/v3/dbs/orders/client }}](dbsassemblyorders/post-api-v3-dbs-orders-client.md) |
| `POST` | `/api/v3/dbs/orders/delivery-date` | dbsAssemblyOrders | [Получить дату и время доставки{{ /api/v3/dbs/orders/delivery-date }}](dbsassemblyorders/post-api-v3-dbs-orders-delivery-date.md) |
