---
title: Закрепить номер ДТ за сборочным заданием{{ /api/marketplace/v3/orders/{orderId}/meta/customs-declaration }}
api: wb-orders-fbs
method: PUT
path: /api/marketplace/v3/orders/{orderId}/meta/customs-declaration
operation_id: putV3OrdersOrderIdMetaCustomsDeclaration
tags:
  - fbsLabelIdentifiers
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 26629a0602ec288b
---

# Закрепить номер ДТ за сборочным заданием{{ /api/marketplace/v3/orders/{orderId}/meta/customs-declaration }}

`PUT /api/marketplace/v3/orders/{orderId}/meta/customs-declaration`

Описание метода

Метод обновляет номер ДТ — декларации на товары — в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta). У одного сборочного задания может быть только один номер ДТ. 

Закрепить номер ДТ можно только за сборочным заданием в [статусе](./orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta) есть поле `customsDeclaration`.

Продавцам из Армении необходимо обязательно указывать номер декларации на товары (ДТ), произведённые вне ЕАЭС, если заказ из Армении доставляется в РФ.

Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1000 запросов | 60 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | ID сборочного задания |

## Запрос

**Тело запроса** (`application/json`):

- `customsDeclaration` — string **обязательный**. Номер ДТ

## Ответы

**204** — Обновлено

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

**404** — Не найдено

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**409** — Ошибка обновления номера ДТ

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
