---
title: Создать пропуск для возврата
api: ozon-seller
method: POST
path: /v1/return/pass/create
operation_id: returnPassCreate
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3e1dbf10fbf7f585
---

# Создать пропуск для возврата

`POST /v1/return/pass/create`

## Запрос

**Тело запроса** (`application/json`):

- `arrival_passes` — array[object] **обязательный**. Список пропусков.
  - `arrival_time` — string<date-time> **обязательный**. Время прибытия в формате UTC. В это время пропуск начнёт действовать.
  - `driver_name` — string **обязательный**. ФИО водителя.
  - `driver_phone` — string **обязательный**. Номер телефона водителя.
  - `dropoff_point_id` — integer<int64> **обязательный**. Идентификатор склада, на который оформляется пропуск.
  - `vehicle_license_plate` — string **обязательный**. Номер автомобиля.
  - `vehicle_model` — string **обязательный**. Модель автомобиля.
  - `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада продавца. Можно получить с помощью метода [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList).

## Ответы

**200** — Пропуск создан

- `arrival_pass_ids` — array[string<int64>]. Идентификаторы пропусков.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
