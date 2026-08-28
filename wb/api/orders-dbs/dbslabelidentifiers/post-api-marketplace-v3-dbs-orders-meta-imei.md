---
title: Закрепить IMEI за сборочными заданиями
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/meta/imei
operation_id: postV3DbsOrdersMetaImei
tags:
  - dbsLabelIdentifiers
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 32ee6b589feb90b1
---

# Закрепить IMEI за сборочными заданиями

`POST /api/marketplace/v3/dbs/orders/meta/imei`

Описание метода

Метод обновляет IMEI в [идентификаторах маркировки сборочных заданий](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails).

У одного сборочного задания может быть только один IMEI. Если у устройства два IMEI — **IMEI** и **IMEI2** или **IMEI1** и **IMEI2** — укажите только **IMEI** или **IMEI1**. **IMEI2** указывать не нужно.

Закрепить IMEI можно только за сборочным заданием в [статусе](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusInfo) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails) есть поле `imei`.

Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 500 запросов | 120 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `imei` — string **обязательный**. IMEI
  - `orderId` — integer **обязательный**. ID сборочного задания

## Ответы

**200** — Успешно

- `requestId` — string. Уникальный ID запроса
- `results` — array[object]
  - `errors` — array[object]. Детали ошибки
    - `code` — integer. Код ошибки: - `404` - `409` - `400`
    - `detail` — string. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI - `OrderNotB2B` — операция доступна только для сборочных заданий с признаком B2B-продажи `"isB2b":true` - `InvalidOriginCountryCode` — некорректный код страны происхождения товара
  - `isError` — boolean. Есть ли ошибки
  - `orderId` — integer. ID сборочного задания с успешно обновлёнными данными

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

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

- `detail` — object. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**409** — Ошибка обновления идентификаторов маркировки

- `detail` — object. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
