---
title: Баланс
api: wb-promotion
method: GET
path: /adv/v1/balance
operation_id: getV1Balance
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 41c585a809239bf9
---

# Баланс

`GET /adv/v1/balance`

Описание метода

Метод возвращает информацию о:
 - счёте кабинета Продвижения WB. Его пополняет продавец.
 - балансе — максимальной сумме для оплаты кампании по взаиморасчету: удержании средств из будущих продаж. Баланс пополнить нельзя, он рассчитывается автоматически на основе отчётов по продвижению.
 - бонусных начислениях WB.

Информацию о бюджете кампаний можно получить в [отдельном методе](./promotion#tag/finances/operation/getV1Budget).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Сервисный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый с секретом | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Ответы

**200** — Успешно

- `balance` — integer. Счёт в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `net` — integer. Баланс в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `bonus` — integer. Бонусы в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `cashbacks` — array[object]. Промо-бонусы
  - `sum` — integer. Промо-бонусы в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
  - `percent` — integer. Процент от суммы пополнения бюджета кампании, который можно оплатить промо-бонусами за один раз
  - `expiration_date` — string<ISO 8601>. Дата окончания действия промо-бонусов

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
