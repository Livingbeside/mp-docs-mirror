---
title: Заказы FBS — все методы
api: wb-orders-fbs
spec_version: order
operations: 47
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: 08e114f6c3f209fe
---

# Заказы FBS

С помощью методов раздела Заказы FBS (Fulfillment by Seller) вы можете:
 - получать информацию о [сборочных заданиях](./orders-fbs#tag/fbsAssemblyOrders) и их статусах, отменять сборочные задания, получать стикеры
 - добавлять, редактировать и удалять [идентификаторы маркировки](./orders-fbs#tag/fbsLabelIdentifiers) сборочных заданий
 - управлять [поставками](./orders-fbs#tag/fbsSupplies)
 - создавать, редактировать и удалять [пропуска](./orders-fbs#tag/fbsPasses) на склады WB

Вы можете протестировать методы заказов FBS в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/marketplaceFbs) для эмуляции действий пользователя

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-0771-7571-aea9-11d5b597f34c/zakazy-fbs) по работе с заказами FBS

 Узнать больше о заказах FBS можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/category/b3e60238-fd4c-49ce-8668-ff688725a12d)

Версия спеки: `order` · методов: **47** · разделов справки: **6**

Источник: https://dev.wildberries.ru/docs/openapi/orders-fbs

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/v3/orders/{orderId}/meta` | fbsLabelIdentifiers | [Удалить идентификаторы маркировки сборочного задания{{ /api/v3/orders/{orderId}/meta }}](fbslabelidentifiers/delete-api-v3-orders-orderid-meta.md) |
| `DELETE` | `/api/v3/passes/{passId}` | fbsPasses | [Удалить пропуск{{ /api/v3/passes/{passId} }}](fbspasses/delete-api-v3-passes-passid.md) |
| `DELETE` | `/api/v3/supplies/{supplyId}/trbx` | fbsSupplies | [Удалить грузоместа из поставки{{ /api/v3/supplies/{supplyId}/trbx }}](fbssupplies/delete-api-v3-supplies-supplyid-trbx.md) |
| `DELETE` | `/api/v3/supplies/{supplyId}` | fbsSupplies | [Удалить поставку{{ /api/v3/supplies/{supplyId} }}](fbssupplies/delete-api-v3-supplies-supplyid.md) |
| `GET` | `/api/marketplace/v3/fbs/dictionaries/countries/oksm` | fbsSupplies | [Получить список стран ОКСМ](fbssupplies/get-api-marketplace-v3-fbs-dictionaries-countries-oksm.md) |
| `GET` | `/api/marketplace/v3/fbs/orders/archive` | fbsAssemblyOrders | [Получить список архивных сборочных заданий](fbsassemblyorders/get-api-marketplace-v3-fbs-orders-archive.md) |
| `GET` | `/api/marketplace/v3/fbs/settings/autoreturns/subcategories/restricted` | autoreturnSettings | [Получить предметы, которые не хранятся на складах WB](autoreturnsettings/get-api-marketplace-v3-fbs-settings-autoreturns-subcategories-restricted.md) |
| `GET` | `/api/marketplace/v3/fbs/settings/autoreturns` | autoreturnSettings | [Получить настройки автовозврата продавца](autoreturnsettings/get-api-marketplace-v3-fbs-settings-autoreturns.md) |
| `GET` | `/api/marketplace/v3/fbs/shipping-points` | fbsSupplies | [Получить список пунктов отгрузки поставок](fbssupplies/get-api-marketplace-v3-fbs-shipping-points.md) |
| `GET` | `/api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot` | fbsSupplies | [Получить QR-код СПОТ{{ /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot }}](fbssupplies/get-api-marketplace-v3-fbs-supplies-supplyid-stickers-spot.md) |
| `GET` | `/api/marketplace/v3/supplies/{supplyId}/order-ids` | fbsSupplies | [Получить ID сборочных заданий поставки{{ /api/marketplace/v3/supplies/{supplyId}/order-ids }}](fbssupplies/get-api-marketplace-v3-supplies-supplyid-order-ids.md) |
| `GET` | `/api/v3/orders/new` | fbsAssemblyOrders | [Получить список новых сборочных заданий](fbsassemblyorders/get-api-v3-orders-new.md) |
| `GET` | `/api/v3/orders` | fbsAssemblyOrders | [Получить информацию о сборочных заданиях](fbsassemblyorders/get-api-v3-orders.md) |
| `GET` | `/api/v3/passes/offices` | fbsPasses | [Получить список складов, для которых требуется пропуск](fbspasses/get-api-v3-passes-offices.md) |
| `GET` | `/api/v3/passes` | fbsPasses | [Получить список пропусков](fbspasses/get-api-v3-passes.md) |
| `GET` | `/api/v3/supplies/orders/reshipment` | fbsAssemblyOrders | [Получить все сборочные задания для повторной отгрузки](fbsassemblyorders/get-api-v3-supplies-orders-reshipment.md) |
| `GET` | `/api/v3/supplies/{supplyId}/barcode` | fbsSupplies | [Получить QR-код поставки{{ /api/v3/supplies/{supplyId}/barcode }}](fbssupplies/get-api-v3-supplies-supplyid-barcode.md) |
| `GET` | `/api/v3/supplies/{supplyId}/trbx` | fbsSupplies | [Получить список грузомест поставки{{ /api/v3/supplies/{supplyId}/trbx }}](fbssupplies/get-api-v3-supplies-supplyid-trbx.md) |
| `GET` | `/api/v3/supplies/{supplyId}` | fbsSupplies | [Получить информацию о поставке{{ /api/v3/supplies/{supplyId} }}](fbssupplies/get-api-v3-supplies-supplyid.md) |
| `GET` | `/api/v3/supplies` | fbsSupplies | [Получить список поставок](fbssupplies/get-api-v3-supplies.md) |
| `PATCH` | `/api/marketplace/v3/fbs/settings/autoreturns/items` | autoreturnSettings | [Обновить настройки автовозврата товаров](autoreturnsettings/patch-api-marketplace-v3-fbs-settings-autoreturns-items.md) |
| `PATCH` | `/api/marketplace/v3/fbs/settings/autoreturns` | autoreturnSettings | [Обновить настройки автовозврата продавца](autoreturnsettings/patch-api-marketplace-v3-fbs-settings-autoreturns.md) |
| `PATCH` | `/api/marketplace/v3/fbs/supplies/shipping-method` | fbsSupplies | [Установить параметры отгрузки поставок](fbssupplies/patch-api-marketplace-v3-fbs-supplies-shipping-method.md) |
| `PATCH` | `/api/marketplace/v3/fbs/supplies/waybill` | fbsSupplies | [Установить ID ЭТрН поставок](fbssupplies/patch-api-marketplace-v3-fbs-supplies-waybill.md) |
| `PATCH` | `/api/marketplace/v3/supplies/{supplyId}/orders` | fbsSupplies | [Добавить сборочные задания к поставке{{ /api/marketplace/v3/supplies/{supplyId}/orders }}](fbssupplies/patch-api-marketplace-v3-supplies-supplyid-orders.md) |
| `PATCH` | `/api/v3/orders/{orderId}/cancel` | fbsAssemblyOrders | [Отменить сборочное задание{{ /api/v3/orders/{orderId}/cancel }}](fbsassemblyorders/patch-api-v3-orders-orderid-cancel.md) |
| `PATCH` | `/api/v3/supplies/{supplyId}/deliver` | fbsSupplies | [Передать поставку в доставку{{ /api/v3/supplies/{supplyId}/deliver }}](fbssupplies/patch-api-v3-supplies-supplyid-deliver.md) |
| `POST` | `/api/marketplace/v3/fbs/settings/autoreturns/items` | autoreturnSettings | [Получить настройки автовозврата товаров](autoreturnsettings/post-api-marketplace-v3-fbs-settings-autoreturns-items.md) |
| `POST` | `/api/marketplace/v3/fbs/supplies/spot/list` | fbsSupplies | [Получить данные СПОТ для списка поставок](fbssupplies/post-api-marketplace-v3-fbs-supplies-spot-list.md) |
| `POST` | `/api/marketplace/v3/orders/meta` | fbsLabelIdentifiers | [Получить идентификаторы маркировки сборочных заданий](fbslabelidentifiers/post-api-marketplace-v3-orders-meta.md) |
| `POST` | `/api/v3/orders/client` | fbsAssemblyOrders | [Заказы с информацией по клиенту](fbsassemblyorders/post-api-v3-orders-client.md) |
| `POST` | `/api/v3/orders/status/history` | fbsAssemblyOrders | [История статусов для сборочных заданий трансграничных поставок](fbsassemblyorders/post-api-v3-orders-status-history.md) |
| `POST` | `/api/v3/orders/status` | fbsAssemblyOrders | [Получить статусы сборочных заданий](fbsassemblyorders/post-api-v3-orders-status.md) |
| `POST` | `/api/v3/orders/stickers/cross-border` | fbsAssemblyOrders | [Получить стикеры сборочных заданий трансграничных поставок](fbsassemblyorders/post-api-v3-orders-stickers-cross-border.md) |
| `POST` | `/api/v3/orders/stickers` | fbsAssemblyOrders | [Получить стикеры сборочных заданий](fbsassemblyorders/post-api-v3-orders-stickers.md) |
| `POST` | `/api/v3/passes` | fbsPasses | [Создать пропуск](fbspasses/post-api-v3-passes.md) |
| `POST` | `/api/v3/supplies/{supplyId}/trbx/stickers` | fbsSupplies | [Получить стикеры грузомест поставки{{ /api/v3/supplies/{supplyId}/trbx/stickers }}](fbssupplies/post-api-v3-supplies-supplyid-trbx-stickers.md) |
| `POST` | `/api/v3/supplies/{supplyId}/trbx` | fbsSupplies | [Добавить грузоместа к поставке{{ /api/v3/supplies/{supplyId}/trbx }}](fbssupplies/post-api-v3-supplies-supplyid-trbx.md) |
| `POST` | `/api/v3/supplies` | fbsSupplies | [Создать новую поставку](fbssupplies/post-api-v3-supplies.md) |
| `PUT` | `/api/marketplace/v3/fbs/supplies/{supplyId}/spot` | fbsSupplies | [Добавить данные СПОТ в поставку{{ /api/marketplace/v3/fbs/supplies/{supplyId}/spot }}](fbssupplies/put-api-marketplace-v3-fbs-supplies-supplyid-spot.md) |
| `PUT` | `/api/marketplace/v3/orders/{orderId}/meta/customs-declaration` | fbsLabelIdentifiers | [Закрепить номер ДТ за сборочным заданием{{ /api/marketplace/v3/orders/{orderId}/meta/customs-declaration }}](fbslabelidentifiers/put-api-marketplace-v3-orders-orderid-meta-customs-declaration.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/expiration` | fbsLabelIdentifiers | [Закрепить за сборочным заданием срок годности товара{{ /api/v3/orders/{orderId}/meta/expiration }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-expiration.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/gtin` | fbsLabelIdentifiers | [Закрепить GTIN за сборочным заданием{{ /api/v3/orders/{orderId}/meta/gtin }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-gtin.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/imei` | fbsLabelIdentifiers | [Закрепить IMEI за сборочным заданием{{ /api/v3/orders/{orderId}/meta/imei }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-imei.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/sgtin` | fbsLabelIdentifiers | [Закрепить код маркировки Честного знака за сборочным заданием{{ /api/v3/orders/{orderId}/meta/sgtin }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-sgtin.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/uin` | fbsLabelIdentifiers | [Закрепить УИН за сборочным заданием{{ /api/v3/orders/{orderId}/meta/uin }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-uin.md) |
| `PUT` | `/api/v3/passes/{passId}` | fbsPasses | [Обновить пропуск{{ /api/v3/passes/{passId} }}](fbspasses/put-api-v3-passes-passid.md) |
