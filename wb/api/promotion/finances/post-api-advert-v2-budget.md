---
title: Остатки бюджетов кампаний
api: wb-promotion
method: POST
path: /api/advert/v2/budget
operation_id: postV2Budget
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 70dc30c3c5e19f29
---

# Остатки бюджетов кампаний

`POST /api/advert/v2/budget`

Описание метода

Метод возвращает информацию об остатках бюджетов [кампаний](./promotion#tag/campaigns/operation/getV2Adverts).
Для кампаний в [статусах](./promotion#tag/campaigns/operation/getV1PromotionCount):
 - `4` — готова к запуску
 - `9` — активна
 - `11` — на паузе

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 20 запросов | 3 сек | 4 запроса |
| Сервисный | 1 мин | 20 запросов | 3 сек | 4 запроса |
| Базовый с секретом | 1 мин | 20 запросов | 3 сек | 4 запроса |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `advertIds` — array[integer] **обязательный**. Список ID кампаний

## Ответы

**200** — Успешно

- `adverts` — array[object] **обязательный**. Данные по кампаниям
  - `advertId` — integer **обязательный**. ID кампании
  - `currency` — string<ISO 4217> **обязательный**. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `total` — integer **обязательный**. Бюджет кампании в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

**400** — Неправильный запрос

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
