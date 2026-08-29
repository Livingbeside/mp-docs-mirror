---
title: Создать склад с методом доставки «Вы или сторонняя служба»
api: ozon-seller
method: POST
path: /v1/warehouse/erfbs/non-integrated/create
operation_id: WarehouseERFBSNonIntegratedCreate
tags:
  - rFBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ec57c0de751c4629
---

# Создать склад с методом доставки «Вы или сторонняя служба»

`POST /v1/warehouse/erfbs/non-integrated/create`

[Подробнее о схеме realFBS Express](https://seller-edu.ozon.ru/rfbs/scheme-of-work/rfbs-express#%D1%87%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-realfbs-express)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `address_coordinates` — object **обязательный**. Координаты адреса склада.
  - `latitude` — number<double> **обязательный**. Широта.
  - `longitude` — number<double> **обязательный**. Долгота.
- `is_auto_assembly` — boolean. `true`, если на складе доступна автосборка. По умолчанию: `False`.
- `delivery_method` — object **обязательный**. Информация о методе доставки «Вы или сторонняя служба».
  - `courier_cutoff` — integer<int64> **обязательный**. Скорость отгрузки в доставку.
  - `cut_in` — integer (15, 30, 60, 120, 180, 240, 300, 360, 420, 480) **обязательный**. Время сборки.
  - `delivery_polygons` — array[object] **обязательный**. Полигоны доставки, созданные через [/v1/polygon/create](#operation/PolygonAPI_CreatePolygon), с указанием времени доставки в каждый.
    - `id` — integer<int64> **обязательный**. Идентификатор полигона.
    - `time` — integer (15, 30, 45, 60, 90, 120, 150) **обязательный**. Время в минутах, за которое доставят товар в этом полигоне.
  - `name` — string **обязательный**. Название метода доставки.
  - `return_settings` — object **обязательный**. Информация о получении возвратов от покупателей.
    - `contact_days` — integer<int64>. Количество дней, за которое вы свяжетесь с покупателем. Параметр обязательный, если `return_method = COURIER`.
    - `post_office_zipcode` — string. Индекс отделения Почты России для [«лёгкого возврата»](https://seller-edu.ozon.ru/rfbs/vozvraty/vozvraty#%C2%AB%D0%BB%D1%91%D0%B3%D0%BA%D0%B8%D0%B8-%D0%B2%D0%BE%D0%B7%D0%B2%D1%80%D0%B0%D1%82%C2%BB-%D0%BF%D0%BE%D1%87%D1%82%D0%BE%D0%B8-%D1%80%D0%BE%D1%81%D1%81%D0%B8%D0%B8).
    - `return_method` — string (COURIER, TRANSPORT_COMPANY) **обязательный**. Способы возврата: - `COURIER` — курьером, - `TRANSPORT_COMPANY` — транспортной компанией.
    - `transport_company_name` — string. Название транспортной компании, если способ возврата `TRANSPORT_COMPANY`.
- `min_order_value` — integer<int64>. Минимальная стоимость заказа в рублях.
- `name` — string **обязательный**. Название склада.
- `phone` — string **обязательный**. Номер телефона склада.
- `timetable_warehouse` — object **обязательный**. Расписание работы склада.
  - `holidays` — array[object]. Выходные дни склада.
    - `day` — string. День в формате `YYYY-MM-DD`.
    - `from` — string. Время начала выходного дня в формате `HH:MM`.
    - `to` — string. Время окончания выходного дня в формате `HH:MM`.
  - `working_days` — array[object] **обязательный**. Рабочие дни склада.
    - `day` — string (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY) **обязательный**. Рабочий день: - `MONDAY` — понедельник, - `TUESDAY` — вторник, - `WEDNESDAY` — среда, - `THURSDAY` — четверг, - `FRIDAY` — пятница, - `SATURDAY` — суббота, - `SUNDAY` — воскресенье.
    - `from` — string **обязательный**. Время начала рабочего дня в формате `HH:MM`.
    - `to` — string **обязательный**. Время окончания рабочего дня в формате `HH:MM`.

## Ответы

**200** — Склад создан

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
