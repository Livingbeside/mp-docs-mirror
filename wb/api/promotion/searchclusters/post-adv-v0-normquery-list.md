---
title: Списки активных и неактивных поисковых кластеров
api: wb-promotion
method: POST
path: /adv/v0/normquery/list
operation_id: postV0NormqueryList
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 589d174782fc21d7
---

# Списки активных и неактивных поисковых кластеров

`POST /adv/v0/normquery/list`

Описание метода

Метод возвращает списки активных и неактивных поисковых кластеров, по которым было не меньше 100 показов.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 5 запросов | 200 мс | 10 запросов |
| Сервисный | 1 сек | 5 запросов | 200 мс | 10 запросов |
| Базовый с секретом | 1 сек | 5 запросов | 200 мс | 10 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `items` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `nmId` — integer<int64> **обязательный**. Артикул WB

## Ответы

**200** — Успешно

- `items` — array[object] **обязательный**
  - `advertId` — integer<int64>. ID кампании
  - `nmId` — integer<int64>. Артикул WB
  - `normQueries` — object. Поисковые кластеры
    - `active` — array[string]. Активные поисковые кластеры
    - `archived` — array[string]. Архивные поисковые кластеры
    - `excluded` — array[string]. Неактивные поисковые кластеры

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

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
