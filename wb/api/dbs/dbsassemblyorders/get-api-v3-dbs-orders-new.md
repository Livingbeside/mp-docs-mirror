---
title: Получить список новых сборочных заданий
api: wb-dbs
method: GET
path: /api/v3/dbs/orders/new
operation_id: getV3DbsOrdersNew
tags:
  - dbsAssemblyOrders
spec_version: dbs
source: "https://dev.wildberries.ru/docs/openapi/dbs"
deprecated: false
content_sha: 68027a31f8c1ee57
---

# Получить список новых сборочных заданий

`GET /api/v3/dbs/orders/new`

Описание метода

Метод возвращает список всех новых [сборочных заданий](./dbs#tag/dbsAssemblyOrders), которые есть у продавца на момент запроса.

Лимит запросов на один аккаунт продавца для методов сборочных заданий DBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Ответы

**200** — Успешно

- `orders` — array[object]. Список новых сборочных заданий
  - `salePrice` — integer. Цена в валюте продажи с учетом скидки продавца, без учета скидки WB Клуба, умноженная на 100. Предоставляется в информационных целях
  - `requiredMeta` — array[string]. Список идентификаторов маркировки, доступных для сборочного задания. [Указывать IMEI](./dbs#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaImei) обязательно для [предмета](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectAll) `Смартфоны`, `"subjectId":515`
  - `comment` — string. Комментарий покупателя
  - `options` — object. Опции заказа
    - `isB2b` — boolean. Признак B2B-продажи: - `false` — не B2B-продажа - `true` — B2B-продажа
  - `address` — object. Адрес покупателя для доставки. При доставке заказов в ПВЗ указан адрес ПВЗ
    - `fullAddress` — string. Адрес доставки
    - `longitude` — number<float64>. Долгота
    - `latitude` — number<float64>. Широта
  - `orderUid` — string. ID транзакции для группировки сборочных заданий. Сборочные задания в одной корзине покупателя будут иметь одинаковый `orderUID`
  - `groupId` — string<UUID>. ID группы сборочных заданий. Объединяет сборочные задания, поступившие на один склад (`warehouseId`) в рамках одной транзакции покупателя (`orderUid`)
  - `article` — string. Артикул продавца
  - `colorCode` — string. Код цвета (только для колеруемых товаров)
  - `rid` — ?. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./customer-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./documents-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./documents-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
  - `createdAt` — string<date-time>. Дата создания сборочного задания
  - `deliveryType` — string (dbs, edbs, dbsPickupPoint). Тип доставки: - `dbs` — доставка силами продавца - `dbsPickupPoint` — доставка силами продавца в ПВЗ - `edbs` — экспресс-доставка силами продавца
  - `skus` — array[string]. Массив баркодов товара
  - `id` — integer<int64>. ID сборочного задания
  - `warehouseId` — integer. ID склада продавца, на который поступило сборочное задание
  - `nmId` — integer. Артикул WB
  - `chrtId` — integer<uint64>. ID размера товара в системе WB
  - `price` — integer. Цена в валюте продажи с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `finalPrice` — integer. Сумма к оплате покупателем в валюте продажи с учётом всех скидок, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях. Используйте значение поля `finalPrice`, только если в ответе метода [POST /api/marketplace/v3/dbs/orders/final-price](./docs/openapi/dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersFinalPrice) вернулось `"data": null`. Во всех остальных случаях используйте значение поля `originalFinalPrice` из ответа того же метода
  - `convertedFinalPrice` — integer. Сумма к оплате покупателем в валюте страны продавца с учетом всех скидок, умноженная на 100. Предоставляется в информационных целях. Используйте значение поля `convertedFinalPrice`, только если в ответе метода [POST /api/marketplace/v3/dbs/orders/final-price](./docs/openapi/dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersFinalPrice) вернулось `"data": null`. Во всех остальных случаях используйте значение поля `convertedOriginalFinalPrice` из ответа того же метода
  - `convertedPrice` — integer. Цена в валюте страны продавца с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Предоставляется в информационных целях
  - `currencyCode` — integer<ISO 4217>. Код валюты продажи
  - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `isZeroOrder` — boolean. Признак заказа товара с нулевым остатком: - `false` — заказ сделан на товар с ненулевым остатком - `true` — заказ сделан на товар с нулевым остатком. Такой заказ можно отменить без штрафа за отмену
  - `wbStickerId` — integer. ID стикера. Отображается только для заказов в ПВЗ

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
