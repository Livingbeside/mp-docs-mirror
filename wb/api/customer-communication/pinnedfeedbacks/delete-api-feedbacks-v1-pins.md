---
title: Открепить отзывы
api: wb-customer-communication
method: DELETE
path: /api/feedbacks/v1/pins
operation_id: deleteFeedbacksV1Pins
tags:
  - pinnedFeedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 111532a1e44d407a
---

# Открепить отзывы

`DELETE /api/feedbacks/v1/pins`

Описание метода

Метод позволяет открепить отзывы в карточке товара или в группе [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек.

Чтобы получить `pinId` — ID операций закрепления, используйте метод [Список закреплённых и откреплённых отзывов](./user-communication#tag/pinnedFeedbacks/operation/getFeedbacksV1Pins).

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Успешно

- `data` — object **обязательный**
- `data` — array[integer]. Список `pinId` — ID операций закрепления отзывов, которые были успешно откреплены

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
