---
title: Список ответов на вопрос
api: ozon-seller
method: POST
path: /v1/question/answer/list
operation_id: QuestionAnswer_List
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 180173ad88f6379b
---

# Список ответов на вопрос

`POST /v1/question/answer/list`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `last_id` — ?. Идентификатор последнего значения на странице. Если запрос первый, оставьте поле пустым. Для следующих значений указывайте `last_id` из ответа предыдущего запроса.
- `question_id` — string **обязательный**. Идентификатор вопроса.
- `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Список ответов на вопрос

- `answers` — ?. Ответы.
  - `author_name` — string. Автор ответа.
  - `id` — string. Идентификатор ответа.
  - `published_at` — timestamp. Дата публикации ответа.
  - `question_id` — string. Идентификатор вопроса.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status_publication` — string (PUBLISHED, AWAITING_MODERATION, MODERATION_FAILED, DUPLICATE). Статус публикации ответа: - `PUBLISHED` — опубликован; - `AWAITING_MODERATION` — ожидает модерации; - `MODERATION_FAILED` — модерация не пройдена; - `DUPLICATE` — дубль.
  - `text` — string. Текст ответа.
- `last_id` — string. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
