---
title: Список вопросов
api: ozon-seller
method: POST
path: /v1/question/list
operation_id: Question_List
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7cac704dc25ca7e3
---

# Список вопросов

`POST /v1/question/list`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр.
  - `date_from` — string<date-time>. Начало периода.
  - `date_to` — string<date-time>. Конец периода.
  - `status` — string. Статусы вопроса: - `NEW` — новый, - `ALL` — все вопросы, - `VIEWED` — просмотренный, - `PROCESSED` — обработанный, - `UNPROCESSED` — необработанный.
- `last_id` — string. Идентификатор последнего значения на странице. Оставьте это поле пустым при выполнении первого запроса. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса.
- `limit` — integer<int64>. Количество значений в ответе.
- `sort_dir` — string (DESC, ASC). Направление сортировки: - `DESC` — по убыванию; - `ASC` — по возрастанию. По умолчанию: `DESC`.

## Ответы

**200** — Список вопросов

- `questions` — ?. Вопросы.
  - `answers_count` — integer<int64>. Количество ответов на вопрос.
  - `author_name` — string. Имя автора вопроса.
  - `id` — string. Идентификатор вопроса.
  - `product_url` — string. Ссылка на товар.
  - `published_at` — timestamp. Дата публикации вопроса.
  - `question_link` — string. Ссылка на вопрос.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — enum. Статусы вопроса: - `NEW` — новый, - `ALL` — все вопросы, - `VIEWED` — просмотренный, - `PROCESSED` — обработанный, - `UNPROCESSED` — необработанный.
  - `text` — string. Текст вопроса.
- `last_id` — string. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.
- `has_next` — boolean. `true`, если в ответе вернулись не все вопросы.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
