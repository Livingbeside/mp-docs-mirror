---
title: Ответ на заявку покупателя
api: wb-customer-communication
method: PATCH
path: /api/v1/claim
operation_id: patchV1Claim
tags:
  - buyersReturns
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 6139b0310fc58bdb
---

# Ответ на заявку покупателя

`PATCH /api/v1/claim`

Описание метода

Метод отправляет ответ на [заявку](./customer-communication#tag/buyersReturns/operation/getV1Claims) покупателя на возврат товаров.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 20 запросов | 3 сек | 10 запросов |
| Сервисный | 1 мин | 20 запросов | 3 сек | 10 запросов |
| Базовый с секретом | 1 мин | 20 запросов | 3 сек | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `id` — string<UUID> **обязательный**. ID заявки
- `action` — string **обязательный**. Действие с заявкой. Используйте одно из значений массива `actions` — ответа [метода получения заявок](./customer-communication#tag/buyersReturns/operation/getV1Claims)
- `comment` — string. Комментарий. Применимо только при `"action":"rejectcustom"` или `"action":"approvecc1"`. При `"action":"rejectcustom"` параметр обязателен

## Ответы

**200** — Успешно

**400** — Неправильный запрос

- `title` — string. ID ошибки
- `detail` — string. Описание ошибки
- `requestId` — string. ID запроса

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
