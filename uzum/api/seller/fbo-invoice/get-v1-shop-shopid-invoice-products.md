---
title: Получение состава накладной
api: uzum-seller
method: GET
path: /v1/shop/{shopId}/invoice/products
operation_id: getShopInvoiceProductsByShopId
tags:
  - FBO Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: a0b175b92fefaa40
---

# Получение состава накладной

`GET /v1/shop/{shopId}/invoice/products`

Этот метод позволяет получить список товаров входящих в накладные

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `invoiceId` | query | integer<int64> | да | ID накладной, для которой необходимо получить содержимое |
| `shopId` | path | integer<int64> | да | ID магазина, для которого необходимо получить список накладных возврата. |

## Ответы

**200** — OK

- `id` — integer<int64>. Уникальный идентификатор продукта для счета-фактуры
- `skuTitle` — string. Название SKU продукта
- `productTitle` — string. Название продукта
- `quantityToStock` — integer<int32>. Количество единиц на складе
- `quantityAccepted` — integer<int32>. Количество принятых единиц
- `purchasePrice` — integer<int64>. Цена закупки единицы продукта
- `skuForInvoiceDtoList` — array[object]. Список SKU, связанных с продуктом для счета-фактуры
  - `id` — integer<int64>. Уникальный идентификатор SKU для счета-фактуры
  - `skuTitle` — string. Название SKU
  - `quantityToStock` — integer<int32>. Количество SKU на складе
  - `quantityAccepted` — integer<int32>. Количество принятых SKU
  - `purchasePrice` — integer<int64>. Цена закупки SKU
