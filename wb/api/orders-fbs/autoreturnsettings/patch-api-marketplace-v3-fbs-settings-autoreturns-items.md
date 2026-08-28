---
title: Обновить настройки автовозврата товаров{{ /api/marketplace/v3/fbs/settings/autoreturns/items }}
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/fbs/settings/autoreturns/items
operation_id: patchMarketplaceV3FbsSettingsAutoreturnsItems
tags:
  - autoreturnSettings
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: a0a1ca11c1dbcb0c
---

# Обновить настройки автовозврата товаров{{ /api/marketplace/v3/fbs/settings/autoreturns/items }}

`PATCH /api/marketplace/v3/fbs/settings/autoreturns/items`

Описание метода Метод доступен по Персональному токену Метод устанавливает настройки автовозврата малогабаритных товаров — `"cargoType":1`. Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `chrtIds` — array[integer] **обязательный**. Список ID размеров товаров в системе WB
- `type` — string (byWarehouse, byPickupPoint) **обязательный**. Тип автовозврата малогабаритных товаров: - `byWarehouse` — все товары отправляются на склад WB - `byPickupPoint` — все товары отправляются на пункт выдачи заказов

## Ответы

**200** — Успешно

- `results` — array[object] **обязательный**
  - `chrtId` — integer **обязательный**. ID размера товара в системе WB
  - `error` — ?. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. Дополнительная информация об ошибке: - `Not Found` — ID размера товара не найден или указан ID размера немалогабаритного товара
  - `success` — boolean. - `true` — настройки автовозврата товара обновлены

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
