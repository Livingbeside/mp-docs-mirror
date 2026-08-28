---
title: Отменить заказ
api: ozon-seller
method: POST
path: /v1/order/cancel
operation_id: OrderAPI_OrderCancel
tags:
  - OrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7d39b6688b0a5022
---

# Отменить заказ

`POST /v1/order/cancel`

Отменяет заказ со всеми отправлениями. Используйте идентификатор причины отмены `reasons.id` из метода [/v1/cancel-reason/list-by-order](#operation/CancelReasonListByOrder).

## Запрос

**Тело запроса** (`application/json`):

- `order_number` — string **обязательный**. Номер заказа.
- `reason_id` — integer<int32> **обязательный**. Идентификатор причины отмены заказа.
- `reason_message` — string. Причина отмены заказа.

## Ответы

**200** — Заказ отменён

- `message` — string. Статус обработки отмены.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
