---
title: Переименование кампании
api: wb-promotion
method: POST
path: /adv/v0/rename
operation_id: postV0Rename
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: f328dc791de821d1
---

# Переименование кампании

`POST /adv/v0/rename`

Описание метода

Метод меняет название [кампании](./promotion#tag/campaigns/operation/getV2Adverts). Это можно сделать в любой момент существования кампании.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Сервисный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый с секретом | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `advertId` — integer **обязательный**. ID кампании, в которой меняется название
- `name` — string **обязательный**. Новое название (максимум 100 символов)

## Ответы

**200** — Успешно

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

**422** — Ошибка обработки параметров запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
