---
title: Получить отчёт{{ /api/v1/analytics/banned-products/blocked }}
api: wb-reports
method: GET
path: /api/v1/analytics/banned-products/blocked
operation_id: getV1AnalyticsBannedProducsBlocked
tags:
  - blockedItems
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: ca0b07eb6c4815fa
---

# Получить отчёт{{ /api/v1/analytics/banned-products/blocked }}

`GET /api/v1/analytics/banned-products/blocked`

Описание метода Метод возвращает список [заблокированных карточек товаров продавца](https://seller.wildberries.ru/analytics-reports/banned-products) с причинами блокировки. Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 10 сек | 1 запрос | 10 сек | 6 запросов | | Сервисный | 10 сек | 1 запрос | 10 сек | 6 запросов | | Базовый с секретом | 10 сек | 1 запрос | 10 сек | 6 запросов | | Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

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
  - `title` — string. Наименование товара
  - `vendorCode` — string. Артикул продавца
  - `reason` — string. Причина блокировки

**400** — Неправильный запрос

- `title` — string. Заголовок ошибки
- `status` — number. HTTP статус-код
- `detail` — string. Детали ошибки
- `requestId` — string. Уникальный ID запроса
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
