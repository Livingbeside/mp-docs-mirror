---
title: Все обновления
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/changelog/all.md"
fetched_at: "2026-09-16T02:27:04Z"
content_sha: 9a3282bb802f5a9f
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/changelog/all.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/changelog/all.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/changelog/all.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/changelog/all.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Все обновления

{% note tip "Следите за обновлениями документации в [Телеграм-канале](https://t.me/yandex_market_api)." %}

 

{% endnote %}

<!-- source: ru/_auto/changelog/all.md -->
<!-- source: ru/_auto/changelog/all/2026-09-10.md -->
### 10 сентября {#10-09-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md)
|
Добавили в ответ необязательный объект `etrnIdentifier` для создания электронной транспортной накладной.
||
||
[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)<br>[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
|
Добавили опциональный товарный код `OKPD2_CODE` в параметре `commodityCodes` — код по Общероссийскому классификатору продукции по видам экономической деятельности (ОКПД 2).
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-09-10.md -->

<!-- source: ru/_auto/changelog/all/2026-09-09.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-09-09.md -->

<!-- source: ru/_auto/changelog/all/2026-08-26.md -->
### 26 августа {#26-08-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[Коды ошибок](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)
|
Добавили ошибку `Campaign 'campaignId' has no order id 'orderId'` для метода [POST v2/campaigns/{campaignId}/orders/{orderId}/delivery/track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md). Ошибка возвращается, если заказ не принадлежит магазину, указанному в запросе.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-08-26.md -->

<!-- source: ru/_auto/changelog/all/2026-08-04.md -->
### 4 августа {#04-08-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)<br>[POST v3/businesses/{businessId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md)

|
Изменили максимальное значение параметра `limit` с 200 до 100, значение по умолчанию — с 100 до 50. Если передано значение больше 100, оно обрезается до 100, ошибка валидации не возвращается.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-08-04.md -->

<!-- source: ru/_auto/changelog/all/2026-07-29.md -->
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
||
[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)<br>[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)<br>[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)<br>[POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md)

|
Уточнили, когда использовать методы: `updateStocks` актуален только для кабинетов с группами складов; `getPagedWarehouses` актуален для кабинетов с группами складов; `getStocks` и `generateStocksOnWarehousesReport` актуальны для моделей FBY и LaaS, а также для FBS, DBS и Экспресс при наличии групп складов.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-07-29.md -->

<!-- source: ru/_auto/changelog/all/2026-07-16.md -->
### 16 июля {#16-07-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md)
|
В ответе метода добавили объект `taxation` с информацией о налогообложении партнера: ставку НДС `vat`. Поддерживаемые значения ставки: `VAT_22`, `VAT_12`, `VAT_10`, `VAT_07`, `VAT_05` и `NO_VAT`.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-07-16.md -->

<!-- source: ru/_auto/changelog/all/2026-06-22.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-06-22.md -->

<!-- source: ru/_auto/changelog/all/2026-06-17.md -->
### 17 июня {#17-06-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)
|
Добавили новый подстатус заказа `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-06-17.md -->

<!-- source: ru/_auto/changelog/all/2026-06-15.md -->
### 15 июня {#15-06-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)
|
В товары заказа добавили поле `itemStatuses`. В нем возвращается информация о статусах отдельных единиц товара.
||
||
[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md) [POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)
|
Удалили устаревший параметр `quantum` — настройку продажи квантами.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-06-15.md -->

<!-- source: ru/_auto/changelog/all/2026-06-10.md -->
### 10 июня {#10-06-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
|
Добавили новый статус товара: `READY_FOR_PUBLICATION`. Статус устанавливается, если товар **Готов к продаже**, но магазин еще не завершил подключение.
||
||
[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)
|
В информации о стоимости услуг добавили значение `ITEM_BOOKING` — бронирование товара.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-06-10.md -->

<!-- source: ru/_auto/changelog/all/2026-06-02.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-06-02.md -->

<!-- source: ru/_auto/changelog/all/2026-05-28.md -->
### 28 мая {#28-05-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
Методы отчётов
|
Изменили доступы к отчётам: для генерации отчётов достаточно read-only доступов API-Key-токена.
||
||
[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
|
Добавили параметр `fake` в запрос создания заказа. Он позволяет проверить работу магазина и его API на тестовых заказах; такой заказ не будет отгружен и не влияет на остатки.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-05-28.md -->

<!-- source: ru/_auto/changelog/all/2026-05-18.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-05-18.md -->

<!-- source: ru/_auto/changelog/all/2026-05-14.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-05-14.md -->

<!-- source: ru/_auto/changelog/all/2026-05-06.md -->
### 6 мая {#06-05-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)
|
В описание способа денежного перевода (`OrdersStatsPaymentSourceType`) добавлено значение `MARKET_CESSION` — уступка задолженности покупателя.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-05-06.md -->

<!-- source: ru/_auto/changelog/all/2026-04-28.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-04-28.md -->

<!-- source: ru/_auto/changelog/all/2026-04-21.md -->
### 21 апреля {#21-04-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)
|
В информации о стоимости услуг добавили значение `CROSSREGIONAL_DELIVERY` — доставка средней мили.
||
|#
<!-- endsource: ru/_auto/changelog/all/2026-04-21.md -->

<!-- source: ru/_auto/changelog/all/2026-04-17.md -->
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
<!-- endsource: ru/_auto/changelog/all/2026-04-17.md -->
<!-- endsource: ru/_auto/changelog/all.md -->

### 7 апреля {#07-04-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | В описание формата отчёта по услугам Маркета добавили колонку **VOLUME** — объём в литрах в блоке габаритов заказа и товара. ||
|#

### 6 апреля {#06-04-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/closure-documents/detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md) | В описание листов отчёта (операции рекламодателя) добавили колонку **SURFACE** — площадка. ||
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
|| [Уведомления Push API](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md) | Для уведомления о новом сообщении в чате уточнили: при отправке стикера такое уведомление не формируется. ||
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
|| [POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md) | Добавили рекомендацию: перед передачей решения по возврату получите список доступных решений с помощью метода [POST v1/businesses/{businessId}/returns/decisions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnAvailableDecisions.md). ||
|#

### 24 марта {#24-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Как изменяются статусы заказов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md) | Обновили документацию статусной модели DBS-заказов: добавили раздел с подстатусами отмены, которые может передавать магазин, с разбивкой по статусам `PROCESSING`, `DELIVERY` и `PICKUP`. ||
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
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | В документации отчета по услугам Маркета добавили колонку **SURFACE_TYPE** — тип площадки размещения. ||
|#

### 17 марта {#17-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v1/businesses/{businessId}/returns/decisions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnAvailableDecisions.md) | Опубликовали метод получения доступных решений по возврату. Используйте его перед передачей решения по возврату. ||
|| [Уведомления API](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md) | Уточнили, что если один и тот же тип уведомления настроен и для кабинета, и для магазина, Маркет отправляет уведомление только на URL магазина. ||
|#

### 12 марта {#12-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| `GET v2/campaigns/{campaignId}/offer-mapping-entries`

`POST v2/campaigns/{campaignId}/offer-mapping-entries/updates`

`POST v2/campaigns/{campaignId}/offer-mapping-entries/suggestions` | Удалили устаревшие методы работы с каталогом товаров. ||
|| [POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md) | В отчёт по реализации добавили колонку **RECEIPT_LINK** (ссылка на чек). ||
|#

### 11 марта {#11-03-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| `POST v2/businesses/{businessId}/offer-mappings/suggestions` | Удалили устаревший метод подбора карточек на Маркете. ||
|| [POST v2/reports/closure-documents/detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md) | В детализацию закрывающих документов по договору на маркетинг добавили колонку **DEDUCTED_BONUSES** (списано бонусов). ||
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
|| [POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md) | Добавлены новые подтипы заявок на вывоз товаров: на маркетплейс Ozon (`EXTERNAL_WITHDRAW_INT_OZON`) и на маркетплейс Wildberries (`EXTERNAL_WITHDRAW_INT_WB`). ||
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

### 19 февраля {#19-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| Методы с параметром пагинации `limit` | Уточнили актуальные ограничения параметра `limit` для всех методов. Указали, что для некоторых методов значение параметра автоматически уменьшается до максимума вместо ошибки. ||
|#

### 18 февраля {#18-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) | Уточнили описание параметров фильтрации по датам: интервал не более 30 дней, значения по умолчанию, включение или невключение границ в интервал. ||
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
|| [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md) | Изменили лимит: не более 500 запросов в час (ранее 1 000 в минуту). ||
|#

### 12 февраля {#12-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md) | Установили ограничение 200 на максимальный размер параметра `offerIds`. ||
|| [POST v2/businesses/{businessId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getBusinessQuarantineOffers.md)

[POST v2/campaigns/{campaignId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md) | Уменьшили размер параметра `offerIds` до 200. ||
|| `GET v2/campaigns/{campaignId}/offer-mapping-entries`  | Установили ограничение 200 на максимальный размер параметров `offer_id` и `shop_sku`. ||
|#

### 10 февраля {#10-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| Методы, возвращающие информацию о заказах и позициях в заказе | Тип тега товара **TURBO** помечен как устаревший. Рекомендуется не использовать его в логике интеграции. ||
|#

### 5 февраля {#05-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md) | В отчёт по реализации товаров добавили колонки **RECEIPT_ID** (идентификатор чека) и **RECEIPT_DATETIME** (дата и время чека). ||
|| [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) | Уточнили условия отправки уведомления `ORDER_CANCELLATION_REQUEST`: не отправляется, если заказ доставляется в ПВЗ Маркета. ||
|#

### 4 февраля {#04-02-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md) | В ответе удалили поле `pager`. ||
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

### 27 января {#27-01-26}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md) | Дополнили описание поля `name` в схеме `TariffParameterDTO`. Теперь указаны все возможные значения параметров тарифов. ||
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

### 25 декабря {#25-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) | Обновили описание поля `instances` в моделях заказов. Уточнили, как передавать маркировку для разных моделей работы (DBS, FBS, Express, FBY). ||
|#

### 24 декабря {#24-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Управление доступом к API](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md) | Добавили статью «Управление доступом к API». Описали, как проверить доступность API для магазина, причины блокировок и способы восстановления доступа. ||
|| [POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | Добавили лист **Комиссия за продажу** (файл **sale_commission**) и лист **Перевод платежа с 1.01.26** (файл **money_withdraw**). Только для продавцов Market Yandex Go. ||
|#

### 22 декабря {#22-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)

[POST v2/reports/shows-sales/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)

[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)

[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)

[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md) | Уточнили список ошибок: теперь возвращается код 404, если магазин не найден или отсутствуют данные для отчета. ||
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
|| [Отчет по стоимости услуг](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) | На листе **Доставка покупателю** добавили колонку **DELIVERY_TYPE** (Информация об услуге/Способ доставки). ||
|#

### 15 декабря {#15-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Отчет по охватному продвижению](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md) | Добавили лист **Данные по срезам** (файл **banners_statistics_report_by_slices**). ||
|#

### 9 декабря {#09-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Передача значений характеристики](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/parameter-values.md) | Добавили новую страницу о сценариях передачи значений характеристик товаров. Описаны правила работы с одиночными и множественными значениями, справочными и собственными значениями, а также удаление характеристик. ||
|| [Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md) | Обновили страницу ошибок:

* Добавлена колонка «Методы, в которых ошибка встречается» для всех кодов ошибок (400, 401, 403, 404, 405, 415, 420, 423, 503).
* Расширен список ошибок 400 — добавлены разделы: ошибки пагинации, при работе с заказами, отгрузками, ценами, товарами, остатками, точками продаж, категориями, акциями, отчетами, отзывами. ||
|| [Лучшие практики интеграции с API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/best-practices.md) | Добавили новую страницу с лучшими практиками интеграции с API Маркета:

* Рекомендации по устойчивости к изменениям API.
* Работа с лимитами и пагинацией.
* Обработка ошибок и повторные запросы.
* Рекомендации по безопасности интеграции.
* Сценарные практики для типовых задач. ||
|#

### 8 декабря {#08-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md) | Уточнили работу с электронной подписью актов приёма-передачи: если параметр `signatory` передан, акт подписывается электронной подписью и печатать его не требуется. ||
|| [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md) | Уточнили описание фильтра `PromoParticipationType`:

* Без фильтра возвращаются акции, в которых продавец участвует или может принять участие.
* При фильтре `PARTICIPATING_NOW` возвращаются только текущие акции, в которых продавец уже участвует (без возможности принять участие). ||
|| [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md) | Добавили информацию о сроке действия ссылки на отчёт: ссылка актуальна 60 минут с момента получения ответа. Рекомендация — скачивать отчёт сразу после получения ссылки. ||
|| [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)

[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)

[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md) | Уточнили, что идентификаторы товаров (`offerId`/`sku`) должны быть уникальны в рамках одного запроса. ||
|#

### 1 декабря {#01-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Создание и использование API-Key-токена](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Уточнили срок действия токена: он не истекает автоматически; активен, пока вы его не удалите. ||
|#

### 29 ноября {#29-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md) | Уточнили, что для модели FBS в ответе может вернуться не только партнерский склад, но и склад возвратов Маркета. ||
|| [Получение заказов: опрос API или уведомления](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/orders-receive.md) | Добавили общую инструкцию по получению информации о заказах. ||
|#

### 26 ноября {#26-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Отчет по стоимости услуг](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md) |
Обновили состав колонок отчета:

* Переименовали колонку **Пользователь заплатил** → **Покупатель заплатил**;
* Добавили колонки **PROMO_AMOUNT**, **CUSTOMER_BONUS_AMOUNT**, **DISCOUNT**.||
|#

### 25 ноября {#25-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md) | Уточнили формат передачи ключей: для одного `id` передавайте один элемент и массив `codes` по количеству ключей ||
|#

 ### 24 ноября {#24-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md) | Уточнили, как правильно обрабатывать чаты через [API-уведомления](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md): по **CHAT_CREATED** сразу сохраните контекст чата в своей системе и больше его не запрашивайте; по **CHAT_MESSAGE_SENT** запрашивайте только сообщение; если чата нет в вашей базе, один раз получите его методом [GET v2/businesses/{businessId}/chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md) и сохраните ||
|#

### 21 ноября {#21-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Коды ошибок](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md) | Добавили описание ошибки **The method is deprecated and is occasionally forbidden. Please stop using it**. Ошибка возвращается интеграциям, которые продолжают использовать устаревшие методы API. ||
|#

### 20 ноября {#20-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [Коды ошибок](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md) | Добавили описание ошибки 499 (**Client Closed Request**). Ошибка возвращается, когда клиент закрывает соединение до завершения обработки запроса на стороне Маркета. ||
|#

### 18 ноября {#18-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md) | Добавили параметр `withRecommendations` (по умолчанию `false`). При значении `true` в ответе возвращаются поля `recommendations` (список рекомендаций к заполнению карточки) и `averageContentRating` (средний рейтинг карточки). ||
|| [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) | Добавили новый метод. Он возвращает информацию о заказах в кабинете. ||
|#

### 17 ноября {#17-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
|| [PUT v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/setShipmentPalletsCount.md) | Уточнили документацию по передаче количества упаковок для доверительной приемки. ||
|#

### 5 ноября {#05-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md)|Уточнили условия подтверждения отгрузки: действие доступно только после формирования отгрузки. До наступления времени подтверждения метод возвращает код `400` с ошибкой **Cutoff time for shipments has not been reached yet**.||
||[GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)|Уточнили, что подтверждение отгрузки и формирование акта доступно только после формирования отгрузки, иначе метод вернет код `400` и ошибку **Closest shipment for reception transfer act generation not found**.||
|#

### 2 ноября {#02-11-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)|Уточнили семантику ответа: при наличии `results.errors` — статус `ERROR` и изменения не применяются; при отсутствии ошибок и наличии `results.warnings` — статус `OK`, изменения применяются.||
|#
### 29 октября {#29-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)|Добавили коды ошибок `PRICE_TOO_BIG` и `OLD_PRICE_TOO_BIG` — возвращаются, если цена по акции или зачеркнутая цена превышает максимально допустимое значение.||
|#

### 27 октября {#27-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)|

Уточнили логику работы фильтров отчета по платежам: в отчет попадают все платежи, которые были выплачены и начислены в выбранный период.

Если перевод выполнен в один день (например, 31 августа) и зачислен в другой (например, 1 сентября), он попадет в отчет за оба месяца.||

||[POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)|В метод проверки статусов кодов маркировки добавили коды системы «Честный ЗНАК».

Уточнили, что неуспешный статус проверки кодов маркировки в системе [«Честный ЗНАК»](https://честныйзнак.рф/) не блокирует перевод заказа в статус `READY_TO_SHIP` до 1 декабря 2025 года.
||
|#

### 24 октября {#24-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md)|Добавили подтип запроса `WITHDRAW_AUTO_UTILIZATION` — автоматическая утилизация изъятия по истечении срока хранения.||
|#

### 23 октября {#23-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)|

Рассказали, что в штрихкодах могут быть только символы ASCII.

Поэтому, если во внешнем идентификаторе вы используете другие символы, на ярлыке в штрихкоде будет отображаться идентификатор заказа Маркета.||

||[Вызов методов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md)<br><br>[Как работать с API Маркета продавцам Market Yandex Go](https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md)
|Рассказали, что в запросах нужно указывать номер версии метода. Его можно найти на странице каждого метода.<br><br>Скоро мы отключим возможность работать с запросами без указания версии.
||
|#

### 15 октября {#15-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|

Уточнили, что параметр `hasStocks` передается только для модели FBY.||
|#

### 14 октября {#14-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|

Уточнили, что параметр `partnerWarehouseId` возвращается только для модели FBY.||

||[POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md)|

Изменили название колонок:

* **Ошибки** на **Критичные ошибки**;
* **Предупреждения** на **Некритичные ошибки**.||
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


### 3 октября {#03-10-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Рассказали, что параметр `payments` может возвращаться пустым, если заказ:

* только начали обрабатывать (даже если он оплачен);
* отменили до момента передачи в доставку.

Окончательная информация о расчетах по заказу появится после его финальной обработки (например, после перехода в статус `DELIVERED`).||

||[POST v2/businesses/{businessId}/chats/new](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/createChat.md)|

Рассказали, что, если чат с покупателем уже есть, метод не создаст новый, а вернет информацию о существующем.||
|#


### 26 сентября {#26-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)|Исправили описание статуса `INCORRECT_PERSONAL_DATA`.||

||[POST v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/updateOutletLicenses.md)|

Добавили ограничение для параметра `licenses` — количество лицензий не может превышать 500.||

||[GET v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md)

[DELETE v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/deleteOutletLicenses.md)|

Добавили ограничение для параметра `ids` — количество идентификаторов лицензий не может превышать 500.||

||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)

[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Добавили параметр `groupId` — идентификатор группы товаров. Он будет совпадать у тех товаров, которые объединены в одну группу.||
|#


### 19 сентября {#19-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md)

[POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md)|

Уточнили, что текст комментария в параметре `text` не должен:

* содержать контакты магазина и ссылки на сторонние ресурсы (сайты, кроме Маркета) — иначе вернется ошибка **Illegal url in comment text**;
* дублировать существующий комментарий — иначе вернется ошибка **Duplicate comment**.||

||[POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md)|Добавили параметр `offerIds` — фильтр по идентификатору товара. Теперь можно передать идентификаторы товаров, чтобы вернулись отзывы только о них.||
|#

### 18 сентября {#18-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|Рассказали, что, если магазин не укладывается в десятисекундный таймаут или возвращает ошибку, Маркет повторяет проблемный запрос, но перестает присылать другие уведомления до тех пор, пока не получит подходящий ответ.||
|#

### 17 сентября {#17-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md)|Добавили фильтр по типу контекста чата — `contextTypes`.||

||[POST v2/businesses/{businessId}/chats/history](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatHistory.md)

[GET v2/businesses/{businessId}/chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md)

[POST v2/businesses/{businessId}/chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md)|

Добавили параметры:

* `customer` — информация о покупателе;
* `campaignId` — идентификатор кампании.||

||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)|

Рассказали, какие бывают типы чатов:

* `ORDER` — по заказам;
* `RETURN` — по возвратам (FBY, FBS и Экспресс);
* `DIRECT` — чат, который начинает покупатель, если у него есть вопросы по товару.||
|#

### 16 сентября {#16-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|

Добавили этап обработки заказа `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)|

Изменили [формат регулярного выражения](*cis-regular-value), которому должно соответствовать значение параметра `cis`.||
|#

### 10 сентября {#10-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|На листе **Платное хранение с 01.06.22** (файл **paid_storage_after_01-06-22**) добавили колонки:

* **SHOP_SKU** (Ваш SKU);
* **OFFER_NAME** (Название товара).||
|#

### 9 сентября {#09-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)|Добавили фильтр по идентификатору кампании — `campaignId`. Если его передать, в ответе вернутся все склады, которые доступны для указанного магазина.||
|#

### 8 сентября {#08-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|Теперь доплата за вес товара при доставке указывается не за 0,1 кг, а за 1 кг. Поэтому в отчете изменили название колонки **TARIFF_FOR_WEIGHT** (**Тариф за 0,1 кг**) на **Тариф за 1 кг**.||
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

### 4 сентября {#04-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||

||[POST v2/businesses/{businessId}/chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md)

[GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md)|

Уточнили, что в параметре `limit` нужно передавать значение не больше 20.||

||[PUT v2/campaigns/{campaignId}/first-mile/shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)|

Уточнили, что в параметре `limit` нужно передавать значение не больше 30.||

||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Описали ошибку **Limit exceeded** — превышено ограничение на количество значений на одной странице (параметр `limit`).||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)|

Добавили параметр `pickupTillDate` — дата, до которой можно забрать товар.||
|#

### 2 сентября {#02-09-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)|Уточнили, что в параметре `limit` нужно передавать значение не больше 100.||
|#

### 29 августа {#29-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)

`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis` |

Уточнили, какому регулярному выражению должно соответствовать значение параметра `cis`.||
|#

### 28 августа {#28-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|На листе **Размещение товаров на витрине** (файл **placement**) в колонке **Уменьшение (скидка) и увеличение стоимости услуги** → **Отмены по вине продавца, отгрузка или доставка не вовремя** добавили колонку **DAYS_OF_DELAY** — опоздание при отгрузке или доставке, дни.||
|#

### 27 августа {#27-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)|Уточнили, что нельзя передавать внешний идентификатор заказа больше одного раза.||
||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)

[Изменение категорийных характеристик](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/content-change.md)|
Рассказали, что в методе [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) для характеристик, у которых есть единицы измерения, в параметре `unit` возвращаются:

* допустимые значения (`units`);

* значение по умолчанию (`defaultUnitId`).

В методе [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) можно изменить идентификатор единицы измерения характеристик — параметр `unitId` в `parameterValues`. Если его не передать, будут использованы единицы измерения по умолчанию (`defaultUnitId`).||
|#

### 25 августа {#25-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|Добавили описание ошибок:

* **Access denied for campaign 'campaignId' because it is not active** — метод недоступен из-за [неактивности магазина](*inactiv-campaign).

* **Restrict access for business 'businessId' because it is not active** — метод недоступен из-за [неактивности кабинета](*inactiv-business).||

||[GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)

[GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md)|

Добавили параметр `apiAvailability` — возможность использовать API.||

||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|

Уточнили, что в параметре `limit` нужно передавать значение не больше 200.||
|#

### 22 августа {#22-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Главные обновления](https://yandex.ru/dev/market/partner-api/doc/ru/changelog/main.md)

[Устаревшие методы и параметры](https://yandex.ru/dev/market/partner-api/doc/ru/changelog/deprecated.md)

[Все обновления](https://yandex.ru/dev/market/partner-api/doc/ru/changelog/all.md)|

Разделили страницу **История обновления API**.||
|#

### 21 августа {#21-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|Добавили тип уведомления — изменение заказа.
||
||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|Изменили частоту, с которой Маркет повторяет запросы, если магазин не укладывается в десятисекундный таймаут или возвращает ошибку.
||
|#

### 20 августа {#20-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|Добавили лист **Приемка поставки** (файл **goods_acceptance**).||
|#

### 19 августа {#19-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)<br><br>[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)<br><br>[Как изменяются статусы возвратов для моделей FBY, FBS и Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fby-fbs-express-return-status-model.md)
|Рассказали, что FBY-магазины могут принимать решения по возвратам и создавать чаты с покупателями, чтобы уточнять детали возврата.
||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)|Добавили параметр `shipmentStatuses` — фильтр по логистическим статусам невыкупов и возвратов.||

||[Создание и использование API-Key-токена](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)|Рассказали, что максимальное количество токенов для кабинета — 30.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Уточнили, что значение в параметре `weightDimensions` должно быть больше 0.||
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
||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)

[Изменение категорийных характеристик](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/content-change.md)

[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)

[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)

[POST v2/categories/max-sale-quantum](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesMaxSaleQuantum.md)|

Уточнили, что используются листовые категории — те, у которых нет дочерних.||

||[GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md)|Из модели `RegionDTO` удалили параметр `children`.

Добавили его в новой модели `RegionWithChildrenDTO`.||
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

### 6 августа {#06-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|

Добавили параметр `hasStocks` — фильтр по наличию товаров.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Удалили значение параметра `FIRST_VIDEO_AS_COVER`.||
|#

### 5 августа {#05-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Уточнили, что в параметре `limit` нужно передавать значение не больше 50.||

||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

На листе **Платное хранение с 01.06.22** (файл **paid_storage_after_01-06-22**) добавили колонки:

* **LENGTH_PRODUCT_M** (Информация об услуге/Длина единицы товара, м);

* **WIDTH_PRODUCT_M** (Информация об услуге/Ширина единицы товара, м);

* **HEIGHT_PRODUCT_M** (Информация об услуге/Высота единицы товара, м);

* **COUNT_PRODUCT_UNIT** (Информация об услуге/Количество единиц товара, шт.);

* **VOLUME_UNITS_OF_GOODS** (Информация об услуге/Объём всех единиц товара, кубометры);

* **MEASUREMENT_UNIT** (Информация об услуге/Единица измерения).||
|#

### 4 августа {#04-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/shows-boost/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsBoostReport.md)

[POST v2/reports/banners-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md)

[POST v2/reports/shelf-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)
|Удалили колонку **AVERAGE_BID**.||
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
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|

Удалили значения `USER_REFUSED_TO_PROVIDE_PERSONAL_DATA` и `RECEIVED_ON_DISTRIBUTION_CENTER` в `substatus`.||

||[GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)<br><br>[GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)
|Отметили устаревшими параметры `shopOutletId` и `workingTime`. Вместо них используйте `shopOutletCode` и `workingSchedule`.
||
|#

### 30 июля {#30-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Уточнили, что в параметре `offerMappings` нужно передавать не больше 100 товаров.||
|#

### 29 июля {#29-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)|

Рассказали, что для характеристик типа `ENUM` нужно передавать вместе параметры `value` и `valueId`.||
|#

### 28 июля {#28-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка заказов с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)|

Рассказали:

* как понять, что в заказе есть цифровые товары;

* что Маркет отправит ключи покупателю в чат, если не получилось доставить письмо.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Удалили параметр `cofinancePrice` и значение `COFINANCE_PRICE` в `deleteParameters`.||

||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Удалили параметр `cofinancePrice`.||

||[POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md)|

Удалили фильтр `FieldStateType` и параметры `cofinancePriceFilter` и `cofinancePrice`.||
|#

### 26 июля {#26-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)|

Удалили параметр `promocodeParams`.||

||[POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)|

Удалили предупреждение `PROMOCODE_PRICE_MORE_THAN_MAX_FAIR_PRICE`.||
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

||[Заявки на поставку товаров на склад, вывоз или утилизацию](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/supplies.md)

[POST v2/campaigns/{campaignId}/supply-requests](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequests.md)|

Уточнили, что родительские и дочерние заявки теперь создаются и для поставок на склад хранения.||
|#

### 22 июля {#22-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)|

Метод стал доступен для продавцов Market Yandex Go.||
|#

### 21 июля {#21-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)

[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Рассказали, что произойдет, если не передать параметры `marketCategoryId` или `parameterValues`.||
|#

### 17 июля {#17-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Уточнили, что вознаграждение и цена товара в параметрах `subsidies`, `price`, `costPerItem` и `total` включает НДС.||
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

### 15 июля {#15-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)|

Добавили примеры для передачи нескольких товаров с уникальными или одинаковыми идентификаторами.||

||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)|

Рассказали, как в кабинете продавца на Маркете узнать источник и время обновления информации.||

||[Список методов, используемых в модели FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md)

[Список методов, используемых в модели FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md)

[Список методов, используемых в модели Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md)

[Список методов, используемых в модели DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md)|

Рассказали о моделях работы на Маркете.||
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

||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/transportation-waybill](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentTransportationWaybill.md)|

Уточнили, что транспортная накладная возвращается только для тех отгрузок, в которых Маркет забирает товары с вашего склада.||

||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)|

Добавили значение параметра `availableActions` — `DOWNLOAD_TRANSPORTATION_WAYBILL` (скачать транспортную накладную).||
|#

### 10 июля {#10-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)|

Рассказали, что характеристики, которые являются особенностями варианта товара, могут зависеть от кабинета.

Чтобы узнать их, в методе [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) передайте параметр `businessId`.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[Тестовые заказы](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md)|

Уточнили, что информация по тестовым заказам по умолчанию не возвращается.||

||[Формат данных запроса и ответа](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/data-format.md)|

Добавили пример тела запроса и ответа.||
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

### 8 июля {#08-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

В ответе добавили параметр `externalOrderId` — внешний идентификатор заказа в системе магазина.||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Добавили параметры:

* `estate` — владение;

* `building` — строение.||
|#

### 7 июля {#07-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)|

Рассказали, какие теги можно использовать для форматирования текста в инструкция по активации.||
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
||[POST v2/reports/shows-sales/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShowsSalesReport.md)|

Удалили колонку **MAX_VISIBILITY_INDEX** — максимальный индекс видимости.||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md).
||
|#

### 25 июня {#25-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md)|

Уточнили, что в ответе не возвращаются данные об акциях, которые создал продавец.||
||[PUT v2/businesses/{businessId}/bids](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/putBidsForBusiness.md)|

Уточнили, что данные обновляются не мгновенно.||
|#

### 23 июня {#23-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Логи запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md)|Рассказали о виджете с информацией об ошибках в запросах и ответах и фильтре **Интеграция**.
||
||[POST v2/reports/documents/shipment-list/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShipmentListDocumentReport.md)|

Уточнили, что в методе нужно обязательно передавать `shipmentId` или `orderIds`.||
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

### 30 мая {#30-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/jewelry-fiscal/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateJewelryFiscalReport.md)|

Добавили колонку **BUYER_PRICE** — цена товара.||
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

### 20 мая {#20-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Указали максимальное количество характеристик (параметр `params` в `UpdateOfferDTO`) — 600.

Указали максимальную длину:

* названия характеристики (параметр `name` в `OfferParamDTO`) — 200 символов;

* ссылки на инструкцию (параметр `url` в `OfferManualDTO`) — 512 символов;

* названия инструкции (параметр `title` в `OfferManualDTO`) — 200 символов;

* комментария (параметр `comment` в `TimePeriodDTO`) — 500 символов.||
|#

### 16 мая {#16-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка FBS-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fbs.md)

[Обработка Экспресс-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/express.md)|

Рассказали, что на шаге проверки новых заказов нужно использовать диапазон дат доставки — параметры `fromDate` и `toDate`. А для получения информации о заказах, в которых были изменения, — фильтры `updatedAtFrom` и `updatedAtTo`.||

||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|

Изменили частоту, с которой Маркет повторяет запрос, если магазин не укладывается в десятисекундный таймаут или на запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) возвращает ошибку, кроме `400`. Теперь эта частота — каждая минута в течение первого часа.||
|#

### 13 мая {#13-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передается или возвращается `campaignId`.|

В описании параметра `campaignId` (идентификатор кампании) рассказали:

* как его узнать;
* что его не следует путать с идентификатором магазина, который указан в кабинете продавца на Маркете рядом с названием магазина и в некоторых отчетах.||
||[Вызов методов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md)|

Рассказали о параметрах пути (path parameters) и параметрах запроса (query parameters).||
|#

### 6 мая {#06-05-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/banners-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateBannersStatisticsReport.md)|

Добавили отчет по охватному продвижению.
||
||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|

Уточнили, что уведомления, связанные с заказами, приходят и по FBY-заказам, если они настроены для кабинета. ||
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

### 29 апреля {#29-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|

Добавили фильтр по идентификатору склада — параметр `stocksWarehouseId`.||

||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)|

Добавили фильтр `MINIMUM_FOR_PROMOS` — товары с установленным минимумом по цене для акций, который соответствует порогу `maxPromoPrice`.||
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
||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|

Рассказали, какие роли нужны для настройки API-уведомлений.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Отметили устаревшим параметр `cofinancePrice`.
||
|#

### 23 апреля {#23-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md)|

Удалили фильтр `recommendedCofinancePriceFilter`.

Удалили параметр `recommendedCofinancePrice` в ответе.||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)
|

Удалили причину отмены заказа `DELIVERY_DATE_CHANGED_TOO_MUCH` — заказ перенесен на слишком много дней.||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)
|

Добавили причину отмены заказа `TOO_LONG_DELIVERY` — заказ доставляется слишком долго.||
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
||[Чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md)|

Обновили инструкцию, как проверить, есть ли новые чаты или сообщения.||

||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|

Рассказали, какие уведомления приходят только для кабинета, а какие — для кабинета и магазина.||

||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Добавили описание ошибки **The method is not supported for Market Yandex Go sellers** — метод недоступен для продавцов Market Yandex Go.||
|#

### 21 апреля {#21-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

Добавили лист **Нанесение знака маркировки** (файл **product_marking**).

Изменили название колонок:

* **SERVICE_DATE** → **SERVICE_DATE_TIME**;

* **serviceDate** → **serviceDateTime**;

* **Информация об услуге/Дата оказания услуги** → **Информация об услуге/Дата и время оказания услуги**.||
|#

### 16 апреля {#16-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)|

Удалили параметр `PageNum`.||

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
||[POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md)|

Уточнили, что не возвращаются отзывы, которые удалили покупатели или Маркет.

Добавили параметр `feedbackIds` — идентификаторы отзывов.Не используйте его одновременно с другими фильтрами.||

||[POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md)|

Уточнили, что не возвращаются комментарии к удаленным отзывам и те, которые удалили пользователи или Маркет.

Параметр `feedbackId` стал необязательным.

Добавили параметр `commentIds` — идентификаторы комментариев. Не используйте его одновременно с другими фильтрами.||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
|

Добавили параметр `countryCode` — страна производства.||

||[Обработка заказов от юридических лиц](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/business-info.md)|

Описали особенности работы с заказами от юридических лиц.||

||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Добавили описание ошибки **String (value) is not a valid country code according to ISO 3166-1 alpha-2** — недопустимый код страны. Укажите код страны в формате ISO 3166-1 alpha-2.||
|#

### 8 апреля {#08-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Невыкупы и возвраты](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/returns.md)|Добавили пошаговую инструкцию, как работать с невыкупами и возвратами.
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Уточнили, что заказ может перейти в статус `PARTIALLY_DELIVERED` не сразу.

Если в доставленном заказе был невыкуп, статус изменится только после получения заказа на складе Маркета.||
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
||[Обработка FBS-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fbs.md)|

Рассказали, что с помощью метода [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md) вы можете не только подтвердить отгрузку, но и подписать и получить электронный акт приема-передачи.||

||[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)

[Передача остатков через API](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/stocks.md)|

Рассказали, как передавать остатки для группы складов — только для **одного любого склада**. Информация для остальных складов в этой группе обновится автоматически.||

||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

Изменили название колонки **Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Скидка (гр.37=гр.35\*гр.36)/37**.

Теперь она называется **Уменьшение (скидка) и увеличение  стоимости услуги/Вызовы и награды/Скидка с учётом минимального тарифа (гр.37=гр.35\*гр.36)/37**.||
|#

### 3 апреля {#03-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Запуск интеграции на Node.js Express](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/quick-start-notifications-node-express.md)|

Добавили страницу о том, как настроить интеграцию для работы с уведомлениями на Node.js Express.||

||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)|

Добавили статусы товара в ответе:

* `RENEWED` — успешно перенесен из предыдущей акции «Бестселлеры Маркета»;

* `RENEW_FAILED` — не получилось перенести из предыдущей акции «Бестселлеры Маркета».||
|#

### 2 апреля {#02-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||—|Опубликовали спецификацию OpenAPI API-уведомлений. Она доступна на [GitHub](https://github.com/yandex-market/yandex-market-notification-api).||
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
||[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getCampaignOffers.md)<br><br>[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)<br><br>[POST v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)
|

Удалили идентификатор НДС 12%.

Уточнили, что для продавцов Market Yandex Go недоступна передача и получение НДС.||

||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|

Добавили параметр `updatedAt` — дата и время изменения статуса невыкупа или возврата.||

||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md).
||
|#

### 28 марта {#28-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)|

Уточнили диапазоны IP-адресов, которые использует Маркет.||
|#

### 27 марта {#27-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)

[POST v2/reports/goods-feedback/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsFeedbackReport.md)|

Отметили недоступными для продавцов Market Yandex Go.||
|#

### 25 марта {#25-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/goods-feedback/comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md)|

В ответе добавили параметр `feedbackId` — идентификатор отзыва.||

||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Добавили описание ошибки **Business is in migration** — в кабинете происходят миграции магазинов.||
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
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Изменили лимит на количество товаров — 10 000 товаров в минуту, не более 100 товаров в одном запросе.


Удалили тип товарного кода `PACK_CODE`.||

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

||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)

[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)|

Добавили примеры ярлыков для продавцов Market Yandex Go.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Рассказали, как передавать название и описание товара для продавцов Market Yandex Go.||
|#

### 17 марта {#17-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как изменяются статусы заказов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|

Добавили описание подстатуса `PICKUP_EXPIRED` — закончился срок хранения заказа в ПВЗ.||
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
||[Рекомендации Маркета по карточкам](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/recommendations.md)|

Вынесли в отдельную инструкцию информацию, как пользоваться рекомендациями Маркета.||

||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)|

Рассказали, как:

* [изменить категории товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md#change-category);
* [изменить характеристики товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md#change-parameters);
* [удалить характеристики товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md#delete);
* [объединить товары на карточке](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md#combine-variants).||
||Документация API Маркета для продавцов.
|

Методы работы с карточками товаров теперь находятся в разделе **Товары**.||
|#

### 13 марта {#13-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/shelf-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)|

Изменили название колонки **Фактические расходы, ₽**. Теперь она называется **Фактические расходы (с НДС), ₽**.||
|#

### 12 марта {#12-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Уточнили, что код `403` приходит не только, когда не сработал токен, но может означать и другую ошибку доступа.

Добавили описание ошибок:

* **Contact not found for login 'login' and campaignId 'campaignId'** — не найдена учетная запись пользователя, логин которой передан для подписи электронного акта приема-передачи;

* **Contacts with available roles for signing not found for login 'login'** — учетная запись пользователя, логин которой передан для подписи электронного акта приема-передачи, не обладает необходимыми доступами.||

||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|

Рассказали, что Маркет может отправлять несколько уведомлений по одному и тому же событию. В некоторых случаях это нормальное поведение. Актуальным считайте более позднее время события.||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)|

Уточнили, что параметр `refundStatus` актуален только для возвратов (`returnType=RETURN`).||
|#

### 11 марта {#11-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы работы с кодами маркировки товаров.|

Уточнили, что для продавцов Market Yandex Go параметры `cis` и `hasCis` актуальны и для системы [«ASL BELGISI»](https://aslbelgisi.uz).||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Уточнили описание параметров:

* `supplierShipmentDateTo` равен `supplierShipmentDateFrom` + сутки, если промежуток времени между ними меньше суток;

* `toDate` равен `fromDate` + сутки, если промежуток времени между ними меньше суток.||
|#

### 10 марта {#10-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md)

[GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)|

Добавили параметр `signatory` — логин пользователя в Яндекс ID, от имени которого будет подписываться электронный акт приема-передачи.||

||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)

[PUT v2/campaigns/{campaignId}/first-mile/shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)|

В ответе добавили параметр `signature` — информация о подписи акта приема-передачи.||
|#

### 7 марта {#07-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|

Добавили параметры:<ul><li>`amount` — сумма возврата;</li><li>`partnerCompensationAmount` — компенсация за обратную доставку.</li></ul>


Отметили устаревшими параметры `refundAmount` и `partnerCompensation`. Вместо них используйте `amount` и `partnerCompensationAmount`.
||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)|

Рассказали, что с помощью [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) можно проверить, какие категорийные характеристики доступны для заданной категории, и получить их настройки.||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|

Уточнили, что в ответе параметр `fastReturn` приходит только для возвратов (`returnType=RETURN`).||
|#

### 6 марта {#06-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как подписывать интеграции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/integration-signing.md)|Рассказали, как подписывать интеграции.
||
|#

### 5 марта {#05-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)

[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Добавили параметр `currency` — валюта, в которой указано значение тарифа.||

||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)|

Удалили колонки **COUNT** (Информация о заказах/Количество) и **TRANSFERRED_FOR_DELIVERY** (Информация о заказах/Передано в доставку).||

||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)|

Добавили колонки:

* **TRANSFERRED_FOR_DELIVERY** (Информация о заказах/Передано в доставку);

* **DELIVERED_OR_RETURNED** (Информация о заказах/Доставлено или возвращено);

* **DELIVERY_DATE** (Информация о заказах/Дата доставки заказа).||
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

### 1 марта {#01-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)|

Уточнили, что условия участия в акциях могут меняться, кроме параметров `price` и `promoPrice`.||
|#

### 27 февраля {#27-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка Экспресс-заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/express.md)|Добавили пошаговую инструкцию по обработке Экспресс-заказов.
||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Уточнили, что значение `MERCHANT_TO_COURIER` в параметре `eacType` временно не возвращается.||

||`POST v2/reports/prices/generate`|

Уточнили, что информация возвращается только по 50 000 товаров.

Если у вас их больше, используйте фильтры.||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)|

Добавили значение `UNKNOWN` (неизвестный статус) в параметре `shipmentStatus`.||
|#

### 26 февраля {#26-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)|Удалили колонку **ORDER_STATUS** (Заказы/Статус заказа).||
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

### 19 февраля {#19-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)|

Добавили причины отмены заказа (параметр `substatus`):

* `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз;

* `DELIVERY_DATE_CHANGED_TOO_MUCH` — заказ перенесен на слишком много дней.||
|#

### 18 февраля {#18-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы получения отчетов.|

Рассказали, что структура и содержание отчетов могут изменяться без предварительного уведомления. Это связано с внутренними процессами Маркета.||
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

### 11 февраля {#11-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Удалили значение `DELIVERY_TO_CUSTOMER_RETURN` в параметре `TariffType`.||
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

||[Сообщения об ошибках](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/error-codes.md)|

Добавили описание ошибок:

* **CANT_GET_RESPONSE (UNSUPPORTED_MEDIA_TYPE)** — в заголовке ответа магазина указан формат данных, отличный от `application/json`;

* **INVALID_RESPONSE (INVALID_DATA)** — в теле ответа магазина переданы некорректные данные или их недостаточно.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Рассказали, как удалить переданные ранее параметры товара — в `deleteParameters` указать значения параметров, которые хотите удалить.

Добавили описание ошибки **Offer at index… cannot have parameter… deleted and set at the same time** — можно передать либо значение параметра в `deleteParameters`, либо соответствующий параметр в `UpdateOfferDTO`.
||

||[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)|

Уточнили описание метода — возвращает список характеристик с допустимыми значениями для заданной **листовой** категории — той, у которой нет дочерних категорий.||
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

||[POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md)|

В ответе добавили параметр `renewalEnabled` — включен ли автоматический перенос ассортимента между акциями «Бестселлеры Маркета».||

||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)|

Уточнили описание параметра `contentRating` — рейтинг карточки.

Добавили параметры в ответе:

* `averageContentRating` — средний рейтинг карточки у товаров той категории, которая указана в `marketCategoryId`;

* `contentRatingStatus` — статус вычисления рейтинга карточки и рекомендаций;

* `remainingRatingPoints` — максимальное количество баллов рейтинга карточки, которые можно получить за выполнение рекомендаций.||

||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)

[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)|

Уточнили описание рекомендации `VIDEO_COUNT` — добавьте хотя бы одно видео.||

||[GET v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md)|

Добавили описание статусов проверки лицензии:

* `REVOKE` — лицензия отозвана службой качества;

* `DONT_WANT` — не проверяется;

* `FAIL_MANUAL` — лицензия не прошла проверку службы качества.||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|

В детали причин возврата добавили описание значения `UNKNOWN` — детали причины не указаны.

В решение по возврату добавили описание значения `UNKNOWN` — не указано.

Удалили тип логистической точки `UNKNOWN`.||

||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

В тип товара добавили описание значения `EXPIRED` — товар с истекшим сроком годности.

Удалили типы товара:

* `FREEZE`

* `AVAILABLE`

* `QUARANTINE`

* `UTILIZATION`

В тип оплаты заказа добавили значение `UNKNOWN` — неизвестный тип оплаты.

Удалили типы оплаты:

* `CREDIT`

* `TINKOFF_CREDIT`||
|#

### 3 февраля {#03-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET campaigns/{campaignId}/feedback/updates`|Удалили устаревший метод.
||
|#

### 31 января {#31-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

На листе **Поставка через транзитный склад** добавили колонки:

* **SERVICES_COLUMN_MANY_WAREHOUSES_SUPPLY** (Информация об услуге/Поставка для нескольких складов);

* **SERVICES_COLUMN_VDC_DIRECTIONS_COUNT** (Информация об услуге/Количество доехавших направлений в поставке).||
|#

### 30 января {#30-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)|

Уточнили, что разрешенное количество символов в параметрах `name` (название интеграции) и `version` (версия интеграции) — от 1 до 100.||
|#

### 29 января {#29-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Уточнили, что параметр `payments` может вернуться пустым, если нет данных о денежных переводах.

Удалили значение `UNKNOWN` в параметре `type`.||

||[POST v2/businesses/{businessId}/offer-mappings/archive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/addOffersToArchive.md)|

В параметре `error` добавили описание значения `UNKNOWN` — неизвестная причина ошибки.||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|

Добавили описание статусов передачи возврата:

* `EXPIRED` — покупатель не принес товар на возврат вовремя;

* `NOT_IN_DEMAND` — возврат не забрали с почты;

* `READY_FOR_EXPROPRIATION` — товары в возврате направлены на перепродажу;

* `RECEIVED_FOR_EXPROPRIATION` — товары в возврате приняты для перепродажи.

Добавили описание логистических статусов конкретных товаров:

* `CREATED` — возврат создан;

* `RECEIVED` — возврат принят у отправителя;

* `IN_TRANSIT` — возврат в пути;

* `READY_FOR_PICKUP` — возврат готов к выдаче магазину;

* `PICKED` — возврат выдан магазину;

* `RECEIVED_ON_FULFILLMENT` — возврат принят на складе Маркета;

* `CANCELLED` — возврат отменен;

* `LOST` — возврат утерян;

* `UTILIZED` — возврат утилизирован;

* `PREPARED_FOR_UTILIZATION` — возврат готов к утилизации;

* `EXPROPRIATED` — товары в возврате направлены на перепродажу;

* `NOT_IN_DEMAND` — возврат не забрали с почты.||
|#

### 28 января {#28-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Изменили описание ошибки **Token is invalid** на **OAuth token is invalid**.

Добавили описание ошибки **OAuth token is invalid (account has been globally logged out)** — пользователь воспользовался функцией **Выйти везде** в Яндекс ID.||

||[Создание и использование OAuth-токена](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md)|

Уточнили случаи, когда токен нужно получать снова.||

||[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)|

На листе **Отчёт о платежах** добавили колонку **BONUS_ACCOUNT_YEAR_MONTH** (Информация о платежах/Расчётный период премии за участие в совместных акциях).||

||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

Изменили название листа **Пуши**. Теперь он называется **Пуш-уведомления**.||
|#

### 27 января {#27-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Добавили описание значения `DEFAULT` — передайте его в параметре `type` для товара, у которого установлен особый тип и вы хотите его убрать.||

||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)

[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)|

Добавили рекомендацию по заполнению параметра `FIRST_VIDEO_SIZE` — замените первое видео на видео высокого качества.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)|

Добавили описание причин, почему обновился состав заказа:

* `PARTNER_REQUESTED_REMOVE` — магазин удалил товар;

* `USER_REQUESTED_REMOVE` — покупатель попросил удалить товар.||
|#

### 24 января {#24-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Уточнили описание параметров:

* `updateFrom` и `updateTo` — начальная или конечная дата периода, за который были изменения в заказе. Например, статуса или информации о платежах.

* `items` — информация о доставке заказа добавляется отдельным элементом в массиве `items` — параметр `offerName` со значением `Доставка`.||
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
||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)

[POST v2/reports/goods-realization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsRealizationReport.md)|

В названиях колонок в XLSX уточнили, что информация указывается в штуках.||
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
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md)|

Отметили обязательным параметр `code` — код для подтверждения ЭАПП.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderShipmentBoxes.md)|

Уточнили описание кода ошибки `400`.

Из тела запроса удалили параметр `id`.||

||[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

Добавили пояснение к колонкам на листе **Пуши**.||

||[POST v2/businesses/{businessId}/bids/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)|Отметили устаревшим параметр `priceRecommendations`.
||
|#

### 17 января {#17-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)

[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)|

Добавили пример ярлыка формата `A9_HORIZONTALLY` и уточнили описание значения `A4`.||

||Методы, в ответе которых возвращается параметр `status`.|

Добавили описание возможных значений параметра `status`.||

||`GET v2/campaigns/{campaignId}/offer-mapping-entries`|

Добавили описание возможных значений параметра `mapping_kind`.||

||[GET v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md)

[POST v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/updateOutletLicenses.md)|

В параметре `LicenseType` добавили описание значения `UNKNOWN` — неизвестный тип лицензии.||

||`GET v2/campaigns/{campaignId}/feeds/{feedId}/index-logs`|

Удалили значение `NOT_INDEXED` в параметре `FeedIndexLogsErrorType`.||
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

### 10 января {#10-01-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Уточнили принцип работы параметра `onlyPartnerMediaContent` — при передаче значения `true` из товаров удаляются **данные, которые добавил Маркет**.||
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

### 26 декабря {#26-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Обработка заказов от юридических лиц](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/business-info.md)|

Рассказали, как определить, что заказ пришел от юридического лица.||
|#

### 24 декабря {#24-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md)|

Описали решения по товару в возврате:

* `REFUND_MONEY` — вернуть деньги за товар;

* `REFUND_MONEY_INCLUDING_SHIPMENT` — вернуть деньги за товар и обратную пересылку;

* `REPAIR` — магазин устранит недостатки товара;

* `REPLACE` — магазин заменит товар;

* `SEND_TO_EXAMINATION` — магазин отправит товар на экспертизу;

* `DECLINE_REFUND` — не возвращать деньги;

* `OTHER_DECISION` — другое решение.||
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

||[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)|

Уточнили, что ответ `200` не значит, что ключи переданы покупателю.

Если письмо с ключами удалось доставить, Маркет переведет заказ в финальный статус `DELIVERED`.||

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

### 13 декабря {#13-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/reports/prices/generate`|Уточнили, что данные в этом отчете постоянно обновляются, поэтому информация в нем и в кабинете продавца на Маркете на странице **Цены** может отличаться.||

||[Пагинация в запросах к API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/pagination.md)|

Рассказали, что в некоторых методах доступны оба вида пагинации — с идентификатором страницы (`page_token`) и с ее номером (`page`).

В таких случаях используйте идентификатор страницы.||
|#

### 12 декабря {#12-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как изменить цены на товары](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md)

[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)|

Уточнили, что метод [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) доступен, только если в кабинете продавца на Маркете есть возможность установить уникальные цены в отдельных магазинах.

Как это проверить — в методе [POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md) в параметре `onlyDefaultPrice` возвращается значение `false`.||
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

### 2 декабря {#02-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Уточнили, что в параметре `language` по умолчанию выбран русский язык — `RU`.||

||Методы работы с заказами.|

Стали обязательными параметры:

* в **OrderItemPromoDTO** — `subsidy`;

* в **OrderItemDetailDTO** — `itemCount`, `itemStatus` и `updateDate`;

* в **OrderSubsidyDTO** — `type` и `amount`;

* в **OrderItemSubsidyDTO** — `type` и `amount`;

* в **OrderItemDTO** — `id`, `offerId`, `offerName`, `price`, `buyerPrice`, `buyerPriceBeforeDiscount`, `count` и `vat`;

* в **OrderDeliveryDatesDTO** — `fromDate`;

* в **OrderTrackDTO** — `deliveryServiceId`;

* в **OrderParcelBoxDTO** — `id` и `fulfilmentId`;

* в **OrderDeliveryDTO** — `type`, `serviceName`, `deliveryPartnerType`, `dates` и `deliveryServiceId`;

* в **OrderBuyerBasicInfoDTO** — `type`;

* в **OrderDTO** — `id`, `status`, `substatus`, `creationDate`, `currency`, `itemsTotal`, `deliveryTotal`, `buyerItemsTotalBeforeDiscount`, `paymentType`, `paymentMethod`, `fake`,`delivery`, `buyer` и `taxSystem`;

* в **RegionDTO** — `id`.||
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


Отметили устаревшим параметр `customsCommodityCode`. Вместо него используйте `commodityCodes` с типом `CUSTOMS_COMMODITY_CODE`.
||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Добавили тип ошибки и предупреждения `INVALID_COMMODITY_CODE` — передан некорректный товарный код.
||
||Методы, где передается или возвращается параметр `vat`.
|Добавили НДС 12%, который используется только в Узбекистане, — идентификатор `9` и значение `VAT_12` в параметре `vat`.
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
||[POST v2/businesses/{businessId}/goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md)|Параметр `orderId` (идентификатор заказа на Маркете) стал необязательным.||
|#

### 25 ноября {#25-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Как изменить цены на товары](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md)

[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)|

Рассказали, что передавать НДС нужно с помощью параметра `vat` в методе [POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md).||
||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)

[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)

[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

Добавили параметр `language` — язык отчета.||
|#

### 22 ноября {#22-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)|

Описали ошибки с кодом `401`:

* **Api-Key token format invalid** — неправильный формат API-Key-токена;

* **Api-Key token length invalid** — неправильная длина API-Key-токена;

* **Api-Key token prefix invalid** — неправильный префикс API-Key-токена.||

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

### 19 ноября {#19-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|

Рассказали, что для модели FBY информация об остатках может возвращаться с нескольких складов Маркета, у которых будут разные `warehouseId`.

[Идентификаторы фулфилмент-складов Маркета](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)||
|#

### 18 ноября {#18-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)

[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)|

Добавили описание ошибок с кодом `400`:

* **datediff-is-to-big-local** — при доставке по своему региону разница между максимальным и минимальным сроком доставки не должна превышать двух дней;

* **datediff-is-to-big-remote** — при доставке в другие регионы разница между максимальным и минимальным сроком доставки не должна превышать четырех дней;

* **datediff-is-to-big-long-period** — при доставке в другие регионы, где минимальный срок доставки больше 18 дней, разница между максимальным и минимальным сроком доставки не должна превышать минимальный срок.||
|#

### 15 ноября {#15-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/bids/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)|

Добавили параметр `benefits` — список доступных субсидий.||

||[POST v2/businesses/{businessId}/bids/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)|

Добавили типы дополнительных инструментов продвижения:

* `BESTS` — участие в акции «Бестселлеры Маркета»;

* `SPLIT_0_0_4` — возможность оплаты со Сплитом сроком на 4 месяца;

* `SPLIT_0_0_6` — возможность оплаты со Сплитом сроком на 6 месяцев;

* `SPLIT_0_0_12` — возможность оплаты со Сплитом сроком на 12 месяцев;

* `MARKET_SUBSIDY_1_4` — скидка от Маркета от 1 до 4%;

* `MARKET_SUBSIDY_5_9` — скидка от Маркета от 5 до 9%;

* `MARKET_SUBSIDY_10` — скидка от Маркета от 10%.||
|#

### 14 ноября {#14-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)|

Рассказали, что процент выполнения указывается для некоторых рекомендаций:

* `PICTURE_COUNT`

* `VIDEO_COUNT`

* `MAIN`

* `ADDITIONAL`

* `DISTINCTIVE`||
|#

### 13 ноября {#13-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)|

Рассказали, что, если хотя бы по одному товару есть ошибка, информация в каталоге не обновится по всем переданным товарам.||
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
|||#

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

### 18 октября {#18-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)|

Рассказали, что параметров `logisticPickupPoint`, `shipmentRecipientType` и `shipmentStatus` может не быть в ответе в случае возврата:

* С опцией **Быстрый возврат денег за дешевый брак**, когда товар остается у покупателя (`fastReturn=true`).

* По заказу от бизнеса, если:

    * статус возврата `STARTED_BY_USER` или `WAITING_FOR_DECISION`;
    * возврат отменен до передачи товара.||
|#

### 17 октября {#17-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Пагинация в запросах к API Яндекс Маркета для продавцов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/pagination.md)|Рассказали о пагинации в запросах.
||
||[Логи запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md)|Рассказали о процессе работы с логами запросов и об уникальном идентификаторе запроса, который поможет быстрее найти логи и пригодится при обращении в поддержку.
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Рассказали, что информация по созданным и обновленным заказам может появляться с задержкой до 40 минут.||
|#

### 16 октября {#16-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST cart`|

Рассказали, что если в параметре `outlets` указать несуществующие идентификаторы пунктов самовывоза, то опция доставки проигнорируется и ее идентификатор не придет в методе `POST order/accept`.||
|#

### 15 октября {#15-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Добавили тип товара `ALCOHOL` — алкоголь.||
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

### 11 октября {#11-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/united-netting/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedNettingReport.md)

[POST v2/reports/united-marketplace-services/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)|

Изменили максимальный период для параметров `dateTimeTo` и `dateTo`. Теперь он составляет 3 месяца.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили тип ошибок **LOCKED_DIMENSIONS** — переданы габариты упаковки, которые нельзя изменить.||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

`POST order/accept`

`POST order/status`

`POST order/cancellation/notify`|

Удалили способы отгрузки `MARKET_PARTNER_OUTLET` и `DROPOFF`.||
|#

### 10 октября {#10-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md)|

Добавили параметр `sortingType` (тип сортировки ярлыков в файле) и его значения:

* `SORT_BY_GIVEN_ORDER` — ярлыки заказов будут расположены в том же порядке, в каком были переданы идентификаторы заказов в запросе;

* `SORT_BY_ORDER_CREATED_AT` — ярлыки будут расположены в соответствии с датой создания заказа с группировкой по магазинам.||
|#

### 9 октября {#09-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Добавили вид маркировки товара `CIS_OPTIONAL` — идентификатор единицы товара в системе «Честный ЗНАК», который необязателен для заполнения, но в ближайшее время потребуется его передача.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)|

Добавили тип ошибок **INVALID_CATEGORY** — указана нелистовая категория.||
|#

### 8 октября {#08-10-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Авторизация](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/authorization.md)|Добавили API-Key-токен и рассказали, как с помощью него настроить доступ только к определенным группам методов.<br><br>Описали, чем различаются способы авторизации.
||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Для параметра `tags` (признаки товара) добавили значения:

* `ULTIMA` — премиум-товар;

* `SAFE_TAG` — товар с защитной меткой;

* `TURBO` — товар, который быстро раскупают.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили фильтрацию заказов по дате оформления — параметры `fromDate` и `toDate`.||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)|

Каждому невыкупу стали присваивать свой идентификатор.||
|#

### 19 сентября {#19-09-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)

[POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)

[POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md)|

Добавили описание ошибки **Promo has ended** — акция закончилась.||
|#

### 4 сентября {#04-09-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/goods-turnover/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md)|

Добавили параметр `date` — дата, за которую нужно рассчитать оборачиваемость.||
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
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили параметры `page_token` и `limit` для навигации по страницам результатов.||

||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)

[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)|

Рассказали, что рекомендации по дополнению или замене контента не возвращаются для карточек, которые заполнены Маркетом или содержат бывшие в употреблении товары.||

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

### 16 августа {#16-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)

[PUT v2/campaigns/{campaignId}/first-mile/shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)|

Добавили параметр `cancelledOrders` — возвращать ли отмененные заказы.||
|#

### 15 августа {#15-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET campaigns/{campaignId}/feedback/updates`|Отметили метод устаревшим.
||
|#

### 13 августа {#13-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили тип ошибки `INVALID_PICKER_URL` — передана ссылка на изображение для миниатюры, которой нет в переданных ссылках на изображение товара.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Добавили параметр `updatedAt` — дата и время последнего обновления заказа.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Рассказали, как найти заказы, в которых Маркет перенес дату отгрузки.||
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
||[POST v2/reports/united-orders/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedOrdersReport.md)|

Добавили параметр `promoId` — идентификатор акции, товары из которой нужны в отчете.||
|#

### 9 августа {#09-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Документация API Маркета для продавцов.
|Обновили меню.
||
||[Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)

[Управление товарами в архиве](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-archive.md)

[Как изменить цены на товары](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md)|

Разделили пошаговую инструкцию «Управление каталогом».||
|#

### 8 августа {#08-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/campaigns/{campaignId}/offer-prices/suggestions`|

Удалили тип цены `MAX_DISCOUNT_BASE`, `MARKET_OUTLIER_PRICE` и `MAX_DISCOUNT_PRICE`

Отметили метод устаревшим. Вместо него используйте [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md).
||
|#

### 5 августа {#05-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Рассказали в описание метода, что параметр `offerId` должен быть уникальным для всех товаров, которые вы передаете.||

||`GET v2/campaigns/{campaignId}/region`|Отметили метод устаревшим. Вместо него используйте [GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md).
||
|#

### 2 августа {#02-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили способ оплаты заказа `BOUND_CARD_ON_DELIVERY` — привязанной картой при получении.||

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

||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Добавили статус товара в магазине `ARCHIVED` — в архиве.||
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

### 29 июля {#29-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md)

[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)

[GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

`GET v2/models/{modelId}/offers`

`GET v2/campaigns/by_login/{login}`|

Указали верхнее ограничение для передачи номера страницы результатов — параметр `page`.

Теперь нельзя указывать номер страницы больше 10 000.||
|#

### 24 июля {#24-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Страница **Автоматическое обновление OAuth-токена**.
|

Рассказали, что токен может не обновиться, если оставшийся срок его жизни достаточно длительный.

Срок действия OAuth-токена — год. Его нужно обновлять до истечения этого срока. Например, раз в девять месяцев.||
|#

### 19 июля {#19-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Повысили верхнее значение для минимальной стоимости товара без скидки до 99% — параметр `discountBase`.
|[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)<br><br>[POST v2/businesses/{businessId}/updateBusinessPrices/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)
||
||[POST v2/reports/competitors-position/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateCompetitorsPositionReport.md)|

Добавили новую величину: если в столбце **POSITION** указано `-1` — значит, в этот день не было заказов с товарами в указанной категории.||

||`POST v2/campaigns/{campaignId}/offer-prices/suggestions`|

Уточнили, что метод доступен только продавцам, устанавливающим цены в рублях.||

||[POST v2/campaigns/{campaignId}/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/deleteCampaignOffers.md)|

Дополнили причины, по которым не получается удалить товары: они не найдены или хранятся на складе Маркета.||

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
||[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)|

Убрали верхнее ограничение для передачи минимального количества единиц товара в заказе — параметр `minQuantity`.||

||`POST order/accept`<br><br>`POST order/status`<br><br>`POST order/cancellation/notify`
|

Добавили параметр `subsidies` — список субсидий по типам.

Отметили устаревшим параметр `subsidy`. Вместо него используйте `subsidies`.
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
||[POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md)|

Добавили параметр `currency` — валюта в кабинете продавца на Маркете.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `buyerTotalBeforeDiscount`.
||
|#

### 4 июля {#04-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/first-mile/shipments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/searchShipments.md)|

Параметры `dateFrom` и `dateTo` стали обязательными.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>`POST order/accept`<br><br>`POST order/status`<br><br>`POST order/cancellation/notify`
|Удалили устаревший параметр `status`.
||
|#

### 3 июля {#03-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Добавили услугу `ILLIQUID_GOODS_SALE` — вознаграждение за продажу невывезенных товаров.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)|

Добавили подстатус заказа `TECHNICAL_ERROR` — техническая ошибка на стороне Маркета.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Теперь можно передавать до 30 ссылок на изображения товара.||
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

### 21 июня {#21-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md)|

Добавили подстатус генерации отчета `RESOURCE_NOT_FOUND` — для такого отчета не удалось найти часть сущностей.

Возвращается, если при генерации PDF-файла с ярлыками в методе [POST v2/reports/documents/labels/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMassOrderLabelsReport.md) не удалось найти часть заказов.||
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

### 18 июня {#18-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Разделили тип субсидий на `OrderSubsidyType` и `OrderItemSubsidyType`.||
|#

### 13 июня {#13-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

Удалили тип субсидии `SPASIBO`.||
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
||
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

### 3 июня {#03-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)|

Добавили примеры запросов для передачи информации о распределении товаров.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили описание ошибок:

* **CATEGORY_MISMATCH** — указана категория, которая не совпадает с категорией товара;

* **INVALID_GROUP_ID_LENGTH** — в названии превышено допустимое значение символов — 255;

* **INVALID_GROUP_ID_CHARACTERS** — переданы недопустимые символы.||
|#

### 31 мая {#31-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили описание ошибки **EMPTY_MARKET_CATEGORY** — не указана категория Маркета при передаче характеристик категории.||
|#

### 29 мая {#29-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Рассказали, как передавать значения одного параметра, если у товара их несколько.||

||[POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)|

Добавили параметр `parameterValues` — список характеристик с их значениями.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили параметр `basicPrice` — цена товара.||
|#

### 27 мая {#27-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md)|Добавили новый метод. Он возвращает информацию о настройках кабинета.
||

||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)|

Добавили параметр `fastReturn` — используется ли опция **Быстрый возврат денег за дешевый брак**.||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|Рассказали, когда надо передавать параметр `realDeliveryDate`.||
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

### 23 мая {#23-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)|

Добавили типы ошибок:

* **INVALID_GROUP_ID_LENGTH** — в названии превышено допустимое значение символов — 255;

* **INVALID_GROUP_ID_CHARACTERS** — переданы недопустимые символы.||
|#

### 22 мая {#22-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)|

Добавили статус возврата денег `COMPLETE_WITHOUT_REFUND` — возврат денег не требуется.||
|#

### 21 мая {#21-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Добавили дополнительные тарифы к услуге размещения:

* `CANCELLED_ORDER_FEE_QI` — отмена заказа по вине продавца;

* `LATE_ORDER_EXECUTION_FEE_QI` — несвоевременная отгрузка или доставка.||
|#

### 20 мая {#20-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)|

Добавили `PROCESSING` к списку статусов заказа, в которых можно получить информацию о покупателе — юридическом лице.||
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
||[POST v2/reports/shelf-statistics/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateShelfsStatisticsReport.md)|

Добавили сводный отчет по полкам.
||
||[POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md)|

Добавили параметр `language` — язык категорий.||
|#

### 13 мая {#13-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST order/status`

`POST order/accept`|

Добавили параметр `shopOrderId` — идентификатор заказа в магазине.||
|#

### 8 мая {#08-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocks.md)|Доработали метод для модели FBY — теперь по нему передается информация по оборачиваемости товаров по каждому складу отдельно, а не общее значение по всем складам.
||

||[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)|

Добавили параметр для расчета стоимости услуг `quantity` — квант продажи.||

||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили:

* параметр `parameterValues` — список характеристик с их значениями;
* ошибки и предупреждения, которые касаются переданных характеристик.||
|#

### 3 мая {#03-05-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Добавили параметр `marketCategoryId` — идентификатор категории на Маркете, к которой вы относите свой товар.|
|
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

### 23 апреля {#23-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/chats/history](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatHistory.md)|

В ответе добавили параметр `orderId` — идентификатор заказа.||
|#

### 19 апреля {#19-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)|

Указали максимальное количество идентификаторов заказов (параметр `orderIds`) — 50.||

||[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)|

Рассказали, как сбросить ранее установленные значения кванта.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>`POST order/accept`<br><br>`POST order/status`<br><br>`POST order/cancellation/notify`
|

Указали неактуальные типы скидки — параметр `type`.

Отметили устаревшим параметр `status`.
||

||`POST cart`|Указали неактуальные типы скидки — параметр `type`.
||
|#

### 18 апреля {#18-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[Передача остатков через API](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/stocks.md)|

Рассказали, как можно проверить работоспособность интеграции по передаче остатков.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшим параметр `price`.
||
|#

### 17 апреля {#17-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили фильтрацию заказов по типу покупателя — параметр `buyerType`.||
|#

### 16 апреля {#16-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md)|

В ответе добавили параметр `orderId` — идентификатор заказа.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили фильтрацию по идентификаторам заказов — параметр `orderIds`.||
|#

### 11 апреля {#11-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Изменили лимит на количество товаров — 5 000 товаров в минуту, не более 500 товаров в одном запросе.
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

||[POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)|

В ответе добавили параметр `units` — информация о допустимых единицах измерения.

Их вы можете указывать при заполнении карточек товаров — метод [POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md).||
|#

### 4 апреля {#04-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md)|

Удалили параметр `orderIds`.||
|#

### 3 апреля {#03-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)

[GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)|

Удалили параметр `additional`.||
|#

### 2 апреля {#02-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md)|

Добавили параметр `parameters` — детали расчета конкретной услуги Маркета.||
|#

### 1 апреля {#01-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Увеличили до 6 максимальное количество ссылок на видео товара — параметр `videos`.||
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

||[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)|

Параметр `updatedAt` стал необязательным.

Если его не передать, будет использоваться текущее время.

Удалили параметр `warehouseId`. Идентификатор склада будет определяться по `campaignId`.

Удалили параметр `type`. Единственно возможное значение `FIT` будет передаваться автоматически.||
|#

### 22 марта {#22-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

В ответе добавили параметр `address` — адрес пункта выдачи.||

||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|Удалили услугу `FULFILLMENT`.||
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

### 14 марта {#14-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)

[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Добавили параметр `manuals` — список инструкций по использованию товара.||
|#

### 13 марта {#13-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)<br><br>`DELETE v2/campaigns/{campaignId}/hidden-offers`
|Изменили лимиты на количество товаров — 5 000 товаров в минуту, не более 500 товаров в одном запросе.
||
||`POST cart`|Увеличили максимальное количество дат в параметре `dates` до 7.||
|#

### 12 марта {#12-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|Удалили услуги `CANCELLED_ORDER_FEE` и `LATE_ORDER_EXECUTION_FEE`.||
|#

### 8 марта {#08-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Добавили услуги:

* `EXPRESS_CANCELLED_BY_PARTNER` — отмена заказа с экспресс-доставкой;

* `DELIVERY_TO_CUSTOMER_RETURN` — возврат доставляемого товара на склад;

* `CROSSBORDER_DELIVERY` — доставка из-за рубежа;

* `INTAKE_SORTING_BULKY_CARGO` — сортировка заказов с крупногабаритными товарами, которые Маркет забрал со склада продавца;

* `INTAKE_SORTING_SMALL_GOODS` — сортировка заказов с малогабаритными товарами, которые Маркет забрал со склада продавца;

* `INTAKE_SORTING_DAILY` — организация забора заказов со склада продавца;

* `FF_STORAGE_BILLING` — хранения товаров на складе.||
|#

### 6 марта {#06-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Добавили значение `NOT_SPECIFIED` (не выбран) для параметров:

* `type` — тип уценки;

* `quality` — внешний вид товара.||
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

### 4 марта {#04-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/reports/stocks-on-warehouses/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)|

Добавили фильтры по категориям на Маркете и по наличию остатков для всех моделей кроме FBY.||
|#

### 1 марта {#01-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Удалили статус заказа `REJECTED`.||
|#

### 29 февраля {#29-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)

[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)

[GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)

[GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)|

Удалили параметр `emails`.||

||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Добавили услуги:

* `CROSSREGIONAL_DELIVERY_RETURN` — доставка невыкупов и возвратов;

* `MIDDLE_MILE` — средняя миля;

* `LATE_ORDER_EXECUTION_FEE` — отгрузка или доставка не вовремя;

* `RETURN_PROCESSING` — обработка невыкупов и возвратов.||
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

### 26 февраля {#26-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)|

Добавили параметр `express` — возможна ли доставка по модели Экспресс.||
|#

### 22 февраля {#22-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Добавили тип оплаты `SPLIT` — оплата картой по частям (Сплит).||
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
||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)

[GET v2/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getFulfillmentWarehouses.md)|

В ответе добавили параметр `address` — адрес склада.||
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
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Добавили услугу для FBY-магазинов `RETURN_PROCESSING` — обработка заказов на складе.||

||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)
|Отметили устаревшим параметр `phone`.<br><br>Чтобы получить номер телефона покупателя, используйте метод [GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md).
||
|#

### 7 февраля {#07-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)

[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)

[GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)

[GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)|

Удалили параметр `cost`.||

||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

`POST cancellation/notify`|

Параметр `email` (адрес электронной почты покупателя) больше не возвращается в ответах.||
|#

### 2 февраля {#02-02-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)|

В ответе добавили параметр `boxId` — идентификатор коробки.||
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
|

Удалили параметр `feedId`.


Отметили устаревшим параметр `shopSku`. Вместо него используйте `offerId`.
||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)|Удалили параметр `feedId`.
||
|#

### 31 января {#31-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)

[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md)

[DELETE v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/deleteOutlet.md)

[GET v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md)

[GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)|

Стали необязательными параметрами:

* `name` — название точки продаж;

* `phones` — номера телефонов точки продаж;

* `address` — адрес точки продаж;

* `regionId` — идентификатор региона;

* `workingSchedule` — список режимов работы точки продаж;

* `scheduleItems` — список расписаний работы точки продаж;

* `startDay` — день недели, в который точка продаж начинает работать;

* `endDay` — день недели, в который точка продаж заканчивает работать;

* `startTime` — время начала работы точки продаж;

* `endTime` — время окончания работы точки продаж;

* `cost` — стоимость самовывоза из точки продаж;

* `type` — тип точки продаж.||
|#

### 30 января {#30-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)|

Указали размеры ярлыков, которые возвращаются в PDF-файле.||
|#

### 29 января {#29-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)

[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)

`DELETE v2/campaigns/{campaignId}/hidden-offers`|

Удалили параметры `ttlInHours` и `feedId`.||
|#

### 25 января {#25-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)

[POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md)

`DELETE v2/campaigns/{campaignId}/hidden-offers`|

Удалили параметр `marketSku`.||
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
||Методы, где передается название товара.|

Увеличили максимальное количество символов в названии товара до 256.||

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
||[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)|

С 1 марта 2024 года изменится лимит на количество запросов в методе — 100 000 товаров в минуту, не более 500 товаров в одном запросе.||
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
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|
Добавили услугу `INTAKE_SORTING` — организация забора заказов со склада продавца.||
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

### 15 ноября {#15-11-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||Методы, где передается SKU.|

Теперь в идентификаторе товара в магазине (SKU) можно использовать букву ё.||
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

### 23 октября {#23-10-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md)|

Увеличили количество регионов в ответе на одной странице до 20 — параметр `limit`.

Добавили возможность указать идентификатор страницы c результатами — параметр `page_token`.||
|#

### 19 октября {#19-10-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили фильтрацию по дате и времени обновления заказа.||

||[POST v2/businesses/{businessId}/offers/recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md)|

Добавили параметр `price` — цена товара в каталоге.||
|#

### 18 октября {#18-10-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили способ оплаты заказа `B2B_ACCOUNT_POSTPAYMENT` — заказ оплачивает организация после доставки.||
|#

### 14 октября {#14-10-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Уточнили, что параметр `warehouses` не будет возвращаться, если товара нет ни на одном складе.||
|#

### 5 октября {#05-10-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Добавили статусы:

* `PARTIALLY_DELIVERED` — заказ частично доставлен;
* `LOST` — заказ утерян.||
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
||[POST v2/businesses/{businessId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getBusinessQuarantineOffers.md)|

Добавили параметр `verdicts` — причины попадания товара в карантин, где `type` — это тип карантина, а `params` — цена, из-за которой товар попал в карантин, и значения для сравнения.||

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

### 8 сентября {#08-09-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md)|

Добавили подстатус `TOO_LARGE` — отчет превысил допустимый размер.||
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

### 31 августа {#31-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Удалили параметр `storage`.||
|#

### 29 августа {#29-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)|

Удалили неактуальные статусы отгрузки.||
|#

### 28 августа {#28-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Теперь можно не включать пустое тело в запрос.

Не передавайте его, если хотите получить список всех товаров в каталоге.||
|#

### 24 августа {#24-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md)|

Установили ограничение на максимальное количество заказов, у которых можно изменить статус в одном запросе, — 30.||
|#

### 23 августа {#23-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Удалили параметр `predicted`.||
|#

### 15 августа {#15-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST cart`

`POST order/accept`

`POST order/status`

`POST order/cancellation/notify`|

В `address` добавили параметр `district` — район в адресе доставки заказа.||
|#

### 12 августа {#12-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)

[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)|

В `OrderDeliveryAddressDTO` добавили параметр `district` — район в адресе доставки заказа.||
|#

### 8 августа {#08-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)|

Теперь на одной странице можно передать не более 200 значений, если запрос выполняется по конкретным товарам.||

||[POST v2/campaigns/{campaignId}/stats/skus](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-stats/getGoodsStats.md)|

Удалили типы остатков товаров `SUGGEST` и `TRANSIT`.||
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

### 1 августа {#01-08-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)

`POST stocks`|

Теперь нужно передавать количество доступного товара на складе без учета резерва.||
|#

### 27 июля {#27-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Теперь можно узнать:

* порог для скидок с Маркетом на момент оформления заказа — параметр `cofinanceThreshold`;
* скидку с Маркетом — параметр `cofinanceValue`.||
|#

### 26 июля {#26-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|

Добавили информацию о стоимости услуг:

* `AGENCY` — прием платежа покупателя;
* `AUCTION_PROMOTION` — буст продаж;
* `DELIVERY_TO_CUSTOMER` — доставка покупателю;
* `EXPRESS_DELIVERY_TO_CUSTOMER` — экспресс-доставка покупателю;
* `FEE` — размещение товара на Маркете;
* `FULFILLMENT` — складская обработка;
* `INSTALLMENT` — рассрочка;
* `LOYALTY_PARTICIPATION_FEE` — участие в программе лояльности и отзывы за баллы, если они подключены;
* `PAYMENT_TRANSFER` — перевод платежа покупателя;
* `RETURNED_ORDERS_STORAGE` — хранение невыкупов и возвратов;
* `SORTING` — обработка заказа.||
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

### 7 июля {#07-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|

Дополнили инструкцию по добавлению нового товара — перечислили параметры, без которых добавить товар в каталог не получится.||
|#

### 4 июля {#04-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)

[GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md)

`GET v2/campaigns/by_login/{login}`|

Теперь можно узнать:

* идентификатор бизнеса — параметр `id` в `business`;
* название бизнеса — параметр `name` в `business`.||
|#

### 3 июля {#03-07-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)

[GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md)

`GET v2/campaigns/by_login/{login}`|

Теперь можно узнать модель, по которой работает магазин, — параметр `placementType`.||
|#

### 30 июня {#30-06-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)

[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)|

Добавили параметр `priceBeforeDiscount`, где указана стоимость товара в валюте магазина до применения скидок.||
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

### 21 июня {#21-06-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||—|

Опубликовали спецификацию OpenAPI для продавцов. Она поможет:

* быстрее написать собственную интеграцию с Маркетом и настроить ее методы под себя;
* сгенерировать файлы клиента на любом языке или фреймворке, которые поддерживает OpenAPI-генератор;
* найти нужный метод и варианты его параметров с минимальным обращением к [документации](https://yandex.ru/dev/market/partner-api/doc/ru/).

Спецификация OpenAPI для запросов магазина к Маркету доступна на [GitHub](https://github.com/yandex-market/yandex-market-partner-api).
||
|#

### 30 мая {#30-05-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)|Добавили новый метод. Он передает Маркету коды маркировки «Честного знака» и УИН для ювелирных изделий.
||

||[PUT v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md)|

Добавили причину отмены `ORDER_IN_DELIVERY`.

Теперь вы можете отказать покупателю в отмене, если заказ уже находится у курьера.||

||`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis`|Отметили метод устаревшим. Вместо него используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
||
|#

### 26 мая {#26-05-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)|

Теперь можно узнать:

* можно ли указать число палет — параметр `CHANGE_PALLETS_COUNT`;
* Количество палет, которое указано в заявке и которое приняли в сортировочном центре, — параметр `PalletsCount`.||
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

[*inactiv-campaign]:
{{ inactiv-campaign }}

[*inactiv-business]:
{{ inactiv-business }}

[*cis-regular-value]:
Значение `cis` должно соответствовать регулярному выражению `^(?=.{1,256}$)\u001D?(\(?01\)?\d{14}\(?21\)?([!-~]{6,8}|[!-~]{13}|[!-~]{20})(\u001D\(?240\)?.{1,30})?\u001D\(?9[1,3]\)?.+)$`.<br><br>Без криптохвоста — `^(?=[!-~]{1,256}$)(\(?01\)?\d{14}\(?21\)?(.{6,8}|.{13}|.{20}))$`.
