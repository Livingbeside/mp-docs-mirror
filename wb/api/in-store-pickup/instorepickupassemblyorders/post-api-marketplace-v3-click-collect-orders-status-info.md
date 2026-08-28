---
title: Получить статусы сборочных заданий{{ /api/marketplace/v3/click-collect/orders/status/info }}
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/status/info
operation_id: postV3ClickCollectOrdersStatusInfo
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: e16ac360fc6449fd
---

# Получить статусы сборочных заданий{{ /api/marketplace/v3/click-collect/orders/status/info }}

`POST /api/marketplace/v3/click-collect/orders/status/info`

Описание метода Метод возвращает статусы [сборочных заданий](./in-store-pickup#tag/inStorePickupAssemblyOrders) по их ID. `supplierStatus` — статус сборочного задания. Триггер его изменения - действие самого продавца. Возможные значения `supplierStatus`: | Статус | Описание | Как перевести сборочное задание в данный статус | | ------- | --------- | --------------------------------------| | `new` | **Новое сборочное задание** | | `confirm` | **На сборке** | [Перевести сборочное задание на сборку](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusConfirm) | `prepare` | **Готов к выдаче** | [Сообщить, что сборочное задание готово к выдаче](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusPrepare) | `receive` | **Получено покупателем** | [Сообщить, что заказ принят покупателем](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusReceive) | `reject` | **Отказ покупателя при получении** | [Сообщить, что покупатель отказался от заказа](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusReject) | `cancel` | **Отменено продавцом** | [Отменить сборочное задание](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusCancel) | `cancel_shelf_life` | **Отмена по истечении срока хранения** | Переводится автоматически по возникновению события `wbStatus` — статус системы Wildberries. Возможные значения `wbStatus`: - `waiting` - сборочное задание в работе - `sold` - заказ получен покупателем - `canceled` - отмена сборочного задания - `canceled_by_client` - покупатель отменил заказ при получении - `declined_by_client` - покупатель отменил заказ в первый чаc Отмена доступна покупателю в первый час с момента заказа, если заказ не переведён на сборку - `defect` - отмена заказа по причине брака - `ready_for_pickup` - заказ готов к выдаче Лимит запросов на один аккаунт продавца: | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 сек | 1 запрос | 1 сек | 10 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]. Информация о статусах
  - `errors` — array[object]. Информация об ошибке
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `supplierStatus` — string. Статус сборочного задания, установленный продавцом
  - `wbStatus` — string. Статус сборочного задания в системе Wildberries

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

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
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
