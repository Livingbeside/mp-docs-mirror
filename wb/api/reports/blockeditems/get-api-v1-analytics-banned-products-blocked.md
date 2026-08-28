---
title: Получить отчёт
api: wb-reports
method: GET
path: /api/v1/analytics/banned-products/blocked
operation_id: getV1AnalyticsBannedProducsBlocked
tags:
  - blockedItems
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 073078056debedaa
---

# Получить отчёт

`GET /api/v1/analytics/banned-products/blocked`

Описание метода

Метод возвращает список [заблокированных карточек товаров продавца](https://seller.wildberries.ru/analytics-reports/banned-products) с причинами блокировки.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 1 запрос | 10 сек | 6 запросов |
| Сервисный | 10 сек | 1 запрос | 10 сек | 6 запросов |
| Базовый с секретом | 10 сек | 1 запрос | 10 сек | 6 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `sort` | query | string (brand, nmId, title, vendorCode, reason) | да | Сортировка - `brand` — по бренду - `nmId` — по артикулу WB - `title` — по наименованию товара - `vendorCode` — по артикулу продавца - `reason` — по причине блокировки |
| `order` | query | string (desc, asc) | да | Порядок выдачи - `desc` — от наибольшего числового значения к наименьшему, от последнего по алфавиту значения к первому - `asc` — от наименьшего числового значения к наибольшему, от первого по алфавиту значения к последнему |

## Ответы

**200** — Успешно

- `report` — array[object]. Отчёт
  - `brand` — string. Бренд
  - `nmId` — integer. Артикул WB
  - `reason` — string. Причина блокировки
  - `title` — string. Наименование товара
  - `vendorCode` — string. Артикул продавца

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
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
