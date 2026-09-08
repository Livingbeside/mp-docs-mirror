---
title: Пополнение бюджета кампании
api: wb-promotion
method: POST
path: /adv/v1/budget/deposit
operation_id: postV1BudgetDeposit
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 22a76814d977d545
---

# Пополнение бюджета кампании

`POST /adv/v1/budget/deposit`

Описание метода

Метод пополняет [бюджет](./promotion#tag/finances/operation/getV1Budget) кампании. 

Чтобы запустить кампанию после пополнения бюджета, используйте метод [Запуск кампании](./promotion#tag/campaignManagement/operation/getV0Start).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Сервисный | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый с секретом | 1 сек | 1 запрос | 1 сек | 5 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | query | integer | да | ID кампании |

## Запрос

**Тело запроса** (`application/json`):

- `sum` — integer. Общая сумма пополнения бюджета в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `cashback_sum` — integer. Сумма пополнения бюджета промо-бонусами. Пополнить можно только определённый процент от общей суммы, указанный в поле `percent` ответа метода получения [баланса](./promotion#tag/finances/operation/getV1Balance). Оставшаяся часть общей суммы спишется с указанного источника пополнения. Пополнить можно только определённый процент от общей суммы, указанный в поле `percent` ответа метода получения [баланса](./promotion#tag/finances/operation/getV1Balance). Оставшаяся часть общей суммы спишется с указанного источника пополнения. Списать промо-бонусы можно только для источников пополнения: - `0` — счёт - `1` — баланс
- `cashback_percent` — integer. Процент от суммы пополнения, который можно пополнить промо-бонусами. Нужно указать значение поля percent из ответа метода получения [баланса](./promotion#tag/finances/operation/getV1Balance) Если вы указали `cashback_sum`, параметр `cashback_percent` становится обязательным
- `type` — integer. Тип источника пополнения: - `0` — Счёт - `1` — Баланс - `3` — Бонусы
- `return` — boolean. Флаг возврата ответа (`true` — в ответе вернется обновлённый размер бюджета кампании, `false` или не указать параметр вообще — не вернётся.)

## Ответы

**200** — Успешно

- `total` — integer. Размер обновлённого бюджета
- `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

**400** — Неправильный запрос

- `error` — string

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
