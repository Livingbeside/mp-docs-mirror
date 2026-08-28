---
title: Отменить заявку на поставку
api: ozon-seller
method: POST
path: /v1/supply-order/cancel
operation_id: SupplyOrderAPI_SupplyOrderCancel
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f06f77150ff5c86a
---

# Отменить заявку на поставку

`POST /v1/supply-order/cancel`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Отмена заявки на поставку в процессе

- `operation_id` — string. Идентификатор операции на отмену заявки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
