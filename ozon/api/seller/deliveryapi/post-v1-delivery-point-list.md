---
title: Получить список точек самовывоза
api: ozon-seller
method: POST
path: /v1/delivery/point/list
operation_id: DeliveryAPI_DeliveryPointList
tags:
  - DeliveryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0f2946c0614eec80
---

# Получить список точек самовывоза

`POST /v1/delivery/point/list`

Возвращает координаты всех точек самовывоза без объединения в кластеры.

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Список точек самовывоза

- `points` — array[object]. Точки самовывоза.
  - `coordinate` — object. Координаты.
    - `lat` — number<double>. Широта.
    - `long` — number<double>. Долгота.
  - `map_point_id` — integer<int64>. Идентификатор точки на карте.
