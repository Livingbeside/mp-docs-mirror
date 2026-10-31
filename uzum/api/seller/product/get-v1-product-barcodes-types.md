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
content_sha: 811c7f7e0626e511
---

# Справочник размеров (типов) этикеток

`GET /v1/product/barcodes/types`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Возвращает доступные размеры этикеток. Полученный id передаётся как barcodeTypeId при печати этикеток SKU.

## Ответы

**200** — Список доступных типов этикеток

- `barcodeLabelTypes` — array[object]. Доступные размеры (типы) этикеток
  - `id` — integer<int64>. Идентификатор размера этикетки (используется как barcodeTypeId)
  - `title` — string. Название размера этикетки
  - `printType` — string. Тип печати

**401** — Заголовок Authorization отсутствует или пуст. Передайте Authorization: API_TOKEN без префикса Bearer; заголовок token не используется.

**403** — Ключ не найден, истёк, выключен, не даёт доступа к магазину или изменениям. Если метод требует shopIds, проверьте наличие этого параметра и доступ ко всем указанным магазинам. Значение Authorization передавайте без Bearer.
