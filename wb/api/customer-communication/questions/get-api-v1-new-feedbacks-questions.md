---
title: Непросмотренные отзывы и вопросы
api: wb-customer-communication
method: GET
path: /api/v1/new-feedbacks-questions
operation_id: getV1NewFeedbacksQuestions
tags:
  - questions
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 000ed870da80b990
---

# Непросмотренные отзывы и вопросы

`GET /api/v1/new-feedbacks-questions`

Описание метода

Метод проверяет наличие непросмотренных [вопросов](./customer-communication#tag/questions/operation/getV1Questions) и [отзывов](./customer-communication#tag/feedbacks/operation/getV1Feedbacks) от покупателей. Если у продавца есть непросмотренные вопросы или отзывы, возвращает `true`.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Ответы

**200** — Успешно

- `data` — object
  - `hasNewQuestions` — boolean. Есть ли непросмотренные вопросы: - `true` — да - `false` — нет
  - `hasNewFeedbacks` — boolean. Есть ли непросмотренные отзывы: - `true` — да - `false` — нет
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**403** — Доступ запрещён

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
