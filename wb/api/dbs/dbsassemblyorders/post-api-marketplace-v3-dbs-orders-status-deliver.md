---
title: Перевести сборочные задания в доставку
api: wb-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/status/deliver
operation_id: postV3DbsOrdersStatusDeliver
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/dbs"
deprecated: false
content_sha: 140b8dcdb6b4b55f
---

# Перевести сборочные задания в доставку

`POST /api/marketplace/v3/dbs/orders/status/deliver`

Описание метода

Метод переводит [сборочные задания](./orders-dbs#tag/dbsAssemblyOrders) из [статуса](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusInfo) `confirm` в статус `deliver` — в доставке.

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

- `requestId` — string. Уникальный ID запроса
- `results` — array[object]
  - `errors` — array[object]. Детали ошибки
    - `code` — integer. Код ошибки: - `404` - `409`
    - `detail` — string. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI - `MetaValidationFail` — ошибки валидации идентификатора маркировки
    - `metaDetails` — array[object]. Детали ошибки валидации идентификаторов маркировки
      - `key` — string. Идентификатор маркировки
      - `value` — string. Значение идентификатора маркировки
      - `decision` — string. Статус проверки: - `sgtin` - `sgtinInvalidFormat` — Неверный формат маркировки - `sgtinNotFound` — Маркировка не найдена в [Честном знаке](https://chestnyznak.ru) - `sgtinEmitted` — Маркировка эмитирована - `sgtinApplied` — Не пройдена процедура Ввод в оборот - `sgtinWrittenOff` — Списан - `sgtinRetired` — Выбыл - `sgtinWithdrawn` — Выбыл - `sgtinDisaggregation` — Расформирован - `sgtinDisaggregated` — Расформирован - `sgtinAppliedNotPaid` — Не оплачен - `pending` — Маркировка на проверке
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
