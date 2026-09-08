---
title: Лимиты закреплённых отзывов
api: wb-customer-communication
method: GET
path: /api/feedbacks/v1/pins/limits
operation_id: getFeedbacksV1PinsLimits
tags:
  - pinnedFeedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 8039df398f8cb168
---

# Лимиты закреплённых отзывов

`GET /api/feedbacks/v1/pins/limits`

Описание метода

Метод возвращает лимиты закреплённых отзывов по тарифу и подписке.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Ответы

**200** — Успешно

- `data` — object **обязательный**
- `data` — object
  - `subscription` — object
    - `perUnitLimit` — integer **обязательный**. Максимальное количество закреплённых отзывов в одной карточке товара или в группе [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек
    - `remaining` — integer **обязательный**. Сколько ещё отзывов можно закрепить
    - `totalLimit` — integer **обязательный**. Общий лимит закреплений
    - `unlimited` — boolean **обязательный**. Количество закреплённых отзывов не ограничено: - `true` — да - `false` — нет
    - `used` — integer **обязательный**. Текущее количество закреплённых отзывов
  - `tariff` — object
    - `perUnitLimit` — integer **обязательный**. Максимальное количество закреплённых отзывов в одной карточке товара или в группе [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек
    - `remaining` — integer **обязательный**. Сколько ещё отзывов можно закрепить
    - `totalLimit` — integer **обязательный**. Общий лимит закреплений
    - `unlimited` — boolean **обязательный**. Количество закреплённых отзывов не ограничено: - `true` — да - `false` — нет
    - `used` — integer **обязательный**. Текущее количество закреплённых отзывов

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
