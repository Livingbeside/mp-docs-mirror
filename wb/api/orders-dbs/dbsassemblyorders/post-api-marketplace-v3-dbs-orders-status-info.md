---
title: Получить статусы сборочных заданий{{ /api/marketplace/v3/dbs/orders/status/info }}
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/status/info
operation_id: postV3DbsOrdersStatusInfo
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 3bb84887db58f226
---

# Получить статусы сборочных заданий{{ /api/marketplace/v3/dbs/orders/status/info }}

`POST /api/marketplace/v3/dbs/orders/status/info`

Описание метода Метод возвращает статусы [сборочных заданий](./orders-dbs#tag/dbsAssemblyOrders) по их ID. `supplierStatus` — статус сборочного задания. Триггер его изменения — действие самого продавца. Возможные значения `supplierStatus`: | Статус | Описание | Как перевести сборочное задание в данный статус | | ------- | --------- | --------------------------------------| | `new` | **Новое сборочное задание** | | | `confirm` | **На сборке** | [Перевести сборочное задание на сборку](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusConfirm) | `deliver` | **В доставке** | [Перевести сборочное задание в доставку](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusDeliver) | `receive` | **Получено покупателем** | [Сообщить, что заказ принят покупателем](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusReceive) | `reject` | **Отказ покупателя при получении** | [Сообщить, что покупатель отказался от заказа](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusReject) | `cancel` | **Отменено продавцом** | [Отменить сборочное задание](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusCancel) | `cancel_missed_call` | **Отмена по причине недозвона** | Статус меняется автоматически | `wbStatus` — статус системы Wildberries. Возможные значения `wbStatus`: - `waiting` — сборочное задание в работе - `sold` — заказ получен покупателем - `canceled` — отмена сборочного задания - `canceled_by_client` — покупатель отменил заказ при получении - `declined_by_client` — покупатель отменил заказ в первый чаc Отмена доступна покупателю в первый час с момента заказа, если заказ не переведен на сборку - `defect` — отмена заказа по причине брака - `ready_for_pickup` — заказ прибыл на ПВЗ - `canceled_by_missed_call` — отмена по причине недозвона Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]. Информация о статусах
  - `errors` — array[object]. Информация об ошибке
    - `code` — integer. Код ошибки: - `404` - `409` - `400`
    - `detail` — string. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI - `OrderNotB2B` — операция доступна только для сборочных заданий с признаком B2B-продажи `"isB2b":true` - `InvalidOriginCountryCode` — некорректный код страны происхождения товара
  - `orderId` — integer. ID сборочного задания
  - `supplierStatus` — string. Статус сборочного задания, установленный продавцом
  - `wbStatus` — string. Статус сборочного задания в системе Wildberries

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

**404** — Не найдено

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
