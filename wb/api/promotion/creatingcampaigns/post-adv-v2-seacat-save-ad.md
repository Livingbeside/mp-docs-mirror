---
title: Создать кампанию
api: wb-promotion
method: POST
path: /adv/v2/seacat/save-ad
operation_id: postV2SeacatSaveAd
tags:
  - creatingCampaigns
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 47adbea2218aea69
---

# Создать кампанию

`POST /adv/v2/seacat/save-ad`

Описание метода

Метод создаёт кампанию:
 - с ручной ставкой для продвижения товаров в поиске и/или рекомендациях
 - с единой ставкой для продвижения товаров одновременно в поиске и рекомендациях

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Сервисный | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Базовый с секретом | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `bid_type` — string (manual, unified). Тип ставки: - `manual` — ручная - `unified` — единая По умолчанию: `manual`.
- `name` — string **обязательный**. Название кампании
- `nms` — array[integer]. Карточки товаров для кампании. Доступные карточки товаров можно получить с помощью метода [Карточки товаров для кампаний](./promotion#tag/creatingCampaigns/operation/postV2SupplierNms). Максимум 50 товаров (`nm`)
- `payment_type` — string (cpm, cpc). Тип оплаты: - `cpm` — за показы - `cpc` — за клик. При создании с этим типом оплаты в кампании автоматически устанавливается минимальная ставка По умолчанию: `cpm`.
- `placement_types` — array[string (search, recommendations)]. Места размещения: - `search` — в поиске - `recommendations` — в рекомендациях Укажите только для кампании с ручной ставкой По умолчанию: `['search']`.

## Ответы

**200** — Успешно

**400** — Неправильный запрос

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
