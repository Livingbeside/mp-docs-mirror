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
content_sha: edd8079214e36420
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

- `acceptedQuantity` — integer. Принято, шт
- `barcode` — string. Баркод товара
- `color` — string. Цвет товара
- `needKiz` — boolean. Нужен ли [код маркировки Честного знака](https://честныйзнак.рф/) для этого товара: - `false` — не нужен - `true` — нужен
- `nmID` — integer. Артикул WB
- `quantity` — integer. Указано в поставке/заказе, шт
- `readyForSaleQuantity` — integer. Поступило в продажу, шт
- `supplierBoxAmount` — integer. Указано в упаковке, шт
- `techSize` — string. Размер товара, указанный продавцом
- `tnved` — string. Код ТНВЭД. Если `"needKiz":true`, а `"tnved":null`, нужно заполнить характеристику товара **ТН ВЭД** в [личном кабинете](https://seller.wildberries.ru/new-goods) или по [API](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post)
- `unloadingQuantity` — integer. Количество товара на раскладке, шт
- `vendorCode` — string. Артикул продавца

**400** — Неправильный запрос

- `detail` — string. Описание ошибки
- `origin` — string. Сервис, вернувший ошибку
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
