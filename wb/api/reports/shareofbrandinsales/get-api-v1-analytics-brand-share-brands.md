---
title: Бренды продавца
api: wb-reports
method: GET
path: /api/v1/analytics/brand-share/brands
operation_id: getV1AnalyticsBrandShareBrands
tags:
  - shareOfBrandInSales
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 4f67c03f0447421a
---

# Бренды продавца

`GET /api/v1/analytics/brand-share/brands`

Описание метода

Метод возвращает список брендов продавца для отчёта о [доле бренда в продажах](https://seller.wildberries.ru/analytics-reports/brand-share). 

Можно получить только бренды, которые:
- Продавались за последние 90 дней
- Есть в наличии, вне зависимости от склада хранения

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Сервисный | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Ответы

**200** — Успешно

- `data` — array[string]. Список брендов

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
