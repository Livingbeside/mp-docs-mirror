---
title: Количество вопросов по статусам
api: ozon-seller
method: POST
path: /v1/question/count
operation_id: Question_Count
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: dfeb8d6a7e10086e
---

# Количество вопросов по статусам

`POST /v1/question/count`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Количество вопросов по статусам

- `all` — integer<int64>. Всего вопросов.
- `new` — integer<int64>. Новые вопросы.
- `processed` — integer<int64>. Обработанные вопросы.
- `unprocessed` — integer<int64>. Необработанные вопросы.
- `viewed` — integer<int64>. Просмотренные вопросы.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
