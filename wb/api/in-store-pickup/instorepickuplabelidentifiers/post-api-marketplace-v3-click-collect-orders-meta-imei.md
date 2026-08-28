---
title: Закрепить IMEI за сборочными заданиями
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/meta/imei
operation_id: postV3ClickCollectOrdersMetaImei
tags:
  - inStorePickupLabelIdentifiers
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 7e9bcd479db99a5e
---

# Закрепить IMEI за сборочными заданиями

`POST /api/marketplace/v3/click-collect/orders/meta/imei`

Описание метода

Метод обновляет IMEI в [идентификаторах маркировки сборочных заданий](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails). 

У одного сборочного задания может быть только один IMEI. Если у устройства два IMEI — **IMEI** и **IMEI2** или **IMEI1** и **IMEI2** — укажите только **IMEI** или **IMEI1**. **IMEI2** указывать не нужно.

Закрепить IMEI можно только за сборочным заданием в [статусе](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusInfo) `confirm` и если в [идентификаторах маркировки сборочного задания](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails) есть поле `imei`.

Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки Самовывоз:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 20 запросов | 3 сек | 500 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `imei` — string **обязательный**. IMEI
  - `orderId` — integer **обязательный**. ID сборочного задания

## Ответы

**200** — Успешно

- `requestId` — ? **обязательный**. Уникальный ID запроса
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `IncorrectRequestBody` — неправильный запрос - `IncorrectRequest` — передан некорректный параметр
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

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные, обогащающие ошибку
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
