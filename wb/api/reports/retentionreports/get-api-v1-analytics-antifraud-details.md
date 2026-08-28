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
content_sha: 8f71fc8f32f14c1b
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
  - `nmID` — integer. Артикул WB
  - `sum` — integer. Сумма заказа
  - `currency` — string. Валюта заказа
  - `dateFrom` — string. Начало отчётного периода
  - `dateTo` — string. Конец отчётного периода

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
