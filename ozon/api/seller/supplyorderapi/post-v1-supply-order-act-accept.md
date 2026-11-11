---
title: Согласовать акт
api: ozon-seller
method: POST
path: /v1/supply-order/act/accept
operation_id: SupplyOrderActAccept
tags:
  - SupplyOrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c5cd82df6c9bbfda
---

# Согласовать акт

`POST /v1/supply-order/act/accept`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `act_id` — integer<int64> **обязательный**. Идентификатор акта из методов [/v1/supply-order/act/summary/get](#operation/SupplyOrderActSummaryGet) или [/v1/supply-order/act/product/get](#operation/SupplyOrderActProductGet).

## Ответы

**200** — Акт согласован

- `error_reasons` — array[string (UNSPECIFIED, INVALID_STATE, SUPPLY_WITH_UTD)]. Ошибки при принятии акта: - `UNSPECIFIED` — не определена; - `INVALID_STATE` — некорректный статус; - `SUPPLY_WITH_UTD` — поставка с УПД.
- `operation_id` — string. Идентификатор операции.

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
