---
title: Получить статус проверки электронной ТТН на прослеживаемой перевозке FBS
api: ozon-seller
method: POST
path: /v1/carriage/ettn/status
operation_id: CarriageEttnStatus
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 59283f8c17abb7a4
---

# Получить статус проверки электронной ТТН на прослеживаемой перевозке FBS

`POST /v1/carriage/ettn/status`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Статус проверки электронной ТТН

- `errors` — array[string]. Ошибки проверки электронной ТТН на прослеживаемой отгрузке.
- `status` — string (NOT_UPLOADED, PROCESSING, SUCCESS, FAILED). Статус проверки электронной ТТН на прослеживаемой отгрузке: - `NOT_UPLOADED` — не загружена; - `PROCESSING` — в процессе проверки; - `SUCCESS` — проверена; - `FAILED` — ошибка.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
