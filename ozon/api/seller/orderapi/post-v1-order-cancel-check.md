---
title: Проверить возможность отмены заказа
api: ozon-seller
method: POST
path: /v1/order/cancel/check
operation_id: OrderAPI_OrderCancelCheck
tags:
  - OrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a6fbd958ab3a9958
---

# Проверить возможность отмены заказа

`POST /v1/order/cancel/check`

Возвращает возможность отмены заказа для покупателя.

## Запрос

**Тело запроса** (`application/json`):

- `order_number` — string **обязательный**. Номер заказа.

## Ответы

**200** — Результат проверки

- `cancellable` — boolean. `true`, если заказ можно отменить.
- `order_number` — string. Номер заказа.
- `posting_groups` — array[object]. Группы отправлений.
  - `posting_numbers` — array[string]. Список отправлений в группе.
- `postings` — array[object]. Информация о возможности отмены отправлений.
  - `cancellable` — boolean. `true`, если отправление можно отменить.
  - `posting_number` — string. Идентификатор отправления.
  - `why_not_cancellable` — string. Причина, по которой отправление нельзя отменить.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
