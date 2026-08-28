---
title: Список отправлений в акте
api: ozon-seller
method: POST
path: /v2/posting/fbs/act/get-postings
operation_id: PostingAPI_ActPostingList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 098414fc0b796adb
---

# Список отправлений в акте

`POST /v2/posting/fbs/act/get-postings`

Возвращает список отправлений в акте по его идентификатору.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `id` — int<int64> **обязательный**. Идентификатор акта. Получите значение параметра методом [/v2/posting/fbs/act/list](#operation/PostingAPI_FbsActList) или [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate).

## Ответы

**200** — Список отправлений

- `result` — array[object]. Информация об отправлениях.
  - `id` — integer<int64>. Идентификатор акта.
  - `multi_box_qty` — integer<int32>. Количество коробок, в которые упакован товар.
  - `posting_number` — string. Номер отправления.
  - `status` — string. Статус отправления.
  - `seller_error` — string. Расшифровка кода ошибки.
  - `updated_at` — string<date-time>. Дата и время обновления записи об отправлении.
  - `created_at` — string<date-time>. Дата и время создания записи об отправлении.
  - `products` — array[object]. Список товаров в отправлении.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — string. Цена товара.
    - `quantity` — integer<int32>. Количество товара в отправлении.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

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
