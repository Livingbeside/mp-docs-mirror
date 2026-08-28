---
title: Заказы FBS — все методы
api: wb-orders-fbs
spec_version: order
operations: 40
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: b7c50f5cd2534e32
---

# Заказы FBS

С помощью методов раздела Заказы FBS (Fulfillment by Seller) вы можете: - получать информацию о [сборочных заданиях](./orders-fbs#tag/Sborochnye-zadaniya-FBS) и их статусах, отменять сборочные задания, получать стикеры - добавлять, редактировать и удалять [идентификаторы маркировки](./orders-fbs#tag/fbsLabelIdentifiers) сборочных заданий - управлять [поставками](./orders-fbs#tag/Postavki-FBS) - создавать, редактировать и удалять [пропуска](./orders-fbs#tag/Propuska-FBS) на склады WB Вы можете протестировать методы заказов FBS в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Marketplejs-FBS) для эмуляции действий пользователя Узнать, как использовать методы в бизнес-кейсах, можно в инструкции по работе с заказами FBS Узнать больше о заказах FBS можно в справочном центре

Версия спеки: `order` · методов: **40**

Источник: https://dev.wildberries.ru/docs/openapi/orders-fbs

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/v3/orders/{orderId}/meta` | fbsLabelIdentifiers | [Удалить идентификаторы маркировки сборочного задания{{ /api/v3/orders/{orderId}/meta }}](fbslabelidentifiers/delete-api-v3-orders-orderid-meta.md) |
| `DELETE` | `/api/v3/passes/{passId}` | Пропуска FBS | [Удалить пропуск{{ /api/v3/passes/{passId} }}](propuska-fbs/delete-api-v3-passes-passid.md) |
| `DELETE` | `/api/v3/supplies/{supplyId}/trbx` | Поставки FBS | [Удалить грузоместа из поставки{{ /api/v3/supplies/{supplyId}/trbx }}](postavki-fbs/delete-api-v3-supplies-supplyid-trbx.md) |
| `DELETE` | `/api/v3/supplies/{supplyId}` | Поставки FBS | [Удалить поставку{{ /api/v3/supplies/{supplyId} }}](postavki-fbs/delete-api-v3-supplies-supplyid.md) |
| `GET` | `/api/marketplace/v3/fbs/orders/archive` | Сборочные задания FBS | [Получить список архивных сборочных заданий{{ /api/marketplace/v3/fbs/orders/archive }}](sborochnye-zadaniya-fbs/get-api-marketplace-v3-fbs-orders-archive.md) |
| `GET` | `/api/marketplace/v3/fbs/settings/autoreturns/subcategories/restricted` | autoreturnSettings | [Получить предметы, которые не хранятся на складах WB{{ /api/marketplace/v3/fbs/settings/autoreturns/subcategories/restricted }}](autoreturnsettings/get-api-marketplace-v3-fbs-settings-autoreturns-subcategories-restricted.md) |
| `GET` | `/api/marketplace/v3/fbs/settings/autoreturns` | autoreturnSettings | [Получить настройки автовозврата продавца{{ /api/marketplace/v3/fbs/settings/autoreturns }}](autoreturnsettings/get-api-marketplace-v3-fbs-settings-autoreturns.md) |
| `GET` | `/api/marketplace/v3/supplies/{supplyId}/order-ids` | Поставки FBS | [Получить ID сборочных заданий поставки{{ /api/marketplace/v3/supplies/{supplyId}/order-ids }}](postavki-fbs/get-api-marketplace-v3-supplies-supplyid-order-ids.md) |
| `GET` | `/api/v3/orders/new` | Сборочные задания FBS | [Получить список новых сборочных заданий{{ /api/v3/orders/new }}](sborochnye-zadaniya-fbs/get-api-v3-orders-new.md) |
| `GET` | `/api/v3/orders` | Сборочные задания FBS | [Получить информацию о сборочных заданиях{{ /api/v3/orders }}](sborochnye-zadaniya-fbs/get-api-v3-orders.md) |
| `GET` | `/api/v3/passes/offices` | Пропуска FBS | [Получить список складов, для которых требуется пропуск{{ /api/v3/passes/offices }}](propuska-fbs/get-api-v3-passes-offices.md) |
| `GET` | `/api/v3/passes` | Пропуска FBS | [Получить список пропусков{{ /api/v3/passes }}](propuska-fbs/get-api-v3-passes.md) |
| `GET` | `/api/v3/supplies/orders/reshipment` | Сборочные задания FBS | [Получить все сборочные задания для повторной отгрузки{{ /api/v3/supplies/orders/reshipment }}](sborochnye-zadaniya-fbs/get-api-v3-supplies-orders-reshipment.md) |
| `GET` | `/api/v3/supplies/{supplyId}/barcode` | Поставки FBS | [Получить QR-код поставки{{ /api/v3/supplies/{supplyId}/barcode }}](postavki-fbs/get-api-v3-supplies-supplyid-barcode.md) |
| `GET` | `/api/v3/supplies/{supplyId}/trbx` | Поставки FBS | [Получить список грузомест поставки{{ /api/v3/supplies/{supplyId}/trbx }}](postavki-fbs/get-api-v3-supplies-supplyid-trbx.md) |
| `GET` | `/api/v3/supplies/{supplyId}` | Поставки FBS | [Получить информацию о поставке{{ /api/v3/supplies/{supplyId} }}](postavki-fbs/get-api-v3-supplies-supplyid.md) |
| `GET` | `/api/v3/supplies` | Поставки FBS | [Получить список поставок{{ /api/v3/supplies }}](postavki-fbs/get-api-v3-supplies.md) |
| `PATCH` | `/api/marketplace/v3/fbs/settings/autoreturns/items` | autoreturnSettings | [Обновить настройки автовозврата товаров{{ /api/marketplace/v3/fbs/settings/autoreturns/items }}](autoreturnsettings/patch-api-marketplace-v3-fbs-settings-autoreturns-items.md) |
| `PATCH` | `/api/marketplace/v3/fbs/settings/autoreturns` | autoreturnSettings | [Обновить настройки автовозврата продавца{{ /api/marketplace/v3/fbs/settings/autoreturns }}](autoreturnsettings/patch-api-marketplace-v3-fbs-settings-autoreturns.md) |
| `PATCH` | `/api/marketplace/v3/supplies/{supplyId}/orders` | Поставки FBS | [Добавить сборочные задания к поставке{{ /api/marketplace/v3/supplies/{supplyId}/orders }}](postavki-fbs/patch-api-marketplace-v3-supplies-supplyid-orders.md) |
| `PATCH` | `/api/v3/orders/{orderId}/cancel` | Сборочные задания FBS | [Отменить сборочное задание{{ /api/v3/orders/{orderId}/cancel }}](sborochnye-zadaniya-fbs/patch-api-v3-orders-orderid-cancel.md) |
| `PATCH` | `/api/v3/supplies/{supplyId}/deliver` | Поставки FBS | [Передать поставку в доставку{{ /api/v3/supplies/{supplyId}/deliver }}](postavki-fbs/patch-api-v3-supplies-supplyid-deliver.md) |
| `POST` | `/api/marketplace/v3/fbs/settings/autoreturns/items` | autoreturnSettings | [Получить настройки автовозврата товаров{{ /api/marketplace/v3/fbs/settings/autoreturns/items }}](autoreturnsettings/post-api-marketplace-v3-fbs-settings-autoreturns-items.md) |
| `POST` | `/api/marketplace/v3/orders/meta` | fbsLabelIdentifiers | [Получить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/orders/meta }}](fbslabelidentifiers/post-api-marketplace-v3-orders-meta.md) |
| `POST` | `/api/v3/orders/client` | Сборочные задания FBS | [Заказы с информацией по клиенту{{ /api/v3/orders/client }}](sborochnye-zadaniya-fbs/post-api-v3-orders-client.md) |
| `POST` | `/api/v3/orders/status/history` | Сборочные задания FBS | [История статусов для сборочных заданий трансграничных поставок{{ /api/v3/orders/status/history }}](sborochnye-zadaniya-fbs/post-api-v3-orders-status-history.md) |
| `POST` | `/api/v3/orders/status` | Сборочные задания FBS | [Получить статусы сборочных заданий{{ /api/v3/orders/status }}](sborochnye-zadaniya-fbs/post-api-v3-orders-status.md) |
| `POST` | `/api/v3/orders/stickers/cross-border` | Сборочные задания FBS | [Получить стикеры сборочных заданий трансграничных поставок{{ /api/v3/orders/stickers/cross-border }}](sborochnye-zadaniya-fbs/post-api-v3-orders-stickers-cross-border.md) |
| `POST` | `/api/v3/orders/stickers` | Сборочные задания FBS | [Получить стикеры сборочных заданий{{ /api/v3/orders/stickers }}](sborochnye-zadaniya-fbs/post-api-v3-orders-stickers.md) |
| `POST` | `/api/v3/passes` | Пропуска FBS | [Создать пропуск{{ /api/v3/passes }}](propuska-fbs/post-api-v3-passes.md) |
| `POST` | `/api/v3/supplies/{supplyId}/trbx/stickers` | Поставки FBS | [Получить стикеры грузомест поставки{{ /api/v3/supplies/{supplyId}/trbx/stickers }}](postavki-fbs/post-api-v3-supplies-supplyid-trbx-stickers.md) |
| `POST` | `/api/v3/supplies/{supplyId}/trbx` | Поставки FBS | [Добавить грузоместа к поставке{{ /api/v3/supplies/{supplyId}/trbx }}](postavki-fbs/post-api-v3-supplies-supplyid-trbx.md) |
| `POST` | `/api/v3/supplies` | Поставки FBS | [Создать новую поставку{{ /api/v3/supplies }}](postavki-fbs/post-api-v3-supplies.md) |
| `PUT` | `/api/marketplace/v3/orders/{orderId}/meta/customs-declaration` | fbsLabelIdentifiers | [Закрепить номер ДТ за сборочным заданием{{ /api/marketplace/v3/orders/{orderId}/meta/customs-declaration }}](fbslabelidentifiers/put-api-marketplace-v3-orders-orderid-meta-customs-declaration.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/expiration` | fbsLabelIdentifiers | [Закрепить за сборочным заданием срок годности товара{{ /api/v3/orders/{orderId}/meta/expiration }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-expiration.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/gtin` | fbsLabelIdentifiers | [Закрепить GTIN за сборочным заданием{{ /api/v3/orders/{orderId}/meta/gtin }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-gtin.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/imei` | fbsLabelIdentifiers | [Закрепить IMEI за сборочным заданием{{ /api/v3/orders/{orderId}/meta/imei }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-imei.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/sgtin` | fbsLabelIdentifiers | [Закрепить код маркировки Честного знака за сборочным заданием{{ /api/v3/orders/{orderId}/meta/sgtin }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-sgtin.md) |
| `PUT` | `/api/v3/orders/{orderId}/meta/uin` | fbsLabelIdentifiers | [Закрепить УИН за сборочным заданием{{ /api/v3/orders/{orderId}/meta/uin }}](fbslabelidentifiers/put-api-v3-orders-orderid-meta-uin.md) |
| `PUT` | `/api/v3/passes/{passId}` | Пропуска FBS | [Обновить пропуск{{ /api/v3/passes/{passId} }}](propuska-fbs/put-api-v3-passes-passid.md) |
