---
title: Получить список товаров из автодобавления в акцию
api: ozon-seller
method: POST
path: /v2/actions/auto-add/products/list
operation_id: ActionsAutoAddProductsListV2
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e08bdd88dddeed05
---

# Получить список товаров из автодобавления в акцию

`POST /v2/actions/auto-add/products/list`

До 13 октября 2026 года метод работает аналогично [/v1/actions/auto-add/products/list](#operation/ActionsAutoAddProductsList).

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

**200** — Список товаров с автодобавлением

- `products` — array[object]. Список товаров с автодобавлением.
  - `action_price_to_auto_add` — object. Цена товара по акции.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `add_mode` — boolean. `true`, если продавец добавил товар вручную.
  - `base_price` — object. Цена товара до скидки.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `currency` — string. Валюта цен.
  - `has_expired_min_seller_price` — boolean. `true`, если истёк срок действия ограничения для акции.
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
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
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
