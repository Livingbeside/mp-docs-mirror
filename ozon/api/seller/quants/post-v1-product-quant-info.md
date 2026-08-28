---
title: Информация об эконом-товаре
api: ozon-seller
method: POST
path: /v1/product/quant/info
operation_id: QuantGetInfo
tags:
  - Quants
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c18bce489dad5eb7
---

# Информация об эконом-товаре

`POST /v1/product/quant/info`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1084-Metody-po-tarifu-Ekonom) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `quant_code` — ? **обязательный**. Список квантов с товарами.

## Ответы

**200** — Информация об эконом-товаре

- `items` — array[object]. Эконом-товары.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `quant_info` — object. Информация о кванте.
    - `quants` — ?. Список квантов.
      - `barcodes_extended` — ?. Информация о штрихкодах.
        - `barcode` — string. Штрихкод.
        - `error` — string. Ошибка получения штрихкода.
        - `status` — string. Статус штрихкода.
      - `dimensions` — object. Габариты.
        - `depth` — integer<int64>. Глубина, мм.
        - `height` — integer<int64>. Высота, мм.
        - `weight` — integer<int64>. Вес, г.
        - `width` — integer<int64>. Ширина, мм.
      - `marketing_price` — object. Цена на товар с учётом всех акций, которая будет указана на витрине Ozon, без учёта скидки по карте Ozon Банка.
        - `price` — string. Цена продажи.
        - `seller_price` — string. Цена, которую указал продавец.
      - `min_price` — string. Минимальная цена, указанная продавцом.
      - `old_price` — string. Зачёркнутая цена, указанная продавцом.
      - `price` — string. Цена продажи, указанная продавцом.
      - `quant_code` — string. Идентификатор эконом-товара.
      - `quant_sice` — integer<int64>. Размер кванта.
      - `shipment_type` — string. Тип доставки товара.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `statuses` — object. Описание статусов.
        - `state_description` — string. Описание статуса.
        - `state_name` — string. Название статуса.
        - `state_sys_name` — string. Системное название статуса.
        - `state_tooltip` — string. Подсказка о текущем состоянии товара.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
