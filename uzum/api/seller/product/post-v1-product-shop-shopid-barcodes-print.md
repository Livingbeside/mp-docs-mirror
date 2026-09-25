---
title: Печать этикеток SKU
api: uzum-seller
method: POST
path: /v1/product/shop/{shopId}/barcodes/print
operation_id: printProductBarcodes
tags:
  - Product
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: b98dd7daf5021a93
---

# Печать этикеток SKU

`POST /v1/product/shop/{shopId}/barcodes/print`

Возвращает PDF с этикетками для переданных SKU. Ограничения: не более 100 SKU и не более 100 штук каждого SKU. Доступные размеры — GET /v1/product/barcodes/types.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopId` | path | integer<int64> | да | Идентификатор магазина |

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**. Список SKU для печати (не более 100)
  - `skuId` — integer<int64> **обязательный**. Идентификатор SKU
  - `amount` — integer<int32> **обязательный**. Количество этикеток данного SKU (не более 100)
  - `barcodeTypeId` — integer<int64> **обязательный**. Идентификатор размера этикетки из справочника /v1/product/barcodes/types

## Ответы

**400** — Ошибка валидации (больше 100 SKU или больше 100 штук каждого SKU)

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**200** — PDF с этикетками SKU
