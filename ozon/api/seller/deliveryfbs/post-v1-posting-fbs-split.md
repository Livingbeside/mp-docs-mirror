---
title: Разделить заказ на отправления без сборки
api: ozon-seller
method: POST
path: /v1/posting/fbs/split
operation_id: FbsSplit
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 889c3e27cdea8f97
---

# Разделить заказ на отправления без сборки

`POST /v1/posting/fbs/split`

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.
- `postings` — array[object] **обязательный**. Список отправлений, на которые поделится заказ. За один запрос можно разделить один заказ.
  - `products` — array[object] **обязательный**. Список товаров в заказе.
    - `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
    - `quantity` — integer<int64> **обязательный**. Количество экземпляров.

## Ответы

**200** — Заказ разделён

- `parent_posting` — object. Информация об изначальном отправлении.
  - `posting_number` — string. Номер изначального отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
    - `quantity` — integer<int64> **обязательный**. Количество экземпляров.
- `postings` — array[object]. Список отправлений, на которые разделился заказ.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
    - `quantity` — integer<int64> **обязательный**. Количество экземпляров.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
