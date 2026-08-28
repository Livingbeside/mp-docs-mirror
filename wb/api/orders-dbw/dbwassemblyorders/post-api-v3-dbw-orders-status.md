---
title: Получить статусы сборочных заданий
api: wb-orders-dbw
method: POST
path: /api/v3/dbw/orders/status
operation_id: postV3DbwOrdersStatus
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 189950ee07a98029
---

# Получить статусы сборочных заданий

`POST /api/v3/dbw/orders/status`

Описание метода

Метод возвращает статусы сборочных заданий по их ID.

`supplierStatus` — статус сборочного задания.
Триггер его изменения — действие самого продавца.

Возможные значения `supplierStatus`:
| Статус | Описание | Как перевести сборочное задание в данный статус |
| ------- | --------- | --------------------------------------|
| `new` | **Новое сборочное задание** | |
| `confirm` | **На сборке** | [Перевести сборочное задание на сборку](./orders-dbw#tag/dbwAssemblyOrders/operation/patchV3DbwOrdersOrderIdConfirm)
| `complete` | **В доставке** | [Перевести сборочное задание в доставку](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatusDeliver) |
| `receive` | **Получено покупателем**| Переводится курьером
| `reject` | **Отказ покупателя при получении**| Переводится курьером
| `cancel` | **Отменено продавцом** | [Отменить сборочное задание](./orders-dbw#tag/dbwAssemblyOrders/operation/patchV3DbwOrdersOrderIdCancel)
| `cancel_missed_call` | **Отмена по причине недозвона**
 | Статус меняется автоматически |

`wbStatus` — статус системы Wildberries.

Возможные значения `wbStatus`:
- `waiting` — сборочное задание в работе
- `sold` — заказ получен покупателем
- `canceled` — отмена сборочного задания
- `canceled_by_client` — покупатель отменил заказ при получении
- `declined_by_client` — покупатель отменил заказ в первый чаc

Отмена доступна покупателю в первый час с момента заказа, если заказ не переведен на сборку
- `defect` — отмена заказа по причине брака
- `canceled_by_missed_call` — отмена заказа по причине недозвона
- `postponed_delivery` — курьерская доставка отложена

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

- `orders` — array[integer<int64>] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]
  - `id` — integer<int64>. ID сборочного задания
  - `supplierStatus` — string. Статус сборочного задания, установленный продавцом
  - `wbStatus` — string. Статус сборочного задания в системе Wildberries

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
