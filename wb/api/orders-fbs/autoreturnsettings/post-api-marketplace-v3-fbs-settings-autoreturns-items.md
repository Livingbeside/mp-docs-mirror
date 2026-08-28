---
title: Получить настройки автовозврата товаров
api: wb-orders-fbs
method: POST
path: /api/marketplace/v3/fbs/settings/autoreturns/items
operation_id: postMarketplaceV3FbsSettingsAutoreturnsItems
tags:
  - autoreturnSettings
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 3e6564f4a35c04d5
---

# Получить настройки автовозврата товаров

`POST /api/marketplace/v3/fbs/settings/autoreturns/items`

Описание метода

 Метод доступен по
 Персональному токену

Метод возвращает настройки автовозврата товаров.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `chrtIds` — array[integer<int64>] **обязательный**. Список ID размеров товаров в системе WB

## Ответы

**200** — Успешно

- `results` — array[object] **обязательный**
  - `changeable` — boolean. - `true` — настройки автовозврата товара можно изменить
  - `chrtId` — integer **обязательный**. ID размера товара в системе WB
  - `error` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. Дополнительная информация об ошибке
  - `success` — boolean. - `true` — настройки автовозврата товара успешно получены
  - `type` — string (auto, byWarehouse, byPickupPoint, byCourier). Куда будет возвращён товар: - `auto` — место возврата определяется автоматически - `byWarehouse` — на склад WB - `byPickupPoint` — на пункт выдачи заказов - `byCourier` — продавцу курьером. Всегда для товаров тех [предметов](/openapi/orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturnsSubcategoriesRestricted), которые автоматически возвращаются в ПВЗ

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
