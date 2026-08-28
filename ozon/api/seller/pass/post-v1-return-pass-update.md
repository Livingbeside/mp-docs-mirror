---
title: Обновить пропуск для возврата
api: ozon-seller
method: POST
path: /v1/return/pass/update
operation_id: returnPassUpdate
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7daaab3d994ddb2f
---

# Обновить пропуск для возврата

`POST /v1/return/pass/update`

## Запрос

**Тело запроса** (`application/json`):

- `arrival_passes` — array[object] **обязательный**. Список пропусков.
  - `arrival_pass_id` — integer<int64> **обязательный**. Идентификатор пропуска.
  - `arrival_time` — string<date-time> **обязательный**. Время прибытия в формате UTC. В это время начнёт действовать пропуск. Чтобы изменить время прибытия, используйте метод [/v1/carriage/pass/update](#operation/carriagePassUpdate).
  - `driver_name` — string **обязательный**. ФИО водителя.
  - `driver_phone` — string **обязательный**. Номер телефона водителя.
  - `vehicle_license_plate` — string **обязательный**. Номер автомобиля.
  - `vehicle_model` — string **обязательный**. Модель автомобиля.

## Ответы

**200** — Пропуск обновлён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
