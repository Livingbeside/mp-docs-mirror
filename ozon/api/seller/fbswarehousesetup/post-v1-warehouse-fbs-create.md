---
title: Создать склад
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/create
operation_id: WarehouseAPI_CreateWarehouseFBS
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b6c52e927fd61f3d
---

# Создать склад

`POST /v1/warehouse/fbs/create`

Если создаёте склад с доставкой в drop-off пункт, используйте метод [/v1/warehouse/fbs/create/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForCreateFBSWarehouse), чтобы получить точки.

## Запрос

**Тело запроса** (`application/json`):

- `address_coordinates` — object **обязательный**. Координаты адреса склада.
  - `latitude` — number<double> **обязательный**. Широта.
  - `longitude` — number<double> **обязательный**. Долгота.
- `cut_in_time` — integer<int64> **обязательный**. Время на приём заказов в минутах. Например, если вы передадите `3000`, приём заказов будет завершён через 50 часов с момента передачи.
- `drop_off_point_id` — integer<int64>. Идентификатор drop-off пункта.
- `first_mile_type` — string (PICK_UP, DROP_OFF) **обязательный**. Тип первой мили: - `PICK_UP` — отгрузка заказов курьеру; - `DROP_OFF` — отгрузка заказов в пункт приёма.
- `is_kgt` — boolean **обязательный**. `true`, если товар крупногабаритный.
- `name` — string **обязательный**. Название склада.
- `options` — object. Параметры склада.
  - `comment` — string. Комментарий для курьера при отгрузке с типом `PICK_UP`.
  - `courier_phones` — array[string]. Номера телефонов для курьера при отгрузке с типом `PICK_UP`. Укажите в формате +7(XXX)XXX-XX-XX.
  - `is_auto_assembly` — boolean. `true`, если автосборка включена.
  - `is_waybill_enabled` — boolean. `true`, если печать транспортной накладной включена.
- `phone` — string **обязательный**. Номер телефона склада. Укажите в формате +7(XXX)XXX-XX-XX.
- `timeslot_id` — integer<int64> **обязательный**. Идентификатор таймслота.
- `return_point_id` — integer<int64>. Идентификатор пункта возврата. Получите значение параметра методом [/v1/warehouse/fbs/create/return-point/list](#operation/WarehouseFBSCreateReturnPointList).
- `working_days` — array[string (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY)]. Рабочие дни склада: - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье.

## Ответы

**200** — Склад создан

- `operation_id` — string. Идентификатор операции на создание FBS-склада. Чтобы получить статус операции, используйте метод [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
