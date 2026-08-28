---
title: Получить список незаполненных атрибутов для прослеживаемых товаров
api: ozon-seller
method: POST
path: /v1/posting/fbs/product/traceable/attribute
operation_id: PostingFbsProductTraceableAttribute
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 412009a7acf11859
---

# Получить список незаполненных атрибутов для прослеживаемых товаров

`POST /v1/posting/fbs/product/traceable/attribute`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Список незаполненных атрибутов

- `products` — array[object]. Список товаров в отправлении.
  - `required_attributes` — array[string]. Обязательные атрибуты.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
