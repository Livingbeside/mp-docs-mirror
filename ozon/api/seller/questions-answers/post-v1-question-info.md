---
title: Информация о вопросе
api: ozon-seller
method: POST
path: /v1/question/info
operation_id: Question_Info
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a18f3bff1a2c7c74
---

# Информация о вопросе

`POST /v1/question/info`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `question_id` — string **обязательный**. Идентификатор вопроса.

## Ответы

**200** — Информация о вопросе

- `answers_count` — integer<int64>. Количество ответов на вопрос.
- `author_name` — string. Автор вопроса.
- `id` — string. Идентификатор вопроса.
- `product_url` — string. Ссылка на товар.
- `published_at` — timestamp. Дата публикации вопроса.
- `question_link` — string. Ссылка на вопрос.
- `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `status` — enum. Статус вопроса: - `NEW` — новый, - `ALL` — все вопросы, - `VIEWED` — просмотренный, - `PROCESSED` — обработанный, - `UNPROCESSED` — необработанный.
- `text` — string. Текст вопроса.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
