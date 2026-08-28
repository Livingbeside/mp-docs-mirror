---
title: Самовыкупы
api: wb-reports
method: GET
path: /api/v1/analytics/antifraud-details
operation_id: getV1AnalyticsAntifraudDetails
tags:
  - retentionReports
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 60952ec9f8cc46c0
---

# Самовыкупы

`GET /api/v1/analytics/antifraud-details`

Описание метода

Метод возвращает отчёт об удержаниях за самовыкупы. Отчёт формируется каждую неделю по средам, до 7:00 по московскому времени, и содержит данные за одну неделю.

Удержание за самовыкуп — 30% от стоимости товаров.
Минимальная сумма всех удержаний — 100 000 ₽, если за неделю в ПВЗ привезли ваших товаров больше, чем на сумму 100 000 ₽.

Данные доступны с августа 2023.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 мин | 1 запрос | 10 мин | 10 запросов |
| Сервисный | 10 мин | 1 запрос | 10 мин | 10 запросов |
| Базовый с секретом | 10 мин | 1 запрос | 10 мин | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `date` | query | string | нет | Дата, которая входит в отчётный период, `ГГГГ-ММ-ДД`. Чтобы получить данные за всё время с августа 2023, не указывайте этот параметр |

## Ответы

**200** — Успешно

- `details` — array[object]
  - `currency` — string. Валюта заказа
  - `dateFrom` — string. Начало отчётного периода
  - `dateTo` — string. Конец отчётного периода
  - `nmID` — integer. Артикул WB
  - `sum` — integer. Сумма заказа

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
