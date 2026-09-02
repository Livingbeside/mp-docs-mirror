---
title: Список отчётов об издержках на приём платежей
api: wb-documents-and-accounting
method: POST
path: /api/finance/v1/acquiring/list
operation_id: postV1AcquiringList
tags:
  - financialReports
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
deprecated: false
content_sha: 84321dce2ff4f944
---

# Список отчётов об издержках на приём платежей

`POST /api/finance/v1/acquiring/list`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод возвращает список отчётов об издержках на приём платежей по формату [таблицы отчётов](https://seller.wildberries.ru/suppliers-mutual-settlements/reports-implementations/acquiring-reports).

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `dateFrom` — string **обязательный**. Начальная дата отчёта. Можно передать дату или дату со временем. Время можно указывать с точностью до секунд или миллисекунд. Дата передаётся в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339), время — в часовом поясе Москва `UTC+3`. Примеры: - `2025-06-20` - `2025-06-20T23:59:59` - `2025-06-20T00:00:00.12345` - `2025-06-20T00:00:00`
- `dateTo` — string **обязательный**. Конечная дата отчёта. Дата в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339). Можно передать дату или дату со временем. Время можно указывать с точностью до секунд или миллисекунд. Время передаётся в часовом поясе Москва `UTC+3`. Примеры: - `2025-06-20` - `2025-06-20T23:59:59` - `2025-06-20T00:00:00.12345` - `2025-06-20T00:00:00`
- `limit` — integer. Количество отчётов в ответе По умолчанию: `1000`.
- `offset` — integer. Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента По умолчанию: `0`.

## Ответы

**200** — Успешно

- `reportId` — integer<int64> **обязательный**. ID отчёта
- `sellerFinanceName` — string **обязательный**. Наименование продавца
- `dateFrom` — string<date> **обязательный**. Дата начала отчётного периода
- `dateTo` — string<date> **обязательный**. Дата конца отчётного периода
- `createDate` — string<date> **обязательный**. Дата формирования отчёта
- `currency` — string **обязательный**. Валюта отчёта
- `acquiringFeeSum` — string **обязательный**. Сумма издержек по эквайрингу
- `acquiringFeeVatSum` — string **обязательный**. В том числе НДС

**204** — Нет данных

**400** — Неправильный запрос

- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
