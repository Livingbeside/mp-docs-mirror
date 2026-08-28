---
title: Получить список товаров с ограничениями по доставке
api: ozon-seller
method: POST
path: /v1/warehouse/invalid-products/get
operation_id: WarehouseInvalidProductsGet
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a194b8fc70db1873
---

# Получить список товаров с ограничениями по доставке

`POST /v1/warehouse/invalid-products/get`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `last_id` — integer<int64>. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада. Получите значение параметра методом [/v1/warehouse/warehouses-with-invalid-products](#operation/WarehouseWithInvalidProducts).

## Ответы

**200** — Список товаров с ограничениями

- `has_next` — boolean. `true`, если в ответе вернулись не все товары.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.
- `validation_results` — array[object]. Результат проверки.
  - `item` — object. Информация о товаре.
    - `size` — object. Габариты товара.
      - `height_mm` — integer<int32>. Высота товара в миллиметрах.
      - `length_mm` — integer<int32>. Длина товара в миллиметрах.
      - `width_mm` — integer<int32>. Ширина товара в миллиметрах.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `weight_g` — number<double>. Вес товара в граммах.
  - `state` — string (UNSPECIFIED, NOT_VALID). Статус проверки: - `UNSPECIFIED` — не определён; - `NOT_VALID` — товар не прошёл проверку. По умолчанию: `UNSPECIFIED`.
  - `validation_errors` — array[object]. Информация об ошибках.
    - `characteristic` — string (UNSPECIFIED, LENGTH, WIDTH, HEIGHT, WEIGHT, SUM_OF_DIMENSIONS, VOLUME_WEIGHT, VOLUME, PRICE, LONGEST_SIDE). Характеристика, по которой товар не прошёл проверку. Возможные ограничения: - `UNSPECIFIED` — не определено; - `LENGTH` — длина, - `WIDTH` — ширина, - `HEIGHT` — высота, - `WEIGHT` — вес, - `SUM_OF_DIMENSIONS` — сумма измерений, - `VOLUME_WEIGHT` — объёмный вес, - `VOLUME` — объём, - `PRICE` — цена, - `LONGEST_SIDE` — самая длинная сторона. По умолчанию: `UNSPECIFIED`.
    - `restriction_price` — object. Ограничение по цене.
      - `currency` — string. Валюта.
      - `value` — number<double>. Значение цены.
    - `restriction_vwc` — number<double>. Значение ограничения по объёмно-весовым характеристикам — ОВХ.
    - `template_id` — integer<int32>. Идентификатор услуги по доставке заказа, на которой установлено ограничение.
    - `type` — string (UNSPECIFIED, LESS_THAN_MIN, GREATER_THAN_MAX). Тип ошибки: - `UNSPECIFIED` — не определён; - `LESS_THAN_MIN` — меньше минимального значения; - `GREATER_THAN_MAX` — больше максимального значения. По умолчанию: `UNSPECIFIED`.
- `warehouse_id` — integer<int64>. Идентификатор склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
