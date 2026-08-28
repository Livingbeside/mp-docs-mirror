---
title: Состояние обработанной загрузки
api: wb-work-with-products
method: GET
path: /api/v2/history/tasks
operation_id: get-api-v2-history-tasks
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: ed72de74d4280f59
---

# Состояние обработанной загрузки

`GET /api/v2/history/tasks`

Описание метода

Метод возвращает информацию об обработанной загрузке цен и скидок.

 Обработанная загрузка — это загрузка цен и скидок для товаров, цен для размеров товаров, скидок WB Клуба и оптовых скидок для B2B-продаж.

Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `uploadID` | query | integer | да | ID загрузки |

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `activationDate` — string<date-time>. Дата и время, когда загрузка отправляется в обработку
  - `overAllGoodsNumber` — integer. Всего товаров
  - `status` — integer. Статус загрузки: * `3` — обработана, в товарах нет ошибок, цены и скидки обновились * `4` — отменена * `5` — обработана, но в товарах есть ошибки. Для товаров без ошибок цены и скидки обновились, а ошибки в остальных товарах можно получить с помощью метода [Детализация обработанной загрузки](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1history~1goods~1task/get) * `6` — обработана, но во всех товарах есть ошибки. Их тоже можно получить с помощью метода [Детализация обработанной загрузки](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1history~1goods~1task/get)
  - `successGoodsNumber` — integer. Товаров без ошибок
  - `uploadDate` — string<date-time>. Дата и время, когда загрузка создана
  - `uploadID` — integer. ID загрузки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

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

**403** — Доступ запрещён

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
