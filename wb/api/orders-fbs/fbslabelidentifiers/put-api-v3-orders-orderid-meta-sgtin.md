---
title: Закрепить код маркировки Честного знака за сборочным заданием{{ /api/v3/orders/{orderId}/meta/sgtin }}
api: wb-orders-fbs
method: PUT
path: /api/v3/orders/{orderId}/meta/sgtin
operation_id: put-api-v3-orders-orderid-meta-sgtin
tags:
  - fbsLabelIdentifiers
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 966bbd2281ee2791
---

# Закрепить код маркировки Честного знака за сборочным заданием{{ /api/v3/orders/{orderId}/meta/sgtin }}

`PUT /api/v3/orders/{orderId}/meta/sgtin`

Описание метода Метод обновляет код маркировки [Честного знака](https://честныйзнак.рф/) в идентификаторах маркировки [сборочного задания](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get). Закрепить код маркировки Честного знака можно только за сборочным заданием в [статусе](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post) есть поле `sgtin`. Получить загруженные маркировки можно в [идентификаторах маркировки сборочного задания](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post). Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки FBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 1000 запросов | 60 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `orderId` | path | integer<int64> | да | ID сборочного задания |

## Запрос

**Тело запроса** (`application/json`):

- `sgtins` — array[string] **обязательный**. Массив кодов маркировки [Честного знака](https://честныйзнак.рф/). Вы [можете передать](https://seller.wildberries.ru/instructions/ru/ru/material/kiz-common-errors#bfd5fce8-e0fd-4f15-9d8b-e616fac02c2e) коды маркировки: - полностью — с GS-разделителями и кодом проверки подлинности (криптохвостом) - в коротком формате — с GS-разделителями без кода проверки подлинности (криптохвоста) GS-разделители необходимо передавать в кодировке Unicode с экранированием — `\u001D`

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

**409** — Ошибка добавления маркировки

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
