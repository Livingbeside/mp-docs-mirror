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
content_sha: 5d739a31e375bce3
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

- `phone` — string. Телефон пользователя, создавшего поставку
- `statusID` — integer (1, 2, 3, 4, 5, 6). ID статуса поставки: - `1` — Не запланировано - `2` — Запланировано - `3` — Отгрузка разрешена - `4` — Идёт приёмка - `5` — Принято - `6` — Отгружено на воротах
- `virtualTypeID` — integer. ID типа виртуальной поставки. Отображается только для поставок с `"boxTypeID":0`. - `0` — Перенос остатков - `1` — Обезличка - `4` — QR-поставка - `5` — Допринято - `6` — Скан-приёмка
- `boxTypeID` — integer. ID типа поставки: - `0` — Без коробов (виртуальная поставка) - `1` и `2` — Короба - `5` — Монопаллеты - `6` — Суперсейф
- `createDate` — string. Дата и время создания поставки
- `supplyDate` — string. Плановая дата отгрузки поставки
- `factDate` — string. Дата фактической отгрузки поставки
- `updatedDate` — string. Дата изменения поставки
- `warehouseID` — integer. ID склада, на который планируется поставка
- `warehouseName` — string. Название склада, на который планируется поставка
- `actualWarehouseID` — integer. ID склада, на который поставка была привезена
- `actualWarehouseName` — string. Название склада, на который поставка привезена
- `transitWarehouseID` — integer. ID транзитного склада
- `transitWarehouseName` — string. Название транзитного склада
- `acceptanceCost` — number. Предварительная стоимость приёмки, ₽
- `paidAcceptanceCoefficient` — number. Коэффициент приёмки
- `rejectReason` — string. Причина, по которой поставка не может быть принята
- `supplierAssignName` — string. Краткое название продавца
- `storageCoef` — string. Коэффициент хранения
- `deliveryCoef` — string. Коэффициент логистики
- `quantity` — integer. Добавлено в поставку/заказ, шт
- `readyForSaleQuantity` — integer. Поступило в продажу, шт
- `acceptedQuantity` — integer. Принято, шт
- `unloadingQuantity` — integer. Количество товара, находящегося на раскладке, шт
- `depersonalizedQuantity` — integer. Количество обезличенного товара, шт
- `discrepancies` — integer. Расхождения между заявленным и фактическим количеством товара в поставке. Только при `"statusID":5`
- `isBoxOnPallet` — boolean. Тип поставки — **Поштучная палета**: - `true` — да - `false` — нет Поле возвращается только при `"boxTypeID": 2`

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

**404** — Не найдено

- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки
- `detail` — string. Описание ошибки
- `requestId` — string. ID запроса
- `origin` — string. Сервис, вернувший ошибку

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
