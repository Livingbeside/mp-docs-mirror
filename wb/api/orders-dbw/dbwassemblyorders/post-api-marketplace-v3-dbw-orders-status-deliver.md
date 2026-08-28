---
title: Перевести сборочные задания в доставку
api: wb-orders-dbw
method: POST
path: /api/marketplace/v3/dbw/orders/status/deliver
operation_id: postV3DbwOrdersStatusDeliver
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: dec447eabcbc7aef
---

# Перевести сборочные задания в доставку

`POST /api/marketplace/v3/dbw/orders/status/deliver`

Описание метода

Метод переводит [сборочные задания](./orders-dbw#tag/dbwAssemblyOrders/operation/getV3DbwOrders) из [статуса](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatus) `confirm` в статус `complete` — в доставке.

Проверяйте ответ метода. Сборочные задания, переведённые в доставку, вернутся с признаком `"isError":false`. Для остальных сборочных заданий смотрите причину ошибки в массиве `errors`

Лимит запросов на один аккаунт продавца для следующих методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 методы сборочных заданий

 

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — string. Уникальный ID запроса, содержащего ошибки.
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки: - `404` - `409`
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI - `MetaValidationFail` — ошибки валидации идентификаторов маркировки
    - `metaDetails` — array[object]. Детали ошибки валидации идентификаторов маркировки
      - `decision` — string **обязательный**. Статус проверки: - `sgtin` - `sgtinInvalidFormat` — Неверный формат маркировки - `sgtinNotFound` — Маркировка не найдена в [Честном знаке](https://chestnyznak.ru) - `sgtinEmitted` — Маркировка эмитирована - `sgtinApplied` — Не пройдена процедура Ввод в оборот - `sgtinWrittenOff` — Списан - `sgtinRetired` — Выбыл - `sgtinWithdrawn` — Выбыл - `sgtinDisaggregation` — Расформирован - `sgtinDisaggregated` — Расформирован - `sgtinAppliedNotPaid` — Не оплачен - `pending` — Маркировка на проверке
      - `key` — string **обязательный**. Идентификатор маркировки
      - `value` — string. Значение идентификатора маркировки
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания с успешно обновлёнными данными

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

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

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
