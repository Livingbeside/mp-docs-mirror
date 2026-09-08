---
title: Получить отчёт{{ /api/v1/acceptance_report/tasks/{task_id}/download }}
api: wb-reports
method: GET
path: /api/v1/acceptance_report/tasks/{task_id}/download
operation_id: getV1AcceptanceReportTasksTaskIdDownload
tags:
  - acceptanceExpenses
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 614ae47f035e6743
---

# Получить отчёт{{ /api/v1/acceptance_report/tasks/{task_id}/download }}

`GET /api/v1/acceptance_report/tasks/{task_id}/download`

Описание метода

Метод возвращает отчёт об [операциях при приёмке](https://seller.wildberries.ru/analytics-reports/acceptance-report) по ID [задания на генерацию](./reports#tag/acceptanceExpenses/operation/getV1AcceptanceReport).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `task_id` | path | string | да | ID задания на генерацию |

## Ответы

**200** — Успешно

- `count` — integer. Количество товаров, шт.
- `giCreateDate` — string<date>. Дата создания поставки
- `incomeId` — integer. Номер поставки
- `nmID` — integer. Артикул WB
- `shkCreateDate` — string<date>. Дата приёмки
- `subjectName` — string. Предмет
- `total` — number. Суммарная стоимость приёмки, ₽ с копейками

**204** — Нет данных

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
