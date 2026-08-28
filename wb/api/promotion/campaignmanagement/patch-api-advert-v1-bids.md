---
title: Изменение ставок в кампаниях
api: wb-promotion
method: PATCH
path: /api/advert/v1/bids
operation_id: patchV1Bids
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: eb64343b85edea4a
---

# Изменение ставок в кампаниях

`PATCH /api/advert/v1/bids`

Описание метода

Метод меняет ставки карточек товаров по артикулам WB в кампаниях:
 - с единой ставкой
 - с ручной ставкой
 - с моделью оплаты `cpc` — за клики

Для кампаний в статусах `4`, `9` и `11`.

В запросе укажите место размещения в параметре `placement`:
 - `combined` — в поиске и рекомендациях для кампаний с единой ставкой
 - `search `или `recommendations` — в поиске или рекомендациях для кампаний с ручной ставкой

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Сервисный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый с секретом | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `bids` — array[object] **обязательный**. Ставки в кампаниях
  - `advert_id` — integer<int64> **обязательный**. ID кампании
  - `nm_bids` — array[object] **обязательный**. Ставки
    - `bid_kopecks` — integer<int64> **обязательный**. Ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `nm_id` — integer<int64> **обязательный**. Артикул WB
    - `placement` — string (search, recommendations, combined) **обязательный**. Место размещения: - `search` — в поиске (для кампаний с ручной ставкой) - `recommendations`— в рекомендациях (для кампаний с ручной ставкой) - `combined` — в поиске и рекомендациях (для кампаний с единой ставкой)

## Ответы

**200** — Успешно

- `bids` — array[object] **обязательный**. Результат отработки запроса
  - `advert_id` — integer<int64> **обязательный**. ID кампании
  - `nm_bids` — array[object] **обязательный**. Ставки
    - `bid_kopecks` — integer<int64> **обязательный**. Ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `nm_id` — integer<int64> **обязательный**. Артикул WB
    - `placement` — string **обязательный**. Место размещения: - `search` — в поиске - `recommendations`— в рекомендациях
- `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

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
