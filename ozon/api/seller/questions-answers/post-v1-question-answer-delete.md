---
title: Удалить ответ на вопрос
api: ozon-seller
method: POST
path: /v1/question/answer/delete
operation_id: QuestionAnswer_Delete
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f3e05e20ff8da4f7
---

# Удалить ответ на вопрос

`POST /v1/question/answer/delete`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `answer_id` — string **обязательный**. Идентификатор ответа.
- `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Ответ удалён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
