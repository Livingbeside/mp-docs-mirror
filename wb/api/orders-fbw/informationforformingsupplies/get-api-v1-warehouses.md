---
title: Список складов
api: wb-orders-fbw
method: GET
path: /api/v1/warehouses
operation_id: getV1Warehouses
tags:
  - informationForFormingSupplies
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 7ad8f3ccbed98a96
---

# Список складов

`GET /api/v1/warehouses`

Описание метода

Метод [временно отключён](https://dev.wildberries.ru/release-notes?id=570)

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Сервисный | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Базовый с секретом | 1 мин | 6 запросов | 10 сек | 6 запросов |
| Базовый | 12 ч | 1 запрос | 12 ч | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов.

## Ответы

**200** — Успешно

- `ID` — integer. ID склада
- `name` — string. Название склада
- `address` — string. Адрес склада
- `workTime` — string. Режим работы склада
- `isActive` — boolean. Доступен ли в качестве склада назначения: - `true` — да - `false` — нет
- `isTransitActive` — boolean. Доступен ли в качестве транзитного склада: - `true` — да - `false` — нет

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**404** — Не найдено

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
