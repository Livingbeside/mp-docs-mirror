---
title: Удалить товары из акции
api: ozon-seller
method: POST
path: /v1/actions/products/deactivate
operation_id: PromosProductsDeactivate
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: ab4574363fcea4b6
---

# Удалить товары из акции

`POST /v1/actions/products/deactivate`

> ⚠️ Метод помечен как **deprecated**.

13 октября 2026 года отключим метод. Переключитесь на [/v2/actions/products/deactivate](#operation/ActionsProductsDeactivate).

Метод для удаления товаров из акции.

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — number<double> **обязательный**. Идентификатор акции. Можно получить с помощью метода [/v1/actions](#operation/Promos).
- `product_ids` — array[number<double>] **обязательный**. Список идентификаторов товаров в системе Ozon — `product_id`.

## Ответы

**200** — Товары удалены из акции

- `result` — object. Результаты запроса.
  - `product_ids` — array[number<double>]. Список идентификаторов товаров, которые удалены из акции.
  - `rejected` — array[object]. Список товаров, которые не удалось удалить из акции.
    - `product_id` — number<double>. Идентификатор товара в системе Ozon — `product_id`.
    - `reason` — string. Причина, почему товар не удалён из акции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
