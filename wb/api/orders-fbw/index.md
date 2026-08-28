---
title: Поставки FBW — все методы
api: wb-orders-fbw
spec_version: ordersfbw
operations: 7
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
content_sha: cecaa9218b6585cf
---

# Поставки FBW

Узнать больше о поставках FBW можно в справочном центре В разделе описаны методы получения: - [информации для формирования поставок](./orders-fbw#tag/informationForFormingSupplies) - [информации о поставках](./orders-fbw#tag/suppliesInformation) Вы можете создавать карточки товара в песочнице [Контента](./api-information#tag/authorization/Kategorii-tokenov), а потом использовать баркоды товаров в песочнице Поставок

Версия спеки: `ordersfbw` · методов: **7**

Источник: https://dev.wildberries.ru/docs/openapi/orders-fbw

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v1/supplies/{ID}/goods` | suppliesInformation | [Товары поставки{{ /api/v1/supplies/{ID}/goods }}](suppliesinformation/get-api-v1-supplies-id-goods.md) |
| `GET` | `/api/v1/supplies/{ID}/package` | suppliesInformation | [Упаковка поставки{{ /api/v1/supplies/{ID}/package }}](suppliesinformation/get-api-v1-supplies-id-package.md) |
| `GET` | `/api/v1/supplies/{ID}` | suppliesInformation | [Детали поставки{{ /api/v1/supplies/{ID} }}](suppliesinformation/get-api-v1-supplies-id.md) |
| `GET` | `/api/v1/transit-tariffs` | informationForFormingSupplies | [Транзитные направления{{ /api/v1/transit-tariffs }}](informationforformingsupplies/get-api-v1-transit-tariffs.md) |
| `GET` | `/api/v1/warehouses` | informationForFormingSupplies | [Список складов{{ /api/v1/warehouses }}](informationforformingsupplies/get-api-v1-warehouses.md) |
| `POST` | `/api/v1/acceptance/options` | informationForFormingSupplies | [Опции приёмки{{ /api/v1/acceptance/options }}](informationforformingsupplies/post-api-v1-acceptance-options.md) |
| `POST` | `/api/v1/supplies` | suppliesInformation | [Список поставок{{ /api/v1/supplies }}](suppliesinformation/post-api-v1-supplies.md) |
