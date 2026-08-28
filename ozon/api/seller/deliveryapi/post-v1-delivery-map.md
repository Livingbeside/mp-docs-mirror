---
title: Отрисовать точки на карте
api: ozon-seller
method: POST
path: /v1/delivery/map
operation_id: DeliveryMap
tags:
  - DeliveryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: eb0e5a15e414540e
---

# Отрисовать точки на карте

`POST /v1/delivery/map`

Возвращает объединённые кластеры точек самовывоза на области из параметра `viewport`. 

Используйте значения из параметра `clusters.viewport`, чтобы получить список точек или мелких кластеров внутри большого кластера.

Используйте метод [/v1/delivery/point/info](#operation/DeliveryPointInfo), чтобы получить информацию о конкретной точке самовывоза.

## Запрос

**Тело запроса** (`application/json`):

- `viewport` — object. Область карты для получения кластеров и точек самовывоза.
  - `left_bottom` — object. Координаты левого нижнего угла области видимости карты.
    - `lat` — number<double>. Широта.
    - `long` — number<double>. Долгота.
  - `right_top` — object. Координаты правого верхнего угла области видимости карты.
    - `lat` — number<double>. Широта.
    - `long` — number<double>. Долгота.
- `zoom` — integer<int32>. Масштаб карты.

## Ответы

**200** — Успешно

- `clusters` — array[object]. Кластеры.
  - `coordinate` — object. Координаты.
    - `lat` — number<double>. Широта.
    - `long` — number<double>. Долгота.
  - `is_same_building` — boolean. `true`, если все точки находятся в одном здании.
  - `map_point_ids` — array[string<int64>]. Идентификаторы точек на карте.
  - `points_count` — integer<int32>. Количество точек в кластере.
  - `viewport` — object. Область карты для получения точек в кластере.
    - `left_bottom` — object. Координаты левого нижнего угла области видимости карты.
      - `lat` — number<double>. Широта.
      - `long` — number<double>. Долгота.
    - `right_top` — object. Координаты правого верхнего угла области видимости карты.
      - `lat` — number<double>. Широта.
      - `long` — number<double>. Долгота.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
