---
title: Самовывоз — все методы
api: wb-in-store-pickup
spec_version: instorepickup
operations: 18
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
content_sha: e9f4acd45dc9baa1
---

# Самовывоз

Управление [сборочными заданиями](./in-store-pickup#tag/inStorePickupAssemblyOrders) и [идентификаторами маркировки](./in-store-pickup#tag/inStorePickupLabelIdentifiers) Самовывоза.

Вы можете протестировать методы Самовывоза в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Marketplejs-Samovyvoz) для эмуляции действий пользователя

Версия спеки: `instorepickup` · методов: **18**

Источник: https://dev.wildberries.ru/docs/openapi/in-store-pickup

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v3/click-collect/orders/new` | inStorePickupAssemblyOrders | [Получить список новых сборочных заданий](instorepickupassemblyorders/get-api-v3-click-collect-orders-new.md) |
| `GET` | `/api/v3/click-collect/orders` | inStorePickupAssemblyOrders | [Получить информацию о завершённых сборочных заданиях](instorepickupassemblyorders/get-api-v3-click-collect-orders.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/final-price` | inStorePickupAssemblyOrders | [Получить цены продавца и суммы к оплате](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-final-price.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/customs-declaration` | inStorePickupLabelIdentifiers | [Закрепить номера ДТ за сборочными заданиями](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-customs-declaration.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/delete` | inStorePickupLabelIdentifiers | [Удалить идентификаторы маркировки сборочных заданий](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-delete.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/details` | inStorePickupLabelIdentifiers | [Получить идентификаторы маркировки сборочных заданий](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-details.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/gtin` | inStorePickupLabelIdentifiers | [Закрепить GTIN за сборочными заданиями](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-gtin.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/imei` | inStorePickupLabelIdentifiers | [Закрепить IMEI за сборочными заданиями](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-imei.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/sgtin` | inStorePickupLabelIdentifiers | [Закрепить коды маркировки Честного знака за сборочными заданиями](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-sgtin.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/meta/uin` | inStorePickupLabelIdentifiers | [Закрепить УИН за сборочными заданиями](instorepickuplabelidentifiers/post-api-marketplace-v3-click-collect-orders-meta-uin.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/status/cancel` | inStorePickupAssemblyOrders | [Отменить сборочные задания](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-status-cancel.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/status/confirm` | inStorePickupAssemblyOrders | [Перевести сборочные задания на сборку](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-status-confirm.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/status/info` | inStorePickupAssemblyOrders | [Получить статусы сборочных заданий](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-status-info.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/status/prepare` | inStorePickupAssemblyOrders | [Сообщить, что сборочные задания готовы к выдаче](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-status-prepare.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/status/receive` | inStorePickupAssemblyOrders | [Сообщить, что заказы приняты покупателями](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-status-receive.md) |
| `POST` | `/api/marketplace/v3/click-collect/orders/status/reject` | inStorePickupAssemblyOrders | [Сообщить об отказе от заказов](instorepickupassemblyorders/post-api-marketplace-v3-click-collect-orders-status-reject.md) |
| `POST` | `/api/v3/click-collect/orders/client/identity` | inStorePickupAssemblyOrders | [Проверить, что заказ принадлежит покупателю](instorepickupassemblyorders/post-api-v3-click-collect-orders-client-identity.md) |
| `POST` | `/api/v3/click-collect/orders/client` | inStorePickupAssemblyOrders | [Информация о покупателе](instorepickupassemblyorders/post-api-v3-click-collect-orders-client.md) |
