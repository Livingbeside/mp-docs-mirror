---
title: Получить отчёт
api: wb-reports
method: POST
path: /api/v1/analytics/excise-report
operation_id: postV1AnalyticsExciseReport
tags:
  - reportOnItemsWithMandatoryLabeling
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: aca48174b1fc3930
---

# Получить отчёт

`POST /api/v1/analytics/excise-report`

Описание метода

Метод возвращает отчёт с [операциями по товарам с обязательной маркировкой](https://seller.wildberries.ru/analytics-reports/excise-report).

Данный отчёт можно сохранить в [формате таблиц](/knowledge-base/articles/019d49a4-650c-7b04-9596-ba441936f9d3).

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 5 ч | 10 запросов | 30 мин | 10 запросов |
| Сервисный | 5 ч | 10 запросов | 30 мин | 10 запросов |
| Базовый с секретом | 5 ч | 10 запросов | 30 мин | 10 запросов |
| Базовый | 24 ч | 2 запроса | 12 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `dateFrom` | query | string | да | Начало отчётного периода, `ГГГГ-ММ-ДД` |
| `dateTo` | query | string | да | Конец отчётного периода, `ГГГГ-ММ-ДД` |

## Запрос

**Тело запроса** (`application/json`):

- `countries` — array[string (AM, BY, KG, KZ, RU, UZ)]. Код стран по стандарту ISO 3166-2. Чтобы получить данные по всем странам, оставьте параметр пустым

## Ответы

**200** — Успешно

- `response` — object
  - `data` — array[object]
    - `name` — string. Страна покупателя
    - `price` — number. Цена товара, с НДС
    - `currency_name_short` — string. Валюта
    - `excise_short` — string. Код маркировки
    - `barcode` — string. Баркод
    - `nm_id` — integer. Артикул WB
    - `operation_type_id` — integer. Тип операции, если есть: * `1` — вывод из оборота * `2` — возврат в оборот
    - `fiscal_doc_number` — integer. Номер фискального документа (чека полного расчёта), если есть
    - `fiscal_dt` — string. Дата фискализации (дата в чеке), если есть, `ГГГГ-ММ-ДД`
    - `fiscal_drive_number` — string. Номер фискального накопителя, если есть
    - `rid` — integer. `Rid`
    - `srid` — string. `Srid`

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
