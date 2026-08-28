---
title: Восстановление карточек товаров из корзины
api: wb-work-with-products
method: POST
path: /content/v2/cards/recover
operation_id: post-content-v2-cards-recover
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: f149a12658ced136
---

# Восстановление карточек товаров из корзины

`POST /content/v2/cards/recover`

Описание метода

Метод восстанавливает [карточки товаров из корзины](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1trash/post).

 Карточка товара сохраняет тот же imtID — ID для объединённых карточек товаров — что был присвоен ей при перемещении в корзину

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 3 запроса | 20 сек | 5 запросов |
| Сервисный | 1 мин | 3 запроса | 20 сек | 5 запросов |
| Базовый с секретом | 1 мин | 3 запроса | 20 сек | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `nmIDs` — array[integer]. Артикулы WB

## Ответы

**200** — Успешно

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**400** — Неправильный запрос

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

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

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
