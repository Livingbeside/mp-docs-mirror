---
title: Получение истории пополнений счёта
api: wb-promotion
method: GET
path: /adv/v1/payments
operation_id: getV1Payments
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: e26d5a079f4f8744
---

# Получение истории пополнений счёта

`GET /adv/v1/payments`

Описание метода

Метод возвращает историю пополнений счёта **WB Продвижение** за заданный период.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Сервисный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый с секретом | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `from` | query | string<date> | нет | Начало интервала |
| `to` | query | string<date> | нет | Конец интервала. (Минимальный интервал 1 день, максимальный 31) |

## Ответы

**200** — Успешно

- `id` — integer. ID платежа
- `date` — string<time-date>. Дата платежа
- `sum` — integer. Сумма платежа
- `type` — integer. Тип источника списания: - `0` — Счёт - `1` — Баланс - `3` — Картой
- `statusId` — integer. Статус: - `0` — ошибка - `1` — обработано
- `cardStatus` — string. Статус операции при оплате картой: - `success` — успех - `fail` — неуспех - `pending` — в ожидании ответа - `unknown` — неизвестно
- `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

**204** — История пополнений счета не найдена

**400** — Неправильный запрос

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
