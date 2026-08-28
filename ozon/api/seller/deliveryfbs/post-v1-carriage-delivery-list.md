---
title: Список методов доставки и отгрузок
api: ozon-seller
method: POST
path: /v1/carriage/delivery/list
operation_id: CarriageAPI_CarriageDeliveryList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 370744ece6b3bf41
---

# Список методов доставки и отгрузок

`POST /v1/carriage/delivery/list`

Метод не возвращает информацию по методам доставки, у которых нет отправлений. Используйте метод, чтобы получить список созданных отгрузок для метода доставки и их статусы. 20 марта 2026 года отключим метод. Переключитесь на /v2/carriage/delivery/list .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `delivery_method_id` — integer<int64>. Идентификатор метода доставки.
- `departure_date` — string<date-time>. Дата отгрузки. По умолчанию — текущая дата.

## Ответы

**200** — Список методов и отгрузок

- `result` — array[object]
  - `assembly_list_availability` — boolean. `true`, если доступен лист подбора.
  - `can_create_another_carriage` — boolean. `true`, если можно создать ещё одну перевозку.
  - `carriage_postings_count` — integer<int32>. Количество отправлений в перевозке.
  - `carriage_quantum_count` — integer<int32>. Количество квантов в перевозке.
  - `carriages` — array[object]. Список перевозок.
    - `id` — string<int64>. Идентификатор перевозки.
    - `postings_count` — integer<int32>. Количество отправлений в перевозке.
    - `quantum_count` — integer<int32>. Количество квантов в перевозке.
    - `status` — string. Статус перевозки для запрашиваемых метода и даты.
  - `cut_in` — string<date-time>. Время начала сборки и часовой пояс времени склада.
  - `delivery_method_id` — integer. Идентификатор метода доставки.
  - `delivery_method_name` — string. Название метода доставки.
  - `delivery_method_status` — string. Статус метода доставки.
  - `departure_date` — string<date-time>. Дата отгрузки.
  - `dropoff_address` — string. Адрес точки отгрузки.
  - `dropoff_change_availability` — string. Статус возможности смены точки отгрузки.
  - `dropoff_point_id` — integer<int64>. Идентификатор точки отгрузки.
  - `dropoff_point_type` — string. Способ отгрузки.
  - `errors` — array[object]. Массив ошибок, которые возникли при обработке запроса.
    - `code` — string. Код ошибки.
    - `description` — string. Описание ошибки.
    - `status` — string. Статус ошибки.
  - `first_mile_changing` — boolean. `true`, если точка отгрузки изменилась.
  - `first_mile_type` — string. Тип первой мили.
  - `has_entrusted_acceptance` — boolean. Признак доверительной приёмки. `true`, если доверительная приёмка включена на складе.
  - `integration_type` — string. Тип интеграции со службой доставки.
  - `is_presort` — boolean. `true`, если отгрузка с предсортировкой.
  - `is_rfbs` — boolean. `true`, если склад работает по схеме rFBS.
  - `recommended_time_local` — string. Рекомендуемое местное время отгрузки в пункт приёма заказов.
  - `recommended_time_utc_offset_in_minutes` — number<int32>. Смещение часового пояса рекомендуемого времени отгрузки от UTC-0 в минутах.
  - `cutoff_at` — string<date-time>. Дата и время, до которых нужно собрать отправление.
  - `mandatory_packaged_count` — integer<int32>. Количество «обязательных» собранных отправлений.
  - `mandatory_packaged_quantum_count` — integer<int32>. Количество «обязательных» собранных квантов.
  - `mandatory_postings_count` — integer<int32>. Количество отправлений, которые нужно собрать.
  - `mandatory_quantum_count` — integer<int32>. Количество квантов, которые нужно собрать.
  - `optional_packaged_count` — integer<int32>. Количество собранных «необязательных» отправлений.
  - `postings_for_another_carriage_count` — integer<int32>. Количество отправлений, которые могут попасть в следующую перевозку.
  - `quantum_for_another_carriage_count` — integer<int32>. Количество квантов, которые могут попасть в следующую перевозку.
  - `timeslot_from` — string<date-time>. Начало таймслота в точке отгрузки.
  - `timeslot_to` — string<date-time>. Окончание таймслота в точке отгрузки.
  - `tpl_provider_icon_url` — string. Ссылка на иконку службы доставки.
  - `tpl_provider_name` — string. Название службы доставки.
  - `warehouse_city` — string. Город склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_name` — string. Название склада.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
