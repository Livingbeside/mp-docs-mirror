---
title: Отменить сборочные задания
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/status/cancel
operation_id: postV3ClickCollectOrdersStatusCancel
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 9585d7cb201bb042
---

# Отменить сборочные задания

`POST /api/marketplace/v3/click-collect/orders/status/cancel`

Описание метода

Переводит [сборочные задания](./in-store-pickup#tag/inStorePickupAssemblyOrders) из [статусов](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusInfo) `new`, `confirm`, `prepare` в статус `cancel` — отменено продавцом.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 сек | 1 запрос | 1 сек | 10 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — ? **обязательный**. Уникальный ID запроса
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer. Код ошибки: - `404` - `409` - `400`
    - `detail` — string. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI - `OrderNotB2B` — операция доступна только для сборочных заданий с признаком B2B-продажи `"isB2b":true` - `InvalidOriginCountryCode` — некорректный код страны происхождения товара
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

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

**403** — Доступ запрещён

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
