---
title: Получить список отчётов{{ /api/v2/nm-report/downloads }}
api: wb-analytics
method: GET
path: /api/v2/nm-report/downloads
operation_id: getV2NmReportDownloads
tags:
  - sellerAnalyticsCsv
spec_version: analytics
source: "https://dev.wildberries.ru/docs/openapi/analytics"
deprecated: false
content_sha: f988bb52ca76af15
---

# Получить список отчётов{{ /api/v2/nm-report/downloads }}

`GET /api/v2/nm-report/downloads`

Описание метода Метод возвращает список отчётов с расширенной аналитикой продавца. Ответ содержит ID [созданных отчётов](./analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads) и статусы генерации. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Сервисный | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый с секретом | 1 мин | 3 запроса | 20 сек | 3 запроса | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `filter[downloadIds]` | query | array[string<uuid>] | нет | ID отчёта |

## Ответы

**200** — Успешно

- `data` — array[object] **обязательный**
  - `id` — string<uuid> **обязательный**. ID отчёта
  - `createdAt` — string **обязательный**. Дата и время завершения генерации
  - `status` — string **обязательный**. Статус отчёта: * `WAITING` — в очереди на обработку * `PROCESSING` — генерируется * `SUCCESS —` готов * `RETRY` — ожидает повторной обработки * `FAILED` — не получилось сгенерировать, сгенерируйте повторно
  - `name` — string **обязательный**. Название отчёта
  - `size` — integer **обязательный**. Размер отчёта, Б
  - `startDate` — string<date> **обязательный**. Начало периода
  - `endDate` — string<date> **обязательный**. Конец периода

**400** — Неправильный запрос

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. Уникальный ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

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
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
