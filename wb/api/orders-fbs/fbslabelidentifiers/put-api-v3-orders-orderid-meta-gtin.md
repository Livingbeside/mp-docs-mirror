---
title: Закрепить GTIN за сборочным заданием{{ /api/v3/orders/{orderId}/meta/gtin }}
api: wb-orders-fbs
method: PUT
path: /api/v3/orders/{orderId}/meta/gtin
operation_id: put-api-v3-orders-orderid-meta-gtin
tags:
  - fbsLabelIdentifiers
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 778a69ef211b2c4a
---

# Закрепить GTIN за сборочным заданием{{ /api/v3/orders/{orderId}/meta/gtin }}

`PUT /api/v3/orders/{orderId}/meta/gtin`

Описание метода

Метод обновляет GTIN, уникальный ID товара в Беларуси, в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post).
У одного сборочного задания может быть только один GTIN.

 Закрепить GTIN можно только за сборочным заданием в [статусе](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post) есть поле `gtin`.

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

- `gtin` — string **обязательный**. GTIN

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

**409** — Ошибка обновления идентификаторов маркировки

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
