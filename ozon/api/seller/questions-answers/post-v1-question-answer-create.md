---
title: Создать ответ на вопрос
api: ozon-seller
method: POST
path: /v1/question/answer/create
operation_id: QuestionAnswer_Create
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0a33399e3d8fc25c
---

# Создать ответ на вопрос

`POST /v1/question/answer/create`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `question_id` — string **обязательный**. Идентификатор вопроса.
- `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
- `text` — string **обязательный**. Текст ответа объёмом от 2 до 3000 символов.

## Ответы

**200** — Идентификатор ответа на вопрос

- `answer_id` — string. Идентификатор ответа на вопрос.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
