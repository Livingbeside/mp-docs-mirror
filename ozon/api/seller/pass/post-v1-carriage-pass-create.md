---
title: Создать пропуск
api: ozon-seller
method: POST
path: /v1/carriage/pass/create
operation_id: carriagePassCreate
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: cdce95a643195e6f
---

# Создать пропуск

`POST /v1/carriage/pass/create`

Идентификатор созданного пропуска добавится к перевозке.

## Запрос

**Тело запроса** (`application/json`):

- `arrival_passes` — array[object] **обязательный**. Список пропусков.
  - `driver_name` — string **обязательный**. ФИО водителя.
  - `driver_phone` — string **обязательный**. Номер телефона водителя.
  - `vehicle_license_plate` — string **обязательный**. Номер автомобиля.
  - `vehicle_model` — string **обязательный**. Модель автомобиля.
  - `with_returns` — boolean. `true`, если будете вывозить возвраты. По умолчанию — `false`.
- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Пропуск создан

- `arrival_pass_ids` — array[string<int64>]. Идентификаторы пропусков.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
