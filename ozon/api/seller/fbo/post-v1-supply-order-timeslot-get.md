---
title: Интервалы поставки
api: ozon-seller
method: POST
path: /v1/supply-order/timeslot/get
operation_id: SupplyOrderAPI_GetSupplyOrderTimeslots
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e428bf0dd99cfde3
---

# Интервалы поставки

`POST /v1/supply-order/timeslot/get`

Метод устаревает и будет отключён 19 августа 2026 года. Переключитесь на /v2/supply-order/timeslot/list .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Список интервалов поставки

- `timeslots` — array[object]. Интервалы поставки.
  - `from` — string<date-time> **обязательный**. Начало интервала по местному времени.
  - `to` — string<date-time> **обязательный**. Конец интервала по местному времени.
- `timezone` — ?. Часовой пояс.
  - `iana_name` — string. Название часового пояса.
  - `offset` — string. Смещение часового пояса от UTC-0 в секундах.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
