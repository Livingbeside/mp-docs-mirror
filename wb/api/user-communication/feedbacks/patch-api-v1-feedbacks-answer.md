---
title: Отредактировать ответ на отзыв
api: wb-user-communication
method: PATCH
path: /api/v1/feedbacks/answer
operation_id: patchV1FeedbacksAnswer
tags:
  - feedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: a23c430ede41b7bd
---

# Отредактировать ответ на отзыв

`PATCH /api/v1/feedbacks/answer`

Описание метода

Метод позволяет отредактировать уже отправленный [ответ на отзыв](./user-communication#tag/feedbacks/operation/postV1FeedbacksAnswer) покупателя.

Отредактировать ответ можно только один раз в течение 60 дней c момента отправки.

 ID отзыва не валидируется. Если в запросе вы передали некорректный ID, вы не получите ошибку.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `id` — string **обязательный**. ID отзыва
- `text` — string **обязательный**. Текст ответа

## Ответы

**204** — Успешно

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
