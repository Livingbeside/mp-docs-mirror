---
title: Удалить идентификаторы маркировки сборочных заданий
api: wb-orders-dbw
method: POST
path: /api/marketplace/v3/dbw/orders/meta/delete
operation_id: postV3DbwOrdersMetaDelete
tags:
  - dbwLabelIdentifiers
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 804b0d862325f0a5
---

# Удалить идентификаторы маркировки сборочных заданий

`POST /api/marketplace/v3/dbw/orders/meta/delete`

Описание метода

Метод удаляет значение указанных [идентификаторов маркировки сборочного задания](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails) для переданного ключа.

В одном запросе можно удалить идентификаторы маркировки только одного типа. Укажите тип идентификаторов маркировки в запросе:
 - `imei` — [IMEI](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei)
 - `uin` — [УИН](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaUin)
 - `gtin` — [GTIN](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei)
 - `sgtin` — [код маркировки Честного знака](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaSgtin)

Можно передать только один ключ.

 
Лимит запросов на один аккаунт продавца для следующих методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 методы сборочных заданий

 

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
