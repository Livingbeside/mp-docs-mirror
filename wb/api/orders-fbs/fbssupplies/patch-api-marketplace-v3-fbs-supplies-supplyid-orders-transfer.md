---
title: Перевести сборочные задания из доставки на сборку{{ /api/marketplace/v3/fbs/supplies/{supplyId}/orders/transfer }}
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/fbs/supplies/{supplyId}/orders/transfer
operation_id: patchV3FbsSuppliesSupplyIdOrdersTransfer
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: d9c79d040f35d065
---

# Перевести сборочные задания из доставки на сборку{{ /api/marketplace/v3/fbs/supplies/{supplyId}/orders/transfer }}

`PATCH /api/marketplace/v3/fbs/supplies/{supplyId}/orders/transfer`

Описание метода

Метод переводит сборочные задания из статуса `complete` — в доставке в статус `confirm` — на сборке.

Используйте метод, чтобы переместить сборочное задание из закрытой поставки в открытую.

Сборочное задание можно перевести из доставки на сборку, если выполнены все условия:
 - сборочное задание находится в статусе `complete` — в доставке
 - поставка, в которую нужно перенести сборочное задание, [не передана в доставку](./orders-fbs#tag/fbsSupplies/operation/patchV3SuppliesSupplyIdDeliver)
 - сборочное задание ранее не переносили из доставки на сборку
 Чтобы проверить, можно ли перевести сборочное задание из доставки на сборку, используйте [статусы сборочных заданий](./orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus), поле `isTransferable`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки, из которой будут перемещены заказы |

## Запрос

**Тело запроса** (`application/json`):

- `orderIds` — array[integer] **обязательный**. Список ID сборочных заданий, которые нужно перевести на сборку
- `newSupplyId` — string **обязательный**. ID поставки, в которую будут перемещены сборочные задания. Поставка не должна быть в доставке

## Ответы

**200** — Успешно

- `transferredOrders` — array[object]
  - `error` — object. Детали ошибки
    - `detail` — string. Детали ошибки
    - `code` — integer. Внутренний код ошибки
  - `success` — boolean. Успешна ли обработка запроса. Может быть только `true`
  - `newStickerId` — integer **обязательный**. Новый ID стикера
  - `oldStickerId` — integer **обязательный**. Старый ID стикера
  - `orderId` — integer **обязательный**. ID сборочного задания

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

**403** — Доступ запрещён

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки
