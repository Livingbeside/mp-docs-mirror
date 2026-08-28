---
title: Обновить настройки автовозврата продавца
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/fbs/settings/autoreturns
operation_id: patchMarketplaceV3FbsSettingsAutoreturns
tags:
  - autoreturnSettings
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 848ff51fd8b1848b
---

# Обновить настройки автовозврата продавца

`PATCH /api/marketplace/v3/fbs/settings/autoreturns`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену

Метод устанавливает настройки автовозврата продавца для малогабаритных товаров — `"cargoType":1`.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `type` — string (allToWarehouse, allToPickupPoint, manual) **обязательный**. Тип автовозврата малогабаритных товаров: - `allToWarehouse` — отправлять все товары на склад WB, кроме товаров тех [предметов](/openapi/orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturnsSubcategoriesRestricted), которые автоматически возвращаются в ПВЗ - `allToPickupPoint` — отправлять все товары на пункт выдачи заказов - `manual` — использовать ручные настройки

## Ответы

**204** — Обновлено

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
