---
title: Закрепить коды маркировки Честного знака за сборочными заданиями
api: wb-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/meta/sgtin
operation_id: postV3DbsOrdersMetaSgtin
tags:
  - dbsLabelIdentifiers
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/dbs"
deprecated: false
content_sha: 587dc96a2175c9a1
---

# Закрепить коды маркировки Честного знака за сборочными заданиями

`POST /api/marketplace/v3/dbs/orders/meta/sgtin`

Описание метода

Метод обновляет код маркировки [Честного знака](https://честныйзнак.рф/) в [идентификаторах маркировки сборочных заданий](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails).

Закрепить код маркировки можно только за сборочным заданием в [статусе](./orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStatusInfo) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails) есть поле `sgtin`.

Получить загруженные маркировки можно в [идентификаторах маркировки сборочного задания](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails).

Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки DBS:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 500 запросов | 120 мс | 20 запросов |
| Сервисный | 1 мин | 500 запросов | 120 мс | 20 запросов |
| Базовый с секретом | 1 мин | 500 запросов | 120 мс | 20 запросов |
| Базовый | 1 ч | 10 запросов | 6 мин | 1 запрос |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `sgtins` — array[string] **обязательный**. Массив кодов маркировки Честного знака. Допускается от 16 до 135 символов для кода одной маркировки

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

- `detail` — object. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
