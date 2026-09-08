---
title: Получить отчёт
api: wb-reports
method: GET
path: /api/v1/analytics/brand-share
operation_id: getV1AnalyticsBrandShare
tags:
  - shareOfBrandInSales
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: c5539ee593bbd6eb
---

# Получить отчёт

`GET /api/v1/analytics/brand-share`

Описание метода

Метод возвращает отчёт о [доле бренда продавца в продажах](https://seller.wildberries.ru/analytics-reports/brand-share). 

Можно получить отчёт максимум за 365 дней. Данные доступны с 1 ноября 2022.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 5 сек | 1 запрос | 5 сек | 20 запросов |
| Сервисный | 5 сек | 1 запрос | 5 сек | 20 запросов |
| Базовый с секретом | 5 сек | 1 запрос | 5 сек | 20 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `parentId` | query | integer | да | ID родительской категории |
| `brand` | query | string | да | Бренд |
| `dateFrom` | query | string | да | Начало отчётного периода, `ГГГГ-ММ-ДД` |
| `dateTo` | query | string | да | Конец отчётного периода, `ГГГГ-ММ-ДД` |

## Ответы

**200** — Успешно

- `report` — array[object]. Отчёт
  - `applyDate` — string<ГГГГ-ММ-ДД>. Дата
  - `brandRating` — integer. Рейтинг бренда в родительской категории
  - `pricePercent` — number<float>. Доля от продаж в родительской категории — цена, %
  - `qtyPercent` — number<float>. Доля от продаж в родительской категории — количество, %

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
