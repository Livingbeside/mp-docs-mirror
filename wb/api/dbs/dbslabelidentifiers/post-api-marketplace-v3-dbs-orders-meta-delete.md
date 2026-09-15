---
title: Удалить идентификаторы маркировки сборочных заданий
api: wb-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/meta/delete
operation_id: postV3DbsOrdersMetaDelete
tags:
  - dbsLabelIdentifiers
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/dbs"
deprecated: false
content_sha: bb1d553831047587
---

# Удалить идентификаторы маркировки сборочных заданий

`POST /api/marketplace/v3/dbs/orders/meta/delete`

Описание метода

Метод удаляет значение указанных [идентификаторов маркировки сборочных заданий](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails).

В одном запросе можно удалить идентификаторы маркировки только одного типа. Укажите тип идентификаторов маркировки в запросе:
 - `imei` — [IMEI](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei)
 - `uin` — [УИН](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaUin)
 - `gtin` — [GTIN](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaGtin)
 - `sgtin` — [код маркировки Честного знака](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaSgtin)
 - `customsDeclaration` — [номер ДТ](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration). При удалении номера ДТ также удаляется код страны происхождения товара — `originCountryCode`

Лимит запросов на один аккаунт продавца для всех методов получения и удаления идентификаторов маркировки DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 150 запросов | 400 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `key` — string (imei, uin, gtin, sgtin, customsDeclaration) **обязательный**. Название идентификатора маркировки для удаления. Передаётся только одно значение
- `orderIds` — array[integer] **обязательный**. Список ID сборочных заданий

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

**409** — Ошибка удаления идентификаторов маркировки

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
