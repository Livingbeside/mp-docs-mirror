---
title: Информация о статусе удаления грузоместа
api: ozon-seller
method: POST
path: /v1/cargoes/delete/status
operation_id: CargoesAPI_CargoesDeleteStatus
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bd856ea89ddd4dff
---

# Информация о статусе удаления грузоместа

`POST /v1/cargoes/delete/status`

Метод для получения статуса удаления грузомест в заявке на поставку.

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции.

## Ответы

**200** — Статус удаления грузоместа

- `errors` — object. Список ошибок, которые возникли при удалении грузомест.
  - `cargo_error_reasons` — array[object]. Ошибки при удалении грузомест.
    - `cargo_id` — integer<int64>. Идентификатор грузоместа.
    - `error_reasons` — array[string (CARGO_NOT_FOUND)]. Список ошибок грузоместа. Если значение `CARGO_NOT_FOUND`, грузоместо не найдено.
  - `supply_error_reasons` — array[string (SUPPLY_NOT_FOUND, CANT_DELETE_ALL_CARGOES, SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR, SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY, SUPPLY_CARGOES_IS_FINALIZED, SUPPLY_CARGOES_LOCKED, OPERATION_NOT_FOUND)]. Список ошибок поставки: - `SUPPLY_NOT_FOUND` — поставка не найдена, - `CANT_DELETE_ALL_CARGOES` — нельзя удалять все грузоместа, - `SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR` — не принадлежит вашему юридическому лицу, - `SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY` — не принадлежит вашему кабинету, - `SUPPLY_CARGOES_IS_FINALIZED` — грузоместа поставки нельзя редактировать, - `SUPPLY_CARGOES_LOCKED` — другой процесс блокирует редактирование грузомест поставки, - `OPERATION_NOT_FOUND` — операция не найдена.
- `status` — string (SUCCESS, IN_PROGRESS, ERROR). Статус удаления грузоместа. Возможные статусы: - `SUCCESS` — грузоместо удалено, - `IN_PROGRESS` — грузоместо в процессе удаления, - `ERROR` — возникла ошибка при удалении грузоместа.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
