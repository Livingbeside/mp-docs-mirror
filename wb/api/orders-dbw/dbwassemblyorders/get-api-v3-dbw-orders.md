---
title: Получить информацию о завершенных сборочных заданиях
api: wb-orders-dbw
method: GET
path: /api/v3/dbw/orders
operation_id: getV3DbwOrders
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 6e666f3db35eff72
---

# Получить информацию о завершенных сборочных заданиях

`GET /api/v3/dbw/orders`

Описание метода

Метод возвращает информацию о завершенных [сборочных заданиях](./orders-dbw#tag/dbwAssemblyOrders).

Можно получить данные за заданный период, максимум 30 календарных дней одним запросом.

Лимит запросов на один аккаунт продавца для следующих методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 методы сборочных заданий

 

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `limit` | query | integer | да | Параметр пагинации. Устанавливает предельное количество возвращаемых данных |
| `next` | query | integer<int64> | да | Параметр пагинации. Устанавливает значение, с которого надо получить следующий пакет данных. Для получения полного списка данных должен быть равен `0` в первом запросе. Для следующих запросов необходимо брать значения из одноименного поля в ответе |
| `dateFrom` | query | integer | да | Дата начала периода в формате Unix timestamp |
| `dateTo` | query | integer | да | Дата конца периода в формате Unix timestamp |

## Ответы

**200** — Успешно

- `next` — integer<int64>. Параметр пагинации. Содержит значение, которое необходимо указать в запросе для получения следующего пакета данных
- `orders` — array[object]
  - `address` — object. Адрес покупателя для доставки
    - `fullAddress` — string. Адрес доставки
    - `longitude` — number<float64>. Долгота
    - `latitude` — number<float64>. Широта
  - `options` — object. Опции заказа
    - `isB2b` — boolean. Признак B2B-продажи: - `false` — не B2B-продажа - `true` — B2B-продажа
  - `orderUid` — string. ID транзакции для группировки сборочных заданий. Сборочные задания в одной корзине покупателя будут иметь одинаковый `orderUid`
  - `groupId` — string<UUID>. ID группы сборочных заданий. Объединяет сборочные задания, поступившие на один склад (`warehouseId`) в рамках одной транзакции покупателя (`orderUid`)
  - `article` — string. Артикул продавца
  - `colorCode` — string. Код цвета (только для колеруемых товаров)
  - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./customer-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
  - `createdAt` — string<date-time>. Дата создания сборочного задания
  - `skus` — array[string]. Массив баркодов товара
  - `id` — integer<int64>. ID сборочного задания
  - `warehouseId` — integer. ID склада продавца, на который поступило сборочное задание
  - `nmId` — integer. Артикул WB
  - `chrtId` — integer<uint64>. ID размера товара в системе WB
  - `price` — integer. Цена в валюте продажи с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `convertedPrice` — integer. Цена в валюте страны продавца с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Предоставляется в информационных целях
  - `currencyCode` — integer<ISO 4217>. Код валюты продажи
  - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `comment` — string. Комментарий покупателя
  - `isZeroOrder` — boolean. Признак заказа товара с нулевым остатком: - `false` — заказ сделан на товар с ненулевым остатком - `true` — заказ сделан на товар с нулевым остатком. Такой заказ можно отменить без штрафа за отмену

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

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

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
