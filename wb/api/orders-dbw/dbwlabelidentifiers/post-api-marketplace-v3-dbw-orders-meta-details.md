---
title: Получить идентификаторы маркировки сборочных заданий
api: wb-orders-dbw
method: POST
path: /api/marketplace/v3/dbw/orders/meta/details
operation_id: postV3DbwOrdersMetaDetails
tags:
  - dbwLabelIdentifiers
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: f5d563a154abffcc
---

# Получить идентификаторы маркировки сборочных заданий

`POST /api/marketplace/v3/dbw/orders/meta/details`

Описание метода

Метод возвращает идентификаторы маркировки [сборочных заданий](./orders-dbw#tag/dbwAssemblyOrders/operation/getV3DbwOrders) и статусы их проверки.

Перечень идентификаторов маркировки, доступных для сборочного задания, можно получить в [списке новых сборочных заданий](./orders-dbw#tag/dbwAssemblyOrders/operation/getV3DbwOrdersNew), поле `requiredMeta`. Если поле `requiredMeta` не содержит какой-либо идентификатор маркировки, значит, у сборочного задания не может быть этого идентификатора — и добавить его нельзя.

Возможные идентификаторы маркировки:
 - `imei` — [IMEI](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei)
 - `uin` — [УИН](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaUin)
 - `gtin` — [GTIN](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaGtin)
 - `sgtin` — [код маркировки Честного знака](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaSgtin)

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

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — string **обязательный**. Уникальный ID запроса
- `orders` — array[object]. Идентификаторы маркировки сборочных заданий и статусы их валидации
  - `orderId` — integer. ID сборочного задания
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `errors` — array[object]. Информация об ошибке
    - `code` — integer. Код ошибки
    - `detail` — string. Дополнительная информация об ошибке
  - `metaDetails` — array[object]. Идентификаторы маркировки и статусы их валидации
    - `key` — string. Идентификатор маркировки
    - `value` — string. Значение идентификатора маркировки
    - `decision` — string. Статус проверки: - `imei` - `pending` — Маркировка на проверке - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `deadlineExceeded` — Валидация пройдена - `imeiMaySell` — Товар допущен к продаже. Валидация пройдена - `imeiSoldB2B` — Товар продан покупателю B2B, допущен к продаже повторно. Валидация пройдена - `required` — Обязательная маркировка не заполнена. Валидация не пройдена - `imeiInvalidFormat` — Неверный формат маркировки. Валидация не пройдена - `imeiAlreadySold` — Товар с этим IMEI уже продан. Валидация не пройдена - `uin` - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `sgtin` - `pending` — Маркировка на проверке - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `deadlineExceeded` — Валидация пройдена - `sgtinIntroduced` — Товар допущен к продаже. Валидация пройдена - `sgtinSoldB2B` — Товар продан покупателю B2B, допущен к продаже повторно. Валидация пройдена - `required` — Обязательная маркировка не заполнена. Валидация не пройдена - `sgtinInvalidFormat` — Неверный формат маркировки. Валидация не пройдена - `sgtinNotFound` — Маркировка не найдена в [Честном Знаке](https://chestnyznak.ru). Валидация не пройдена - `sgtinEmitted` — Маркировка эмитирована. Валидация не пройдена - `sgtinApplied` — Не пройдена процедура Ввод в оборот. Валидация не пройдена - `sgtinWrittenOff` — Списан. Валидация не пройдена - `sgtinRetired` — Выбыл. Валидация не пройдена - `sgtinWithdrawn` — Выбыл. Валидация не пройдена - `sgtinDisaggregation` — Расформирован. Валидация не пройдена - `sgtinDisaggregated` — Расформирован. Валидация не пройдена - `sgtinAppliedNotPaid` — Не оплачен. Валидация не пройдена - `gtin` - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `customsDeclaration` - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
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

- `detail` — string. Детали ошибки
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
