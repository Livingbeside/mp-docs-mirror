---
title: Список методов доставки и отгрузок
api: ozon-seller
method: POST
path: /v2/carriage/delivery/list
operation_id: CarriageAPI_CarriageDeliveryListV2
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 04194fd26aaf337d
---

# Список методов доставки и отгрузок

`POST /v2/carriage/delivery/list`

Метод не возвращает информацию по методам доставки, у которых нет отправлений.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтр для поиска методов доставки и отгрузок.
  - `delivery_method_id` — integer<int64>. Идентификатор метода доставки. Для realFBS-складов получите его с помощью метода [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2). Для FBS-складов используйте значение параметра `warehouse_id`. Его можно получить с помощью метода [/v2/warehouse/list](#operation/WarehouseListV2).
  - `departure_date` — string. Дата отгрузки. По умолчанию — текущая дата.
- `limit` — integer<int64> **обязательный**. Количество значений на странице.

## Ответы

**200** — Список методов и отгрузок

- `cursor` — string. Указатель для выборки следующих данных.
- `has_next` — boolean. `true`, если в ответе вернулись не все методы доставки.
- `methods` — array[object]. Список методов доставки.
  - `carriage_postings_count` — integer<int32>. Количество отправлений во всех отгрузках.
  - `carriages` — array[object]. Список отгрузок.
    - `all_blr_traceable` — boolean. `true`, если в отгрузке есть товары, для которых нужны дополнительные документы при отправке в Беларусь.
    - `available_actions` — array[string]. Доступные действия с отгрузкой.
    - `carriage_volume` — number<float>. Объём отгрузки в литрах.
    - `id` — integer<int64>. Идентификатор отгрузки. Если `0` — отгрузка, которую можно создать.
    - `pickup_fee` — object. Стоимость отгрузки pick-up.
      - `currency_code` — string. Код валюты.
      - `value` — number<float>. Предварительная стоимость отгрузки курьеру Ozon.
    - `postings_count` — integer<int32>. Количество отправлений в отгрузке.
    - `quantum_count` — integer<int32>. Количество квантов в отгрузке.
    - `status` — string. Статус отгрузки для запрашиваемых метода и даты.
  - `cut_in` — string. Время начала сборки и часовой пояс времени склада.
  - `cutoff_at` — string. Дата и время, до которых нужно собрать отправление.
  - `delivery_method_id` — integer<int64>. Идентификатор метода доставки.
  - `delivery_method_name` — string. Название метода доставки.
  - `delivery_method_status` — string. Статус метода доставки.
  - `departure_date` — string. Дата отгрузки.
  - `dropoff_address` — string. Адрес точки отгрузки.
  - `dropoff_change_availability` — string. Статус возможности смены точки отгрузки.
  - `dropoff_point_id` — integer<int64>. Идентификатор точки отгрузки.
  - `dropoff_point_type` — string. Способ отгрузки.
  - `errors` — array[object]. Список ошибок, которые возникли при обработке запроса.
    - `code` — string. Код ошибки.
    - `description` — string. Описание ошибки.
    - `status` — string. Статус ошибки.
  - `first_mile_changing` — boolean. `true`, если точка отгрузки изменилась.
  - `first_mile_type` — string. Тип первой мили.
  - `has_entrusted_acceptance` — boolean. `true`, если на складе включена доверительная приёмка.
  - `integration_type` — string. Тип интеграции со службой доставки.
  - `is_optional_carriage` — boolean. `true`, если отгрузка не обязательна.
  - `is_presort` — boolean. `true`, если отгрузка с предсортировкой.
  - `is_rfbs` — boolean. `true`, если склад работает по схеме rFBS.
  - `mandatory_packaged_count` — integer<int32>. Количество собранных обязательных отправлений.
  - `mandatory_postings_count` — integer<int32>. Количество отправлений, которые нужно собрать.
  - `optional_packaged_count` — integer<int32>. Количество собранных необязательных отправлений.
  - `recommended_time_local` — string. Рекомендуемое местное время отгрузки в пункт приёма заказов.
  - `recommended_time_utc_offset_in_minutes` — integer<int32>. Смещение часового пояса рекомендуемого времени отгрузки от UTC-0 в минутах.
  - `timeslot_from` — string. Начало таймслота в точке отгрузки.
  - `timeslot_to` — string. Окончание таймслота в точке отгрузки.
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
