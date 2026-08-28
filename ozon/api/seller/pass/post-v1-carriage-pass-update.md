---
title: Обновить пропуск
api: ozon-seller
method: POST
path: /v1/carriage/pass/update
operation_id: carriagePassUpdate
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 93a2da22be562c10
---

# Обновить пропуск

`POST /v1/carriage/pass/update`

## Запрос

**Тело запроса** (`application/json`):

- `arrival_passes` — array[object] **обязательный**. Список пропусков.
  - `driver_name` — string **обязательный**. ФИО водителя.
  - `driver_phone` — string **обязательный**. Номер телефона водителя.
  - `id` — integer<int64> **обязательный**. Идентификатор пропуска.
  - `vehicle_license_plate` — string **обязательный**. Номер автомобиля.
  - `vehicle_model` — string **обязательный**. Модель автомобиля.
  - `with_returns` — boolean. `true`, если будете вывозить возвраты. По умолчанию — `false`.
- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Пропуск обновлён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
