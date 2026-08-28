---
title: Получить список новых сборочных заданий{{ /api/v3/dbw/orders/new }}
api: wb-orders-dbw
method: GET
path: /api/v3/dbw/orders/new
operation_id: getV3DbwOrdersNew
tags:
  - dbwAssemblyOrders
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: 148862a9b312d9ad
---

# Получить список новых сборочных заданий{{ /api/v3/dbw/orders/new }}

`GET /api/v3/dbw/orders/new`

Описание метода Метод возвращает список всех новых [сборочных заданий](./orders-dbw#tag/dbwAssemblyOrders), которые есть у продавца на момент запроса. Лимит запросов на один аккаунт продавца для следующих методов DBW: получение и обновление списка контактов получение и удаление идентификаторов маркировки методы сборочных заданий | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Ответы

**200** — Успешно

- `orders` — array[object]. Список новых сборочных заданий
  - `address` — object. Адрес покупателя для доставки
    - `fullAddress` — string. Адрес доставки
    - `longitude` — number<float64>. Долгота
    - `latitude` — number<float64>. Широта
  - `salePrice` — integer. Цена в валюте продажи с учетом скидки продавца, без учета скидки WB Клуба, умноженная на 100. Предоставляется в информационных целях
  - `requiredMeta` — array[string]. Список идентификаторов маркировки, доступных для сборочного задания. [Указывать IMEI](./orders-dbw#tag/dbwLabelIdentifiers/operation/putV3DbwOrdersOrderIdMetaImei) обязательно для [предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1all/get) `Смартфоны`, `"subjectId":515`
  - `comment` — string. Комментарий покупателя
  - `options` — object. Опции заказа
    - `isB2b` — boolean. Признак B2B-продажи: - `false` — не B2B-продажа - `true` — B2B-продажа
  - `orderUid` — string. ID транзакции для группировки сборочных заданий. Сборочные задания в одной корзине покупателя будут иметь одинаковый `orderUid`
  - `groupId` — string<UUID>. ID группы сборочных заданий. Объединяет сборочные задания, поступившие на один склад (`warehouseId`) в рамках одной транзакции покупателя (`orderUid`)
  - `article` — string. Артикул продавца
  - `colorCode` — string. Код цвета (только для колеруемых товаров)
  - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
  - `createdAt` — string<date-time>. Дата создания сборочного задания
  - `skus` — array[string]. Массив баркодов товара
  - `id` — integer<int64>. ID сборочного задания
  - `warehouseId` — integer. ID склада продавца, на который поступило сборочное задание
  - `nmId` — integer. Артикул WB
  - `chrtId` — integer. ID размера товара в системе WB
  - `price` — integer. Цена в валюте продажи с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `convertedPrice` — integer. Цена в валюте страны продавца с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Предоставляется в информационных целях
  - `currencyCode` — integer<ISO 4217>. Код валюты продажи
  - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `isZeroOrder` — boolean. Признак заказа товара с нулевым остатком: - `false` — заказ сделан на товар с ненулевым остатком - `true` — заказ сделан на товар с нулевым остатком. Такой заказ можно отменить без штрафа за отмену

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
