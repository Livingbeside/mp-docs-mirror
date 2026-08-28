---
title: Бренды продавца{{ /api/v1/analytics/brand-share/brands }}
api: wb-reports
method: GET
path: /api/v1/analytics/brand-share/brands
operation_id: getV1AnalyticsBrandShareBrands
tags:
  - shareOfBrandInSales
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: c23c0c9d038028c0
---

# Бренды продавца{{ /api/v1/analytics/brand-share/brands }}

`GET /api/v1/analytics/brand-share/brands`

Описание метода Метод возвращает список брендов продавца для отчёта о [доле бренда в продажах](https://seller.wildberries.ru/analytics-reports/brand-share). Можно получить только бренды, которые: - Продавались за последние 90 дней - Есть в наличии, вне зависимости от склада хранения Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 1 запрос | 1 мин | 10 запросов | | Сервисный | 1 мин | 1 запрос | 1 мин | 10 запросов | | Базовый с секретом | 1 мин | 1 запрос | 1 мин | 10 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Ответы

**200** — Успешно

- `data` — array[string]. Список брендов

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
