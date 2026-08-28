---
title: Получить идентификаторы маркировки сборочных заданий
api: wb-orders-dbs
method: POST
path: /api/marketplace/v3/dbs/orders/meta/details
operation_id: postV3DbsOrdersMetaDetails
tags:
  - dbsLabelIdentifiers
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: 718b51b22ffec5ab
---

# Получить идентификаторы маркировки сборочных заданий

`POST /api/marketplace/v3/dbs/orders/meta/details`

Описание метода

Метод возвращает идентификаторы маркировки [сборочных заданий](./orders-dbs#tag/dbsAssemblyOrders) и статусы их проверки. 

Перечень идентификаторов маркировки, доступных для сборочного задания, можно получить в [списке новых сборочных заданий](./orders-dbs#tag/dbsAssemblyOrders/operation/getV3DbsOrdersNew), поле `requiredMeta`. Если поле `requiredMeta` не содержит какой-либо идентификатор маркировки, значит, у сборочного задания не может быть этого идентификатора — и добавить его нельзя.

Возможные идентификаторы маркировки:
 - `imei` — [IMEI](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei)
 - `uin` — [УИН](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaUin)
 - `gtin` — [GTIN](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaGtin)
 - `sgtin` — [код маркировки Честного знака](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaSgtin)
 - `customsDeclaration` — [номер ДТ](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration)
 - `originCountryCode` — [числовой код страны происхождения товара](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration) из [Общероссийского классификатора стран мира](https://esnsi.gosuslugi.ru/classifiers/16269)

Лимит запросов на один аккаунт продавца для всех методов получения и удаления идентификаторов маркировки DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `orders` — array[object]. Идентификаторы маркировки сборочных заданий и статусы их валидации
  - `errors` — array[object]. Информация об ошибке
    - `code` — integer. Код ошибки
    - `detail` — string. Дополнительная информация об ошибке
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `metaDetails` — array[object]. Идентификаторы маркировки и статусы их валидации
    - `decision` — string. Статус проверки: - `imei` - `pending` — Маркировка на проверке - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `deadlineExceeded` — Валидация пройдена - `imeiMaySell` — Товар допущен к продаже. Валидация пройдена - `imeiSoldB2B` — Товар продан покупателю B2B, допущен к продаже повторно. Валидация пройдена - `required` — Обязательная маркировка не заполнена. Валидация не пройдена - `imeiInvalidFormat` — Неверный формат маркировки. Валидация не пройдена - `imeiAlreadySold` — Товар с этим IMEI уже продан. Валидация не пройдена - `uin` - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `sgtin` - `pending` — Маркировка на проверке - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `deadlineExceeded` — Валидация пройдена - `sgtinIntroduced` — Товар допущен к продаже. Валидация пройдена - `sgtinSoldB2B` — Товар продан покупателю B2B, допущен к продаже повторно. Валидация пройдена - `required` — Обязательная маркировка не заполнена. Валидация не пройдена - `sgtinInvalidFormat` — Неверный формат маркировки. Валидация не пройдена - `sgtinNotFound` — Маркировка не найдена в [Честном Знаке](https://chestnyznak.ru). Валидация не пройдена - `sgtinEmitted` — Маркировка эмитирована. Валидация не пройдена - `sgtinApplied` — Не пройдена процедура Ввод в оборот. Валидация не пройдена - `sgtinWrittenOff` — Списан. Валидация не пройдена - `sgtinRetired` — Выбыл. Валидация не пройдена - `sgtinWithdrawn` — Выбыл. Валидация не пройдена - `sgtinDisaggregation` — Расформирован. Валидация не пройдена - `sgtinDisaggregated` — Расформирован. Валидация не пройдена - `sgtinAppliedNotPaid` — Не оплачен. Валидация не пройдена - `gtin` - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена - `customsDeclaration` - `optional` — Маркировка не обязательна - `filled` — Валидация пройдена
    - `key` — string. Идентификатор маркировки: - `imei` — [IMEI](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei) - `uin` — [УИН](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaUin) - `gtin` — [GTIN](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaGtin) - `sgtin` — [код маркировки](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaSgtin) - `customsDeclaration` — [номер ДТ](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration) - `originCountryCode` — [числовой код страны происхождения](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration) из [Общероссийского классификатора стран мира](https://esnsi.gosuslugi.ru/classifiers/16269) post)
    - `value` — string. Значение идентификатора маркировки
  - `orderId` — integer. ID сборочного задания
- `requestId` — string **обязательный**. Уникальный ID запроса

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
