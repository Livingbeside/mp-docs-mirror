---
title: Количество вопросов
api: wb-user-communication
method: GET
path: /api/v1/questions/count
operation_id: getV1QuestionsCount
tags:
  - questions
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 1bdfb4376d85dbd6
---

# Количество вопросов

`GET /api/v1/questions/count`

Описание метода

Метод возвращает количество отвеченных или неотвеченных [вопросов](./user-communication#tag/questions/operation/getV1Questions) за заданный период.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | integer | нет | Дата начала периода в формате Unix timestamp |
| `dateTo` | query | integer | нет | Дата конца периода в формате Unix timestamp |
| `isAnswered` | query | boolean | нет | Есть ли ответ на вопрос: - `true` — да - `false` — нет |

## Ответы

**200** — Успешно

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — integer. Количество вопросов
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки

**400** — Неправильный запрос

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `requestId` — string

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
