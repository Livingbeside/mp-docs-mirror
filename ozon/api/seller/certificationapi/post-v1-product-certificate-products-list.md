---
title: Список товаров, привязанных к сертификату
api: ozon-seller
method: POST
path: /v1/product/certificate/products/list
operation_id: CertificateProductsList
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0fb5dd200f98c532
---

# Список товаров, привязанных к сертификату

`POST /v1/product/certificate/products/list`

28 сентября 2026 года отключим параметры page и page_size в запросе метода. Используйте параметры last_id и limit.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Список товаров

- `result` — object. Товары, привязанные к сертификату.
  - `items` — array[object]. Список товаров.
    - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
    - `product_status_code` — string. Статус обработки товара при привязке к сертификату.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `count` — integer<int64>. Количество найденных товаров.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
