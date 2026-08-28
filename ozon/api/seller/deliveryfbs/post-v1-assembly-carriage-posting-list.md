---
title: Получить список отправлений в отгрузке
api: ozon-seller
method: POST
path: /v1/assembly/carriage/posting/list
operation_id: AssemblyCarriagePostingList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: cbb22e0156a48b62
---

# Получить список отправлений в отгрузке

`POST /v1/assembly/carriage/posting/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object **обязательный**. Фильтр.
  - `carriage_id` — integer<int64> **обязательный**. Идентификатор перевозки.
  - `cutoff_from` — string<date-time>. Фильтр по времени, до которого продавцу нужно собрать заказ. Начало периода. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2020-03-18T07:34:50.359Z`.
  - `cutoff_to` — string<date-time>. Фильтр по времени, до которого продавцу нужно собрать заказ. Конец периода. Формат: `YYYY-MM-DDThh:mm:ss.mcsZ`. Пример: `2020-03-18T07:34:50.359Z`.
  - `delivery_method_id` — integer<int64>. Идентификатор способа доставки. Можно получить с помощью метода [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList).
- `limit` — integer<int64> **обязательный**. Количество значений на странице.

## Ответы

**200** — Список отправлений

- `can_print_mass_label` — boolean. `true`, если можно распечатать этикетки массово.
- `cursor` — string. Указатель для выборки следующих данных. Если параметр пустой, данных больше нет.
- `postings` — array[object]. Список отправлений.
  - `assembly_code` — string. Код листа подбора.
  - `can_print_label` — boolean. `true`, если можно распечатать этикетку.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `picture_url` — string. Ссылка на изображение товара.
    - `product_name` — string. Название товара.
    - `quantity` — integer<int64>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
