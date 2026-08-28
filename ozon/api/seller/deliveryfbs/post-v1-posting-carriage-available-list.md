---
title: Список доступных перевозок
api: ozon-seller
method: POST
path: /v1/posting/carriage-available/list
operation_id: PostingAPI_GetCarriageAvailableList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bb6d8f9c367d9e7c
---

# Список доступных перевозок

`POST /v1/posting/carriage-available/list`

20 марта 2026 года отключим метод. Переключитесь на /v2/carriage/delivery/list . Метод для получения перевозок, по которым нужно распечатать штрихкод для отгрузки и документы: - для продацов из России — лист отгрузки и транспортную накладную; - для продавцов из СНГ — акт и транспортную накладную.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `delivery_method_id` — integer<int64> **обязательный**. Фильтр по методу доставки. Можно получить с помощью метода [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2).
- `departure_date` — string<date-time>. Дата отгрузки. По умолчанию — текущая дата.

## Ответы

**200** — Список перевозок

- `result` — ?. Результат работы метода.
  - `carriage_id` — integer<int64>. Идентификатор перевозки (также номер задания на формирование документов).
  - `carriage_postings_count` — integer<int32>. Количество отправлений в перевозке.
  - `carriage_status` — string. Статус перевозки для запрашиваемого метода доставки и даты отгрузки.
  - `cutoff_at` — string<date-time>. Дата и время, до которых нужно собрать отправление.
  - `delivery_method_id` — integer<int64>. Идентификатор метода доставки.
  - `delivery_method_name` — string. Название метода доставки.
  - `errors` — ?. Список ошибок.
    - `code` — string. Код ошибки.
    - `status` — string. Тип ошибки: - `warning` — предупреждение; - `critical` — критическая ошибка.
  - `first_mile_type` — string. Тип первой мили.
  - `has_entrusted_acceptance` — boolean. Признак доверительной приёмки. `true`, если доверительная приёмка включена на складе.
  - `mandatory_postings_count` — integer<int32>. Количество отправлений, которые нужно собрать.
  - `mandatory_packaged_count` — integer<int32>. Количество собранных отправлений.
  - `recommended_time_local` — string. Рекомендуемое местное время отгрузки на пункт приёма заказов.
  - `recommended_time_utc_offset_in_minutes` — number<int32>. Смещение часового пояса рекомендуемого времени отгрузки от UTC-0 в минутах.
  - `tpl_provider_icon_url` — string. Ссылка на иконку службы доставки.
  - `tpl_provider_name` — string. Название службы доставки.
  - `warehouse_city` — string. Город склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_name` — string. Название склада.
  - `warehouse_timezone` — string. Часовой пояс, в котором находится склад.

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
