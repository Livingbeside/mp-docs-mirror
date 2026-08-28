---
title: Изменение мест размещения в кампаниях с ручной ставкой{{ /adv/v0/auction/placements }}
api: wb-promotion
method: PUT
path: /adv/v0/auction/placements
operation_id: putV0AuctionPlacements
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: ea447b7c06741728
---

# Изменение мест размещения в кампаниях с ручной ставкой{{ /adv/v0/auction/placements }}

`PUT /adv/v0/auction/placements`

Описание метода Метод меняет места размещения в кампаниях с ручной ставкой и моделью оплаты за показы — `cpm`. Для кампаний в статусах `4`, `9` и `11`. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 1 запрос | 1 сек | 1 запрос | | Сервисный | 1 сек | 1 запрос | 1 сек | 1 запрос | | Базовый с секретом | 1 сек | 1 запрос | 1 сек | 1 запрос | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `placements` — array[object] **обязательный**. Места размещения в кампаниях
  - `advert_id` — integer<int64> **обязательный**. ID кампании
  - `placements` — object **обязательный**. Места размещения
    - `search` — boolean **обязательный**. Размещение в поиске: - `false` — отключено - `true` — включено
    - `recommendations` — boolean **обязательный**. Размещение в рекомендациях: - `false` — отключено - `true` — включено

## Ответы

**204** — Успешно

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
