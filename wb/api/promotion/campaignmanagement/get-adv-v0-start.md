---
title: Запуск кампании
api: wb-promotion
method: GET
path: /adv/v0/start
operation_id: getV0Start
tags:
  - campaignManagement
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: 8cb52436d8716628
---

# Запуск кампании

`GET /adv/v0/start`

Описание метода

Метод запускает [кампании](./promotion#tag/campaigns/operation/getV2Adverts) в статусах `4` — готово к запуску — или `11` — пауза.
Чтобы запустить кампанию, проверьте ее бюджет. Если бюджета недостаточно, [пополните его](./promotion#tag/finances/operation/postV1BudgetDeposit).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Сервисный | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый с секретом | 1 сек | 5 запросов | 200 мс | 5 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | query | integer | да | ID кампании |

## Ответы

**200** — Успешно

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

**422** — Статус не изменен

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
