---
title: Бюджет кампании
api: wb-promotion
method: GET
path: /adv/v1/budget
operation_id: getV1Budget
tags:
  - finances
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: c384089f38b148ee
---

# Бюджет кампании

`GET /adv/v1/budget`

Описание метода

Метод возвращает информацию о бюджете [кампании](./promotion#tag/campaigns/operation/getV2Adverts) — максимальной сумме затрат на кампанию. Бюджет кампании можно [пополнить](./promotion#tag/finances/operation/postV1BudgetDeposit).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 4 запроса | 250 мс | 4 запроса |
| Сервисный | 1 сек | 4 запроса | 250 мс | 4 запроса |
| Базовый с секретом | 1 сек | 4 запроса | 250 мс | 4 запроса |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | query | integer | да | ID кампании |

## Ответы

**200** — Успешно

- `cash` — integer. Поле не используется. Значение всегда 0.
- `currency` — string<ISO 4217>. Валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)
- `netting` — integer. Поле не используется. Значение всегда 0.
- `total` — integer. Бюджет кампании в базовых единицах валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances)

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
