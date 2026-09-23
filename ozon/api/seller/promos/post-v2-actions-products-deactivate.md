---
title: Удалить товары из акции «Промокоды»
api: ozon-seller
method: POST
path: /v2/actions/products/deactivate
operation_id: ActionsProductsDeactivate
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d9bbbae86b2ad534
---

# Удалить товары из акции «Промокоды»

`POST /v2/actions/products/deactivate`

Чтобы удалить товары из акций «Эластичный бустинг» или «Максимальный бустинг», используйте метод [/v1/actions/products/update](#operation/ActionsProductsUpdate) и измените цену товара `action_price` на значение меньше или равное лимиту акции.

До 13 октября 2026 года метод работает аналогично [/v1/actions/products/deactivate](#operation/PromosProductsDeactivate).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции. Получите методом [/v1/actions](#operation/Promos).
- `product_ids` — array[string<uint64>] **обязательный**. Список идентификаторов товаров в системе Ozon — `product_id`.

## Ответы

**200** — Товары удалены из акции

- `product_ids` — array[string<uint64>]. Список идентификаторов товаров, которые удалены из акции.

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
