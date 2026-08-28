---
title: Списки активных и неактивных поисковых кластеров{{ /adv/v0/normquery/list }}
api: wb-promotion
method: POST
path: /adv/v0/normquery/list
operation_id: postV0NormqueryList
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: d5750f71706e9c3c
---

# Списки активных и неактивных поисковых кластеров{{ /adv/v0/normquery/list }}

`POST /adv/v0/normquery/list`

Описание метода Метод возвращает списки активных и неактивных поисковых кластеров, по которым было не меньше 100 показов. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 5 запросов | 200 мс | 10 запросов | | Сервисный | 1 сек | 5 запросов | 200 мс | 10 запросов | | Базовый с секретом | 1 сек | 5 запросов | 200 мс | 10 запросов | | Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

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
    - `excluded` — array[string]. Неактивные поисковые кластеры
    - `archived` — array[string]. Архивные поисковые кластеры

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
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
