---
title: Получить список товаров в отправлениях
api: ozon-seller
method: POST
path: /v1/assembly/fbs/product/list
operation_id: AssemblyFbsProductList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9918fe819d3603fc
---

# Получить список товаров в отправлениях

`POST /v1/assembly/fbs/product/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object **обязательный**. Фильтр.
  - `cutoff_from` — string<date-time> **обязательный**. Фильтр по времени, до которого продавцу нужно собрать заказ. Начало периода. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2020-03-18T07:34:50.359Z`.
  - `cutoff_to` — string<date-time> **обязательный**. Фильтр по времени, до которого продавцу нужно собрать заказ. Конец периода. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2020-03-18T07:34:50.359Z`.
  - `delivery_method_id` — integer<int64>. Идентификатор способа доставки. Можно получить с помощью метода [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList).
- `limit` — integer<int64> **обязательный**. Количество значений на странице.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, ответ начнётся с 11 найденного элемента.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.

## Ответы

**200** — Список товаров в отправлениях

- `has_next` — boolean. Признак, что в ответе вернули не все товары: - `true` — сделайте повторный запрос с другим значением `offset`, чтобы получить остальные значения; - `false` — ответ содержит все значения.
- `products` — array[object]. Список товаров.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `picture_url` — string. Ссылка на изображение товара.
  - `postings` — array[object]. Список отправлений.
    - `posting_number` — string. Номер отправления.
    - `quantity` — integer<int32>. Количество товаров в отправлении.
  - `product_name` — string. Название товара.
  - `quantity` — integer<int32>. Количество товара.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `products_count` — integer<int32>. Количество товаров.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
