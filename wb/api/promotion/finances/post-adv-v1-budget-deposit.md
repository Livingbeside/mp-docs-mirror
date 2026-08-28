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
content_sha: 1996a79f7b38adc8
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

- `cashback_percent` — integer. Процент от суммы пополнения, который можно пополнить промо-бонусами. Нужно указать значение поля percent из ответа метода получения [баланса](./promotion#tag/finances/operation/getV1Balance) Если вы указали `cashback_sum`, параметр `cashback_percent` становится обязательным
- `cashback_sum` — integer. Сумма пополнения бюджета промо-бонусами. Пополнить можно только определённый процент от общей суммы, указанный в поле `percent` ответа метода получения [баланса](./promotion#tag/finances/operation/getV1Balance). Оставшаяся часть общей суммы спишется с указанного источника пополнения. Пополнить можно только определённый процент от общей суммы, указанный в поле `percent` ответа метода получения [баланса](./promotion#tag/finances/operation/getV1Balance). Оставшаяся часть общей суммы спишется с указанного источника пополнения. Списать промо-бонусы можно только для источников пополнения: - `0` — счёт - `1` — баланс
- `return` — boolean. Флаг возврата ответа (`true` — в ответе вернется обновлённый размер бюджета кампании, `false` или не указать параметр вообще — не вернётся.)
- `sum` — integer. Общая сумма пополнения бюджета в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `type` — integer. Тип источника пополнения: - `0` — Счёт - `1` — Баланс - `3` — Бонусы

## Ответы

**200** — Успешно

- `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `total` — integer. Размер обновлённого бюджета

**400** — Неправильный запрос

- `error` — string

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
