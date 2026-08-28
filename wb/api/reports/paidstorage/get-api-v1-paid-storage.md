---
title: Создать отчёт
api: wb-reports
method: GET
path: /api/v1/paid_storage
operation_id: getV1PaidStorage
tags:
  - paidStorage
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: f9f2867d3489f489
---

# Создать отчёт

`GET /api/v1/paid_storage`

Описание метода

Метод создаёт [задание на генерацию](./reports#tag/paidStorage/operation/getV1PaidStorageTasksTaskIdStatus) отчёта о [платном хранении](./reports#tag/paidStorage/operation/getV1PaidStorageTasksTaskIdDownload).

Можно получить отчёт максимум за 8 дней.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 5 запросов |
| Сервисный | 1 мин | 1 запрос | 1 мин | 5 запросов |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string | да | Начало отчётного периода в формате RFC3339. Можно передать дату или дату со временем. Примеры: * `2019-06-20` * `2019-06-20T23:59:59` * `2019-06-20T00:00:00.12345` * `2017-03-25T00:00:00` |
| `dateTo` | query | string | да | Конец отчётного периода в формате RFC3339. Можно передать дату или дату со временем. Примеры: * `2019-06-20` * `2019-06-20T23:59:59` * `2019-06-20T00:00:00.12345` * `2017-03-25T00:00:00` |

## Ответы

**200** — Успешно

- `data` — object
  - `taskId` — string. ID задания на генерацию

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
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
