---
title: Получить подробную информацию о ценах товаров
api: ozon-seller
method: POST
path: /v1/product/prices/details
operation_id: ProductPricesDetails
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 126e3461347f7028
---

# Получить подробную информацию о ценах товаров

`POST /v1/product/prices/details`

Доступно для продавцов с подпиской Premium Pro.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>] **обязательный**. Список SKU.

## Ответы

**200** — Информация о ценах товаров

- `prices` — array[object]. Цены товаров.
  - `customer_price` — object. Цена товара на сайте.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `discount_percent` — number<float>. Процент скидки за счёт Ozon.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `price` — object. Цена товара с учётом акции или продвижения.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `price_indexes` — array[object]. Индекс цен.
    - `external_index_data` — object. Цена товара конкурента.
      - `min_price` — object. Минимальная цена товара конкурента.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `price_index` — number<double>. Индекс цены.
      - `url` — string. Ссылка на товар конкурента.
    - `self_index_data` — object. Цена вашего товара.
      - `min_price` — object. Минимальная цена вашего товара.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `price_index` — number<double>. Индекс цены.
      - `url` — string. Ссылка на ваш товар.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `weight_index` — array[object]. Средневзвешенный индекс цен. Если `weight_index = null`, индекс получить не удалось.
    - `self_wb_index` — number<double>. Индекс цены на Wildberries.
    - `self_wb_min_competitor_price` — array[object]. Минимальная цена.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `self_wb_url` — string. Ссылка на товар по средней цене на Wildberries.
    - `weight_percent` — number<double>. Коэффициент влияния цены товара на общий индекс товаров.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
