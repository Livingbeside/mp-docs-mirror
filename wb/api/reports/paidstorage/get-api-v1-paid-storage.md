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
content_sha: 94da2447fa805ce3
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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

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
