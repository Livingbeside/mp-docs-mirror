---
title: Закрепить номера ДТ за сборочными заданиями
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/meta/customs-declaration
operation_id: postV3ClickCollectOrdersMetaCustomsDeclaration
tags:
  - inStorePickupLabelIdentifiers
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 0e32ba2b59716412
---

# Закрепить номера ДТ за сборочными заданиями

`POST /api/marketplace/v3/click-collect/orders/meta/customs-declaration`

Описание метода

Метод обновляет номера ДТ — деклараций на товары — и коды стран происхождения товаров в [идентификаторах маркировки сборочных заданий](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails). У одного сборочного задания может быть только один номер ДТ. 

Закрепить номер ДТ можно, только если выполняются все условия:
 - сборочное задание имеет признак B2B-продажи — `"isB2b":true` в ответе метода [получения новых сборочных заданий](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/getV3ClickCollectOrdersNew)
 - сборочное задание находится в [статусах](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusInfo) `confirm` или `prepare`
 - поле `customsDeclaration` есть в [идентификаторах маркировки сборочного задания](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails)

Лимит запросов на один аккаунт продавца для всех методов закрепления идентификаторов маркировки Самовывоз:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 20 запросов | 3 сек | 500 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `customsDeclaration` — string **обязательный**. Номер ДТ
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `originCountryCode` — string **обязательный**. Числовой код страны происхождения товара из [Общероссийского классификатора стран мира](https://esnsi.gosuslugi.ru/classifiers/16269). Необходимо указывать только для сборочных заданий с признаком B2B-продажи "isB2b":true

## Ответы

**200** — Успешно

- `requestId` — ? **обязательный**. Уникальный ID запроса
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки: - `404` - `409` - `400`
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `OrderNotB2B` — операция доступна только для сборочных заданий с признаком B2B-продажи `"isB2b":true` - `InvalidOriginCountryCode` — некорректный код страны происхождения товара
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
