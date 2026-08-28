---
title: Получить баланс продавца
api: wb-financial-reports-and-accounting
method: GET
path: /api/v1/account/balance
operation_id: getV1AccountBalance
tags:
  - balance
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: de525655b43b9ebf
---

# Получить баланс продавца

`GET /api/v1/account/balance`

Описание метода

Метод возвращает данные виджета баланса на [главной странице](https://seller.wildberries.ru) портала продавцов.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый | 24 ч | 1 запрос | 24 ч | 1 запрос |

## Ответы

**200** — Успешно

- `currency` — string. Валюта
- `current` — number. Текущий баланс продавца
- `for_withdraw` — number. Сумма, доступная к выводу

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
