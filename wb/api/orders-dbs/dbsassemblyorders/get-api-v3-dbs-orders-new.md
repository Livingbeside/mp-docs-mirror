---
title: Получить список новых сборочных заданий
api: wb-orders-dbs
method: GET
path: /api/v3/dbs/orders/new
operation_id: getV3DbsOrdersNew
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/orders-dbs"
deprecated: false
content_sha: d6a7b2a4032ec175
---

# Получить список новых сборочных заданий

`GET /api/v3/dbs/orders/new`

Описание метода

Метод возвращает список всех новых [сборочных заданий](./orders-dbs#tag/dbsAssemblyOrders), которые есть у продавца на момент запроса.

Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Ответы

**200** — Успешно

- `orders` — array[object]. Список новых сборочных заданий
  - `address` — object. Адрес покупателя для доставки. При доставке заказов в ПВЗ указан адрес ПВЗ
    - `fullAddress` — string. Адрес доставки
    - `latitude` — number<float64>. Широта
    - `longitude` — number<float64>. Долгота
  - `article` — string. Артикул продавца
  - `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `chrtId` — integer. ID размера товара в системе WB
  - `colorCode` — string. Код цвета (только для колеруемых товаров)
  - `comment` — string. Комментарий покупателя
  - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `convertedFinalPrice` — integer. Сумма к оплате покупателем в валюте страны продавца с учетом всех скидок, умноженная на 100. Предоставляется в информационных целях. Используйте значение поля `convertedFinalPrice`, только если в ответе метода [POST /api/marketplace/v3/dbs/orders/final-price](./docs/openapi/orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersFinalPrice) вернулось `"data": null`. Во всех остальных случаях используйте значение поля `convertedOriginalFinalPrice` из ответа того же метода
  - `convertedPrice` — integer. Цена в валюте страны продавца с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Предоставляется в информационных целях
  - `createdAt` — string<date-time>. Дата создания сборочного задания
  - `currencyCode` — integer<ISO 4217>. Код валюты продажи
  - `deliveryType` — string (dbs, edbs, dbsPickupPoint). Тип доставки: - `dbs` — доставка силами продавца - `dbsPickupPoint` — доставка силами продавца в ПВЗ - `edbs` — экспресс-доставка силами продавца
  - `finalPrice` — integer. Сумма к оплате покупателем в валюте продажи с учётом всех скидок, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях. Используйте значение поля `finalPrice`, только если в ответе метода [POST /api/marketplace/v3/dbs/orders/final-price](./docs/openapi/orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersFinalPrice) вернулось `"data": null`. Во всех остальных случаях используйте значение поля `originalFinalPrice` из ответа того же метода
  - `groupId` — string<UUID>. ID группы сборочных заданий. Объединяет сборочные задания, поступившие на один склад (`warehouseId`) в рамках одной транзакции покупателя (`orderUid`)
  - `id` — integer<int64>. ID сборочного задания
  - `isZeroOrder` — boolean. Признак заказа товара с нулевым остатком: - `false` — заказ сделан на товар с ненулевым остатком - `true` — заказ сделан на товар с нулевым остатком. Такой заказ можно отменить без штрафа за отмену
  - `nmId` — integer. Артикул WB
  - `options` — object. Опции заказа
    - `isB2b` — boolean. Признак B2B-продажи: - `false` — не B2B-продажа - `true` — B2B-продажа
  - `orderUid` — string. ID транзакции для группировки сборочных заданий. Сборочные задания в одной корзине покупателя будут иметь одинаковый `orderUID`
  - `price` — integer. Цена в валюте продажи с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `requiredMeta` — array[string]. Список идентификаторов маркировки, доступных для сборочного задания. [Указывать IMEI](./orders-dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei) обязательно для [предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1all/get) `Смартфоны`, `"subjectId":515`
  - `rid` — ?. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
  - `salePrice` — integer. Цена в валюте продажи с учетом скидки продавца, без учета скидки WB Клуба, умноженная на 100. Предоставляется в информационных целях
  - `skus` — array[string]. Массив баркодов товара
  - `warehouseId` — integer. ID склада продавца, на который поступило сборочное задание
  - `wbStickerId` — integer. ID стикера. Отображается только для заказов в ПВЗ

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

**403** — Доступ запрещён

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
