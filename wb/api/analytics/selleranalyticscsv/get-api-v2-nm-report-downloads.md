---
title: Получить список отчётов
api: wb-analytics
method: GET
path: /api/v2/nm-report/downloads
operation_id: getV2NmReportDownloads
tags:
  - sellerAnalyticsCsv
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: 0bb3177d9cbd6282
---

# Получить список отчётов

`GET /api/v2/nm-report/downloads`

Описание метода

Метод возвращает список отчётов с расширенной аналитикой продавца. Ответ содержит ID [созданных отчётов](./analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads) и статусы генерации.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `filter[downloadIds]` | query | array[string<uuid>] | нет | ID отчёта |

## Ответы

**200** — Успешно

- `data` — array[object] **обязательный**
  - `createdAt` — string **обязательный**. Дата и время завершения генерации
  - `endDate` — string<date> **обязательный**. Конец периода
  - `id` — string<uuid> **обязательный**. ID отчёта
  - `name` — string **обязательный**. Название отчёта
  - `size` — integer **обязательный**. Размер отчёта, Б
  - `startDate` — string<date> **обязательный**. Начало периода
  - `status` — string **обязательный**. Статус отчёта: * `WAITING` — в очереди на обработку * `PROCESSING` — генерируется * `SUCCESS —` готов * `RETRY` — ожидает повторной обработки * `FAILED` — не получилось сгенерировать, сгенерируйте повторно

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

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
