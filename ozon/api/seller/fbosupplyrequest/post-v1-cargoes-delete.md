---
title: Удалить грузоместо в заявке на поставку
api: ozon-seller
method: POST
path: /v1/cargoes/delete
operation_id: CargoesAPI_CargoesDelete
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5cb6a4cdb4994392
---

# Удалить грузоместо в заявке на поставку

`POST /v1/cargoes/delete`

Метод для удаления грузомест в заявке на поставку.

Чтобы проверить статус удаления, используйте метод [/v1/cargoes/delete/status](#operation/CargoesAPI_CargoesDeleteStatus).

## Запрос

**Тело запроса** (`application/json`):

- `cargo_ids` — array[string<int64>] **обязательный**. Список идентификаторов грузомест, которые нужно удалить. Максимум 70 значений.
- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки.

## Ответы

**200** — Грузоместо удалено

- `errors` — object. Список ошибок, которые возникли при удалении грузомест.
  - `cargo_error_reasons` — array[object]. Ошибки при удалении грузомест.
    - `cargo_id` — integer<int64>. Идентификатор грузоместа.
    - `error_reasons` — array[string (CARGO_NOT_FOUND)]. Список ошибок грузоместа. Если значение `CARGO_NOT_FOUND`, грузоместо не найдено.
  - `supply_error_reasons` — array[string (SUPPLY_NOT_FOUND, CANT_DELETE_ALL_CARGOES, SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR, SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY, SUPPLY_CARGOES_IS_FINALIZED, SUPPLY_CARGOES_LOCKED, OPERATION_NOT_FOUND)]. Список ошибок поставки: - `SUPPLY_NOT_FOUND` — поставка не найдена, - `CANT_DELETE_ALL_CARGOES` — нельзя удалять все грузоместа, - `SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR` — не принадлежит вашему юридическому лицу, - `SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY` — не принадлежит вашему кабинету, - `SUPPLY_CARGOES_IS_FINALIZED` — грузоместа поставки нельзя редактировать, - `SUPPLY_CARGOES_LOCKED` — другой процесс блокирует редактирование грузомест поставки, - `OPERATION_NOT_FOUND` — операция не найдена.
- `operation_id` — string. Идентификатор операции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
