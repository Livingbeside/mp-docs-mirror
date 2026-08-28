---
title: Получить информацию о завершённых сборочных заданиях{{ /api/v3/click-collect/orders }}
api: wb-in-store-pickup
method: GET
path: /api/v3/click-collect/orders
operation_id: getV3ClickCollectOrders
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 3f51998345955da7
---

# Получить информацию о завершённых сборочных заданиях{{ /api/v3/click-collect/orders }}

`GET /api/v3/click-collect/orders`

Описание метода Метод возвращает информацию о завершённых сборочных заданиях после продажи или отмены заказа. Можно получить данные за заданный период, максимум 30 календарных дней одним запросом. Лимит запросов на один аккаунт продавца для методов сборочных заданий Самовывоз : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 300 запросов | 200 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов. В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `limit` | query | integer | да | Количество элементов в ответе |
| `next` | query | integer | да | Параметр пагинации. Чтобы получить полный список данных, укажите `0` в первом запросе. Чтобы получить следующий пакет данных, используйте значение `next` из ответа |
| `dateFrom` | query | integer | да | Дата начала периода в формате Unix timestamp |
| `dateTo` | query | integer | да | Дата конца периода в формате Unix timestamp |

## Ответы

**200** — Успешно

- `next` — integer. Параметр пагинации. Содержит значение, которое необходимо указать в запросе для получения следующего пакета данных
- `orders` — array[object]. Список сборочных заданий
  - `article` — string. Артикул продавца
  - `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `chrtId` — integer. ID размера товара в системе WB
  - `createdAt` — string<date-time>. Дата и время создания сборочного задания
  - `price` — integer. Цена в валюте продажи с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `finalPrice` — integer. Сумма к оплате покупателем в валюте продажи с учётом всех скидок, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях. Используйте значение поля `finalPrice`, только если в ответе метода [POST /api/marketplace/v3/click-collect/orders/final-price](./docs/openapi/in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersFinalPrice) вернулось `"data": null`. Во всех остальных случаях используйте значение поля `originalFinalPrice` из ответа указанного метода
  - `convertedPrice` — integer. Цена в валюте страны продавца с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `convertedFinalPrice` — integer. Сумма к оплате покупателем в валюте страны продавца с учетом всех скидок, умноженная на 100. Предоставляется в информационных целях. Используйте значение поля `convertedFinalPrice`, только если в ответе метода [POST /api/marketplace/v3/click-collect/orders/final-price](./docs/openapi/in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersFinalPrice) вернулось `"data": null`. Во всех остальных случаях используйте значение поля `convertedOriginalFinalPrice` из ответа того же метода
  - `currencyCode` — integer<ISO 4217>. Код валюты продажи
  - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `id` — integer. ID сборочного задания
  - `isZeroOrder` — boolean. Признак заказа товара с нулевым остатком: - `false` — заказ сделан на товар с ненулевым остатком - `true` — заказ сделан на товар с нулевым остатком. Такой заказ можно отменить без штрафа за отмену
  - `nmId` — integer. Артикул WB
  - `orderCode` — string. Уникальный ID заказа покупателя
  - `payMode` — string. Режим оплаты: - `prepaid` — предоплатный - `postpaid` — постоплатный - `unknown` — неизвестный
  - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчет о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
  - `skus` — array[string]. Массив баркодов товара
  - `warehouseAddress` — string. Адрес магазина (склада продавца), на который поступило сборочное задание
  - `warehouseId` — integer. ID склада продавца, на который поступило сборочное задание
  - `options` — object. Опции заказа
    - `isB2b` — boolean. Признак B2B-продажи: - `false` — не B2B-продажа - `true` — B2B-продажа

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные, обогащающие ошибку

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
- `data` — object. Дополнительные данные, обогащающие ошибку

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
