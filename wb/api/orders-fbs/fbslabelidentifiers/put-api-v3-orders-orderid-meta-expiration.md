---
title: Закрепить за сборочным заданием срок годности товара{{ /api/v3/orders/{orderId}/meta/expiration }}
api: wb-orders-fbs
method: PUT
path: /api/v3/orders/{orderId}/meta/expiration
operation_id: putV3OrdersOrderIdMetaExpiration
tags:
  - fbsLabelIdentifiers
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: c416d0a1f53498fc
---

# Закрепить за сборочным заданием срок годности товара{{ /api/v3/orders/{orderId}/meta/expiration }}

`PUT /api/v3/orders/{orderId}/meta/expiration`

Описание метода

Метод закрепляет за [сборочным заданием](./orders-fbs#tag/fbsAssemblyOrders/operation/getV3Orders) срок годности товара. Товар годен до указанной даты. 

Закрепить срок годности можно только за сборочным заданием в [статусе](./orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta) есть поле `expiration`.

Получить загруженные данные можно в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta).

Чтобы изменить срок годности, отправьте запрос с новой датой. Удалить срок годности сборочного задания невозможно.

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

- `expiration` — string<date (dd.mm.yyyy)> **обязательный**. Дата, до которой годен товар. Не менее 30 дней с текущей даты

## Ответы

**204** — Отправлено

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

**409** — Ошибка добавления срока годности

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
