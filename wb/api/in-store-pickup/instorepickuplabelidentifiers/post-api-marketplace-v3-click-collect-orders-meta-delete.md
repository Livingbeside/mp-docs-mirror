---
title: Удалить идентификаторы маркировки сборочных заданий
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/meta/delete
operation_id: postV3ClickCollectOrdersMetaDelete
tags:
  - inStorePickupLabelIdentifiers
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 179abce6db4ae806
---

# Удалить идентификаторы маркировки сборочных заданий

`POST /api/marketplace/v3/click-collect/orders/meta/delete`

Описание метода

Метод удаляет значения указанных [идентификаторов маркировки сборочных заданий](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails).

В одном запросе можно удалить идентификаторы маркировки только одного типа. Укажите тип идентификаторов маркировки в запросе:
 - `imei` — [IMEI](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaImei)
 - `uin` — [УИН](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaUin)
 - `gtin` — [GTIN](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaGtin)
 - `sgtin` — [код маркировки](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaSgtin)
 - `customsDeclaration` — [номер ДТ](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration). При удалении номера ДТ также удаляется код страны происхождения товара — `originCountryCode`

Лимит запросов на один аккаунт продавца для всех методов получения и удаления идентификаторов маркировки Самовывоз:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 150 запросов | 400 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `key` — string (imei, uin, gtin, sgtin, customsDeclaration) **обязательный**. Тип идентификаторов маркировки для удаления. Передаётся только одно значение
- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — ? **обязательный**. Уникальный ID запроса
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

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
- `data` — object. Дополнительные данные, обогащающие ошибку
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
