---
title: Список доступных для акции товаров
api: ozon-seller
method: POST
path: /v1/actions/candidates
operation_id: PromosCandidates
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: 7e508bfeeeca45db
---

# Список доступных для акции товаров

`POST /v1/actions/candidates`

> ⚠️ Метод помечен как **deprecated**.

13 октября 2026 года отключим метод. Переключитесь на [/v2/actions/candidates](#operation/ActionsCandidates).

Метод для получения списка товаров, которые могут участвовать в акции, по её идентификатору.

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — number<double> **обязательный**. Идентификатор акции. Можно получить с помощью метода [/v1/actions](#operation/Promos).
- `limit` — number<double>. Количество ответов на странице. По умолчанию — 100.
- `last_id` — number<double>. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым.

## Ответы

**200** — Список товаров

- `result` — object. Результаты запроса.
  - `products` — array[object]. Список товаров.
    - `id` — number<double>. Идентификатор товара в системе Ozon — `product_id`.
    - `price` — number<double>. Текущая цена товара без скидки.
    - `action_price` — number<double>. Цена товара по акции.
    - `alert_max_action_price_failed` — boolean. `true`, если цена товара выше рекомендуемой. Товар отмечен красным и может быть исключён из акции.
    - `alert_max_action_price` — number<double>. Рекомендуемая цена товара по акции.
    - `max_action_price` — number<double>. Максимально возможная цена товара по акции.
    - `add_mode` — string. Тип добавления товара в акцию: автоматически или вручную продавцом.
    - `min_stock` — number<double>. Минимальное число единиц товара в акции типа «Скидка на сток».
    - `stock` — number<double>. Число единиц товара в акции типа «Скидка на сток».
    - `current_boost` — number<double>. Размер бустинга товара.
    - `price_min_elastic` — number<double>. Цена товара для минимального размера бустинга.
    - `price_max_elastic` — number<double>. Цена товара для максимального размера бустинга.
    - `min_boost` — number<double>. Минимальный размер бустинга в процентах.
    - `max_boost` — number<double>. Максимальный размер бустинга в процентах.
  - `total` — number<double>. Общее количество товаров, которое доступно для акции.
  - `last_id` — number<double>. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
