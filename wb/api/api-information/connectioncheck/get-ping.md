---
title: Проверка подключения
api: wb-api-information
method: GET
path: /ping
operation_id: getPing
tags:
  - connectionCheck
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: ee72ea126285073c
---

# Проверка подключения

`GET /ping`

Описание метода

Метод проверяет:
 1. Успешно ли запрос доходит до WB API
 2. Валидность токена авторизации и URL запроса
 3. Совпадают ли категория токена и сервис

 Метод не предназначен для проверки доступности сервисов WB

У каждого сервиса есть свой вариант метода в зависимости от домена:

| Категория | URL запроса |
|---------------|-----------------------|
| Контент | `https://content-api.wildberries.ru/ping`<br>`https://content-api-sandbox.wildberries.ru/ping` |
| Аналитика | `https://seller-analytics-api.wildberries.ru/ping` |
| Цены и скидки | `https://discounts-prices-api.wildberries.ru/ping`<br>`https://discounts-prices-api-sandbox.wildberries.ru/ping` |
| Маркетплейс | `https://marketplace-api.wildberries.ru/ping` |
| Статистика | `https://statistics-api.wildberries.ru/ping`<br>`https://statistics-api-sandbox.wildberries.ru/ping` |
| Продвижение | `https://advert-api.wildberries.ru/ping`<br>`https://advert-api-sandbox.wildberries.ru/ping` |
| Вопросы и отзывы | `https://feedbacks-api.wildberries.ru/ping`<br>`https://feedbacks-api-sandbox.wildberries.ru/ping` |
| Чат с покупателями | `https://buyer-chat-api.wildberries.ru/ping` |
| Поставки | `https://supplies-api.wildberries.ru/ping` |
| Возвраты покупателями | `https://returns-api.wildberries.ru/ping` |
| Документы | `https://documents-api.wildberries.ru/ping` |
| Финансы | `https://finance-api.wildberries.ru/ping` |
| Тарифы, Новости, Получить информацию о продавце | `https://common-api.wildberries.ru/ping` |
| Управление пользователями продавца | `https://user-management-api.wildberries.ru/ping` |

 Максимум 3 запроса за 30 секунд. Если попытаться автоматизировать использование метода, запросы будут временно заблокированы. Лимит действует отдельно для каждого варианта метода в зависимости от домена

## Ответы

**200** — Успешно

- `Status` — string (OK). Статус
- `TS` — string. Timestamp запроса

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
