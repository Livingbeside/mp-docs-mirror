---
title: Маркировка товара
api: wb-reports
method: GET
path: /api/v1/analytics/goods-labeling
operation_id: getV1AnalyticsGoodsLabeling
tags:
  - retentionReports
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 27b3e645e3b4a4e3
---

# Маркировка товара

`GET /api/v1/analytics/goods-labeling`

Описание метода

Метод возвращает отчёт о штрафах за отсутствие обязательной маркировки товаров.

В отчёте представлены фотографии товаров, на которых маркировка отсутствует либо не считывается.

Можно получить данные максимум за 31 день. Данные доступны с марта 2024.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Сервисный | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string<date> | да | Начало отчётного периода, `ГГГГ-ММ-ДД` |
| `dateTo` | query | string<date> | да | Конец отчётного периода, `ГГГГ-ММ-ДД` |

## Ответы

**200** — Успешно

- `report` — array[object]
  - `amount` — number. Сумма штрафа, руб
  - `date` — string<date-time>. Дата
  - `incomeId` — integer. Номер поставки
  - `nmID` — integer. Артикул WB
  - `photoUrls` — array[string]. URL фото товара
  - `shkID` — integer. Штрихкод товара в WB
  - `sku` — string. Баркод из карточки товара

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
