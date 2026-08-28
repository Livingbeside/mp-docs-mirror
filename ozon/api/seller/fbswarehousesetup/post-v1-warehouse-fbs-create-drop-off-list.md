---
title: Получить список drop-off пунктов для создания склада
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/create/drop-off/list
operation_id: WarehouseAPI_ListDropOffPointsForCreateFBSWarehouse
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 545ec459787f5f60
---

# Получить список drop-off пунктов для создания склада

`POST /v1/warehouse/fbs/create/drop-off/list`

## Запрос

**Тело запроса** (`application/json`):

- `coordinates` — object. Координаты.
  - `latitude` — number<double> **обязательный**. Широта.
  - `longitude` — number<double> **обязательный**. Долгота.
- `country_code` — string **обязательный**. Код страны в формате ISO 2.
- `is_kgt` — boolean **обязательный**. `true`, если товар крупногабаритный.
- `search` — object. Параметры поиска.
  - `address` — string. Адрес drop-off пункта.
  - `types` — array[string (PVZ, PPZ, SC)]. Тип drop-off пункта: - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов; - `SC` — сортировочный центр.

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
