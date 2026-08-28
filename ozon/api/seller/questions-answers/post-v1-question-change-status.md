---
title: Изменить статус вопросов
api: ozon-seller
method: POST
path: /v1/question/change-status
operation_id: Question_ChangeStatus
tags:
  - Questions&Answers
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a545208ad13cd3af
---

# Изменить статус вопросов

`POST /v1/question/change-status`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `question_ids` — ? **обязательный**. Идентификаторы вопросов.
- `status` — string **обязательный**. Статусы вопросов: - `NEW` — новые, - `VIEWED` — просмотренные, - `PROCESSED` — обработанные.

## Ответы

**200** — Статус изменён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — string. Дополнительная информация об ошибке.
- `message` — string. Описание ошибки.
