---
title: Получить информацию о черновике поставки
api: ozon-seller
method: POST
path: /v1/fbp/draft/get
operation_id: FbpAPI_FbpDraftGet
tags:
  - DeliveryFBPDraft
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b48aa0db60512fd5
---

# Получить информацию о черновике поставки

`POST /v1/fbp/draft/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Детали черновика поставки

- `bundle_id` — string. Идентификатор списка провалидированных товаров.
- `cancellation_state` — object. Статус отмены.
  - `cancellation_error` — object. Ошибка отмены.
    - `error_code` — string (CODE_UNSPECIFIED, NO_RESPONSE_FROM_3PF, ACCEPTANCE_ALREADY_STARTED). Код ошибки: - `CODE_UNSPECIFIED` — не определён; - `NO_RESPONSE_FROM_3PF` — отмена заявки не подтверждена, мы не получили ответа от склада партнёра; - `ACCEPTANCE_ALREADY_STARTED` — отмена заявки не подтверждена, приёмка уже началась. По умолчанию: `CODE_UNSPECIFIED`.
    - `message` — string. Описание ошибки.
  - `cancellation_status` — string (STATUS_UNSPECIFIED, CONFIRMATION, CANCELED, NOT_CANCELED). Статус ошибки: - `STATUS_UNSPECIFIED` — не определён; - `CONFIRMATION` — ожидается подтверждение отмены заявки; - `CANCELED` — подтверждение получено; - `NOT_CANCELED` — подтверждение не получено. По умолчанию: `STATUS_UNSPECIFIED`.
- `created_at` — string<date-time>. Дата создания черновика.
- `decline_reason` — object. Причина отказа.
  - `failed_sku_ids` — array[string<int64>]. Некорректные идентификаторы SKU.
  - `message` — string. Текст отказа.
- `deleted_at` — string<date-time>. Дата удаления черновика.
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
- `editable` — boolean. `true`, если черновик можно изменить.
- `id` — integer<int64>. Идентификатор черновика.
- `is_cancelable` — boolean. `true`, если черновик можно отменить.
- `is_deletable` — boolean. `true`, если черновик можно удалить.
- `is_registration_available` — boolean. `true`, если доступна регистрация.
- `locked` — boolean. `true`, если черновик заблокирован.
- `package_units_count` — integer<int32>. Количество грузомест.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.
- `status` — string (DRAFT_STATUS_UNSPECIFIED, NEW, SUPPLY_VARIANT_CONFIRMATION, SUPPLY_NOT_CONFIRMED). Статус черновика: - `DRAFT_STATUS_UNSPECIFIED` — не определён; - `NEW` — новый; - `SUPPLY_VARIANT_CONFIRMATION` — ожидает подтверждения; - `SUPPLY_NOT_CONFIRMED` — отклонён складом. По умолчанию: `DRAFT_STATUS_UNSPECIFIED`.
- `supply_id` — string. Идентификатор поставки.
- `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
