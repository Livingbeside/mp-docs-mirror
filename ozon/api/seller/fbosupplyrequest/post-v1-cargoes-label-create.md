---
title: Сгенерировать этикетки для грузомест
api: ozon-seller
method: POST
path: /v1/cargoes-label/create
operation_id: CargoesAPI_CargoesLabelCreate
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 287dbefa25c041c6
---

# Сгенерировать этикетки для грузомест

`POST /v1/cargoes-label/create`

Используйте метод, чтобы сгенерировать этикетки для грузомест из заявки на поставку.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cargoes` — array[object]. Информация о грузоместах.
  - `cargo_id` — integer<int64>. Идентификатор грузоместа.
- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки.

## Ответы

**200** — Результат запроса

- `operation_id` — string. Идентификатор операции.
- `errors` — object. Ошибки.
  - `error_reasons` — array[string (INVALID_STATE, OPERATION_NOT_FOUND, OPERATION_FAILED, SUPPLY_NOT_BELONG_CONTRACTOR, SUPPLY_NOT_BELONG_COMPANY, SUPPLY_IS_EMPTY, CARGOES_NOT_FOUND)]. Причина ошибки: - `INVALID_STATE` — недопустимое состояние поставки. - `OPERATION_NOT_FOUND` — операция не найдена. - `OPERATION_FAILED` — операция завершилась с ошибкой. - `SUPPLY_NOT_BELONG_CONTRACTOR` — контрагент не соответствует поставке. - `SUPPLY_NOT_BELONG_COMPANY` — компания не соответствует поставке. - `SUPPLY_IS_EMPTY` — поставка без грузомест. - `CARGOES_NOT_FOUND` — грузоместа не найдены.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
