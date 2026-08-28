---
title: Получить список отправлений
api: ozon-seller
method: POST
path: /v1/assembly/fbs/posting/list
operation_id: AssemblyFbsPostingList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 804538af2ba37c63
---

# Получить список отправлений

`POST /v1/assembly/fbs/posting/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object **обязательный**. Фильтр.
  - `cutoff_from` — string<date-time> **обязательный**. Фильтр по времени, до которого продавцу нужно собрать заказ. Начало периода. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2020-03-18T07:34:50.359Z`.
  - `cutoff_to` — string<date-time> **обязательный**. Фильтр по времени, до которого продавцу нужно собрать заказ. Конец периода. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2020-03-18T07:34:50.359Z`.
  - `delivery_method_id` — integer<int64>. Идентификатор способа доставки. Можно получить с помощью метода [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList).
- `limit` — integer<int64> **обязательный**. Количество значений на странице.
- `sort_dir` — string (ASC, DESC) **обязательный**. Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.

## Ответы

**200** — Список отправлений

- `cursor` — string. Указатель для выборки следующих данных. Если параметр пустой, данных больше нет.
- `cutoff` — string<date-time>. Время, до которого продавцу нужно собрать заказ.
- `postings` — array[object]. Список отправлений.
  - `assembly_code` — string. Код листа подбора.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `picture_url` — string. Ссылка на изображение товара.
    - `product_name` — string. Название товара.
    - `quantity` — integer<int32>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
