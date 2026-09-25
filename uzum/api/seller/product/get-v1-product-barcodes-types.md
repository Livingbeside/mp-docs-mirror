---
title: Справочник размеров (типов) этикеток
api: uzum-seller
method: GET
path: /v1/product/barcodes/types
operation_id: getBarcodeTypes
tags:
  - Product
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 75a8345d9b45569a
---

# Справочник размеров (типов) этикеток

`GET /v1/product/barcodes/types`

Возвращает доступные размеры этикеток. Полученный id передаётся как barcodeTypeId при печати этикеток SKU.

## Ответы

**200** — Список доступных типов этикеток

- `barcodeLabelTypes` — array[object]. Доступные размеры (типы) этикеток
  - `id` — integer<int64>. Идентификатор размера этикетки (используется как barcodeTypeId)
  - `title` — string. Название размера этикетки
  - `printType` — string. Тип печати
