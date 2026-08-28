---
title: Список складов
api: ozon-seller
method: POST
path: /v2/warehouse/list
operation_id: WarehouseListV2
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 64df58404b5ae8b6
---

# Список складов

`POST /v2/warehouse/list`

Метод возвращает список складов FBS и rFBS. Чтобы получить список складов FBO, используйте метод [/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer **обязательный**. Количество значений в ответе.
- `cursor` — string. Указатель для выборки следующих данных.
- `warehouse_ids` — array[string<int64>]. Идентификаторы складов.

## Ответы

**200** — Список складов

- `cursor` — string. Указатель для выборки следующих данных.
- `warehouses` — array[object]. Список складов.
  - `address_info` — object. Информация о расположении склада.
    - `address` — string. Адрес склада.
    - `latitude` — number<double>. Широта.
    - `longitude` — number<double>. Долгота.
    - `utc` — string. Часовой пояс.
  - `carriage_label_type` — string (UNSPECIFIED, BIG, SMALL). Тип этикетки: - `UNSPECIFIED` — неизвестный тип; - `BIG` — большая этикетка; - `SMALL` — маленькая этикетка. По умолчанию: `UNSPECIFIED`.
  - `courier_comment` — string. Комментарий для курьера.
  - `courier_phones` — array[string]. Номера телефонов для связи с курьером.
  - `created_at` — string<date-time>. Дата и время создания склада.
  - `cut_in_time` — integer<int64>. Время на отгрузку в минутах.
  - `first_mile` — object. Первая миля.
    - `dropoff_point_id` — string. Идентификатор drop-off пункта.
    - `first_mile_is_changing` — boolean. Признак, что настройки склада обновляются.
    - `timeslot_from` — string. Время начала таймслота.
    - `timeslot_id` — integer<int64>. Идентификатор таймслота.
    - `timeslot_to` — string. Время окончания таймслота.
    - `type` — string (UNSPECIFIED, PICK_UP, DROP_OFF). Тип первой мили — `PICK_UP` или `DROP_OFF`. По умолчанию: `UNSPECIFIED`.
  - `has_entrusted_acceptance` — boolean. Признак подключения доверительной приемки.
  - `has_postings_limit` — boolean. Признак наличия лимита минимального количества заказов. `true`, если лимит есть.
  - `is_auto_assembly` — boolean. Признак включённой автосборки.
  - `is_comfort` — boolean. Признак доставки comfort. Время доставки до покупателя от 60 минут.
  - `is_express` — boolean. Признак доставки express. Время доставки до покупателя не больше 60 минут.
  - `is_kgt` — boolean. Признак, что склад принимает крупногабаритные товары.
  - `is_rfbs` — boolean. Признак работы склада по схеме rFBS.
  - `is_waybill_enabled` — boolean. Признак включённой печати транспортной накладной.
  - `min_postings_limit` — integer<int32>. Минимальное количество заказов, которое можно привезти в одной поставке.
  - `name` — string. Название склада.
  - `pause_at` — string<date-time>. Дата, когда продавец поставил склад на паузу. Если значение `null`, склад активный. Только для rFBS-склада.
  - `phone` — string. Номер телефона склада.
  - `postings_limit` — integer<int32>. Лимит заказов. `-1`, если лимита нет.
  - `sla_cut_in` — integer<int64>. Минимальное время на сборку заказа в минутах.
  - `status` — string. Статус склада.
  - `timetable` — object. Расписание работы склада.
    - `timetable_from` — string<date-time>. Дата начала работы склада.
    - `timetable_to` — string<date-time>. Дата окончания работы склада.
    - `working_hours` — array[object]. Часы работы склада.
      - `time_from` — string<date-time>. Время начала работы.
      - `time_to` — string<date-time>. Время окончания работы.
  - `updated_at` — string<date-time>. Дата и время последнего обновления данных склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_type` — string. Тип склада.
  - `with_item_list` — boolean. Признак включённой печати листа подбора.
  - `working_days` — array[string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY)]. Рабочие дни склада: - `UNSPECIFIED` — значение не определено; - `MONDAY` — понедельник; - `TUESDAY` — вторник; - `WEDNESDAY` — среда; - `THURSDAY` — четверг; - `FRIDAY` — пятница; - `SATURDAY` — суббота; - `SUNDAY` — воскресенье.
- `has_next` — boolean. `true`, если в ответе вернулись не все значения.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
