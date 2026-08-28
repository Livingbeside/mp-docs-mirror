---
title: Получить список drop-off пунктов для изменения информации склада
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/update/drop-off/list
operation_id: WarehouseAPI_ListDropOffPointsForUpdateFBSWarehouse
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e16e49e1efd0fbe7
---

# Получить список drop-off пунктов для изменения информации склада

`POST /v1/warehouse/fbs/update/drop-off/list`

## Запрос

**Тело запроса** (`application/json`):

- `search` — object. Параметры поиска.
  - `address` — string. Поиск по адресу drop-off пункта.
  - `types` — array[string (PVZ, PPZ, SC)]. Тип drop-off пункта: - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов; - `SC` — сортировочный центр.
- `warehouse_id` — integer<int64> **обязательный**. Фильтр по существующему FBS-складу.

## Ответы

**200** — Список получен

- `points` — array[object]. Список пунктов.
  - `address` — string. Адрес drop-off пункта.
  - `coordinates` — object. Координаты drop-off пункта.
    - `latitude` — number<double>. Широта.
    - `longitude` — number<double>. Долгота.
  - `discount_percent` — number<float>. Процент скидки за передачу отправления.
  - `id` — string. Идентификатор drop-off пункта.
  - `last_transit_time_local` — object. Время, до которого нужно передать отправления, чтобы получить скидку за отгрузку.
    - `hours` — integer<int32>. Час.
    - `minutes` — integer<int32>. Минута.
    - `nanos` — integer<int32>. Наносекунда.
    - `seconds` — integer<int32>. Секунда.
  - `type` — string (PVZ, PPZ, SC). Тип drop-off пункта: - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов; - `SC` — сортировочный центр.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
