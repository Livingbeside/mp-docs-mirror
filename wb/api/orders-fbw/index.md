---
title: Поставки FBW — все методы
api: wb-orders-fbw
spec_version: ordersfbw
operations: 7
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
content_sha: 1d610d2defce2ee5
---

# Поставки FBW

Узнать больше о поставках FBW можно в [справочном центре](https://seller.wildberries.ru/instructions/subcategory/5a8e1202-0865-45b7-acae-5d0afc7add56?goBackOption=prevRoute&categoryId=479385c6-de01-4b4d-ad4e-ed941e65582e)

В разделе описаны методы получения:
 - [информации для формирования поставок](./orders-fbw#tag/informationForFormingSupplies)
 - [информации о поставках](./orders-fbw#tag/suppliesInformation)

Вы можете создавать карточки товара в песочнице [Контента](./api-information#tag/authorization/Kategorii-tokenov), а потом использовать баркоды товаров в песочнице Поставок

Версия спеки: `ordersfbw` · методов: **7** · разделов справки: **3**

Источник: https://dev.wildberries.ru/docs/openapi/orders-fbw

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/api/v1/supplies/{ID}/goods` | suppliesInformation | [Товары поставки{{ /api/v1/supplies/{ID}/goods }}](suppliesinformation/get-api-v1-supplies-id-goods.md) |
| `GET` | `/api/v1/supplies/{ID}/package` | suppliesInformation | [Упаковка поставки{{ /api/v1/supplies/{ID}/package }}](suppliesinformation/get-api-v1-supplies-id-package.md) |
| `GET` | `/api/v1/supplies/{ID}` | suppliesInformation | [Детали поставки{{ /api/v1/supplies/{ID} }}](suppliesinformation/get-api-v1-supplies-id.md) |
| `GET` | `/api/v1/transit-tariffs` | informationForFormingSupplies | [Транзитные направления](informationforformingsupplies/get-api-v1-transit-tariffs.md) |
| `GET` | `/api/v1/warehouses` | informationForFormingSupplies | [Список складов](informationforformingsupplies/get-api-v1-warehouses.md) |
| `POST` | `/api/v1/acceptance/options` | informationForFormingSupplies | [Опции приёмки](informationforformingsupplies/post-api-v1-acceptance-options.md) |
| `POST` | `/api/v1/supplies` | suppliesInformation | [Список поставок](suppliesinformation/post-api-v1-supplies.md) |
