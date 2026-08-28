---
title: Установить ставки для поисковых кластеров
api: wb-promotion
method: POST
path: /adv/v0/normquery/bids
operation_id: postV0NormqueryBids
tags:
  - searchClusters
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 9880d6fa5f9133ec
---

# Установить ставки для поисковых кластеров

`POST /adv/v0/normquery/bids`

Описание метода

Метод устанавливает ставки в рублях на поисковые кластеры.

Можно использовать только для кампаний с:
 - ручной ставкой
 - моделью оплаты `cpm` — за показы

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 2 запроса | 500 мс | 4 запроса |
| Сервисный | 1 сек | 2 запроса | 500 мс | 4 запроса |
| Базовый с секретом | 1 сек | 2 запроса | 500 мс | 4 запроса |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `bids` — array[object] **обязательный**
  - `advert_id` — integer **обязательный**. ID кампании
  - `bid` — integer **обязательный**. Ставка за тысячу показов в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `nm_id` — integer **обязательный**. Артикул WB
  - `norm_query` — string **обязательный**. Поисковый кластер

## Ответы

**200** — Успешно

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
