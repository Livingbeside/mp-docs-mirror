---
title: Список методов доставки realFBS-склада
api: ozon-seller
method: POST
path: /v2/delivery-method/list
operation_id: WarehouseAPI_DeliveryMethodListV2
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 97969492f088f7eb
---

# Список методов доставки realFBS-склада

`POST /v2/delivery-method/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтр для поиска методов доставки.
  - `delivery_method_ids` — array[string<int64>]. Идентификаторы методов доставки.
  - `provider_ids` — array[string<int64>]. Идентификаторы служб доставки.
  - `status` — array[string (NEW, EDITED, ACTIVE, DISABLED, WAITING, BROKEN)]. Статус метода доставки: - `NEW` — создан, - `EDITED` — редактируется, - `ACTIVE` — активный, - `DISABLED` — неактивный, - `WAITING` — на проверке, - `BROKEN` — с ошибкой. По умолчанию: `NEW`.
  - `warehouse_ids` — array[string<int64>]. Идентификаторы складов. Получите с помощью метода [/v2/warehouse/list](#operation/WarehouseListV2).
- `limit` — integer<int64> **обязательный**. Количество значений в ответе.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию.

## Ответы

**200** — Список методов склада

- `cursor` — string. Указатель для выборки следующих данных.
- `delivery_methods` — array[object]. Методы доставки.
  - `created_at` — string<date-time>. Дата создания метода доставки.
  - `cutoff` — string. Время, до которого продавцу нужно собрать заказ.
  - `id` — integer<int64>. Идентификатор метода доставки.
  - `is_express` — boolean. `true`, если доступна быстрая доставка Ozon Express.
  - `name` — string. Название метода доставки.
  - `provider_id` — integer<int64>. Идентификатор службы доставки.
  - `sla_cut_in` — integer<int64>. Минимальное время на сборку заказа в минутах в соответствии с настройками склада.
  - `status` — string. Статус метода доставки: - `NEW` — создан, - `EDITED` — редактируется, - `ACTIVE` — активный, - `DISABLED` — неактивный, - `WAITING` — на проверке, - `BROKEN` — с ошибкой. По умолчанию: `NEW`.
  - `template_id` — integer<int64>. Идентификатор услуги по доставке заказа.
  - `tpl_dropoff_point` — object. Информация о drop-off пункте.
    - `address` — string. Адрес drop-off пункта.
    - `address_coordinates` — object. Координаты drop-off пункта.
      - `latitude` — number<double>. Широта.
      - `longitude` — number<double>. Долгота.
    - `code` — string. Код drop-off пункта в системе транспортной компании.
    - `name` — string. Название drop-off пункта.
  - `tpl_integration_type` — string. Тип интеграции со службой доставки: - `aggregator` — доставка внешней службой, Ozon регистрирует заказ; - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ; - `non_integrated` — доставка силами продавца; - `hybrid` — гибридная интеграция.
  - `updated_at` — string<date-time>. Дата и время последнего обновления метода метода доставки.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
- `has_next` — boolean. `true`, если в ответе вернули не все методы доставки.

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
