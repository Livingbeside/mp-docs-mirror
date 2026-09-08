---
title: Добавить данные СПОТ в поставку{{ /api/marketplace/v3/fbs/supplies/{supplyId}/spot }}
api: wb-orders-fbs
method: PUT
path: /api/marketplace/v3/fbs/supplies/{supplyId}/spot
operation_id: putV3FbsSuppliesSupplyIdSpot
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 434ba02ff007e8f0
---

# Добавить данные СПОТ в поставку{{ /api/marketplace/v3/fbs/supplies/{supplyId}/spot }}

`PUT /api/marketplace/v3/fbs/supplies/{supplyId}/spot`

Описание метода

Метод добавляет данные СПОТ в поставку.

СПОТ можно добавить только в [поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/get) с признаком `"spotAvailable":true`.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |

## Запрос

**Тело запроса** (`application/json`):

- `carrierName` — string **обязательный**. Наименование перевозчика
- `carrierTaxNumber` — string **обязательный**. ИНН перевозчика
- `carrierCountryCode` — string **обязательный**. Код страны перевозчика по [ОКСМ](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsDictionariesCountriesOksm)
- `vehicleRegistrationNumber` — string **обязательный**. Регистрационный номер транспортного средства
- `trailerRegistrationNumber` — string. Регистрационный номер прицепа

## Ответы

**204** — Добавлено

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**404** — Не найдено

- `detail` — string **обязательный**. Детали ошибки
- `title` — string **обязательный**. Заголовок ошибки

**409** — Ошибка добавления данных СПОТ

- `detail` — string **обязательный**. Детали ошибки
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
