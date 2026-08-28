---
title: Упаковка поставки{{ /api/v1/supplies/{ID}/package }}
api: wb-orders-fbw
method: GET
path: /api/v1/supplies/{ID}/package
operation_id: getV1SuppliesIdPackage
tags:
  - suppliesInformation
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: f6f20c495dc7bb82
---

# Упаковка поставки{{ /api/v1/supplies/{ID}/package }}

`GET /api/v1/supplies/{ID}/package`

Описание метода

Метод возвращает информацию об упаковке поставки.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 30 запросов | 2 сек | 10 запросов |
| Сервисный | 1 мин | 30 запросов | 2 сек | 10 запросов |
| Базовый с секретом | 1 мин | 30 запросов | 2 сек | 10 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `ID` | path | integer | да | ID поставки |

## Ответы

**200** — Успешно

- `barcodes` — array[object]. Список упакованных товаров
  - `barcode` — string. Баркод
  - `quantity` — integer. Количество, шт
- `packageCode` — string. Штрих-код упаковки
- `quantity` — integer. Суммарное количество товара в упаковке, шт

**400** — Неправильный запрос

- `detail` — string. Описание ошибки
- `origin` — string. Сервис, вернувший ошибку
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки

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
