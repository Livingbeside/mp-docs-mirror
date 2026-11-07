---
title: Получить код выдачи заказа
api: ozon-seller
method: POST
path: /v1/order/code/get
operation_id: OrderAPI_OrderCodeGet
tags:
  - OrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 62e1b1bb96278a47
---

# Получить код выдачи заказа

`POST /v1/order/code/get`

Метод возвращает код выдачи заказа для покупателя. Используйте полученный код, чтобы сформировать QR-код.

## Запрос

**Тело запроса** (`application/json`):

- `order_number` — string **обязательный**. Номер заказа.

## Ответы

**200** — Код выдачи заказа

- `code` — string. Код выдачи.
- `valid_until` — string<date-time>. Дата и время, до которого действует код выдачи.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
