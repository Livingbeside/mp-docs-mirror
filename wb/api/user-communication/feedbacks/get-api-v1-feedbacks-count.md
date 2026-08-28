---
title: Количество отзывов
api: wb-user-communication
method: GET
path: /api/v1/feedbacks/count
operation_id: getV1FeedbacksCount
tags:
  - feedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 1089e001c1fc69ae
---

# Количество отзывов

`GET /api/v1/feedbacks/count`

Описание метода

Метод возвращает количество обработанных или необработанных [отзывов](./user-communication#tag/feedbacks/operation/getV1Feedbacks) за заданный период.
Отзыв считается обработанным, если выполняется одно из условий:
 - на отзыв получен ответ
 - отзыв содержит только оценку (без текста и фото)

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
| `isAnswered` | query | boolean | да | Вернуть только обработанные отзывы: - `true` — да - `false` — нет |

## Ответы

**200** — Успешно

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — integer. Количество отзывов
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
