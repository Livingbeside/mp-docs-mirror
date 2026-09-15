---
title: Товары поставки{{ /api/v1/supplies/{ID}/goods }}
api: wb-orders-fbw
method: GET
path: /api/v1/supplies/{ID}/goods
operation_id: getV1SuppliesIdGoods
tags:
  - suppliesInformation
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 154e4233effea255
---

# Товары поставки{{ /api/v1/supplies/{ID}/goods }}

`GET /api/v1/supplies/{ID}/goods`

Описание метода

Метод возвращает информацию о товарах в поставке.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 30 запросов | 2 сек | 10 запросов |
| Сервисный | 1 мин | 30 запросов | 2 сек | 10 запросов |
| Базовый с секретом | 1 мин | 30 запросов | 2 сек | 10 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `limit` | query | integer | нет | Количество записей в ответе |
| `offset` | query | integer | нет | После какого элемента выдавать данные |
| `isPreorderID` | query | boolean | нет | Поиск по: - `true` — ID заказа, если в `ID` передаёте ID заказа - `false` — ID поставки, если в `ID` передаёте ID поставки |
| `ID` | path | integer | да | ID поставки или заказа |

## Ответы

**200** — Успешно

- `barcode` — string. Баркод товара
- `vendorCode` — string. Артикул продавца
- `nmID` — integer. Артикул WB
- `needKiz` — boolean. Нужен ли [код маркировки Честного знака](https://честныйзнак.рф/) для этого товара: - `false` — не нужен - `true` — нужен
- `tnved` — string. Код ТНВЭД. Если `"needKiz":true`, а `"tnved":null`, нужно заполнить характеристику товара **ТН ВЭД** в [личном кабинете](https://seller.wildberries.ru/new-goods) или по [API](./item-management#tag/listings/operation/postV2CardsUpdate)
- `techSize` — string. Размер товара, указанный продавцом
- `color` — string. Цвет товара
- `supplierBoxAmount` — integer. Указано в упаковке, шт
- `quantity` — integer. Указано в поставке/заказе, шт
- `readyForSaleQuantity` — integer. Поступило в продажу, шт
- `acceptedQuantity` — integer. Принято, шт
- `unloadingQuantity` — integer. Количество товара на раскладке, шт

**400** — Неправильный запрос

- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки
- `detail` — string. Описание ошибки
- `requestId` — string. ID запроса
- `origin` — string. Сервис, вернувший ошибку

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
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
