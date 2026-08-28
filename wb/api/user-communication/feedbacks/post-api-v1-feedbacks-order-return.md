---
title: Возврат товара по ID отзыва
api: wb-user-communication
method: POST
path: /api/v1/feedbacks/order/return
operation_id: postV1FeedbacksOrderReturn
tags:
  - feedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 1d6e82c007574b02
---

# Возврат товара по ID отзыва

`POST /api/v1/feedbacks/order/return`

Описание метода

Метод запрашивает возврат товара, по которому оставлен [отзыв](./user-communication#tag/feedbacks/operation/getV1Feedbacks).

Возврат доступен для отзывов с полем `"isAbleReturnProductOrders": true`.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `feedbackId` — string. ID отзыва

## Ответы

**200** — Успешно

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
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

**422** — Ошибка обработки параметров запроса

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
