---
title: Получить список поставок
api: ozon-seller
method: POST
path: /v1/fbp/order/list
operation_id: FbpAPI_FbpOrderList
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bc3d5644180d4082
---

# Получить список поставок

`POST /v1/fbp/order/list`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `count` — integer<int32> **обязательный**. Количество поставок в ответе.
- `last_id` — integer<int64>. Идентификатор последней поставки на странице. Для первого запроса оставьте это поле пустым. Чтобы получить следующие значения, укажите `id` последней поставки из ответа предыдущего запроса.

## Ответы

**200** — Список поставок

- `has_next` — boolean. `true`, если в ответе вернули не все поставки.
- `items` — array[object]. Поставки.
  - `attention_reasons` — array[string (ORDER_ATTENTION_TYPE_UNSPECIFIED, OLD, TIME_SLOT_EXPIRED)]. Причины предупреждения: - `ORDER_ATTENTION_TYPE_UNSPECIFIED` — не определена; - `OLD` — устаревшая заявка; - `TIME_SLOT_EXPIRED` — таймслот просрочен. По умолчанию: `ORDER_ATTENTION_TYPE_UNSPECIFIED`.
  - `bundle_summary` — object. Сводная информация по товарам в поставке.
    - `rounded_total_volume_in_litres` — number<double>. Общий объём товаров в литрах.
    - `total_item_count` — integer<int32>. Количество SKU в поставке.
    - `total_quantity` — integer<int32>. Количество единиц товаров в поставке.
  - `can_be_cancelled` — boolean. `true`, если заявку можно отменить.
  - `cancellation_state` — object. Статус отмены.
    - `cancellation_error` — object. Ошибка отмены.
      - `error_code` — string (CODE_UNSPECIFIED, NO_RESPONSE_FROM_3PF, ACCEPTANCE_ALREADY_STARTED). Код ошибки: - `CODE_UNSPECIFIED` — не определён; - `NO_RESPONSE_FROM_3PF` — отмена заявки не подтверждена, мы не получили ответа от склада партнёра; - `ACCEPTANCE_ALREADY_STARTED` — отмена заявки не подтверждена, приёмка уже началась. По умолчанию: `CODE_UNSPECIFIED`.
      - `message` — string. Описание ошибки.
    - `cancellation_status` — string (STATUS_UNSPECIFIED, CONFIRMATION, CANCELED, NOT_CANCELED). Статус ошибки: - `STATUS_UNSPECIFIED` — не определён; - `CONFIRMATION` — ожидается подтверждение отмены заявки; - `CANCELED` — подтверждение получено; - `NOT_CANCELED` — подтверждение не получено. По умолчанию: `STATUS_UNSPECIFIED`.
  - `created_date` — string<date-time>. Дата создания поставки.
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
  - `has_consignment_note` — boolean. `true`, если есть подписанные документы.
  - `has_label` — boolean. `true`, если есть этикетки.
  - `id` — integer<int64>. Идентификатор заявки на поставку.
  - `locked` — boolean. `true`, если нельзя редактировать поставку.
  - `order_number` — string. Номер поставки.
  - `package_units_count` — integer<int32>. Количество грузомест.
  - `receive_date` — string<date-time>. Дата и время принятия поставки.
  - `status` — string (ORDER_STATUS_UNSPECIFIED, READY_TO_SUPPLY, FILLING_DELIVERY_DETAILS, COURIER_ASSIGNED, COURIER_PICKED_UP, ACCEPTANCE_AT_DROP_OFF_POINT, IN_TRANSIT_TO_STORAGE_WAREHOUSE, ACCEPTANCE_AT_STORAGE_WAREHOUSE, CANCELLED). Статус заказа: - `ORDER_STATUS_UNSPECIFIED` — не определён; - `READY_TO_SUPPLY` — готов к отгрузке; - `FILLING_DELIVERY_DETAILS` — заполнение данных поставки; - `COURIER_ASSIGNED` — курьер назначен; - `COURIER_PICKED_UP` — курьер забрал поставку; - `ACCEPTANCE_AT_DROP_OFF_POINT` — принято на drop-off пункте; - `IN_TRANSIT_TO_STORAGE_WAREHOUSE` — в пути на склад размещения; - `ACCEPTANCE_AT_STORAGE_WAREHOUSE` — приёмка на складе; - `CANCELLED` — заявка отменена. По умолчанию: `ORDER_STATUS_UNSPECIFIED`.
  - `supply_id` — string. Идентификатор поставки.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
- `last_id` — integer<int64>. Идентификатор последней поставки на странице.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
