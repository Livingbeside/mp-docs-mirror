---
title: Получить список товаров, которые могут участвовать в акции
api: ozon-seller
method: POST
path: /v2/actions/candidates
operation_id: ActionsCandidates
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: abf48a8f2921d63d
---

# Получить список товаров, которые могут участвовать в акции

`POST /v2/actions/candidates`

До 13 октября 2026 года метод работает аналогично [/v1/actions/candidates](#operation/PromosCandidates).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64>. Идентификатор акции. Получите методом [/v1/actions](#operation/Promos).
- `last_id` — string. Идентификатор последнего значения на странице. При первом запросе оставьте пустым.
- `limit` — integer<uint64>. Количество значений на странице.

## Ответы

**200** — Список товаров, которые могут участвовать в акции

- `last_id` — string. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.
- `products` — array[object]. Список товаров.
  - `action_price` — object. Цена товара по акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `alert_max_action_price` — object. Рекомендуемая цена товара по акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `alert_max_action_price_failed` — boolean. `true`, если цена товара выше рекомендуемой. Товар может быть исключён из акции.
  - `current_boost` — number<double>. Размер бустинга товара.
  - `id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `is_quarantined` — boolean. `true`, если товар в карантине.
  - `marketplace_seller_price` — object. Цена товара с учётом акций, кроме акций за счёт Ozon.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `max_action_price` — object. Максимальная цена товара по акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `max_boost` — number<double>. Максимальный размер бустинга в процентах.
  - `min_boost` — number<double>. Минимальный размер бустинга в процентах.
  - `min_seller_price` — object. Минимальная цена товара после применения акций.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `min_stock` — integer<uint64>. Минимальное число единиц товара в акции типа «Скидка на сток».
  - `price` — object. Цена товара без скидки.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `price_max_elastic` — object. Цена товара для максимального размера бустинга.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `price_min_elastic` — object. Цена товара для минимального размера бустинга.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `recommended_stock` — integer<uint64>. Рекомендуемое количество товара для участия в акции.
  - `website_prices` — object. Цены товара на сайте.
    - `price` — object. Минимальная средняя цена по схемам доставки на сайте.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `prices_by_schema` — object. Цены товара по схемам доставки.
- `total` — integer<uint64>. Общее количество товаров, которое доступно для акции.

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
