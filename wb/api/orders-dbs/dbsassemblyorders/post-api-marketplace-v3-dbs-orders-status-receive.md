---
title: Сообщить о получении заказов{{ /api/marketplace/v3/dbs/orders/status/receive }}
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/status/receive
operation_id: postV3DbsOrdersStatusReceive
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 26a71bfa45c53b1f
---

# Сообщить о получении заказов{{ /api/marketplace/v3/dbs/orders/status/receive }}

`POST /api/marketplace/v3/dbs/orders/status/receive`

Описание метода Метод переводит [сборочные задания](./orders-dbs#tag/dbsAssemblyOrders) из [статуса](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusInfo) `deliver` в статус `receive` — получено покупателем. Лимит запросов на один аккаунт продавца: | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 сек | 1 запрос | 1 сек | 10 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `code` — string. Код подтверждения. Отображается у покупателя на сайте и в приложении Wildberries
  - `orderId` — integer. ID сборочного задания

## Ответы

**200** — Успешно

- `requestId` — string. Уникальный ID запроса
- `results` — array[object]
  - `errors` — array[object]. Детали ошибки
    - `code` — integer. Код ошибки
    - `detail` — string. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `SGTINIsNotFilled` — обязательный [код маркировки](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaSgtin) не указан
  - `isError` — boolean. Есть ли ошибки
  - `orderId` — integer. ID сборочного задания с успешно обновлёнными данными

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
