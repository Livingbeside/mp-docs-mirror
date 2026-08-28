---
title: Список ставок поисковых кластеров
api: wb-promotion
method: POST
path: /adv/v0/normquery/get-bids
operation_id: postV0NormqueryGetBids
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 3a05747b37eec88b
---

# Список ставок поисковых кластеров

`POST /adv/v0/normquery/get-bids`

Описание метода

Метод возвращает список поисковых кластеров со ставками по:
 - ID кампаний
 - артикулам WB

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
  - `advert_id` — integer **обязательный**. ID кампании
  - `nm_id` — integer **обязательный**. Артикул WB

## Ответы

**200** — Успешно

- `bids` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `bid` — integer **обязательный**. Текущая ставка в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) за тысячу показов
  - `bid_kopecks` — integer **обязательный**. Текущая ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) за тысячу показов
  - `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `nm_id` — integer **обязательный**. Артикул WB
  - `norm_query` — string **обязательный**. Поисковый кластер

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

**403** — Доступ запрещён

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `request_id` — string **обязательный**. Уникальный ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
