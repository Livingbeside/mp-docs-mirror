---
title: Непросмотренные отзывы и вопросы
api: wb-user-communication
method: GET
path: /api/v1/new-feedbacks-questions
operation_id: getV1NewFeedbacksQuestions
tags:
  - questions
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: b7047a06ea1ade84
---

# Непросмотренные отзывы и вопросы

`GET /api/v1/new-feedbacks-questions`

Описание метода

Метод проверяет наличие непросмотренных [вопросов](./user-communication#tag/questions/operation/getV1Questions) и [отзывов](./user-communication#tag/feedbacks/operation/getV1Feedbacks) от покупателей. Если у продавца есть непросмотренные вопросы или отзывы, возвращает `true`.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Ответы

**200** — Успешно

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
  - `hasNewFeedbacks` — boolean. Есть ли непросмотренные отзывы: - `true` — да - `false` — нет
  - `hasNewQuestions` — boolean. Есть ли непросмотренные вопросы: - `true` — да - `false` — нет
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки

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

**403** — Доступ запрещён

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `requestId` — string

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
