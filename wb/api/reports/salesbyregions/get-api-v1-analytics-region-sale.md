---
title: Получить отчёт
api: wb-reports
method: GET
path: /api/v1/analytics/region-sale
operation_id: getV1AnalyticsRegionSale
tags:
  - salesByRegions
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 7094a349d3574921
---

# Получить отчёт

`GET /api/v1/analytics/region-sale`

Описание метода

Метод возвращает отчёт с [данными продаж, сгруппированных по регионам стран](https://seller.wildberries.ru/analytics-reports/region-sale).

Можно получить отчёт максимум за 31 день.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Сервисный | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Базовый с секретом | 10 сек | 1 запрос | 10 сек | 5 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string | да | Начало отчётного периода, `ГГГГ-ММ-ДД` |
| `dateTo` | query | string | да | Конец отчётного периода, `ГГГГ-ММ-ДД` |

## Ответы

**200** — Успешно

- `report` — array[object]
  - `cityName` — string. Населённый пункт
  - `countryName` — string. Страна
  - `foName` — string. Федеральный округ
  - `nmID` — integer. Артикул WB
  - `regionName` — string. Регион
  - `sa` — string. Артикул продавца
  - `saleInvoiceCostPrice` — number<float>. К перечислению за товар, ₽
  - `saleInvoiceCostPricePerc` — number<float>. Доля, %
  - `saleItemInvoiceQty` — integer. Выкупили, шт.

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
