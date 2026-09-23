---
title: Получить список доступных товаров для автодобавления в акцию
api: ozon-seller
method: POST
path: /v1/actions/auto-add/products/candidates
operation_id: ActionsAutoAddProductsCandidates
tags:
  - PromosBeta
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: 1c3726f3bc94b2eb
---

# Получить список доступных товаров для автодобавления в акцию

`POST /v1/actions/auto-add/products/candidates`

> ⚠️ Метод помечен как **deprecated**.

13 октября 2026 года отключим метод. Переключитесь на [/v2/actions/auto-add/products/candidates](#operation/ActionsAutoAddProductsCandidatesV2).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2009-Novye-metody-dlia-upravleniia-avtodobavleniem-tovarov-v-aktsii/) в сообществе разработчиков Ozon for dev.

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
  - `action_price_to_auto_add` — number<double>. Цена товара по акции.
  - `base_price` — number<double>. Цена товара до скидки.
  - `currency` — string. Валюта цен.
  - `marketplace_seller_price` — number<double>. Цена товара с учётом акций, кроме акций за счёт Ozon.
  - `max_discount_price` — number<double>. Максимальная цена товара для автодобавления в акцию.
  - `min_action_quantity` — integer<uint64>. Минимальное число единиц товара в акции типа «Скидка на сток».
  - `min_seller_price` — number<double>. Минимальная цена товара после применения акций.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `price` — number<double>. Цена товара без скидки.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `quantity_to_auto_add` — integer<uint64>. Количество товара в акции.
  - `sku` — integer<uint64>. Идентификатор товара в системе Ozon — SKU.
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
