---
title: Список участвующих в акции товаров
api: ozon-seller
method: POST
path: /v1/actions/products
operation_id: PromosProducts
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 073087c301a460cc
---

# Список участвующих в акции товаров

`POST /v1/actions/products`

Метод для получения списка товаров, участвующих в акции, по её идентификатору.

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — number<double> **обязательный**. Идентификатор акции. Можно получить с помощью метода [/v1/actions](#operation/Promos).
- `last_id` — number<double>. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым.
- `limit` — number<double>. Количество ответов на странице. По умолчанию — 100.

## Ответы

**200** — Список товаров

- `result` — object. Результаты запроса.
  - `last_id` — number<double>. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.
  - `products` — array[object]. Список товаров.
    - `action_price` — number<double>. Цена товара по акции.
    - `add_mode` — string. Тип добавления товара в акцию: автоматически или вручную продавцом.
    - `alert_max_action_price` — number<double>. Рекомендуемая цена товара по акции.
    - `alert_max_action_price_failed` — boolean. `true`, если цена товара выше рекомендуемой. Товар отмечен красным и может быть исключён из акции.
    - `current_boost` — number<double>. Размер бустинга товара.
    - `id` — number<double>. Идентификатор товара в системе Ozon — `product_id`.
    - `max_action_price` — number<double>. Максимально возможная цена товара по акции.
    - `max_boost` — number<double>. Максимальный размер бустинга в процентах.
    - `min_boost` — number<double>. Минимальный размер бустинга в процентах.
    - `min_stock` — number<double>. Минимальное число единиц товара в акции типа «Скидка на сток».
    - `price` — number<double>. Текущая цена товара без скидки.
    - `price_max_elastic` — number<double>. Цена товара для максимального размера бустинга.
    - `price_min_elastic` — number<double>. Цена товара для минимального размера бустинга.
    - `stock` — number<double>. Число единиц товара в акции типа «Скидка на сток».
  - `total` — number<double>. Общее количество товаров, которое доступно для акции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
