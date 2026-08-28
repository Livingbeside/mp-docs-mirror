---
title: Список пропусков
api: ozon-seller
method: POST
path: /v1/pass/list
operation_id: PassList
tags:
  - Pass
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 77e9e27e1948362a
---

# Список пропусков

`POST /v1/pass/list`

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтры.
  - `arrival_pass_ids` — array[string<int64>]. Фильтр по идентификатору пропуска.
  - `arrival_reason` — string. Фильтр по цели въезда: - `FBS_DELIVERY` — отгрузка. - `FBS_RETURN` — вывоз возвратов. Если параметр не указан, учитываются обе цели. Указанная причина должна быть в списке причин в пропусках.
  - `dropoff_point_ids` — array[string<int64>]. Фильтр по точке отгрузки.
  - `only_active_passes` — boolean. `true`, чтобы получить только активные заявки на пропуск.
  - `warehouse_ids` — array[string<int64>]. Фильтр по складу продавца. Можно получить с помощью метода [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList).
- `limit` — integer<int32> **обязательный**. Ограничение по количеству записей в ответе. По умолчанию: `1000`.

## Ответы

**200** — Список пропусков

- `arrival_passes` — array[object]. Список пропусков для перевозки.
  - `arrival_pass_id` — integer<int64>. Идентификатор пропуска.
  - `arrival_reasons` — array[string]. Цель приезда.
  - `arrival_time` — string<date-time>. Дата и время въезда в формате UTC.
  - `driver_name` — string. ФИО водителя.
  - `driver_phone` — string. Номер телефона водителя.
  - `dropoff_point_id` — integer<int64>. Идентификатор точки отгрузки.
  - `is_active` — boolean. `true`, если заявка активна.
  - `vehicle_license_plate` — string. Номер автомобиля.
  - `vehicle_model` — string. Модель автомобиля.
  - `warehouse_id` — integer<int64>. Идентификатор склада продавца.
- `cursor` — string. Указатель для выборки следующих данных. Если параметр пустой, данных больше нет.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
