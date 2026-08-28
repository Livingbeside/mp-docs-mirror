---
title: Получить статус отмены заказа
api: ozon-seller
method: POST
path: /v1/order/cancel/status
operation_id: OrderAPI_OrderCancelStatus
tags:
  - OrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a1279d3e91024f7c
---

# Получить статус отмены заказа

`POST /v1/order/cancel/status`

## Запрос

**Тело запроса** (`application/json`):

- `order_number` — string **обязательный**. Номер заказа.

## Ответы

**200** — Статус отмены заказа

- `order_number` — string. Номер заказа.
- `posting_number` — array[string]. Список отправлений в заказе.
- `state` — string. Статус отмены заказа: - `Подтверждена`, - `На подтверждении`, - `Отклонена`, - `Ожидает обработки`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
