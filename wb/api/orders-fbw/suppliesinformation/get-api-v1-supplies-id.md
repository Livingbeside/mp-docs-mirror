---
title: Детали поставки{{ /api/v1/supplies/{ID} }}
api: wb-orders-fbw
method: GET
path: /api/v1/supplies/{ID}
operation_id: getV1SuppliesId
tags:
  - suppliesInformation
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: f0c76779d56a05f9
---

# Детали поставки{{ /api/v1/supplies/{ID} }}

`GET /api/v1/supplies/{ID}`

Описание метода

Метод возвращает детали поставки по ID.

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
| `ID` | path | integer | да | ID поставки или заказа |
| `isPreorderID` | query | boolean | нет | Поиск по: - `true` — ID заказа, если в `ID` передаёте ID заказа - `false` — ID поставки, если в `ID` передаёте ID поставки |

## Ответы

**200** — Успешно

- `acceptanceCost` — number. Предварительная стоимость приёмки, ₽
- `acceptedQuantity` — integer. Принято, шт
- `actualWarehouseID` — integer. ID склада, на который поставка была привезена
- `actualWarehouseName` — string. Название склада, на который поставка привезена
- `boxTypeID` — integer. ID типа поставки: - `0` — Без коробов (виртуальная поставка) - `1` и `2` — Короба - `5` — Монопаллеты - `6` — Суперсейф
- `createDate` — string. Дата и время создания поставки
- `deliveryCoef` — string. Коэффициент логистики
- `depersonalizedQuantity` — integer. Количество обезличенного товара, шт
- `factDate` — string. Дата фактической отгрузки поставки
- `isBoxOnPallet` — boolean. Тип поставки — **Поштучная палета**: - `true` — да - `false` — нет Поле возвращается только при `"boxTypeID": 2`
- `paidAcceptanceCoefficient` — number. Коэффициент приёмки
- `phone` — string. Телефон пользователя, создавшего поставку
- `quantity` — integer. Добавлено в поставку/заказ, шт
- `readyForSaleQuantity` — integer. Поступило в продажу, шт
- `rejectReason` — string. Причина, по которой поставка не может быть принята
- `statusID` — integer (1, 2, 3, 4, 5, 6). ID статуса поставки: - `1` — Не запланировано - `2` — Запланировано - `3` — Отгрузка разрешена - `4` — Идёт приёмка - `5` — Принято - `6` — Отгружено на воротах
- `storageCoef` — string. Коэффициент хранения
- `supplierAssignName` — string. Краткое название продавца
- `supplyDate` — string. Плановая дата отгрузки поставки
- `transitWarehouseID` — integer. ID транзитного склада
- `transitWarehouseName` — string. Название транзитного склада
- `unloadingQuantity` — integer. Количество товара, находящегося на раскладке, шт
- `updatedDate` — string. Дата изменения поставки
- `virtualTypeID` — integer. ID типа виртуальной поставки. Отображается только для поставок с `"boxTypeID":0`. - `0` — Перенос остатков - `1` — Обезличка - `4` — QR-поставка - `5` — Допринято - `6` — Скан-приёмка
- `warehouseID` — integer. ID склада, на который планируется поставка
- `warehouseName` — string. Название склада, на который планируется поставка

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

**404** — Не найдено

- `detail` — string. Описание ошибки
- `origin` — string. Сервис, вернувший ошибку
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
