---
title: Поиск точек для отгрузки поставки
api: ozon-seller
method: POST
path: /v1/warehouse/fbo/list
operation_id: SupplyDraftAPI_DraftGetWarehouseFboList
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 8e6054236c5315b2
---

# Поиск точек для отгрузки поставки

`POST /v1/warehouse/fbo/list`

Используйте метод, чтобы найти точки отгрузки для кросс-докинга и прямых поставок.

Вы можете посмотреть адреса всех точек на карте и в виде таблицы в [Базе знаний](https://seller-edu.ozon.ru/fbo/warehouses/adresa-skladov-fbo).

## Запрос

**Тело запроса** (`application/json`):

- `filter_by_supply_type` — array[string (CREATE_TYPE_CROSSDOCK, CREATE_TYPE_DIRECT)] **обязательный**. Тип поставки: - `CREATE_TYPE_CROSSDOCK` — кросс-докинг, - `CREATE_TYPE_DIRECT` — прямая.
- `search` — string **обязательный**. Поиск по названию склада. Для поиска пунктов выдачи заказов укажите полное название.

## Ответы

**200** — Информация о складах

- `search` — array[object]. Результат поиска складов.
  - `address` — string. Адрес склада.
  - `coordinates` — object. Координаты склада.
    - `latitude` — number<double>. Широта.
    - `longitude` — number<double>. Долгота.
  - `name` — string. Название склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада, пункта выдачи заказов или сортировочного центра.
  - `warehouse_type` — string (WAREHOUSE_TYPE_DELIVERY_POINT, WAREHOUSE_TYPE_ORDERS_RECEIVING_POINT, WAREHOUSE_TYPE_SORTING_CENTER, WAREHOUSE_TYPE_FULL_FILLMENT, WAREHOUSE_TYPE_CROSS_DOCK). Тип склада, пункта выдачи заказов или сортировочного центра: - `WAREHOUSE_TYPE_DELIVERY_POINT` — пункт выдачи заказов, - `WAREHOUSE_TYPE_ORDERS_RECEIVING_POINT` — пункт приёма заказов, - `WAREHOUSE_TYPE_SORTING_CENTER` — сортировочный центр, - `WAREHOUSE_TYPE_FULL_FILLMENT` — фулфилмент, - `WAREHOUSE_TYPE_CROSS_DOCK` — кросс-докинг.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
