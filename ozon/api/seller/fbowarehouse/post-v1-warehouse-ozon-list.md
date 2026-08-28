---
title: Получить список складов Ozon
api: ozon-seller
method: POST
path: /v1/warehouse/ozon/list
operation_id: WarehouseOZONList
tags:
  - FBOWarehouse
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5dd77e30d23ca1d6
---

# Получить список складов Ozon

`POST /v1/warehouse/ozon/list`

Возвращает список складов Ozon, которые работают по схемам FBO и FBO Fresh, и возвратных складов.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `warehouse_types` — array[string (FULL_FILLMENT, FULL_FILLMENT_RETURNS, FULL_FILLMENT_DEFECT, EXPRESS_DARK_STORE, CROSS_DOCK, SORTING_CENTER, PHARMACY, DISTRIBUTION_CENTER, ORDERS_RECEIVING_POINT, OUTSOURCE_FF, B2B, EXTERNAL_FF)]. Тип склада Ozon: - `FULL_FILLMENT` — фулфилмент; - `FULL_FILLMENT_RETURNS` — склад возвратов; - `FULL_FILLMENT_DEFECT` — склад брака; - `EXPRESS_DARK_STORE` — фреш; - `CROSS_DOCK` — кросс-док; - `SORTING_CENTER` — сортировочный центр; - `PHARMACY` — склад аптеки; - `DISTRIBUTION_CENTER` — распределительный центр; - `ORDERS_RECEIVING_POINT` — пункты приёма заказов; - `OUTSOURCE_FF` — аутсорс-склады; - `B2B` — B2B-склад; - `EXTERNAL_FF` — склады партнёров.

## Ответы

**200** — Список складов Ozon

- `warehouses` — array[object]. Список складов.
  - `address` — string. Адрес склада.
  - `country_iso_numeric` — integer<int32>. Код страны в формате ISO 3166-1 numeric.
  - `is_active` — boolean. `true`, если склад активный.
  - `is_cross_dock` — boolean. `true`, если тип склада — кросс-док.
  - `is_distribution_center` — boolean. `true`, если тип склада — распределительный центр.
  - `is_edo` — boolean. `true`, если склад работает с электронным документооборотом.
  - `is_express` — boolean. `true`, если тип склада — фреш.
  - `is_for_supply` — boolean. `true`, если склад доступен для создания поставки.
  - `name` — string. Название склада.
  - `short_name` — string. Короткое название склада.
  - `timezone` — string. Часовой пояс склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_type` — string (UNSPECIFIED, FULL_FILLMENT, FULL_FILLMENT_RETURNS, FULL_FILLMENT_DEFECT, EXPRESS_DARK_STORE, CROSS_DOCK, SORTING_CENTER, PHARMACY, DISTRIBUTION_CENTER, ORDERS_RECEIVING_POINT, OUTSOURCE_FF, B2B…). Тип склада: - `UNSPECIFIED` — не указан; - `FULL_FILLMENT` — фулфилмент; - `FULL_FILLMENT_RETURNS` — склад возвратов; - `FULL_FILLMENT_DEFECT` — склад брака; - `EXPRESS_DARK_STORE` — фреш; - `CROSS_DOCK` — кросс-док; - `SORTING_CENTER` — сортировочный центр; - `PHARMACY` — склад аптеки; - `DISTRIBUTION_CENTER` — распределительный центр; - `ORDERS_RECEIVING_POINT` — пункты приёма заказов; - `OUTSOURCE_FF` — аутсорс-склады; - `B2B` — B2B-склад; - `EXTERNAL_FF` — склады партнёров. По умолчанию: `UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
