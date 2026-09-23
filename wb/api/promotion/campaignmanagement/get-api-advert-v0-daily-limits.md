---
title: Получить настройки дневных лимитов кампаний
api: wb-promotion
method: GET
path: /api/advert/v0/daily-limits
operation_id: getV0DailyLimits
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: dc9147dc4d172c3c
---

# Получить настройки дневных лимитов кампаний

`GET /api/advert/v0/daily-limits`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод возвращает текущие настройки [дневных лимитов кампаний CPC](https://cmp.wildberries.ru/campaigns/help/knowledge-base/options#%D0%94%D0%BD%D0%B5%D0%B2%D0%BD%D0%BE%D0%B9%D0%BB%D0%B8%D0%BC%D0%B8%D1%82%D0%B2%D0%BA%D0%B0%D0%BC%D0%BF%D0%B0%D0%BD%D0%B8%D1%8F%D1%85%D1%81%D0%BE%D0%BF%D0%BB%D0%B0%D1%82%D0%BE%D0%B9%D0%B7%D0%B0%D0%BA%D0%BB%D0%B8%D0%BA%D0%B8%D0%A1%D0%A0%D0%A1) — максимальных сумм, которые кампании могут потратить на продвижение в течение суток.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 5 запросов | 12 сек | 5 запросов |
| Сервисный | 1 мин | 5 запросов | 12 сек | 5 запросов |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `advertIds` | query | string | да | ID кампаний, максимум 100. Укажите значения через запятую |

## Ответы

**200** — Успешно

- `adverts` — array[object] **обязательный**
  - `advertId` — integer<int64> **обязательный**. ID кампании
  - `enabled` — boolean **обязательный**. - `true` — дневной лимит включен - `false` — дневной лимит отключен
  - `dailyLimit` — integer<int64> **обязательный**. Размер дневного лимита в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `spentToday` — integer<int64> **обязательный**. Потрачено сегодня в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `currency` — string<ISO 4217> **обязательный**. Код валюты
  - `carryOverEnabled` — boolean **обязательный**. Перенос остатка дневного лимита на следующий день. Если за 24 часа лимит потратится не полностью, добавим остаток суммы к лимиту следующего дня. Расходы на продвижение не увеличатся. - `true` — перенос остатка включен - `false` — перенос остатка отключен
  - `valid` — boolean **обязательный**. Хватает ли текущего размера лимита на установку ставок кампании: - `true` — да - `false` — нет, рекомендуем повысить лимит, иначе бюджет кампании может расходоваться неравномерно
  - `requiredLimit` — integer<int64> **обязательный**. Рекомендуемый минимальный размер дневного лимита при текущих ставках кампании. Указывается в разменных единицах — 0,01 от базовой валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).

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
