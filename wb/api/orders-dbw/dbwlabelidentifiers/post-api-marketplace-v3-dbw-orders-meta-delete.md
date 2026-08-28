---
title: Удалить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/dbw/orders/meta/delete }}
api: wb-orders-dbw
method: POST
path: /api/marketplace/v3/dbw/orders/meta/delete
operation_id: postV3DbwOrdersMetaDelete
tags:
  - dbwLabelIdentifiers
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 272533a8eecc8f03
---

# Удалить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/dbw/orders/meta/delete }}

`POST /api/marketplace/v3/dbw/orders/meta/delete`

Описание метода Метод удаляет значение указанных [идентификаторов маркировки сборочного задания](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails) для переданного ключа. В одном запросе можно удалить идентификаторы маркировки только одного типа. Укажите тип идентификаторов маркировки в запросе: - `imei` — [IMEI](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei) - `uin` — [УИН](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaUin) - `gtin` — [GTIN](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei) - `sgtin` — [код маркировки Честного знака](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaSgtin) Можно передать только один ключ. Лимит запросов на один аккаунт продавца для следующих методов DBW: получение и обновление списка контактов получение и удаление идентификаторов маркировки методы сборочных заданий | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `key` — string (imei, uin, gtin, sgtin) **обязательный**. Название идентификатора маркировки для удаления. Передаётся только одно значение
- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — string. Уникальный ID запроса. Отображается для ответов с ошибками
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки: - `404` - `409`
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания с успешно обновлёнными данными

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
