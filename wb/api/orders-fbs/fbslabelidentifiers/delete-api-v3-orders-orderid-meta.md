---
title: Удалить идентификаторы маркировки сборочного задания{{ /api/v3/orders/{orderId}/meta }}
api: wb-orders-fbs
method: DELETE
path: /api/v3/orders/{orderId}/meta
operation_id: deleteV3OrdersOrderIdMeta
tags:
  - fbsLabelIdentifiers
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 4684c84351968c67
---

# Удалить идентификаторы маркировки сборочного задания{{ /api/v3/orders/{orderId}/meta }}

`DELETE /api/v3/orders/{orderId}/meta`

Описание метода

Метод удаляет значение [идентификаторов маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta) для переданного ключа.

Возможные идентификаторы маркировки:
 - `imei` — [IMEI](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaImei)
 - `uin` — [УИН](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaUin)
 - `gtin` — [GTIN](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaGtin)
 - `sgtin` — [код маркировки Честного знака](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaSgtin)
 - `customsDeclaration` — [номер ДТ](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaCustomsDeclaration)

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

**409** — Ошибка удаления идентификаторов маркировки

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
