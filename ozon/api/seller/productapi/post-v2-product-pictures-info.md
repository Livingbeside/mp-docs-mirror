---
title: Получить изображения товаров
api: ozon-seller
method: POST
path: /v2/product/pictures/info
operation_id: ProductAPI_ProductInfoPicturesV2
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5912605a830f946f
---

# Получить изображения товаров

`POST /v2/product/pictures/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `product_id` — ? **обязательный**. Список идентификаторов товаров в системе Ozon — `product_id`.

## Ответы

**200** — Изображения товаров

- `items` — array[object]. Изображения товаров.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `primary_photo` — array[string]. Ссылка на главное изображение.
  - `photo` — array[string]. Ссылки на фотографии товара.
  - `color_photo` — array[string]. Ссылки на загруженные образцы цвета.
  - `errors` — array[object]. Список ошибок по изображениям товара.
    - `message` — string. Описание ошибки.
    - `url` — string. Ссылка на изображение.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
