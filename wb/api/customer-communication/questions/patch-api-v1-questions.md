---
title: Работа с вопросами
api: wb-customer-communication
method: PATCH
path: /api/v1/questions
operation_id: patchV1Questions
tags:
  - questions
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: df49e62287115539
---

# Работа с вопросами

`PATCH /api/v1/questions`

Описание метода

В зависимости от тела запроса, метод позволяет:
 - отметить [вопрос](./customer-communication#tag/questions/operation/getV1Questions) как просмотренный
 - отклонить вопрос
 - ответить на вопрос или отредактировать ответ

Все ответы продавцов проходят предварительную модерацию перед публикацией

 Отредактировать ответ на вопрос можно 1 раз в течение 60 дней после отправки ответа

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `id` — string **обязательный**. Id вопроса
- `wasViewed` — boolean **обязательный**. Просмотрен ли вопрос
- `id` — string **обязательный**. Id вопроса
- `answer` — object **обязательный**
  - `text` — string **обязательный**. Текст ответа
- `state` — string **обязательный**. Статус вопроса: - `none` - вопрос отклонён продавцом (такой вопрос не отображается на портале покупателей) - `wbRu` - ответ предоставлен, вопрос отображается на сайте покупателей.

## Ответы

**200** — Успешно

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

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

**404** — Не найдено

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

**422** — Ошибка обработки параметров запроса

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
