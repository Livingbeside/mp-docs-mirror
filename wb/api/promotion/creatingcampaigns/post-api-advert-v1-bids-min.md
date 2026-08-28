---
title: Минимальные ставки для карточек товаров
api: wb-promotion
method: POST
path: /api/advert/v1/bids/min
operation_id: postV1BidsMin
tags:
  - creatingCampaigns
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 152671d4d6afc015
---

# Минимальные ставки для карточек товаров

`POST /api/advert/v1/bids/min`

Описание метода

Метод возвращает минимальные ставки для карточек товаров в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) — по типу оплаты и местам размещения.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 20 запросов | 3 сек | 5 запросов |
| Сервисный | 1 мин | 20 запросов | 3 сек | 5 запросов |
| Базовый с секретом | 1 мин | 20 запросов | 3 сек | 5 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `advert_id` — integer<int64> **обязательный**. ID кампании
- `nm_ids` — array[integer<int64>] **обязательный**. Список артикулов WB
- `payment_type` — string (cpm, cpc) **обязательный**. Тип оплаты: - `cpm` — за показы - `cpc` — за клик
- `placement_types` — array[string (combined, search, recommendation)] **обязательный**. Места размещения: - `search` — поиск - `recommendation` — рекомендации - `combined` — поиск и рекомендации

## Ответы

**200** — Успешно

- `bids` — array[object] **обязательный**. Список карточек товаров со ставками
  - `bids` — array[object] **обязательный**. Список ставок по местам размещения
    - `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
    - `type` — string (combined, search, recommendation) **обязательный**. Места размещения: - `search` — поиск - `recommendation` — рекомендации - `combined` — поиск и рекомендации
    - `value` — integer **обязательный**. Минимальная ставка в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `nm_id` — integer<int64> **обязательный**. Артикул WB

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
