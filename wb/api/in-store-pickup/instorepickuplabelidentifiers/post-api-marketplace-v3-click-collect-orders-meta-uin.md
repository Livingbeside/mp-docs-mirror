---
title: Закрепить УИН за сборочными заданиями{{ /api/marketplace/v3/click-collect/orders/meta/uin }}
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/meta/uin
operation_id: postV3ClickCollectOrdersMetaUin
tags:
  - inStorePickupLabelIdentifiers
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 13edc0db25c1f324
---

# Закрепить УИН за сборочными заданиями{{ /api/marketplace/v3/click-collect/orders/meta/uin }}

`POST /api/marketplace/v3/click-collect/orders/meta/uin`

Описание метода Метод обновляет УИН, уникальные идентификационные номера, в [идентификаторах маркировки сборочных заданий](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails). У одного сборочного задания может быть только один УИН. Закрепить УИН можно только за сборочным заданием в [статусе](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusInfo) `confirm` и если в [идентификаторах маркировки сборочного задания](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails) есть поле `uin`. Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки Самовывоз : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 20 запросов | 3 сек | 500 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `uin` — string **обязательный**. УИН

## Ответы

**200** — Успешно

- `requestId` — ? **обязательный**. Уникальный ID запроса
- `results` — array[object] **обязательный**
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `IncorrectRequestBody` — неправильный запрос - `IncorrectRequest` — передан некорректный параметр

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

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные, обогащающие ошибку

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
