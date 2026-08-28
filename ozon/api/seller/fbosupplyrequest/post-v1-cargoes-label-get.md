---
title: Получить идентификатор этикетки для грузомест
api: ozon-seller
method: POST
path: /v1/cargoes-label/get
operation_id: CargoesAPI_CargoesLabelGet
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 25c413b5ba4b15e2
---

# Получить идентификатор этикетки для грузомест

`POST /v1/cargoes-label/get`

Возвращает статус формирования этикеток и ссылку на PDF-файл с ними.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции.

## Ответы

**200** — Этикетка для грузомест

- `result` — object. Информация об этикетках.
  - `file_guid` — string. Идентификатор для получения файла с этикетками.
  - `file_url` — string. Ссылка на PDF-файл с этикетками.
- `status` — string (SUCCESS, IN_PROGRESS, FAILED). Статус формирования этикеток: - `SUCCESS` — готовы. - `IN_PROGRESS` — формируются. - `FAILED` — ошибка при формировании. По умолчанию: `SUCCESS`.
- `errors` — object. Ошибки.
  - `error_reasons` — array[string (INVALID_STATE, OPERATION_NOT_FOUND, OPERATION_FAILED, SUPPLY_NOT_BELONG_CONTRACTOR, SUPPLY_NOT_BELONG_COMPANY, SUPPLY_IS_EMPTY, CARGOES_NOT_FOUND)]. Причина ошибки: - `INVALID_STATE` — недопустимое состояние поставки. - `OPERATION_NOT_FOUND` — операция не найдена. - `OPERATION_FAILED` — операция завершилась с ошибкой. - `SUPPLY_NOT_BELONG_CONTRACTOR` — контрагент не соответствует поставке. - `SUPPLY_NOT_BELONG_COMPANY` — компания не соответствует поставке. - `SUPPLY_IS_EMPTY` — поставка без грузомест. - `CARGOES_NOT_FOUND` — грузоместа не найдены.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
