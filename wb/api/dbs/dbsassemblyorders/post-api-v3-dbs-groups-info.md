---
title: Получить информацию о платной доставке
api: wb-dbs
method: POST
path: /api/v3/dbs/groups/info
operation_id: postV3DbsGroupsInfo
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/dbs"
deprecated: false
content_sha: 5566748e7eadc6e6
---

# Получить информацию о платной доставке

`POST /api/v3/dbs/groups/info`

Описание метода

Метод возвращает информацию о платной доставке сборочных заданий, которые поступили на один склад (`warehouseId`) в рамках одной транзакции покупателя (`orderUid`).

Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `groups` — array[string]. Список значений `groupId`. Можно получить из [новых](./orders-dbs#tag/dbsAssemblyOrders/operation/getV3DbsOrdersNew) и [завершенных](./orders-dbs#tag/dbsAssemblyOrders/operation/getV3DbsOrders) сборочных заданий

## Ответы

**200** — Успешно

- `groupID` — string<UUID>. ID группы сборочных заданий
- `deliveryCost` — integer. Стоимость платной доставки в валюте продажи, умноженная на 100
- `convertedDeliveryCost` — integer. Стоимость платной доставки в валюте страны продавца, умноженная на 100. Предоставляется в информационных целях.
- `currencyCode` — integer<ISO 4217>. Код валюты продажи
- `convertedCurrencyCode` — integer. Код валюты страны продавца

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

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

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
