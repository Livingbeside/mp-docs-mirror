---
title: Товары с наибольшим количеством вопросов
api: ozon-seller
method: POST
path: /v1/question/top-sku
operation_id: Question_TopSku
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a2af463b1f83d3ba
---

# Товары с наибольшим количеством вопросов

`POST /v1/question/top-sku`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<int64> **обязательный**. Количество значений в ответе.

## Ответы

**200** — Идентификаторы товаров

- `sku` — ?. Список идентификаторов товаров в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
