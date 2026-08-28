---
title: Обновить количество цифровых товаров
api: ozon-seller
method: POST
path: /v1/product/digital/stocks/import
operation_id: DigitalProductAPI_StocksImport
tags:
  - Digital
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b8e7f0cb3f9ea94c
---

# Обновить количество цифровых товаров

`POST /v1/product/digital/stocks/import`

Метод доступен только продавцам, работающим с цифровыми товарами. 

Используйте метод, чтобы изменить информацию о количестве товара в наличии.

## Запрос

**Тело запроса** (`application/json`):

- `stocks` — array[object]. Данные об остатках.
  - `offer_id` — string **обязательный**. Идентификатор товара в системе продавца — артикул.
  - `stock` — integer<int64> **обязательный**. Количество товара в наличии.

## Ответы

**200** — Количество товаров обновлено

- `status` — array[object]. Информация о товарах.
  - `errors` — array[object]. Ошибки, которые возникли при обработке запроса.
    - `code` — string. Код ошибки.
    - `message` — string. Описание ошибки.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `updated` — boolean. `true`, если запрос выполнен успешно и остатки обновлены.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
