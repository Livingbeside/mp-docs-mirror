---
title: Обновить настройки автовозврата продавца{{ /api/marketplace/v3/fbs/settings/autoreturns }}
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/fbs/settings/autoreturns
operation_id: patchMarketplaceV3FbsSettingsAutoreturns
tags:
  - autoreturnSettings
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 2841f76c9bf4339f
---

# Обновить настройки автовозврата продавца{{ /api/marketplace/v3/fbs/settings/autoreturns }}

`PATCH /api/marketplace/v3/fbs/settings/autoreturns`

Описание метода Метод доступен по Персональному токену Метод устанавливает настройки автовозврата продавца для малогабаритных товаров — `"cargoType":1`. Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `type` — string (allToWarehouse, allToPickupPoint, manual) **обязательный**. Тип автовозврата малогабаритных товаров: - `allToWarehouse` — отправлять все товары на склад WB, кроме товаров тех [предметов](/openapi/orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturnsSubcategoriesRestricted), которые автоматически возвращаются в ПВЗ - `allToPickupPoint` — отправлять все товары на пункт выдачи заказов - `manual` — использовать ручные настройки

## Ответы

**204** — Обновлено

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
