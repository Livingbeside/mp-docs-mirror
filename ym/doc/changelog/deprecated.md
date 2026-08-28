---
title: Устаревшие методы и параметры
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/changelog/deprecated.md"
fetched_at: "2026-08-28T11:51:44Z"
content_sha: 48d20fca877c7cc2
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/changelog/deprecated.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/changelog/deprecated.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/changelog/deprecated.md
  - href: ru/changelog/deprecated.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Устаревшие методы и параметры

{% note tip "Следите за обновлениями документации в [Телеграм-канале](https://t.me/yandex_market_api)." %}

 

{% endnote %}

<!-- source: ru/_auto/changelog/deprecated.md -->
<!-- source: ru/_auto/changelog/deprecated/2026-07-29.md -->
### 29 июля {#29-07-26}

#|
|| **Методы или страницы документации**
 | **Описание изменений**
 ||
||
[POST v2/campaigns/{campaignId}/warehouse/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseStatus.md)
|
Пометили метод как устаревший. Вместо него используйте [POST v3/businesses/{businessId}/warehouse/models/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseModelStatus.md).
||
|#
<!-- endsource: ru/_auto/changelog/deprecated/2026-07-29.md -->
<!-- endsource: ru/_auto/changelog/deprecated.md -->

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
|| [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md) | Поле `regions` в ответе помечено как устаревшее. Используйте поле `region`. ||
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

## 2025 {#2025}

### 17 декабря {#17-12-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)|Отметили устаревшими методы получения заказов магазина. Вместо них используйте [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md).
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

### 15 августа {#15-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/reports/prices/generate`|Отметили метод устаревшим. Вместо него используйте [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md).
||
|#

### 1 августа {#01-08-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
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

### 16 июля {#16-07-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|Отметили устаревшим параметр `id` в `LogisticPickupPointDTO`.
||
|#

### 30 июня {#30-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md).
||
|#

### 4 июня {#04-06-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderShipmentBoxes.md)|Отметили метод устаревшим. Вместо него используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
||
|#

### 29 мая {#29-05-25}
#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`GET v2/campaigns/{campaignId}/offers`<br><br>`GET v2/campaigns/{campaignId}/offers/all`<br><br>`GET v2/campaigns/{campaignId}/feeds`<br><br>`GET v2/campaigns/{campaignId}/feeds/{feedId}`<br><br>`GET v2/campaigns/{campaignId}/feeds/{feedId}/index-logs`<br><br>`POST v2/campaigns/{campaignId}/feeds/{feedId}/params`<br><br>`POST v2/campaigns/{campaignId}/feeds/{feedId}/refresh`<br><br>
|Удалили устаревшие методы.
||
|#

### 24 апреля {#24-04-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Отметили устаревшим параметр `cofinancePrice`.
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

### 31 марта {#31-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getWarehouses.md)|Отметили метод устаревшим. Вместо него используйте [POST v2/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md).
||
|#

### 7 марта {#07-03-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
|Отметили устаревшими параметры `refundAmount` и `partnerCompensation`. Вместо них используйте `amount` и `partnerCompensationAmount`.
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

### 10 февраля {#10-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/businesses/{businessId}/offer-mappings/suggestions`|Отметили метод устаревшим.
||
|#

### 4 февраля {#04-02-25}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)|Отметили устаревшим параметр `statusType`. Вместо него используйте `statuses`.
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

### 17 декабря {#17-12-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
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
|#

### 29 ноября {#29-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
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
||[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)|Отметили устаревшим параметр `category`. Вместо него используйте `marketCategoryId`.
||
|#

### 20 ноября {#20-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)|Отметили устаревшим параметр `code`. Вместо него используйте `codes`.
||
|#

### 6 ноября {#06-11-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md)|Отметили устаревшими cпособы денежного перевода `CASHBACK`, `MARKETPLACE` и `SPLIT`.
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

### 8 августа {#08-08-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||`POST v2/campaigns/{campaignId}/offer-prices/suggestions`|Отметили метод устаревшим. Вместо него используйте [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md).
||
|#

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

### 19 июля {#19-07-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
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

### 24 июня {#24-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
|Отметили устаревшими параметры `priceBeforeDiscount`, `buyerItemsTotal` и `buyerTotal`.
||
|#

### 5 июня {#05-06-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
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
||[GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)|Удалили устаревший параметр `total`.
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)
|Удалили устаревшие параметры `total`, `subsidyTotal` и `totalWithSubsidy`.
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

### 24 апреля {#24-04-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
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

### 15 марта {#15-03-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis`
|Отметили устаревшим параметр `feedCategoryId`.
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
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)<br><br>[GET v2/campaigns/{campaignId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrders.md)<br><br>[GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)
|Отметили устаревшим параметр `shopSku`. Вместо него используйте `offerId`.
||
|#

### 22 января {#22-01-24}

#|
||**Методы или страницы документации**
|**Описание изменений**
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

## 2023 {#2023}

### 26 декабря {#26-12-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
||
||[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderShipmentBoxes.md)<br><br>[PUT v2/campaigns/{campaignId}/orders/{orderId}/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderItems.md)
|Отметили методы устравшими для модели FBS. Вместо них используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).
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

### 22 июня {#22-06-23}

#|
||**Методы или страницы документации**
|**Описание изменений**
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
||`PUT v2/campaigns/{campaignId}/orders/{orderId}/cis`|Отметили метод устаревшим. Вместо него используйте [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
||
|#
