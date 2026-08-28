---
title: Получить информацию о точке самовывоза
api: ozon-seller
method: POST
path: /v1/delivery/point/info
operation_id: DeliveryPointInfo
tags:
  - DeliveryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4844b3e606172081
---

# Получить информацию о точке самовывоза

`POST /v1/delivery/point/info`

Возвращает подробную информацию о точке самовывоза для пользователя.

## Запрос

**Тело запроса** (`application/json`):

- `map_point_ids` — array[string<int64>]. Идентификаторы точек на карте.

## Ответы

**200** — Информация о точке самовывоза

- `points` — array[object]. Информация о пунктах самовывоза.
  - `delivery_method` — object. Метод доставки.
    - `address` — string. Адрес.
    - `address_details` — object. Детали адреса.
      - `city` — string. Город.
      - `house` — string. Дом.
      - `region` — string. Регион.
      - `street` — string. Улица.
    - `coordinates` — object. Координаты.
      - `lat` — number<double>. Широта.
      - `long` — number<double>. Долгота.
    - `delivery_type` — object. Способ доставки.
      - `id` — integer<int64>. Идентификатор способа доставки.
      - `name` — string. Название способа доставки.
    - `description` — string. Описание.
    - `fitting_rooms_count` — integer<int64>. Количество гардеробов.
    - `holidays` — array[object]. Праздничные дни.
      - `begin` — string<date-time>. Дата и время начала праздничных дней.
      - `end` — string<date-time>. Дата и время окончания праздничных дней.
    - `holidays_filled` — boolean. `true`, если праздники заполнены.
    - `images` — array[string]. Изображения.
    - `location_id` — string. Идентификатор локации.
    - `map_point_id` — integer<int64>. Идентификатор точки на карте.
    - `name` — string. Название.
    - `properties` — array[object]. Свойства.
      - `enabled` — boolean. `true`, если свойство доступно.
      - `name` — string. Название свойства.
    - `pvz_rating` — integer<int64>. Рейтинг пункта выдачи заказов.
    - `storage_period` — integer<int64>. Период хранения.
    - `working_hours` — array[object]. Часы работы.
      - `date` — string<date-time>. Дата.
      - `periods` — array[object]. Периоды работы.
        - `max` — object. Период максимального времени.
          - `hours` — integer<int32>. Часы.
          - `minutes` — integer<int32>. Минуты.
        - `min` — object. Период минимального времени.
          - `hours` — integer<int32>. Часы.
          - `minutes` — integer<int32>. Минуты.
  - `enabled` — boolean. `true`, если пункт самовывоза доступен.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
