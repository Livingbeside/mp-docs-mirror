---
title: Добавить товар в акцию
api: ozon-seller
method: POST
path: /v1/actions/products/activate
operation_id: PromosProductsActivate
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: aed80228203170cc
---

# Добавить товар в акцию

`POST /v1/actions/products/activate`

Метод для добавления товаров в доступную акцию.

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — number<double> **обязательный**. Идентификатор акции. Можно получить с помощью метода [/v1/actions](#operation/Promos).
- `products` — array[object] **обязательный**. Список товаров.
  - `action_price` — number<double> **обязательный**. Цена товара по акции.
  - `product_id` — number<double> **обязательный**. Идентификатор товара в системе Ozon — `product_id`.
  - `stock` — number<double>. Количество единиц товара в акции типа «Скидка на сток».

## Ответы

**200** — Товар добавлен в акцию

- `result` — object. Результаты запроса.
  - `product_ids` — array[number<double>]. Список идентификаторов товаров, которые добавлены в акцию.
  - `rejected` — array[object]. Список товаров, которые не удалось добавить в акцию.
    - `product_id` — number<double>. Идентификатор товара в системе Ozon — `product_id`.
    - `reason` — string. Причина, почему товар не добавлен в акцию.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
