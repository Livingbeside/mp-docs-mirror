---
title: Информация о перевозке
api: ozon-seller
method: POST
path: /v1/carriage/get
operation_id: CarriageGet
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 56bf473cccca1746
---

# Информация о перевозке

`POST /v1/carriage/get`

## Запрос

**Тело запроса** (`application/json`):

- `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.

## Ответы

**200** — Информация о перевозке

- `act_type` — string. Тип акта приёма-передачи. Актуально для продавцов FBS.
- `all_blr_traceable` — boolean. `true`, если отгрузка с прослеживаемыми товарами.
- `arrival_pass_ids` — array[string<int64>]. Список идентификаторов пропусков, оформленных на перевозку.
- `available_actions` — array[string]. Доступные действия с перевозкой: - `get_shipping_list` — получить лист отгрузки; - `get_act_of_acceptance` — получить акт приёма-передачи; - `get_waybill` — получить товарную накладную в формате PDF; - `set_arrival_passes` — [оформить пропуск](#operation/carriagePassCreate).
- `cancel_availability` — object. Возможность отмены.
  - `is_cancel_available` — boolean. `true`, если перевозку можно отменить.
  - `reason` — string. Причина, почему перевозку нельзя отменить.
- `carriage_id` — integer<int64>. Идентификатор перевозки.
- `company_id` — integer<int64>. Идентификатор продавца.
- `containers_count` — integer<int32>. Количество грузовых мест.
- `created_at` — string<date-time>. Дата создания перевозки.
- `delivery_method_id` — integer<int64>. Идентификатор метода доставки.
- `departure_date` — string. Дата выполнения перевозки.
- `first_mile_type` — string. Тип первой мили.
- `has_postings_for_next_carriage` — boolean. `true`, если есть отправления, которые не попали в перевозку, но нужно отгрузить.
- `integration_type` — string. Тип перевозки.
- `is_container_label_printed` — boolean. `true`, если вы уже напечатали этикетки на грузовые места.
- `is_econom` — boolean. `true`, если отгрузка относится к товарам «Суперэконом».
- `is_partial` — boolean. `true`, если перевозка частичная.
- `is_waybill_enabled` — boolean. `true`, если доступна печать транспортной накладной.
- `partial_num` — integer<int64>. Порядковый номер частичной перевозки.
- `retry_count` — integer<int32>. Количество повторных попыток создания перевозки.
- `status` — string. Статус перевозки: - `received` — идёт приёмка, - `closed` — завершена после приёмки, - `sended` — отправлена, - `cancelled` — отменена.
- `tpl_provider_id` — integer<int64>. Идентификатор провайдера доставки.
- `updated_at` — string<date-time>. Дата последнего обновления информации о перевозке.
- `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
