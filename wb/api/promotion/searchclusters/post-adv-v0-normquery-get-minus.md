---
title: Список минус-фраз кампаний{{ /adv/v0/normquery/get-minus }}
api: wb-promotion
method: POST
path: /adv/v0/normquery/get-minus
operation_id: postV0NormqueryGetMinus
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 96d1a436b61659d4
---

# Список минус-фраз кампаний{{ /adv/v0/normquery/get-minus }}

`POST /adv/v0/normquery/get-minus`

Описание метода Метод возвращает список минус-фраз по: - ID кампаний - артикулам WB Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 5 запросов | 200 мс | 10 запросов | | Сервисный | 1 сек | 5 запросов | 200 мс | 10 запросов | | Базовый с секретом | 1 сек | 5 запросов | 200 мс | 10 запросов | | Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `items` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB

## Ответы

**200** — Успешно

- `items` — array[object]
  - `advert_id` — integer. ID кампании
  - `nm_id` — integer. Артикул WB
  - `norm_queries` — array[string]. Список минус-фраз

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

**403** — Доступ запрещён

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
