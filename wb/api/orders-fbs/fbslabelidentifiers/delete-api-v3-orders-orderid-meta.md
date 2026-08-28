---
title: Удалить идентификаторы маркировки сборочного задания{{ /api/v3/orders/{orderId}/meta }}
api: wb-orders-fbs
method: DELETE
path: /api/v3/orders/{orderId}/meta
operation_id: delete-api-v3-orders-orderid-meta
tags:
  - fbsLabelIdentifiers
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: fd922ae3ce09d0e4
---

# Удалить идентификаторы маркировки сборочного задания{{ /api/v3/orders/{orderId}/meta }}

`DELETE /api/v3/orders/{orderId}/meta`

Описание метода

Метод удаляет значение [идентификаторов маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post) для переданного ключа.

Возможные идентификаторы маркировки:
 - `imei` — [IMEI](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1imei/put)
 - `uin` — [УИН](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1uin/put)
 - `gtin` — [GTIN](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1gtin/put)
 - `sgtin` — [код маркировки Честного знака](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1sgtin/put)
 - `customsDeclaration` — [номер ДТ](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1%7BorderId%7D~1meta~1customs-declaration/put)

Можно передать только один ключ.

Лимит запросов на один аккаунт продавца для всех методов получения и удаления идентификаторов маркировки FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | ID сборочного задания |
| `key` | query | string (imei, uin, gtin, sgtin, customsDeclaration) | да | Название идентификаторов маркировки для удаления. Передаётся только одно значение. |

## Ответы

**204** — Удалено

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

**409** — Ошибка удаления идентификаторов маркировки

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
