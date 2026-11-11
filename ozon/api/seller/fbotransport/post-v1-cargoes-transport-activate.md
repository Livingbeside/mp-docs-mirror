---
title: Включить или отключить транспортные грузоместа в поставке
api: ozon-seller
method: POST
path: /v1/cargoes/transport/activate
operation_id: CargoesTransportActivate
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 27b2ebe55d56abdc
---

# Включить или отключить транспортные грузоместа в поставке

`POST /v1/cargoes/transport/activate`

Если в поставке создано грузоместо, отключить транспортные грузоместа не получится.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `is_transport` — boolean **обязательный**. `true`, чтобы включить транспортные грузоместа.
- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки. Получите значение параметра методом [/v3/supply-order/get](#operation/SupplyOrderGet).

## Ответы

**200** — Транспортные грузоместа включены или отключены

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/cargoes/transport/activate/status](#operation/CargoesTransportActivateStatus).

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
