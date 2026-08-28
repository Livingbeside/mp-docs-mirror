---
title: Получить список доступных интервалов поставки
api: ozon-seller
method: POST
path: /v2/supply-order/timeslot/list
operation_id: SupplyOrderTimeslotList
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4c10437686d0aba3
---

# Получить список доступных интервалов поставки

`POST /v2/supply-order/timeslot/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Список интервалов поставки

- `limit_exceeded` — object. Информация о превышении лимита изменений интервала поставки.
  - `changes_limit` — integer<int32>. Остаток доступных изменений интервала поставки.
- `timeslot_change_forbidden` — object. Информация о причинах, по которым нельзя изменить интервал поставки.
  - `error_reasons` — array[string (INVALID_ORDER_STATE, IS_VIRTUAL, SET_TIMESLOT_DEADLINE_EXCEED, ORDER_DOES_NOT_BELONG_TO_COMPANY)]. Причина, по которой нельзя изменить интервал поставки: - `INVALID_ORDER_STATE` — неверный статус заявки на поставку; - `IS_VIRTUAL` — заявка на поставку виртуальная; - `SET_TIMESLOT_DEADLINE_EXCEED` — заявка на поставку просрочена; - `ORDER_DOES_NOT_BELONG_TO_COMPANY` — заявка на поставку не принадлежит продавцу.
- `timeslots_info` — object. Информация об интервалах поставки.
  - `limitations` — object. Ограничения на обновления интервала поставки.
    - `changes_count` — integer<int64>. Количество изменений интервала поставки.
    - `changes_limit` — integer<int64>. Остаток доступных изменений интервала поставки.
  - `timeslots` — array[object]. Список интервалов поставки.
    - `from` — string<date-time>. Начало интервала по местному времени.
    - `to` — string<date-time>. Конец интервала по местному времени.
  - `timezone` — object. Часовой пояс.
    - `iana_name` — string. Название часового пояса.
    - `offset` — integer<int64>. Смещение часового пояса от UTC-0 в секундах.

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
