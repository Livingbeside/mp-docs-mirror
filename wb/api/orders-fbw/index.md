---
title: Поставки FBW — все методы
api: wb-orders-fbw
spec_version: ordersfbw
operations: 14
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
content_sha: 7063313b3397ab48
---

# Поставки FBW

Узнать больше о поставках FBW можно в [справочном центре](https://seller.wildberries.ru/instructions/subcategory/5a8e1202-0865-45b7-acae-5d0afc7add56?goBackOption=prevRoute&categoryId=479385c6-de01-4b4d-ad4e-ed941e65582e)

В разделе описаны методы получения:
 - [информации для формирования поставок](./orders-fbw#tag/informationForFormingSupplies)
 - [информации о поставках](./orders-fbw#tag/suppliesInformation)

Вы можете создавать карточки товара в песочнице [Контента](./api-information#tag/authorization/Kategorii-tokenov), а потом использовать баркоды товаров в песочнице Поставок

Версия спеки: `ordersfbw` · методов: **14** · разделов справки: **4**

Источник: https://dev.wildberries.ru/docs/openapi/orders-fbw

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/supplies/v1/drafts/{draftId}/items` | supplyDrafts | [Удалить товары из черновика{{ /api/supplies/v1/drafts/{draftId}/items }}](supplydrafts/delete-api-supplies-v1-drafts-draftid-items.md) |
| `DELETE` | `/api/supplies/v1/drafts/{draftId}` | supplyDrafts | [Удалить черновик{{ /api/supplies/v1/drafts/{draftId} }}](supplydrafts/delete-api-supplies-v1-drafts-draftid.md) |
| `GET` | `/api/supplies/v1/discrepancies/{supplyId}` | suppliesInformation | [Расхождения в поставке{{ /api/supplies/v1/discrepancies/{supplyId} }}](suppliesinformation/get-api-supplies-v1-discrepancies-supplyid.md) |
| `GET` | `/api/supplies/v1/drafts/{draftId}/items` | supplyDrafts | [Список товаров в черновике{{ /api/supplies/v1/drafts/{draftId}/items }}](supplydrafts/get-api-supplies-v1-drafts-draftid-items.md) |
| `GET` | `/api/supplies/v1/drafts` | supplyDrafts | [Список черновиков](supplydrafts/get-api-supplies-v1-drafts.md) |
| `GET` | `/api/v1/supplies/{ID}/goods` | suppliesInformation | [Товары поставки{{ /api/v1/supplies/{ID}/goods }}](suppliesinformation/get-api-v1-supplies-id-goods.md) |
| `GET` | `/api/v1/supplies/{ID}/package` | suppliesInformation | [Упаковка поставки{{ /api/v1/supplies/{ID}/package }}](suppliesinformation/get-api-v1-supplies-id-package.md) |
| `GET` | `/api/v1/supplies/{ID}` | suppliesInformation | [Детали поставки{{ /api/v1/supplies/{ID} }}](suppliesinformation/get-api-v1-supplies-id.md) |
| `GET` | `/api/v1/transit-tariffs` | informationForFormingSupplies | [Транзитные направления](informationforformingsupplies/get-api-v1-transit-tariffs.md) |
| `GET` | `/api/v1/warehouses` | informationForFormingSupplies | [Список складов](informationforformingsupplies/get-api-v1-warehouses.md) |
| `POST` | `/api/supplies/v1/drafts/{draftId}/items` | supplyDrafts | [Добавить товары в черновик{{ /api/supplies/v1/drafts/{draftId}/items }}](supplydrafts/post-api-supplies-v1-drafts-draftid-items.md) |
| `POST` | `/api/supplies/v1/drafts` | supplyDrafts | [Создать черновик](supplydrafts/post-api-supplies-v1-drafts.md) |
| `POST` | `/api/v1/acceptance/options` | informationForFormingSupplies | [Опции приёмки](informationforformingsupplies/post-api-v1-acceptance-options.md) |
| `POST` | `/api/v1/supplies` | suppliesInformation | [Список поставок](suppliesinformation/post-api-v1-supplies.md) |
