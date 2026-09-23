---
title: Получить список доступных товаров для автодобавления в акцию
api: ozon-seller
method: POST
path: /v2/actions/auto-add/products/candidates
operation_id: ActionsAutoAddProductsCandidatesV2
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4c53b4964c089b04
---

# Получить список доступных товаров для автодобавления в акцию

`POST /v2/actions/auto-add/products/candidates`

До 13 октября 2026 года метод работает аналогично [/v1/actions/auto-add/products/candidates](#operation/ActionsAutoAddProductsCandidates).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции.
- `auto_add_date` — string<date-time> **обязательный**. Дата и время автодобавления товаров в акцию из параметра `result.auto_add_dates` в ответе метода [/v1/actions](#operation/Promos).
- `limit` — integer<uint64> **обязательный**. Количество значений в ответе.
- `offset` — integer<uint64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, ответ начнётся с 11-го найденного элемента. По умолчанию: `0`.

## Ответы

**200** — Список доступных товаров для автодобавления в акцию

- `products` — array[object]. Список доступных товаров для автодобавления.
  - `action_price_to_auto_add` — object. Цена товара по акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `base_price` — object. Цена товара до скидки.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `currency` — string. Валюта цен.
  - `has_expired_min_seller_price` — boolean. `true`, если истёк срок действия ограничения для акции.
  - `id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `is_manually_added` — boolean. `true`, если товар добавлен вручную.
  - `marketplace_seller_price` — object. Цена товара с учётом акций, кроме акций за счёт Ozon.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `max_discount_price` — object. Максимальная цена товара для автодобавления в акцию.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `min_action_quantity` — integer<uint64>. Минимальное число единиц товара в акции типа «Скидка на сток».
  - `min_seller_price` — object. Минимальная цена товара после применения акций.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `price` — object. Цена товара без скидки.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `quantity_to_auto_add` — integer<uint64>. Количество товара в акции.
  - `sku` — integer<uint64>. Идентификатор товара в системе Ozon — SKU.
  - `website_prices` — object. Цены товара на сайте.
    - `price` — object. Минимальная средняя цена по схемам доставки на сайте.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `prices_by_schema` — object. Цены товара по схемам доставки.
  - `will_be_quarantined` — boolean. `true`, если товар попадает в карантин после автодобавления.
- `total` — integer<uint64>. Количество товаров.

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
