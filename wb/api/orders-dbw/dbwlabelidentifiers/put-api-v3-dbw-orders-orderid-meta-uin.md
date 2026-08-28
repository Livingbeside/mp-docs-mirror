---
title: Закрепить УИН за сборочным заданием{{ /api/v3/dbw/orders/{orderId}/meta/uin }}
api: wb-orders-dbw
method: PUT
path: /api/v3/dbw/orders/{orderId}/meta/uin
operation_id: putV3DbwOrdersOrderIdMetaUin
tags:
  - dbwLabelIdentifiers
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: f34d0c8e76f28922
---

# Закрепить УИН за сборочным заданием{{ /api/v3/dbw/orders/{orderId}/meta/uin }}

`PUT /api/v3/dbw/orders/{orderId}/meta/uin`

Описание метода

Метод обновляет УИН, уникальный идентификационный номер, в [идентификаторах маркировки сборочного задания](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails). У одного сборочного задания может быть только один УИН. 

Закрепить УИН можно только за сборочным заданием в [статусе](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatus) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails) есть поле `uin`.

Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки DBW:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1000 запросов | 60 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | ID сборочного задания |

## Запрос

**Тело запроса** (`application/json`):

- `uin` — string **обязательный**. УИН

## Ответы

**204** — Обновлено

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

**404** — Не найдено

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**409** — Ошибка добавления идентификаторов маркировки

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
