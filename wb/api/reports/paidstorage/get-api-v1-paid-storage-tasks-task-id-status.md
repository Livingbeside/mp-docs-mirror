---
title: Проверить статус{{ /api/v1/paid_storage/tasks/{task_id}/status }}
api: wb-reports
method: GET
path: /api/v1/paid_storage/tasks/{task_id}/status
operation_id: getV1PaidStorageTasksTaskIdStatus
tags:
  - paidStorage
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 7fc7072b69b1c554
---

# Проверить статус{{ /api/v1/paid_storage/tasks/{task_id}/status }}

`GET /api/v1/paid_storage/tasks/{task_id}/status`

Описание метода Метод возвращает статус [задания на генерацию](./reports#tag/paidStorage/operation/getV1PaidStorage) отчёта о [платном хранении](./reports#tag/paidStorage/operation/getV1PaidStorageTasksTaskIdDownload). Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 5 сек | 1 запрос | 5 сек | 5 запросов | | Сервисный | 5 сек | 1 запрос | 5 сек | 5 запросов | | Базовый с секретом | 5 сек | 1 запрос | 5 сек | 5 запросов | | Базовый | 1 ч | 2 запроса | 30 мин | 2 запроса |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `task_id` | path | string | да | ID задания на генерацию |

## Ответы

**200** — Успешно

- `data` — object
  - `id` — string. ID задания
  - `status` — string. Статус задания: * `new` — новое * `processing` — обрабатывается * `done` — отчёт готов * `purged` — отчёт удалён * `canceled` — отклонено

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

**404** — Не найдено

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
