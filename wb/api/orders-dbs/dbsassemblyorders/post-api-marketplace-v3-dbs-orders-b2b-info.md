---
title: Информация о покупателе B2B{{ /api/marketplace/v3/dbs/orders/b2b/info }}
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/b2b/info
operation_id: postV3DbsOrdersB2bInfo
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 5a6eb02db371f08c
---

# Информация о покупателе B2B{{ /api/marketplace/v3/dbs/orders/b2b/info }}

`POST /api/marketplace/v3/dbs/orders/b2b/info`

Описание метода Метод возвращает данные B2B-покупателей по ID сборочных заданий: - ИНН - КПП - Наименование организации Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — string **обязательный**. Уникальный ID запроса
- `results` — array[object]
  - `data` — object. Данные покупателя B2B
    - `inn` — string. Индивидуальный номер налогоплательщика (ИНН)
    - `kpp` — string. Код причины постановки на учёт (КПП)
    - `orgName` — string. Наименование организации
  - `errors` — array[object]. Детали ошибки
    - `code` — integer. Код ошибки
    - `detail` — string. Описание ошибки
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
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

- `detail` — object. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
