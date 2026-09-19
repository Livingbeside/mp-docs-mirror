---
title: Получить статусы сборочных заданий
api: wb-orders-fbs
method: POST
path: /api/v3/orders/status
operation_id: postV3OrdersStatus
tags:
  - fbsAssemblyOrders
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: f0b81e331c778412
---

# Получить статусы сборочных заданий

`POST /api/v3/orders/status`

Описание метода

Метод возвращает статусы [сборочных заданий](./orders-fbs#tag/fbsAssemblyOrders/operation/getV3Orders) по их ID.

`supplierStatus` — статус сборочного задания. Триггер его изменения — действие самого продавца.

Возможные значения `supplierStatus`:

| Статус | Описание | Как перевести сборочное задание в данный статус |
|-------|----------------------|--------------------------------------|
| `new` | **Новое сборочное задание** | |
| `confirm` | **На сборке** |[Добавить сборочное задание к поставке](./orders-fbs#tag/fbsSupplies/operation/patchV3SuppliesSupplyIdOrders)
| `complete` | **В доставке** | [Передать поставку в доставку](./orders-fbs#tag/fbsSupplies/operation/patchV3SuppliesSupplyIdDeliver) |
| `cancel` | **Отменено продавцом** | [Отменить сборочное задание](./orders-fbs#tag/fbsAssemblyOrders/operation/patchV3OrdersOrderIdCancel)|
| `cancel_carrier` | **Отменено перевозчиком** <br>Только для трансграничных поставок | Переводится перевозчиком |

`wbStatus` — статус системы Wildberries.

Возможные значения `wbStatus`:
- `waiting` — сборочное задание в работе
- `sorted` — сборочное задание отсортировано
- `sold` — заказ получен покупателем
- `canceled` — отмена сборочного задания
- `canceled_by_client` — покупатель отменил заказ при получении
- `declined_by_client` — покупатель отменил заказ. Отмена доступна покупателю в первый час с момента заказа, если заказ не переведён на сборку
- `defect` — отмена заказа по причине брака
- `ready_for_pickup` — заказ прибыл на пункт выдачи заказов (ПВЗ)
- `accepted_by_carrier` — продавец передал заказ в службу доставки в своей стране
- `sent_to_carrier` — заказ отправлен на склад службы доставки в стране продавца
- `canceled_by_carrier` — заказ отменён перевозчиком. Только для трансграничных поставок

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer<int64>] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]
  - `id` — integer<int64>. ID сборочного задания
  - `isCancellable` — boolean. Доступна ли [отмена](./orders-fbs#tag/fbsAssemblyOrders/operation/patchV3OrdersOrderIdCancel) сборочного задания: - `false` — недоступна - `true` — доступна
  - `supplierStatus` — string (new, confirm, complete, cancel). Статус сборочного задания, установленный продавцом
  - `wbStatus` — string (waiting, sorted, sold, canceled, canceled_by_client, declined_by_client, defect, ready_for_pickup, postponed_delivery, accepted_by_carrier, sent_to_carrier). Статус сборочного задания в системе Wildberries

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
