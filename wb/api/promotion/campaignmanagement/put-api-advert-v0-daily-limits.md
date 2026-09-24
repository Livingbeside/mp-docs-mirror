---
title: Настройка дневных лимитов кампаний
api: wb-promotion
method: PUT
path: /api/advert/v0/daily-limits
operation_id: putV0DailyLimits
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 7b83096f7acfec4f
---

# Настройка дневных лимитов кампаний

`PUT /api/advert/v0/daily-limits`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод включает, выключает и обновляет дневной лимит кампаний.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Сервисный | 1 мин | 5 запросов | 12 сек | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `advertIds` — array[integer<int64>] **обязательный**. ID кампаний
- `enabled` — boolean **обязательный**. Включить лимит: - `true` — да - `false` — нет
- `dailyLimit` — integer<int64>. Сумма дневного лимита. Параметр обязателен при `"enabled": true`. Минимально допустимая сумма указана в поле `minDailyLimit` метода [GET /api/advert/v1/config]()
- `carryOverEnabled` — boolean. Переносить неиспользованный остаток лимита на следующий день: - `true` — да - `false` — нет Параметр обязателен при `"enabled": true`

## Ответы

**200** — Успешно

- `adverts` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `belowMinLimit` — boolean **обязательный**. Установленный размер дневного лимита ниже рекомендуемого минимума относительно текущих ставок `requiredLimit`: - `true` — да - `false` — нет
  - `requiredLimit` — integer<int64> **обязательный**. Рекомендуемый минимальный размер дневного лимита при текущих ставках кампании. Указывается в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). С меньшим лимитом бюджет может расходоваться неравномерно и в кампании возникнут ошибки

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
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
