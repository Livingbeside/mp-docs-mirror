---
title: Получить список новых сборочных заданий
api: wb-orders-fbs
method: GET
path: /api/v3/orders/new
operation_id: get-api-v3-orders-new
tags:
  - Сборочные задания FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: dbc921588d360771
---

# Получить список новых сборочных заданий

`GET /api/v3/orders/new`

Описание метода

Метод возвращает список всех новых [сборочных заданий](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get), которые есть у продавца на момент запроса.

Наличие в сборочных заданиях идентификаторов маркировки, указанных в полях requiredMeta и optionalMeta, влияет только на возможность перевести поставку в доставку. Если ваш товар подлежит обязательной маркировке средствами
идентификации, необходимо указывать идентификаторы маркировки независимо от того, в каком поле они были получены (п. 4.6 Оферты).

Рекомендуем добавлять в сборочные задания все идентификаторы маркировки, полученные в полях requiredMeta и optionalMeta

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Ответы

**200** — Успешно

- `orders` — array[object]. Список новых сборочных заданий
  - `address` — object. Точный адрес покупателя для доставки, если применимо. Из-за особенностей адреса некоторые поля могут быть пустыми
    - `fullAddress` — string. Адрес доставки
    - `latitude` — number<float64>. Широта
    - `longitude` — number<float64>. Долгота
  - `article` — string. Артикул продавца
  - `cargoType` — integer (1, 2, 3). Тип товара: - `1` — малогабаритный товар (МГТ) - `2` — сверхгабаритный товар (СГТ) - `3` — крупногабаритный товар (КГТ+)
  - `chrtId` — integer. ID размера товара в системе WB
  - `colorCode` — string. Код цвета (только для колеруемых товаров)
  - `comment` — string. Комментарий покупателя
  - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `convertedFinalPrice` — integer. Сумма к оплате покупателем в валюте страны продавца с учетом всех скидок, умноженная на 100. Предоставляется в информационных целях
  - `convertedPrice` — integer. Цена в валюте страны продавца с учетом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Предоставляется в информационных целях
  - `createdAt` — string<date-time>. Дата создания сборочного задания (RFC3339)
  - `crossBorderType` — integer (0, 1). Тип сборочного задания: - `0` — внутренняя поставка - `1` — трансграничная поставка
  - `currencyCode` — integer<ISO 4217>. Код валюты продажи
  - `ddate` — string. Планируемая дата доставки заказа покупателю. Поле отображается для сборочных заданий со сверхгабаритными товарами `СГТ`, `cargoType: 2`
  - `deliveryType` — string (fbs). Тип доставки: - `fbs` — доставка на склад Wildberries (FBS)
  - `finalPrice` — integer. Сумма к оплате покупателем в валюте продажи с учетом всех скидок, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
  - `id` — integer<int64>. ID сборочного задания
  - `isPickupPointShipmentAllowed` — boolean. Можно ли отгрузить заказ на ПВЗ: - `false` — нет - `true` — да
  - `isZeroOrder` — boolean. Признак заказа товара с нулевым остатком: - `false` — заказ сделан на товар с ненулевым остатком - `true` — заказ сделан на товар с нулевым остатком. Такой заказ можно отменить без штрафа за отмену
  - `nmId` — integer. Артикул WB
  - `officeId` — integer<int64>. ID склада WB, к которому привязан склад продавца
  - `offices` — array[string]. Список офисов, куда следует привезти товар
  - `optionalMeta` — array[string]. Список идентификаторов маркировки, которые [можно добавить](/knowledge-base/articles/019e9273-118b-7b69-a25a-ea1d756f05d9/rabota-s-markirovkoi-po-modeli-fbs) в сборочное задание. Поставку со сборочным заданием без этих идентификаторов маркировки можно перевести в доставку, но они могут потребоваться, например, при возврате товара покупателем
  - `options` — object. Опции заказа
    - `isB2B` — boolean. Признак B2B-продажи: - `false` — не B2B-продажа - `true` — B2B-продажа
  - `orderUid` — string. ID транзакции для группировки сборочных заданий. Сборочные задания в одной корзине покупателя будут иметь одинаковый `orderUid`
  - `price` — integer. Цена в валюте продажи с учётом всех скидок, кроме скидки по WB Кошельку, умноженная на 100. Код валюты продажи — в поле `currencyCode`. Предоставляется в информационных целях
  - `requiredMeta` — array[string]. Список идентификаторов маркировки, которые [необходимо добавить](/knowledge-base/articles/019e9273-118b-7b69-a25a-ea1d756f05d9/rabota-s-markirovkoi-po-modeli-fbs) в сборочное задание, чтобы поставку с этим сборочным заданием можно было перевести в доставку
  - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
  - `salePrice` — integer. Цена продавца в валюте продажи с учётом скидки продавца, без учёта скидки WB Клуба, умноженная на 100. Предоставляется в информационных целях
  - `scanPrice` — number<uint32>. Цена приёмки в копейках. Отображается после фактической приёмки заказа. Для данного метода всегда будет возвращаться `null`. Предоставляется в информационных целях
  - `sellerDate` — string. Рекомендуемая дата доставки СГТ в сортировочный центр или на склад. Поле отображается для сборочных заданий со сверхгабаритными товарами `СГТ`, `cargoType: 2`
  - `skus` — array[string]. Список баркодов
  - `warehouseId` — integer. ID склада продавца, на который поступило сборочное задание

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
