---
title: Список неоплаченных товаров, заказанных юридическими лицами
api: ozon-seller
method: POST
path: /v1/posting/unpaid-legal/product/list
operation_id: PostingAPI_UnpaidLegalProductList
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 40c58596f5143774
---

# Список неоплаченных товаров, заказанных юридическими лицами

`POST /v1/posting/unpaid-legal/product/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `limit` — integer<int32> **обязательный**. Количество значений в ответе.

## Ответы

**200** — Список неоплаченных товаров

- `products` — array[object]. Список неоплаченных товаров.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `quantity` — integer<int32>. Количество экземпляров.
  - `name` — string. Название товара.
  - `image_url` — string. Ссылка на изображение товара.
- `cursor` — string. Указатель для выборки следующих данных.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
