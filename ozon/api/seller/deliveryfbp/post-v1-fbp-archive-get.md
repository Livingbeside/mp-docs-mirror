---
title: Получить информацию о завершённой поставке
api: ozon-seller
method: POST
path: /v1/fbp/archive/get
operation_id: FbpAPI_FbpArchiveGet
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ba35c8854fe10e0e
---

# Получить информацию о завершённой поставке

`POST /v1/fbp/archive/get`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Информация о завершённой поставке

- `act_file_uuid` — string. Идентификатор акта приёмки.
- `bundle_id` — string. Идентификатор провалидированного списка товаров.
- `bundle_sku_summary` — object. Сводная информация по товарам в поставке.
  - `rounded_total_volume_in_litres` — number<double>. Общий объём товаров в литрах.
  - `total_items_count` — integer<int64>. Количество SKU в поставке.
  - `total_quantity` — integer<int64>. Количество единиц товаров в поставке.
- `business_flow_type_id` — integer<int64>. Идентификатор типа поставки.
- `created_date` — string<date-time>. Дата и время создания заявки на поставку.
- `decline_reason` — object. Причина отклонения поставки.
  - `code` — string (DECLINE_REASON_CODE_UNSPECIFIED, CANNOT_CREATE_SUPPLY_ON_TPF, DROP_OFF_POINT_CLOSED, CODE_SUPPLY_LOST, COURIER_PICK_UP_REJECTED_BY_SELLER, BONDED_DOCUMENTS_REJECTED_BY_WAREHOUSE). Код причины отклонения поставки: - `DECLINE_REASON_CODE_UNSPECIFIED` — не определён; - `CANNOT_CREATE_SUPPLY_ON_TPF` — не удалось создать поставку на стороне 3PF; - `DROP_OFF_POINT_CLOSED` — дроп-офф точка закрыта; - `CODE_SUPPLY_LOST` — поставка потеряна; - `COURIER_PICK_UP_REJECTED_BY_SELLER` — продавец отказался от забора поставки курьером; - `BONDED_DOCUMENTS_REJECTED_BY_WAREHOUSE` — проблемы с бондовыми документами. По умолчанию: `DECLINE_REASON_CODE_UNSPECIFIED`.
  - `message` — string. Описание причины отклонения.
- `delivery_details` — object. Детали доставки.
  - `direct_details` — object. Детали доставки продавцом.
    - `by_seller_details` — object. Детали доставки силами продавца.
      - `driver_name` — string. ФИО водителя.
      - `vehicle_registration_number` — string. Регистрационный номер транспорта.
      - `vehicle_type` — string. Тип транспорта.
    - `by_tpl_details` — object. Детали доставки сторонней транспортной компанией.
      - `tracking_number` — string. Трек-номер отправления.
      - `transport_company_name` — string. Название транспортной компании.
    - `timeslot_details` — object. Детали интервала поставки.
      - `timeslot` — object. Таймслот.
        - `timeslot_end` — string<date-time>. Время окончания таймслота по UTC.
        - `timeslot_start` — string<date-time>. Время начала таймслота по UTC.
      - `timeslot_reservation_id` — string. Идентификатор бронирования интервала поставки.
  - `drop_off_point` — object. Детали drop-off пункта.
    - `id` — integer<int64>. Идентификатор drop-off пункта.
    - `province_uuid` — string. Уникальный идентификатор провинции.
    - `timeslot` — object. Таймслот.
      - `timeslot_end` — string<date-time>. Время окончания таймслота по UTC.
      - `timeslot_start` — string<date-time>. Время начала таймслота по UTC.
  - `pickup_details` — object. Детали пункта выдачи.
    - `address` — string. Адрес.
    - `comment` — string. Комментарий.
    - `date` — string<date-time>. Дата доставки.
    - `sender_name` — string. ФИО отправителя.
    - `sender_phone` — string. Номер телефона отправителя.
  - `supply_type` — string (SUPPLY_TYPE_UNSPECIFIED, DIRECT_BY_SELLER, DIRECT_BY_TPL, DROP_OFF, PICK_UP). Тип поставки: - `SUPPLY_TYPE_UNSPECIFIED` — не определён; - `DIRECT_BY_SELLER` — доставка до склада силами продавца; - `DIRECT_BY_TPL` — доставка до склада сторонней транспортной компанией; - `DROP_OFF` — доставка до drop-off пункта; - `PICK_UP` — доставка курьером от склада продавца. По умолчанию: `SUPPLY_TYPE_UNSPECIFIED`.
- `has_act` — boolean. `true`, если был сформирован акт приёмки.
- `has_label` — boolean. `true`, если были сформированы этикетки.
- `id` — integer<int64>. Номер записи в архиве.
- `order_draft_id` — integer<int64>. Идентификатор черновика поставки.
- `order_number` — string. Идентификатор завершённой поставки.
- `package_units_count` — integer<int32>. Количество грузомест.
- `receive_date` — string<date-time>. Дата и время принятия поставки.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.
- `status` — string (ARCHIVE_STATUS_UNSPECIFIED, COMPLETED, REJECTED_AT_SUPPLY_WAREHOUSE, CANCELLED_BY_SELLER). Статус завершённой поставки: - `ARCHIVE_STATUS_UNSPECIFIED` — не определён; - `COMPLETED` — завершена; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отклонена складом; - `CANCELLED_BY_SELLER` — отменена продавцом. По умолчанию: `ARCHIVE_STATUS_UNSPECIFIED`.
- `supply_id` — string. Идентификатор поставки.
- `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
