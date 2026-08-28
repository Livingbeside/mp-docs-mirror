---
title: Проверить статус{{ /api/v1/acceptance_report/tasks/{task_id}/status }}
api: wb-reports
method: GET
path: /api/v1/acceptance_report/tasks/{task_id}/status
operation_id: getV1AcceptanceReportTasksTaskIdStatus
tags:
  - acceptanceExpenses
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: eeef865083cce63f
---

# Проверить статус{{ /api/v1/acceptance_report/tasks/{task_id}/status }}

`GET /api/v1/acceptance_report/tasks/{task_id}/status`

Описание метода

Метод возвращает статус [задания на генерацию](./reports#tag/acceptanceExpenses/operation/getV1AcceptanceReport) отчёта об [операциях при приёмке](./reports#tag/acceptanceExpenses/operation/getV1AcceptanceReportTasksTaskIdDownload).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 5 сек | 1 запрос | 5 сек | 1 запрос |
| Сервисный | 5 сек | 1 запрос | 5 сек | 1 запрос |
| Базовый с секретом | 5 сек | 1 запрос | 5 сек | 1 запрос |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

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

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**404** — Не найдено

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
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
