---
title: Получить статус операции
api: ozon-seller
method: POST
path: /v1/warehouse/operation/status
operation_id: GetWarehouseFBSOperationStatus
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 99529eb3ec165fb9
---

# Получить статус операции

`POST /v1/warehouse/operation/status`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции.

## Ответы

**200** — Статус операции

- `error` — object. Ошибка при обработке операции.
  - `code` — string. Код ошибки.
  - `message` — string. Описание ошибки.
- `result` — object. Результат операции.
  - `entity_id` — integer<int64>. Идентификатор обрабатываемой сущности. Если операция `CREATE_FBS_WAREHOUSE`, вернётся идентификатор склада.
- `status` — string (UNSPECIFIED, IN_PROGRESS, SUCCESS, ERROR). Статус операции: - `UNSPECIFIED` — не определено; - `IN_PROGRESS` — в процессе; - `SUCCESS` — выполнена; - `ERROR` — завершилась с ошибкой. По умолчанию: `UNSPECIFIED`.
- `type` — string (UNSPECIFIED, CREATE_FBS_WAREHOUSE, UPDATE_FBS_WAREHOUSE, SET_FIRST_MILE, WAREHOUSE_ENABLE_DISABLE, WAREHOUSE_PAUSE_UNPAUSE). Тип операции: - `UNSPECIFIED` — не определено; - `CREATE_FBS_WAREHOUSE` — создание FBS-склада; - `UPDATE_FBS_WAREHOUSE` — обновление FBS-склада; - `SET_FIRST_MILE` — установка первой мили; - `WAREHOUSE_ENABLE_DISABLE` — архивация или разархивация FBS-склада; - `WAREHOUSE_PAUSE_UNPAUSE` — включение или выключение паузы rFBS-склада. По умолчанию: `UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
