---
title: Главные обновления
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/changelog/main.md"
fetched_at: "2026-09-24T02:13:31Z"
content_sha: 990989392991f2b0
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/changelog/main.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/changelog/main.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/changelog/main.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/changelog/main.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Главные обновления

{% note tip "Следите за обновлениями документации в [Телеграм-канале](https://t.me/yandex_market_api)." %}

 

{% endnote %}

<!-- source: ru/_auto/changelog/main.md -->
<!-- source: ru/_auto/changelog/main/2026-09-09.md -->
### 9 сентября {#09-09-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v1/businesses/{businessId}/offers/documents/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/createDocuments.md)<br>[POST v1/businesses/{businessId}/offers/documents/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/updateDocuments.md)<br>[POST v1/businesses/{businessId}/offers/documents/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/deleteDocuments.md)<br>[POST v1/businesses/{businessId}/offers/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/getDocuments.md)

|
Добавили методы для создания, обновления, удаления и получения документов на товары. Создавать, обновлять и удалять документы можно пакетами до 100 документов. Для получения доступны фильтры и постраничная загрузка.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-09-09.md -->

<!-- source: ru/_auto/changelog/main/2026-07-29.md -->
### 29 июля {#29-07-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v3/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md)<br>[POST v3/businesses/{businessId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md)<br>[POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md)<br>[POST v3/businesses/{businessId}/warehouse/models/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseModelStatus.md)<br>[POST v3/businesses/{businessId}/reports/stocks/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksReport.md)<br>[Передача остатков через API](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/stocks.md)<br>[Работа со складами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/warehouses.md)

|
Добавили методы для работы со складами и остатками на уровне кабинета: получение списка складов, просмотр и передача остатков, включение и выключение модели работы склада, генерация отчета по остаткам. Методы подходят для кабинетов без групп складов. Обновили инструкции по передаче остатков и работе со складами.
||
||
[POST v2/campaigns/{campaignId}/warehouse/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseStatus.md)
|
Пометили метод как устаревший. Вместо него используйте [POST v3/businesses/{businessId}/warehouse/models/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseModelStatus.md).
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-07-29.md -->

<!-- source: ru/_auto/changelog/main/2026-06-22.md -->
### 22 июня {#22-06-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)<br>[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)<br>[Обработка заказов с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)
|
В ответах методов получения заказов у объекта `delivery` добавили поле `digitalGoods` с информацией о способе доставки цифрового товара: тип (`EMAIL`, `ACTIVATION_CODE`, `STEAM_GIFT` или `CHAT`) и ссылка `steamLink` на Steam-аккаунт покупателя (только для типа `STEAM_GIFT`). Переработали инструкцию по работе с цифровыми товарами: описали флоу для каждого из четырех типов доставки.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-06-22.md -->

<!-- source: ru/_auto/changelog/main/2026-06-15.md -->
### 15 июня {#15-06-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md) [POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
|
Удалили устаревший параметр `quantum` — настройку продажи квантами.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-06-15.md -->

<!-- source: ru/_auto/changelog/main/2026-06-02.md -->
### 2 июня {#02-06-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v1/businesses/{businessId}/reports/marketing-detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMarketingDetalizationReport.md)
|
Добавили новый метод для генерации отчета по счету маркетинга.
||
||
[POST v2/reports/closure-documents/detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md)
|
Из параметра `contractType` удалили значение `MARKETING`. Для генерации отчета по счету маркетинга используйте [POST v1/businesses/{businessId}/reports/marketing-detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMarketingDetalizationReport.md).
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-06-02.md -->

<!-- source: ru/_auto/changelog/main/2026-05-28.md -->
### 28 мая {#28-05-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
|
Добавили параметр `fake` в запрос создания заказа. Он позволяет проверить работу магазина и его API на тестовых заказах; такой заказ не будет отгружен и не влияет на остатки.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-05-28.md -->

<!-- source: ru/_auto/changelog/main/2026-05-18.md -->
### 18 мая {#18-05-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)
|
Уточнили описания ошибок, связанных с тарифными ограничениями и передачей идентификатора бизнеса в заголовке `X-Business-Id`.
||
||
[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)
|
В блоке `delivery` добавили поле `receiveBarcode` — штрихкод получения заказа на ПВЗ. Возвращается только для модели LaaS.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-05-18.md -->

<!-- source: ru/_auto/changelog/main/2026-05-14.md -->
### 14 мая {#14-05-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
Типы решений по возврату
|
В типы решений по возврату (`ReturnDecisionType` и `ReturnRequestDecisionType`) добавили значение `PARTIAL_MONEY_REFUND` — частичный возврат денег.
||
||
[POST v1/businesses/{businessId}/returns/decisions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnAvailableDecisions.md)
|
Добавили поле `partialCompensationBounds` — пределы суммы частичной компенсации. Возвращается для `decisionType` = `PARTIAL_MONEY_REFUND`.
||
||
[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md)<br>[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md)
|
Добавили поле `compensation` — сумму добровольной компенсации по позиции; передавайте при решении `PARTIAL_MONEY_REFUND`.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-05-14.md -->

<!-- source: ru/_auto/changelog/main/2026-04-28.md -->
### 28 апреля {#28-04-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)
|
На листах «Буст продаж, оплата за показы» (файл `cpm-boost`) и «Видеобаннеры в такси» (файл `pads`) добавили колонку `SURFACE_TYPE` — площадка размещения.
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-04-28.md -->

<!-- source: ru/_auto/changelog/main/2026-04-17.md -->
### 17 апреля {#17-04-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)
|
Для кабинетов в РФ добавлена валидация параметров выплат. Поддерживаются: частота `DAILY`; либо частота `WEEKLY` с отсрочкой выплат 1, 2 или 4 недели (параметр `paymentDelayWeeks`). При передаче других комбинаций метод вернёт ошибку. [Подробнее об ошибках](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#tariffs).
||
|#
<!-- endsource: ru/_auto/changelog/main/2026-04-17.md -->
<!-- endsource: ru/_auto/changelog/main.md -->

### 7 апреля {#07-04-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | В отчёт по услугам Маркета добавили колонку **VOLUME** (объём, л). ||
|#

### 2 апреля {#02-04-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/banners-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md)

[POST v2/reports/boost-consolidated/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBoostConsolidatedReport.md)

[POST v2/reports/competitors-position/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateCompetitorsPositionReport.md)

[POST v2/reports/goods-feedback/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md)

[POST v2/reports/goods-movement/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)

[POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md)

[POST v2/reports/goods-turnover/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)

[POST v2/reports/jewelry-fiscal/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateJewelryFiscalReport.md)

[POST v2/reports/key-indicators/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md)

[POST v2/reports/sales-geography/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateSalesGeographyReport.md)

[POST v2/reports/shelf-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)

[POST v2/reports/shows-boost/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md)

[POST v2/reports/shows-sales/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)

[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)

[POST v2/reports/united-returns/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedReturnsReport.md) | В описание добавили предупреждение: с 18 мая 2026 года период доступных данных и число одновременно создаваемых отчетов зависят от тарифного плана. ||
|| [Ограничения для запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/limits.md) | В описаниях методов добавили лимиты запросов отдельно для случая без подписки и для тарифа «Медиум». Конкретные значения — на странице каждого метода; общие правила — в разделе [Ограничения](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/limits.md). Лимиты по тарифам начнут действовать с 18 мая 2026 года. ||
|| [Создание и использование OAuth-токена](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md) | Для расширенных возможностей API по подписке при авторизации через OAuth нужно передавать идентификатор бизнеса в заголовке `X-Business-Id`. ||
|#

### 30 марта {#30-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/application](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnApplication.md) | Уточнили, что в ответе заявление на возврат отдается в формате PDF (`application/pdf`). ||
|| [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/{itemId}/image/{imageHash}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnPhoto.md) | Уточнили что в ответе фото возвращается как `image/jpeg` или `image/png`; формат можно узнать из заголовка `Content-Type`. Уточнили, откуда брать `imageHash`, и что максимальный размер файла — 50 МБ. ||
|#

### 27 марта {#27-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) | Время получения ответа для проверочного уведомления типа `PING` снижен с 10 до 1 секунды. Для обычных уведомлений допустимое время ответа по-прежнему составляет 10 секунд. ||
|#

### 23 марта {#23-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| Методы, в которых передается `vat` (ставка НДС) | Значение `7` (НДС 20%) теперь автоматически заменяется на `14` (НДС 22%). С 1 июля 2026 года значение `7` будет недоступно для передачи. ||
|#

### 20 марта {#20-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | В отчет по стоимости услуг добавили колонку **SURFACE_TYPE** — тип площадки размещения. ||
|#

### 17 марта {#17-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v1/businesses/{businessId}/returns/decisions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnAvailableDecisions.md) | Опубликовали метод получения доступных решений по возврату. Используйте его перед передачей решения по возврату. ||
|#

### 12 марта {#12-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| `GET v2/campaigns/{campaignId}/offer-mapping-entries`

`POST v2/campaigns/{campaignId}/offer-mapping-entries/updates`

`POST v2/campaigns/{campaignId}/offer-mapping-entries/suggestions` | Удалили устаревшие методы работы с каталогом товаров. ||
|#

### 11 марта {#11-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| `POST v2/businesses/{businessId}/offer-mappings/suggestions` | Удалили устаревший метод подбора карточек на Маркете. ||
|#

### 10 марта {#10-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/businesses/{businessId}/bids/info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsInfoForBusiness.md)

[POST v2/campaigns/{campaignId}/bids/info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsInfoForCampaign.md) | Уменьшили максимальное значение параметра `limit` с 1500 до 500. Уменьшили максимальный размер параметра `skus` до 500. ||
|| [GET v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPrices.md)

[POST v2/businesses/{businessId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getDefaultPrices.md) | Уменьшили максимальное значение параметра `limit` с 2000 до 500. ||
|| [POST v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md) | Уменьшили максимальное значение параметра `limit` с 2000 до 500. Уменьшили максимальный размер параметра `offerIds` до 500. ||
|| [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md) | В ответе добавили поле `region` с информацией о регионе. Поле `regions` помечено как устаревшее. ||
|#

### 4 марта {#04-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md) | Параметры `page` и `pageSize` помечены как устаревшие. Используйте токенную пагинацию через `pageToken` и `limit`. ||
|#

### 3 марта {#03-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) | Добавлена поддержка токенной пагинации: новые параметры `pageToken` и `limit`, а также поле `paging` в ответе. ||
|#

### 27 февраля {#27-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Документация для модели LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md) | Опубликована документация для методов API, доступных для модели размещения LaaS (Фулфилмент Яндекс Маркета). ||
|#

### 26 февраля {#26-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md) | Добавлен параметр `paymentDelayWeeks` — отсрочка выплат при еженедельном графике. Используется вместе с параметром `frequency`. ||
|#

### 25 февраля {#25-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md) | Добавлена поддержка токенной пагинации: новые параметры `pageToken` и `limit`. ||
|#

### 20 февраля {#20-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | В отчёт добавили колонку **MERCHANT_PRICE** (Ваша цена). ||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | Уточнили колонку **TARIFF_FOR_TRANSFER**: до 28.02.2026 тариф считается в % от платежа покупателя, с 1.03.2026 — в % от цены товара. ||
|#

### 17 февраля {#17-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| Методы заказов (информация о заказе и позициях) | Удалили тип тега товара **TURBO** из ответов. ||
|#

### 13 февраля {#13-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md) | Изменили лимит: не более 500 запросов в час. ||
|#

### 10 февраля {#10-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| Методы заказов (информация о заказе и позициях) | Тип тега товара **TURBO** помечен как устаревший. ||
|#

### 5 февраля {#05-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md) | В отчёт по реализации товаров добавили колонки **RECEIPT_ID** (идентификатор чека) и **RECEIPT_DATETIME** (дата и время чека). ||
|#

### 30 января {#30-01-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md) | Добавили новый статус заявки на вывоз **ЭАПП подписан складом** (`WAREHOUSE_SIGNED_ACT`). Статус присваивается, когда склад подписал акт приёма-передачи. ||
|#

### 28 января {#28-01-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md) | Изменили лимит количества товаров в одном запросе с 200 до 100. ||
|| [POST v2/reports/goods-feedback/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md) | Удалили из отчёта поля **ESTIMATED_OPINIONS_COUNT** ("Еще можно получить") и **ORDERED_ITEMS_TOTAL_AMOUNT** ("Заказанные товары на сумму"). ||
|#

### 15 января {#15-01-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| `POST /v2/reports/prices/generate` | Удалили устаревший метод генерации отчёта по ценам. Используйте метод [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md). ||
|#

### 12 января {#12-01-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) | Добавили ограничение на параметр `pageSize`. Теперь возвращается не более 100 магазинов за запрос. ||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | Переименовали листы отчёта:

* **Комиссия за продажу** → **Поручение на продажу**
* **Перевод платежа с 1.01.26** → **Поручение на перевод платежа** ||
|#

## 2025 {#2025}

### 26 декабря {#26-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Вопросы и ответы о товарах](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/goods-questions.md) | Добавили пошаговую инструкцию «Вопросы и ответы о товарах». В ней описали сценарии работы с вопросами пользователей: получение списка вопросов, публикация ответов и комментариев. ||
|| [POST v1/businesses/{businessId}/goods-questions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md)

[POST v1/businesses/{businessId}/goods-questions/answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md)

[POST v1/businesses/{businessId}/goods-questions/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md) | Добавили новые методы для работы с вопросами и ответами о товарах. ||
|#

### 24 декабря {#24-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Управление доступом к API](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md) | Добавили статью «Управление доступом к API». Описали, как проверить доступность API для магазина, причины блокировок и способы восстановления доступа. ||
|#

### 21 декабря {#21-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| Методы, в которых передается `offerId`/`shopSku` (идентификатор товара). | Уточнили, что пробельные символы в начале и конце значения `offerId`/`shopSku` автоматически удаляются. ||
|#

### 17 декабря {#17-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md) | Пометили методы как устаревшие. Используйте [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) для получения информации о заказах. ||
|#

### 9 декабря {#09-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md) | Обновили страницу ошибок — добавлена колонка «Методы» для всех кодов ошибок (400, 401, 403, 404 и др.) и расширен список ошибок 400 с разбивкой по категориям. ||
|| [Лучшие практики интеграции с API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/best-practices.md) | Добавили новую страницу с лучшими практиками интеграции с API: устойчивость к изменениям, работа с лимитами, обработка ошибок, безопасность. ||
|#

### 21 ноября {#21-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Коды ошибок](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md) | Добавили описание ошибки **The method is deprecated and is occasionally forbidden. Please stop using it**. Ошибка возвращается интеграциям, которые продолжают использовать устаревшие методы API. ||
|#

### 18 ноября {#18-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md) | Добавили параметр `withRecommendations` (по умолчанию `false`). При значении `true` в ответе возвращаются поля `recommendations` (список рекомендаций к заполнению карточки) и `averageContentRating` (средний рейтинг карточки). ||
|| [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) | Добавили новый метод. Он возвращает информацию о заказах в кабинете. ||
|#

### 27 октября {#27-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)|В метод проверки статусов кодов маркировки добавили коды системы «Честный ЗНАК».

Уточнили, что неуспешный статус проверки кодов маркировки в системе [«Честный ЗНАК»](https://честныйзнак.рф/) не блокирует перевод заказа в статус `READY_TO_SHIP` до 1 декабря 2025 года.
||
|#

### 23 октября {#23-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Вызов методов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md)<br><br>[Как работать с API Маркета продавцам Market Yandex Go](https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md)
|Рассказали, что в запросах нужно указывать номер версии метода. Его можно найти на странице каждого метода.<br><br>Скоро мы отключим возможность работать с запросами без указания версии.
||
|#

### 13 октября {#13-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v1/businesses/{businessId}/offer-mappings/barcodes/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/generateOfferBarcodes.md)|Добавили новый метод. Он генерирует штрихкоды и присваивает их указанным товарам.
||
||[POST v1/reports/documents/barcodes/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBarcodesReport.md)|Добавили новый метод. Он запускает генерацию PDF-файла со штрихкодами переданных товаров или товаров в указанной заявке на поставку.
||
|#

### 5 сентября {#05-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)|Отметили устаревшим параметр `shipmentId`.
||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `id` в `OrderShipmentDTO`.
||
|#

### 21 августа {#21-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|Добавили тип уведомления — изменение заказа.
||
|#

### 19 августа {#19-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)<br><br>[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)<br><br>[Как изменяются статусы возвратов для моделей FBY, FBS и Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fby-fbs-express-return-status-model.md)
|Рассказали, что FBY-магазины могут принимать решения по возвратам и создавать чаты с покупателями, чтобы уточнять детали возврата.
||
|#

### 15 августа {#15-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md)|Добавили отчет «Цены».
||
||`POST v2/reports/prices/generate`|Отметили метод устаревшим. Вместо него используйте [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md).
||
|#

### 11 августа {#11-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|Так как ошибочно отметили параметр `id` в `LogisticPickupPointDTO` устаревшим, убрали это указание.
||
|#

### 7 августа {#07-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|Добавили параметр `showcaseUrls` — ссылки на один и тот же товар на разных витринах Маркета.
||
|#

### 1 августа {#01-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)|Уточнили, что для моделей DBS, FBS и Экспресс параметр `campaignId` скоро станет недоступен.<br><br>Для получения информации об остатках на складе магазина используйте `businessId` и идентификатор нужного магазина в `campaignIds`.
||
||[GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md)|Отметили устаревшими параметры `showInContext`, `showInPremium` и `useOpenStat`.
||
||`GET v2/campaigns/{campaignId}/region`|Удалили устаревший метод.
||
|#

### 31 июля {#31-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)<br><br>[GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)
|Отметили устаревшими параметры `shopOutletId` и `workingTime`. Вместо них используйте `shopOutletCode` и `workingSchedule`.
||
|#

### 25 июля {#25-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/categories/max-sale-quantum](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesMaxSaleQuantum.md)|Отметили метод устаревшим.
||
||[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
|Отметили устаревшим параметр `quantum`.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|Отметили устаревшим параметр `firstVideoAsCover`.
||
|#

### 23 июля {#23-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)|Параметр `campaignId` перестал быть обязательным. Если его передать, вернется отчет об остатках на соответствующем складе магазина.<br><br>Добавили параметр `businessId`. Если его передать, в отчете вернется информация об остатках на всех складах магазинов в кабинете, кроме FBY.<br><br>Добавили параметр `campaignIds` — фильтр по магазинам для отчета по кабинету (кроме модели FBY).
||
|#

### 16 июля {#16-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|Отметили устаревшим параметр `id` в `LogisticPickupPointDTO`.
||
|#

### 11 июля {#11-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getDefaultPrices.md)|Добавили новый метод. Он возвращает список цен, которые вы установили для всех магазинов.
||
||[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)|Добавили параметр `minimumForBestseller` — минимальная цена товара для попадания в акцию «Бестселлеры Маркета».
||
|#

### 9 июля {#09-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)<br><br>[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)<br><br>[Как изменяются статусы возвратов для моделей FBY, FBS и Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fby-fbs-express-return-status-model.md)
|Рассказали, что Экспресс-магазины могут принимать решения по возвратам и создавать чаты с покупателями, чтобы уточнять детали возврата.
||
|#

### 3 июля {#03-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/closure-documents/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsReport.md)|Добавили новый метод. Он дает возможность получить закрывающие документы.
||
||[POST v2/reports/closure-documents/detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md)|Добавили отчет по схождению с закрывающими документами.
||
||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|Описали ошибку **Contract with type MARKETING was signed with the agency** (договор на маркетинг заключен с агентством), которую Маркет может вернуть в ответе на запрос.
||
|#

### 1 июля {#01-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)<br><br>[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)
|Рассказали, что FBS-магазины могут создавать чаты с покупателями не только по заказам, но и возвратам.
||
|#

### 30 июня {#30-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[FBS-магазины](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fby-fbs-express-return-status-model.md)<br><br>[DBS-магазины](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/dbs-return-status-model.md)
|Добавили схемы, как изменяются статусы возвратов.
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md)|Теперь метод передает и подтверждает решения по возврату для всех моделей размещения, кроме FBY.
||
||[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)|Рассказали, как работать с возвратами, по которым требуется решение.
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md).
||
|#

### 23 июня {#23-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Логи запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md)|Рассказали о виджете с информацией об ошибках в запросах и ответах и фильтре **Интеграция**.
||
|#

### 4 июня {#04-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/key-indicators/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateKeyIndicatorsReport.md)|Добавили отчет по ключевым показателям.
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderShipmentBoxes.md)|Отметили метод устаревшим. Вместо него используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
||
|#

### 3 июня {#03-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)<br><br>[GET v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPrices.md)
|Изменили лимиты на количество товаров — 150 000 товаров в минуту.
||
||`GET v2/campaigns/{campaignId}/offer-mapping-entries`|Изменили лимит на количество товаров — 10 000 товаров в минуту.
||
|#

### 29 мая {#29-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/sales-geography/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateSalesGeographyReport.md)|Добавили отчет по географии продаж.
||
||`GET v2/campaigns/{campaignId}/offers`<br><br>`GET v2/campaigns/{campaignId}/offers/all`<br><br>`GET v2/campaigns/{campaignId}/feeds`<br><br>`GET v2/campaigns/{campaignId}/feeds/{feedId}`<br><br>`GET v2/campaigns/{campaignId}/feeds/{feedId}/index-logs`<br><br>`POST v2/campaigns/{campaignId}/feeds/{feedId}/params`<br><br>`POST v2/campaigns/{campaignId}/feeds/{feedId}/refresh`<br><br>
|Удалили устаревшие методы.
||
|#

### 28 мая {#28-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)|Добавили новый метод. Он возвращает статусы проверки УИНов в заказе.
||
|#

### 27 мая {#27-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/jewelry-fiscal/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateJewelryFiscalReport.md)|Добавили отчет по заказам с ювелирными изделиями.
||
|#

### 6 мая {#06-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/banners-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md)|Добавили отчет по охватному продвижению.
||
|#

### 30 апреля {#30-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/shows-boost/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md)|Добавили отчет по бусту показов.
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)|Добавили новый метод. Он передает внешний идентификатор заказа в системе магазина.
||
|#

### 28 апреля {#28-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md) — получение информации о заявках на поставку, вывоз и утилизацию;<br><br>[POST v2/campaigns/{campaignId}/supply-requests/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestItems.md) — получение товаров в заявке на поставку, вывоз или утилизацию;<br><br>[POST v2/campaigns/{campaignId}/supply-requests/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md) — получение документов по заявке на поставку, вывоз или утилизацию.
|Добавили методы работы с FBY-заявками.
||
||[Заявки на поставку товаров на склад, вывоз или утилизацию](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/supplies.md)|Добавили пошаговую инструкцию по работе с FBY-заявками.
||
|#

### 24 апреля {#24-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/auth/token](https://yandex.ru/dev/market/partner-api/doc/ru/reference/auth/getAuthTokenInfo.md)|Добавили новый метод. Он возвращает информацию о переданном токене авторизации.
||
||[Модуль для системы «1С:Предприятие»](https://yandex.ru/dev/market/partner-api/doc/ru/modules/1c.md)|Рассказали о модуле для системы «1С:Предприятие», с помощью которого можно управлять товарами и обрабатывать заказы на Маркете.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Отметили устаревшим параметр `cofinancePrice`.
||
|#

### 22 апреля {#22-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)|Добавили отчет о баллах Маркета.
||
||[GET v2/businesses/{businessId}/chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md) — возвращает чат по его идентификатору;<br><br>[GET v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md) — возвращает сообщение по его идентификатору.
|Добавили методы работы с чатами.
||
||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|Добавили типы уведомлений:<ul><li>создание чата с покупателем;</li><li>добавление сообщения в чате;</li><li>начало спора;</li><li>завершение спора;</li><li>создание отзыва о товаре;</li><li>создание комментария к отзыву.</li></ul>
||
|#

### 16 апреля {#16-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передаются или возвращаются эти типы скидки.
|Удалили устаревшие типы скидки:<br><br>`YANDEX_PLUS`<br><br>`YANDEX_EMPLOYEE`<br><br>`LIMITED_FREE_DELIVERY_PROMO`<br><br>`FREE_DELIVERY_THRESHOLD`<br><br>`MULTICART_DISCOUNT`<br><br>`FREE_DELIVERY_FOR_LDI`<br><br>`FREE_DELIVERY_FOR_LSC`<br><br>`FREE_PICKUP`<br><br>`SUPPLIER_MULTICART_DISCOUNT`<br><br>`ANNOUNCEMENT_PROMO`<br><br>`EMPTY_PROMO`<br><br>`BLOCKING_PROMO`<br><br>`MARKET_DEAL`<br><br>`MARKET_PRIME`<br><br>`BERU_PLUS`
||
|#

### 15 апреля {#15-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как пользоваться консолью](https://yandex.ru/dev/market/partner-api/doc/ru/console.md)|Рассказали, как авторизоваться в консоли в зависимости от типа токена.
||
|#

### 11 апреля {#11-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передаются или возвращаются эти параметры.
|Отметили устаревшими параметры `marketModelId`, `marketModelName`, `modelIds` и `modelId`.
||
||`GET v2/models/{modelId}`<br><br>`POST v2/models`<br><br>`GET v2/models/{modelId}/offers`<br><br>`POST v2/models/offers`<br><br>`GET v2/models`
|Отметили методы устаревшими.
||
|#

### 10 апреля {#10-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Работа со складами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/warehouses.md)|Добавили пошаговую инструкцию, как работать со складами.
||
|#

### 9 апреля {#09-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/regions/countries](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)|Добавили новый метод. Он возвращает список стран с их кодами.
||
||[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)|Изменили лимит на количество товаров — 10 000 товаров в минуту, не более 500 товаров в одном запросе в методе.
||
||[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)|Изменили лимит на количество товаров — 10 000 товаров в минуту.
||
|#

### 8 апреля {#08-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)|Добавили пошаговую инструкцию, как работать с невыкупами и возвратами.
||
|#

### 6 апреля {#06-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)|Отчет по реализации стал доступен и для модели DBS.
||
|#

### 4 апреля {#04-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)|Изменили лимит на количество категорий — 100 категорий в минуту.
||
||[POST v2/categories/max-sale-quantum](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesMaxSaleQuantum.md)|Изменили лимит на количество запросов — 5 000 запросов в час.
||
||[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)<br><br>[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)<br><br>[POST v2/campaigns/{campaignId}/hidden-offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md)
|Изменили лимиты на количество товаров — 10 000 товаров в минуту.
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)|Изменили лимит на количество товаров — 10 000 товаров в минуту, не более 500 товаров в одном запросе.
||
|#

### 1 апреля {#01-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Пошаговые инструкции и методы, где передаются или возвращаются коды маркировки в системе «Честный ЗНАК».
|Рассказали, что маркировка товаров в системе [«Честный ЗНАК»](https://честныйзнак.рф/) теперь необязательна для заказов от физических лиц.<br><br>Для заказов от бизнеса все еще нужно передавать коды маркировки.
||
|#

### 31 марта {#31-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md) — возвращает список складов и информацию о них;<br><br>[POST v2/campaigns/{campaignId}/warehouse/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseStatus.md) — отключает или включает склад.
|Добавили методы работы со складами.
||
||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md).
||
|#

### 20 марта {#20-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как работать с API Маркета продавцам Market Yandex Go](https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md)|Добавили страницу о том, как работать с API Маркета продавцам Market Yandex Go.
||
||[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/deleteCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md)<br><br>[POST v2/campaigns/{campaignId}/price-quarantine/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmCampaignPrices.md)
|Изменили лимиты на количество товаров — 10 000 товаров в минуту.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Изменили лимит на количество товаров — 10 000 товаров в минуту, не более 100 товаров в одном запросе.
||
||[POST v2/businesses/{businessId}/offer-mappings/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffers.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings/archive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/addOffersToArchive.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings/unarchive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffersFromArchive.md)<br><br>[POST v2/businesses/{businessId}/price-quarantine/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmBusinessPrices.md)
|Изменили лимиты на количество товаров — 10 000 товаров в минуту, не более 200 товаров в одном запросе.
||
||[POST v2/businesses/{businessId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getBusinessQuarantineOffers.md)|Изменили лимит на количество товаров — 10 000 товаров в минуту, не более 500 товаров в одном запросе.
||
|#

### 18 марта {#18-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|Добавили типы уведомлений:<ul><li>создание заявки на отмену заказа;</li><li>изменение статуса невыкупа или возврата.</li></ul>
||
|#

### 14 марта {#14-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как изменяются статусы заказов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md)|Рассказали, как изменяются статусы DBS-заказов.
||
||[POST v2/reports/united-returns/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedReturnsReport.md)|Добавили отчет по невыкупам и возвратам.
||
|#

### 7 марта {#07-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|Добавили параметры:<ul><li>`amount` — сумма возврата;</li><li>`partnerCompensationAmount` — компенсация за обратную доставку.</li></ul>


Отметили устаревшими параметры `refundAmount` и `partnerCompensation`. Вместо них используйте `amount` и `partnerCompensationAmount`.
||
|#

### 6 марта {#06-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как подписывать интеграции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/integration-signing.md)|Рассказали, как подписывать интеграции.
||
|#

### 3 марта {#03-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/campaigns/{campaignId}/logins`<br><br>`GET v2/campaigns/by_login/{login}`
|Удалили устаревшие методы.
||
|#

### 27 февраля {#27-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка Экспресс-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/express.md)|Добавили пошаговую инструкцию по обработке Экспресс-заказов.
||
|#

### 20 февраля {#20-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
|Отметили устаревшим параметр `available`. Вместо него используйте методы скрытия товаров с витрины:<br><br>[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)<br><br>[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)<br><br>[POST v2/campaigns/{campaignId}/hidden-offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md)
||
|#

### 13 февраля {#13-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `details`.
||
|#

### 12 февраля {#12-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Отчеты, которые можно выгрузить в формате `FILE` или `CSV`.
|Добавили формат — `JSON`.<br><br>В пояснениях к колонкам появился блок **Название колонки в JSON**.
||
|#

### 10 февраля {#10-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/businesses/{businessId}/offer-mappings/suggestions`|Отметили метод устаревшим.
||
|#

### 7 февраля {#07-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/index.md)|Рассказали о подключении API-уведомлений.
||
||[Формат данных запроса и ответа](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md)|Добавили страницу **Формат данных** API-уведомлений.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Рассказали, как удалить переданные ранее параметры товара — в `deleteParameters` указать значения параметров, которые хотите удалить.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Добавили описание ошибки **Offer at index… cannot have parameter… deleted and set at the same time** — можно передать либо значение параметра в `deleteParameters`, либо соответствующий параметр в `UpdateOfferDTO`.
||
|#

### 5 февраля {#05-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/campaigns/{campaignId}/offers`|Изменили лимит на количество товаров — 100 товаров в час.
||
|#

### 4 февраля {#04-02-25}
#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)|Добавили параметр `statuses` — фильтр для товаров, которые могут участвовать в акции.


Отметили устаревшим параметр `statusType`. Вместо него используйте `statuses`.
||
|#

### 3 февраля {#03-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET campaigns/{campaignId}/feedback/updates`|Удалили устаревший метод.
||
|#

### 22 января {#22-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)<br><br>[Сообщения об ошибках](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/error-codes.md)<br><br>[Получение уведомлений](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)
|Добавили API-уведомления — подключите их и Маркет будет отправлять вам информацию о событиях:<ul><li>создание заказа;</li><li>отмена заказа;</li><li>изменение статуса заказа;</li><li>создание невыкупа или возврата.</li></ul>
||
||[Тестовые заказы](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md)|Уточнили, что если у вас подключены API-уведомления, то Маркет будет отправлять вам запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) с информацией о событии также и по тестовым заказам.
||
|#

### 21 января {#21-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Все методы.
|Указали модели размещения, для которых доступен метод.
||
|#

### 20 января {#20-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/bids/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)|Отметили устаревшим параметр `priceRecommendations`.
||
|#

### 14 января {#14-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Все методы, где передается или возвращается `offset`.
|Удалили устаревший параметр `offset`.
||
|#

## 2024 {#2024}

### 27 декабря {#27-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/campaigns/{campaignId}/logins`<br><br>`GET v2/campaigns/by_login/{login}`
|Отметили методы устаревшими.
||
|#

### 20 декабря {#20-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Сравнение методов по моделям](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md)|Добавили таблицы, где можно посмотреть, для каких моделей работы доступен метод.
||
|#

### 17 декабря {#17-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/models/{modelId}`

`POST v2/models`|Изменили лимиты на количество моделей — 100 000 моделей в час.
||

||`GET v2/models/{modelId}/offers`

`POST v2/models/offers`|Изменили лимиты на количество предложений — 100 000 предложений в час.
||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `id` в `delivery`.
||
|#

### 16 декабря {#16-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Инструкции и методы работы с push-схемой.
|Удалили страницы.<br><br>Не рекомендуем настраивать новые интеграции с push-компонентом.
||
||[Тестовые заказы](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md)|Добавили инструкцию, как работать с тестовыми заказами.
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md)|Добавили параметр `trusted` — проверенный покупатель.<br><br>Если параметр вернулся со значением `true`, Маркет уже проверил покупателя — не звоните ему. Обработайте заказ как обычно и передайте его курьеру или отвезите в ПВЗ.
||
|#

### 10 декабря {#10-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передается или возвращается параметр `vat`.
|Добавили НДС 5% и 7% — значения `VAT_05` и `VAT_07` в параметре `vat`. Они будут применяться для упрощенной системы налогообложения (УСН) с 2025 года.
||
|#

### 9 декабря {#09-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|Добавили параметр `firstVideoAsCover` — возможность использовать первое видео в карточке как видеообложку.
||
|#

### 3 декабря {#03-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)<br><br>[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)
|Добавили формат размещения ярлыков на странице — `A9_HORIZONTALLY`.<br><br>Он доступен только для продавцов из России.
||
|#

### 29 ноября {#29-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)<br><br>[Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)<br><br>[Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)<br><br>[Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md)<br><br>[Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)<br><br>[Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)<br><br>[Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)<br><br>[Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)<br><br>[Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)<br><br>[Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)<br><br>[Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
|Добавили страницы с перечислением всех доступных методов для определенного доступа.
||
||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|Добавили информацию о медиафайле товара — `OfferMediaFileDTO` в `uploadState`.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|Добавили параметры:<ul><li>`commodityCodes` (товарные коды) и его типы `CommodityCodeType`:<ul><li>`CUSTOMS_COMMODITY_CODE` — код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД);</li><li>`IKPU_CODE` — идентификационный код продукции и услуг (ИКПУ) в Узбекистане;</li><li>`PACK_CODE` — код упаковки для ИКПУ.</li></ul></li><li>`language` — язык, на котором принимаются и возвращаются значения в параметрах `name` и `description`.</li></ul>
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Добавили тип ошибки и предупреждения `INVALID_COMMODITY_CODE` — передан некорректный товарный код.
||
||Методы, где передается или возвращается параметр `vat`.
|Добавили НДС 12%, который используется только в Узбекистане, — идентификатор `9` и значение `VAT_12` в параметре `vat`.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|Отметили устаревшим параметр `customsCommodityCode`. Вместо него используйте `commodityCodes` с типом `CUSTOMS_COMMODITY_CODE`.
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)|Отметили устаревшим параметр `url`.
||
|#

### 28 ноября {#28-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передается или возвращается SKU.
|Рассказали, что SKU можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/assortment/operations/edit-sku).
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Добавили возможность изменить категорию товара на Маркете. Для этого передайте идентификатор новой категории в параметре `marketCategoryId` или `categoryId`.<br><br>Также уточнили, что при изменении категории значения общих характеристик для старой и новой категории сохранятся, передавать их не нужно.


Отметили устаревшим параметр `category`. Вместо него используйте `marketCategoryId`.
||
|#

### 26 ноября {#26-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Все методы.
|<b>Для продавцов, которые используют [API-Key-токены](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)</b>: добавили список доступов, один из которых необходим для вызова этого метода.
||
|#

### 22 ноября {#22-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Отчеты, которые можно выгрузить в формате `FILE` или `CSV`.
|Добавили названия колонок, которые есть в отчете.
||
|#

### 20 ноября {#20-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)|Упростили процесс массовой передачи цифровых кодов: каждый товар с уникальным `id` нужно передавать в виде отдельного элемента в массиве `items`, а ключи товара — в массиве `codes`.


Отметили устаревшим параметр `code`. Вместо него используйте `codes`.
||
|#

### 8 ноября {#08-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)<br><br>[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md).</li></ul>
|Добавили формат размещения ярлыков на странице — `A9`.<br><br>Его дизайн отличается от других форматов, а также он доступен только для продавцов из России.
||
|#

### 6 ноября {#06-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|Добавили параметр `subsidies` — начисление баллов, которые используются для уменьшения стоимости размещения, и их списание в случае невыкупа или возврата.


Отметили устаревшими cпособы денежного перевода `CASHBACK`, `MARKETPLACE` и `SPLIT`.
||
|#

### 2 ноября {#02-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передается или возвращается SKU.
|Уточнили, что SKU товара не может состоять только из пробелов и символов табуляции.
||
|#

### 1 ноября {#01-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||—|Название характеристики товара **Цвет** изменилось на **Цвет для фильтра**.
||
|#

### 17 октября {#17-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Пагинация в запросах к API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/pagination.md)|Рассказали о пагинации в запросах.
||
||[Логи запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md)|Рассказали о процессе работы с логами запросов и об уникальном идентификаторе запроса, который поможет быстрее найти логи и пригодится при обращении в поддержку.
||
|#

### 14 октября {#14-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderShipmentBoxes.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)<br><br>[POST v2/campaigns/{campaignId}/orders/{orderId}/delivery/track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md)<br><br>[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)<br><br>
|Изменили лимиты на количество запросов — 100 000 запросов в час.
||
|#

### 8 октября {#08-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Авторизация](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/authorization.md)|Добавили API-Key-токен и рассказали, как с помощью него настроить доступ только к определенным группам методов.<br><br>Описали, чем различаются способы авторизации.
||
|#

### 29 августа {#29-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)
|Параметр `value` в `parameterValues` стал необязательным.<br><br>Рассказали, что нужно передавать:<ul><li>пустое значение, чтобы удалить характеристики, которые заданы в параметрах с типом `string`;</li><li>только те характеристики, значение которых хотите обновить;</li><li>`parameterId` с пустым `value`, чтобы удалить значение заданной характеристики.</li></ul>
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Добавили параметр `onlyPartnerMediaContent` — будут использоваться только переданные вами изображения товаров.<br><br>Если вы указали значение `true` и у товара были изображения от Маркета, они удалятся.
||
|#

### 26 августа {#26-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)<br><br>[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)
|Отметили устаревшими рекомендации `HAS_VIDEO`, `FILTERABLE`, `HAS_DESCRIPTION` и `HAS_BARCODE`.
||
|#

### 21 августа {#21-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/campaigns/{campaignId}/feeds/{feedId}/categories`<br><br>`GET v2/campaigns/{campaignId}/feeds/categories`
|Удалили устаревшие методы.
||
|#

### 15 августа {#15-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET campaigns/{campaignId}/feedback/updates`|Отметили метод устаревшим.
||
|#

### 12 августа {#12-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md) — показывает информацию об акциях Маркета;<br><br>[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md) — показывает список товаров, которые участвуют или могут участвовать в акции;<br><br>[POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md) — добавляет товары в акцию или изменяет их цены;<br><br>[POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md) — удаляет товары из акции.
|Добавили методы работы с акциями.
||
||[Управление акциями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/promos.md)|Рассказали, как управлять акциями.
||
|#

### 9 августа {#09-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Документация API Маркета для продавцов.
|Обновили меню.
||
|#

### 8 августа {#08-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/campaigns/{campaignId}/offer-prices/suggestions`|Отметили метод устаревшим. Вместо него используйте [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md).
|||#

### 5 августа {#05-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/campaigns/{campaignId}/region`|Отметили метод устаревшим. Вместо него используйте [GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md).
||
|#

### 2 августа {#02-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)|Удалили устаревшие параметры `id` и `shopSku`.
||
|#

### 31 июля {#31-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)<br><br>[POST v2/campaigns/{campaignId}/orders/{orderId}/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)
|Методы стали доступны и для модели DBS.
||
|#

### 30 июля {#30-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md) — показывает все отзывы о товарах продавца;<br><br>[POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md) — показывает все комментарии к отзыву;<br><br>[POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) — добавляет комментарий магазина или изменяет комментарий, который магазин оставлял ранее;<br><br>[POST v2/businesses/{businessId}/goods-feedback/skip-reaction](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/skipGoodsFeedbacksReaction.md) — пропускает отзывы;<br><br>[POST v2/businesses/{businessId}/goods-feedback/comments/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/deleteGoodsFeedbackComment.md) — удаляет комментарий магазина.
|Добавили методы работы с отзывами о товарах.
||
||[Отзывы о товарах](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/goods-feedback.md)|Рассказали, как работать с отзывами о товарах.
||
||[POST v2/reports/goods-feedback/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md)|Добавили отчет по отзывам о товарах.
||
|#

### 19 июля {#19-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/updateBusinessPrices/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)
|Повысили верхнее значение для минимальной стоимости товара без скидки до 99% — параметр `discountBase`.
||
||`POST cart`|Отметили устаревшим параметр `subsidy`.
||
|#

### 11 июля {#11-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`DELETE v2/campaigns/{campaignId}/hidden-offers`|Отметили метод устаревшим. Вместо него используйте [POST v2/campaigns/{campaignId}/hidden-offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md).
||
|#

### 9 июля {#09-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST order/accept`<br><br>`POST order/status`<br><br>`POST order/cancellation/notify`
|Отметили устаревшим параметр `subsidy`. Вместо него используйте `subsidies`.
||
|#

### 8 июля {#08-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/ratings/quality](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatings.md) — показывает значение индекса качества магазинов и его составляющие;<br><br>[POST v2/campaigns/{campaignId}/ratings/quality/details](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatingDetails.md) — возвращает список заказов, которые повлияли на индекс качества магазина.
|Добавили методы работы с индексом качества.
||
|#

### 5 июля {#05-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `buyerTotalBeforeDiscount`.
||
|#

### 4 июля {#04-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>`POST order/accept`<br><br>`POST order/status`<br><br>`POST order/cancellation/notify`
|Удалили устаревший параметр `status`.
||
|#

### 28 июня {#28-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)|Теперь с помощью метода вы можете подтверждать ближайшую отгрузку заранее, не только в день отгрузки или накануне.
||
|#

### 27 июня {#27-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/categories/max-sale-quantum](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesMaxSaleQuantum.md)|Добавили новый метод. Он возвращает лимит на установку кванта и минимального количества товаров в заказе.
||
|#

### 26 июня {#26-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|Описали ошибку **Campaign type is not allowed** (метод не поддерживает модель работы вашего магазина), которую Маркет может вернуть в ответе на запрос.
||
|#

### 24 июня {#24-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшими параметры `priceBeforeDiscount`, `buyerItemsTotal` и `buyerTotal`.
||
|#

### 20 июня {#20-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передается или возвращается SKU.
|Изменили формат параметра `ShopSku`. Теперь это может быть любая последовательность длиной до 255 знаков.
||
|#

### 11 июня {#11-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)|Добавили новый метод. Он запускает генерацию PDF-файла с ярлыками для нескольких заказов.
||
|#

### 6 июня {#06-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка заказов с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)|Теперь для работы с цифровыми товарами не нужно настраивать push-компонент API Маркета.
||
|#

### 5 июня {#05-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) — при добавлении товаров в каталог передает их цены, категории на Маркете и характеристики, необходимые для этих категорий;<br><br>[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md) — возвращает категории товаров на Маркете и их характеристики;<br><br>[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md) — возвращает переданные характеристики товаров.
|Обновили работу с категориями Маркета и характеристиками товаров, которые необходимы для этих категорий.
||
||[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)<br><br>[DELETE v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/deleteOutlet.md)
|Добавили описание ошибки **Outlet is disabled for editing by partner** — нельзя изменить информацию или удалить точку продажи магазина.
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|Отметили устаревшим параметр `params`. Вместо него используйте `parameterValues`.
|||
|#

### 4 июня {#04-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)
|Удалили устаревшие параметры `total`, `subsidyTotal` и `totalWithSubsidy`.
||
|#

### 27 мая {#27-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md)|Добавили новый метод. Он возвращает информацию о настройках кабинета.
||
|#

### 24 мая {#24-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Создание и использование OAuth-токена](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md)|Рассказали, что токен нужно будет получать снова, если пользователь, который его создал, выйдет со всех устройств в аккаунте Яндекса.
||
||[POST v2/reports/competitors-position/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateCompetitorsPositionReport.md)|Добавили отчет «Конкурентная позиция».
||
|#

### 17 мая {#17-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)|Удалили устаревший параметр `marketSku`.
||
|#

### 16 мая {#16-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)<br><br>[GET v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPrices.md)
|Удалили устаревший параметр `feed`.
||
|#

### 14 мая {#14-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/shelf-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)|Добавили сводный отчет по полкам.
||
|#

### 8 мая {#08-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|Доработали метод для модели FBY — теперь по нему передается информация по оборачиваемости товаров по каждому складу отдельно, а не общее значение по всем складам.
||
|#

### 24 апреля {#24-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|Метода стал доступен для моделей DBS и Экспресс.
||
||[GET v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPrices.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md).
||
|#

### 19 апреля {#19-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>`POST order/accept`<br><br>`POST order/status`<br><br>`POST order/cancellation/notify`
|Отметили устаревшим параметр `status`.
||
|#

### 18 апреля {#18-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `price`.
||
|#

### 11 апреля {#11-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|Изменили лимит на количество товаров — 5 000 товаров в минуту, не более 500 товаров в одном запросе.
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis`
|Удалили устаревший параметр `feedCategoryId`.
||
|#

### 10 апреля {#10-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)<br><br>[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)
|Отметили устаревшими параметры `dateTimeFrom` и `dateTimeTo`. Вместо них используйте `dateFrom` и `dateTo`.
||
|#

### 9 апреля {#09-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST cart`|Для модели FBS отключили метод.<br><br>Для DBS-магазинов, которые не продают цифровые товары, сделали метод необязательным. Рекомендуем не использовать его и отключить эту возможность в кабинете продавца на Маркете — нажмите на иконку вашего аккаунта → **Настройки**, в меню слева выберите **API и модули** → вкладка **Push API** и активируйте опцию **Не использовать метод POST cart**.<br><br>Если вы продаете цифровые товары, метод остается обязательным.
||
|#

### 29 марта {#29-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/documents/shipment-list/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShipmentListDocumentReport.md)|Добавили лист сборки для отгрузки.
||
||[Обработка FBS-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fbs.md)|Рассказали, как генерировать лист сборки.
||
|#

### 15 марта {#15-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md)|Добавили новый метод. Он возвращает дерево категорий Маркета.
||
||[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)|Добавили новый метод. Он рассчитывает стоимость услуг Маркета для товаров с заданными параметрами.
||
||[POST v2/reports/boost-consolidated/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBoostConsolidatedReport.md)|Добавили отчет по бусту продаж.
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis`
|Отметили устаревшим параметр `feedCategoryId`.
||
|#

### 13 марта {#13-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)<br><br>`DELETE v2/campaigns/{campaignId}/hidden-offers`
|Изменили лимиты на количество товаров — 5 000 товаров в минуту, не более 500 товаров в одном запросе.
||
|#

### 5 марта {#05-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-turnover/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)<br><br>`POST v2/reports/prices/generate`
|Теперь доступны два формата отчета:<ul><li>`FILE` — электронная таблица;</li><li>`CSV` — ZIP-архив с CSV-файлами.</li></ul>
||
|#

### 27 февраля {#27-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)<br><br>[POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)<br><br>[POST v2/reports/goods-movement/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)<br><br>[POST v2/reports/shows-sales/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)
|Теперь доступны два формата отчета:<ul><li>`FILE` — электронная таблица;</li><li>`CSV` — ZIP-архив с CSV-файлами.</li></ul>
||
|#

### 15 февраля {#15-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)|Теперь доступны два формата отчета:<ul><li>`FILE` — электронная таблица;</li><li>`CSV` — ZIP-архив с CSV-файлами.</li></ul>
||
|#

### 14 февраля {#14-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)|Теперь кроме УПД возвращается информация о других документах:<ul><li>УКД;</li><li>товарной накладной;</li><li>счете-фактуре;</li><li>корректировочном счете-фактуре.</li></ul>
||
|#

### 12 февраля {#12-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)|Изменили лимит на количество запросов — 600 запросов в минуту, не более 200 товаров в одном запросе.
||
|#

### 8 февраля {#08-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)
|Отметили устаревшим параметр `phone`.<br><br>Чтобы получить номер телефона покупателя, используйте метод [GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md).
||
|#

### 1 февраля {#01-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)<br><br>[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)
|Теперь доступны два формата отчета:<ul><li>`FILE` — электронная таблица;</li><li>`CSV` — ZIP-архив с CSV-файлами.</li></ul>
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)
|Отметили устаревшим параметр `shopSku`. Вместо него используйте `offerId`.
||
|#

### 22 января {#22-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)|Удалили устаревший параметр `total`.
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)
|Отметили устаревшими параметры `total`, `subsidyTotal` и `totalWithSubsidy`.
||
|#

### 18 января {#18-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)<br><br>[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)<br><br>`DELETE v2/campaigns/{campaignId}/hidden-offers`
|Удалили устаревшие параметры `comment` и `priority`.
||
|#

### 17 января {#17-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)|Удалили устаревший параметр `feed_id`.
||
|#

### 10 января {#10-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)|Изменили лимит на количество товаров — 5 000 товаров в минуту, не более 500 товаров в одном запросе.
||
|#

### 9 января {#09-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)|Добавили возможность получить информацию о покупателе — юридическом лице.
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)|Добавили возможность получить информацию об УПД.
||
||[Обработка заказов от юридических лиц](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/business-info.md)|Добавили пошаговую инструкцию по работе с заказами от юридических лиц.
||
|#

## 2023 {#2023}

### 29 декабря {#29-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|Теперь метод называется **Детальная информация по заказам**.
||
||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)|Добавили отчет по заказам.
||
|#

### 26 декабря {#26-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/index.md)|Рассказали про компоненты API Маркета: pull-компонент (магазин отправляет запросы Маркету) и push-компонент (Маркет отправляет запросы магазину), а также о том, как настроить интеграцию.
||
||[Обработка FBS-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fbs.md)|Добавили пошаговую инструкцию по обработке заказов для модели FBS.
||
||[POST v2/reports/goods-turnover/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)|Добавили отчет по оборачиваемости.
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)|Добавили новый метод. Он передает раскладку по коробкам и коды маркировки, а также изменяет состав заказа.
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderShipmentBoxes.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)
|Отметили методы устравшими для модели FBS. Вместо них используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
||
|#

### 25 декабря {#25-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Управление товарами в архиве](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-archive.md)|Рассказали, как управлять товарами в архиве.
||
|#

### 22 декабря {#22-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/chats/new](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/createChat.md) — создает чат;<br><br>[POST v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendMessageToChat.md) — отправляет сообщение в чат;<br><br>[POST v2/businesses/{businessId}/chats/file/send](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendFileToChat.md) — отправляет файл в чат;<br><br>[POST v2/businesses/{businessId}/chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md) — возвращает список чатов;<br><br>[POST v2/businesses/{businessId}/chats/history](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatHistory.md) — возвращает историю сообщений.
|Добавили методы для общения с покупателями в чатах.
||
||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)|Добавили пошаговую инструкцию по работе с чатами.
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md)|Изменили лимит на количество запросов — 1 000 000 запросов в час.
||
||[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)|Изменили лимит на количеств товаров — 5 000 товаров в минуту, не более 200 товаров в одном запросе.
||
||[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)|Изменили лимит на количеств товаров — 100 000 товаров в минуту.
||
|#

### 8 декабря {#08-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md)|Добавили параметр `shows`, где указано количество показов карточки товара за последние 7 дней.
||
|#

### 6 декабря {#06-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как изменить цены на товары](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md)|Рассказали, как изменить цены в конкретном магазине.
||
|#

### 5 декабря {#05-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Работа с бустом продаж](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/boost.md)|Добавили пошаговую инструкцию по работе с бустом продаж.
||
|#

### 27 ноября {#27-11-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Запуск интеграции на JavaScript](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/quick-start-js.md)|Добавили пошаговую инструкцию по запуску интеграции на JavaScript.
||
|#

### 23 ноября {#23-11-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)
|Добавили методы для получения заказов по модели FBY.
||
|#

### 20 ноября {#20-11-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)<br><br>[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)
|Добавили фильтрацию по нахождению товаров в архиве.
||
|#

### 14 ноября {#14-11-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/archive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/addOffersToArchive.md) — помещает товары в архив;<br><br>[POST v2/businesses/{businessId}/offer-mappings/unarchive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffersFromArchive.md) — восстанавливает товары из архива.
|Добавили методы работы с архивом.
||
|#

### 8 ноября {#08-11-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)<br><br>`DELETE v2/campaigns/{campaignId}/hidden-offers`
|Изменили лимит на количество товаров — 1 000 товаров в минуту, не более 500 товаров в одном запросе.
||
|#

### 3 октября {#03-10-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/shows-sales/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)|Добавили отчет «Аналитика продаж».
||
||Методы работы с заказами с внешних площадок.
|Удалили методы.
||
|#

### 29 сентября {#29-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)<br><br>`GET v2/campaigns/by_login/{login}`
|Методы больше не работают для модели ADV.
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|Добавили новый метод. Он возвращает информацию по остаткам товаров на витрине (для моделей FBY, FBS и Экспресс) и об оборачиваемости товаров (для модели FBY).
||
||[Акт приема-передачи](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md)<br><br>[Фактический акт приема-передачи](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentInboundAct.md)<br><br>[Акт расхождений](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentDiscrepancyAct.md)<br><br>[Транспортная накладная](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentTransportationWaybill.md)
|Добавили методы для получения документов по отгрузкам (FBS).
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)
|Добавили параметры:<ul><li>`rnpt` — регистрационный номер партии товара;</li><li>`gtd` — номер грузовой таможенной декларации.</li></ul>
||
|#

### 28 сентября {#28-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md) — передает категорийные характеристики товаров;<br><br>[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md) — показывает статусы и степень заполненности карточек;<br><br>[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) — возвращает список характеристик с допустимыми значениями для заданной категории.
|Теперь через API можно управлять контентом на карточках товаров.
||
||[PUT v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/setShipmentPalletsCount.md)|Добавили новый метод. Он передает количество упаковок в отгрузке.
||
||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallet/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentPalletLabels.md)|Добавили новый метод. Он возвращает ярлыки для упаковок в отгрузке.
||
|#

### 27 сентября {#27-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/reports/prices/generate`|Добавили отчет «Цены на рынке».
||
|#

### 25 сентября {#25-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md)|Отметили устаревшими параметры `currentPrice` и `lastValidPrice`. Вместо них используйте `params`.
||
|#

### 15 сентября {#15-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)|Добавили отчет по остаткам на складах Маркета (FBY).
||
|#

### 14 сентября {#14-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)|Добавили новый метод. Он возвращает список складов Маркета (FBY) с их идентификаторами.
||
|#

### 7 сентября {#07-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)|Добавили отчет по остаткам на складах магазина (FBS).
||
|#

### 5 сентября {#05-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-movement/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsMovementReport.md)|Добавили отчет по движению товаров.
||
|#

### 4 сентября {#04-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Все методы.
|Теперь в ответе `400 Bad Request` возвращаем название поля, в котором есть ошибка.
||
|#

### 4 августа {#04-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)|Добавили отчет по реализации.
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|Добавили отчет по стоимости услуг.
||
||[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)|Добавили отчет по платежам.
||
|#

### 20 июля {#20-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/bids/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)|Добавили новый метод. Он показывает рекомендованные ставки.
||
|#

### 19 июля {#19-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)|Добавили новый метод. Он показывает список складов и групп складов.
||
|#

### 13 июля {#13-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||—|Изменили формат токена авторизации — вместо 21 знака теперь в нем 48 знаков. Вы можете обновить токен прямо сейчас, чтобы усилить защиту своей интеграции.
||
||Страница **Автоматическое обновление OAuth-токена**.
|Рассказали, как автоматически обновлять OAuth-токен через API сервиса Яндекс ID.
||
||[POST v2/businesses/{businessId}/bids/info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsInfoForBusiness.md)|Добавили новый метод. Он показывает значения ставок для заданных товаров.
||
||[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)|Теперь можно не передавать этапы обработки заказа или причины его отмены — параметр `substatus` в `orders` стал необязательным.
||
|#

### 22 июня {#22-06-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Добавление товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)<br><br>[Изменение цен](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md)
|Большое обновление: расширили возможности API для работы с каталогом.<br><br>Теперь можно:<br><ul><li>работать с общими данными о товарах в кабинете и управлять размещением в отдельных магазинах;</li><li>устанавливать основную цену;</li><li>проверять товары, которые находятся в карантине;</li><li>удалять товары из кабинета и магазина.</li>
||
||`POST v2/campaigns/{campaignId}/offer-mapping-entries/suggestions`<br><br>`POST v2/campaigns/{campaignId}/offer-mapping-entries/updates<br><br>`GET v2/campaigns/{campaignId}/offer-mapping-entries<br><br>`GET v2/campaigns/{campaignId}/offers`<br><br>`GET v2/campaigns/{campaignId}/offers/all`<br><br>`GET v2/campaigns/{campaignId}/feeds`<br><br>`GET v2/campaigns/{campaignId}/feeds/{feedId}`<br><br>`GET v2/campaigns/{campaignId}/feeds/{feedId}/index-logs`<br><br>`POST v2/campaigns/{campaignId}/feeds/{feedId}/params`<br><br>`POST v2/campaigns/{campaignId}/feeds/{feedId}/refresh`<br><br>
|Отметили методы устаревшими.
||
|#

### 30 мая {#30-05-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)|Добавили новый метод. Он передает Маркету коды маркировки «Честного знака» и УИН для ювелирных изделий.
||
||`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis`|Отметили метод устаревшим. Вместо него используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
||
|#

### 14 апреля {#14-04-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, в которых лимиты вычисляются по формуле.
|Изменили лимиты на количество запросов — указываем точное количество запросов в час. Так вам будет легче планировать интеграции, а Маркету — нагрузку.
||
||[Обработка заказов с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)|Рассказали, как работать с цифровыми товарами.
||
|#

### 29 марта {#29-03-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/businesses/{businessId}/bids](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/putBidsForBusiness.md) — создает кампанию, добавляет в нее товары, назначает или изменяет ставки.
|Добавили новый метод. Он помогает управлять бустом продаж.
||
|#

### 17 марта {#17-03-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Документация API Маркета для продавцов.
|Редизайн документации:<ul><li>собрали вместе инструкции для разных моделей;</li><li>осовременили внешний вид;</li><li>добавили пошаговые инструкции для частых сценариев.</li></ul>
||
||[Как пользоваться консолью](https://yandex.ru/dev/market/partner-api/doc/ru/console.md)|Запустили консоль — интерфейс тестирования запросов.
||
|#
