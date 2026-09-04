---
title: Журнал изменений WB API
api: wildberries
kind: changelog
source: "https://dev.wildberries.ru/release-notes"
window: последние записи, страница отдаёт не всю историю
fetched_at: "2026-09-04T01:57:31Z"
content_sha: dd3371a9c5db1be6
---

# Журнал изменений WB API

> Страница WB отдаёт в DOM только последние записи (прокрутка остальные не подгружает), поэтому здесь скользящее окно, а не вся история. Полная история накапливается в git: `mpdocs changes`.

# Журнал изменений

2026

Сен

Пн

31

Вт

1

Ср

2

Чт

3

Пт

4

Сб

5

Вс

6

Пн

7

Поиск

Все обновления

Выберите теги

Все обновления

Новое

Изменения

Устарело

Сентябрь
2026

Новое

## 03.09.2026

Заказы FBS

Поставки FBS

Новые методы Поставок FBS

Добавили методы для работы с данными [СПОТ](https://www.nalog.gov.ru/rn77/related_activities/spot/) — системы ввоза товаров автомобильным транспортом из стран ЕАЭС. Заполнять данные СПОТ обязательно для всех поставок из ЕАЭС в РФ.

С помощью новых методов вы можете:

- Получать список стран ОКСМ — [GET /api/marketplace/v3/fbs/dictionaries/countries/oksm](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/getV3FbsDictionariesCountriesOksm)
- Добавлять данные СПОТ в поставку — [PUT /api/marketplace/v3/fbs/supplies/{supplyId}/spot](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/putV3FbsSuppliesSupplyIdSpot)
- Получать данные СПОТ для списка поставок — [POST /api/marketplace/v3/fbs/supplies/spot/list](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/postV3FbsSuppliesSpotList)
- Получать сформированные QR-коды СПОТ — [GET /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/getV3FbsSuppliesSupplyIdStickersSpot)

Также добавили поле `spotAvailable` — доступен ли СПОТ для данной поставки — в методы:

- Получить список поставок — [GET /api/v3/supplies](/docs/openapi/orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies/get)
- Получить информацию о поставке — [GET /api/v3/supplies/{supplyId}](/docs/openapi/orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/get)

Сейчас методы доступны только для продавцов из Кыргызстана. В дальнейшем методы будут доступны продавцам из любой страны ЕАЭС кроме РФ, следите за обновлениями.

Август
2026

Новое

## 31.08.2026

Критичное изменение

Заказы FBS

Поставки FBS

Новые методы Поставок FBS

С **1 сентября** с помощью WB API продавцы из РФ смогут указывать параметры отгрузки поставок в РФ. Для этого добавили методы:

- Получить список мест отгрузки поставок — [GET /api/marketplace/v3/fbs/shipping-points](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/getV3FbsShippingPoints)
- Установить параметры отгрузки поставок — [PATCH /api/marketplace/v3/fbs/supplies/shipping-method](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/patchV3FbsSuppliesShippingMethod)

Для доставки транспортной компанией можно будет указывать ID ЭТрН — электронной транспортной накладной. Чтобы добавить ID ЭТрН в поставку, нужно будет использовать метод [PATCH /api/marketplace/v3/fbs/supplies/waybill](/docs/openapi/orders-fbs#tag/Postavki-FBS/operation/patchV3FbsSuppliesWaybill). Пока метод находится в доработке, о его доступности сообщим дополнительно.

С **1 октября** добавление параметров отгрузки и ID ЭТрН станет обязательным. Без этого нельзя будет перевести поставку в доставку — вы получите ошибку `409` в методе [PATCH /api/v3/supplies/ {supplyId} /deliver](/docs/openapi/orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1deliver/patch).

Новое

## 24.08.2026

Аналитика и данные

История остатков

Новый отчёт по остаткам на складах продавца

Добавили отчёт по остаткам на складах продавца — [POST /api/analytics/v1/stocks-report/seller-warehouses](/docs/openapi/analytics#tag/stocksReport/operation/postAnalyticsV1StocksReportSellerWarehouses).

Используйте новый отчёт вместо метода [POST /api/v3/stocks/{warehouseId}](/docs/openapi/work-with-products#tag/Ostatki-na-skladah-prodavca/paths/~1api~1v3~1stocks~1%7BwarehouseId%7D/post), чтобы получить остатки без указания ID складов продавца и ID размеров в запросе.

Данные в отчёте обновляются 1 раз в 30 минут.

Метод доступен по **Персональному** и **Сервисному** токену категории **Аналитика**.

Изменения

## 15.08.2026

Поставки FBW

Информация для формирования поставок

Тарифы

Стоимость возврата продавцу

Тарифы на поставку

Тарифы на остаток

Отчёты

Основные отчёты

Отчёт об остатках на складах

Платное хранение

Аналитика и данные

Воронка продаж

Аналитика продавца CSV

История остатков

Лента заказов

Документы и бухгалтерия

Финансовые отчёты

Временные изменения в работе WB API со складами WB с 15 августа

C **15 августа** вносим временные изменения в работу WB API. Часть информации по складам WB будет недоступна, подробнее — в [новости](https://seller.wildberries.ru/news-v2/news-details?id=13442) на Портале продавцов.

- Методы [Информации для формирования поставок](/docs/openapi/orders-fbw#tag/informationForFormingSupplies) и [Тарифов на поставку](/docs/openapi/wb-tariffs#tag/supplyRates) отключены
- В [Тарифах на остаток](/docs/openapi/wb-tariffs#tag/stockRates) возвращаются данные:   в [Тарифах для коробов](/docs/openapi/wb-tariffs#tag/stockRates/operation/getV1TariffsBox) — только для складов вне РФ, а также с `warehouseName`:   `Свой склад РФ` `Свой склад СГТ РФ`   в [Тарифах для монопаллет](/docs/openapi/wb-tariffs#tag/stockRates/operation/getV1TariffsPallet) — только для складов вне РФ
- В [Тарифах на возврат](/docs/openapi/wb-tariffs#tag/returnCostToSeller) возвращаются данные только для складов вне РФ, а также с `warehouseName`:   `Свой склад РФ` `Свой склад СГТ РФ` `Склад WB РФ` `Склад WB СГТ РФ`
- В массиве `warehouses` [Отчёта об остатках на складах WB](/docs/openapi/reports#tag/warehousesInventoryReport/operation/getV1WarehouseRemainsTasksTaskIdDownload) вместо данных по складам в РФ, кроме указанных в [новости](https://seller.wildberries.ru/news-v2/news-details?id=13440) отдельно и [Коледино](https://seller.wildberries.ru/news-v2/news-details?id=13458), возвращаются суммарные с `warehouseName`:   `Склад WB РФ` `Склад WB СГТ РФ`
- В отчёте [Платное хранение](/docs/openapi/reports#tag/paidStorage/operation/getV1PaidStorageTasksTaskIdDownload) и в отчётах [Аналитики и данных](/docs/openapi/analytics) с детализацией по складам WB данные в разрезе складов WB возвращаются только суммарными по размерам товаров
- В строках отчётов установлены следующие постоянные значения:

Список постоянных значений

- В строках отчётов установлены следующие постоянные значения для складов WB:

Список постоянных значений

- В строках отчётов установлены следующие постоянные значения для складов отгрузки в РФ:

Список постоянных значений

- В детализациях к отчётам реализации [по ID отчётов](/docs/openapi/financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) и [за период](/docs/openapi/financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) значения поля `officeName` для складов в РФ, начиная с ежедневных отчётов за 13 августа, сведены к четырём, указанным в [новости](https://seller.wildberries.ru/news-v2/news-details?id=13440)

О дальнейших изменениях мы сообщим дополнительно.

Новое

## 12.08.2026

Маркетинг и продвижение

Управление кампаниями

Рекомендованные ставки для CPC-кампаний

Добавили отображение рекомендованных ставок для CPC-кампаний — по предложениям пользователей в [Сообществе WB API](https://dev.wildberries.ru/forum/topics/2079/publichnye-idei-i-predlozheniia-wb-api).

Теперь метод [GET /api/advert/v0/bids/recommendations](/docs/openapi/promotion/#tag/campaignManagement/operation/patchV0AuctionNms) возвращает рекомендованные ставки не только для кампаний с типом оплаты CPM за показы, но и для CPC — за клики.

Новое

## 11.08.2026

DBS

Сборочные задания DBS

Самовывоз

Сборочные задания Самовывоз

Изменения в сборочных заданиях DBS и Самовывоз

Добавили методы получения данных о ценах продавца без учёта скидок и суммах к оплате покупателем с учетом всех скидок и кэшбека по ID сборочных заданий:

- DBS — [POST /api/marketplace/v3/dbs/orders/final-price](/docs/openapi/orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersFinalPrice)
- Самовывоз — [POST /api/marketplace/v3/click-collect/orders/final-price](/docs/openapi/in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersFinalPrice)

Для расчётов используйте суммы к оплате покупателем из ответов новых методов, поля:

- `originalFinalPrice` — сумма к оплате покупателем в валюте продажи с учетом всех скидок и кэшбека, умноженная на 100.
- `convertedOriginalFinalPrice` — сумма к оплате покупателем в валюте страны продавца с учетом всех скидок и кэшбека, умноженная на 100.

Значения полей `finalPrice` и `convertedFinalPrice` из ответов методов получения сборочных заданий используйте только в случае, когда в ответе новых методов для переданных сборочных заданий возвращается `"data": null.`

Изменения

## 11.08.2026

Критичное изменение

Заказы FBS

Идентификаторы маркировки FBS

Изменения в Заказах FBS

С **18 августа** добавить номер декларации на товары (ДТ) можно будет только к сборочным заданиям в [статусе](https://dev.wildberries.ru/docs/openapi/orders-fbs/#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `confirm`.

Также с **18 августа** продавцам из Армении будет обязательно указывать номер ДТ для товаров, произведённых вне ЕАЭС, если заказ из Армении доставляется в РФ.

Чтобы проверить, обязательно ли закреплять номер ДТ за сборочным заданием, используйте метод [GET /api/v3/orders/new](/docs/openapi/orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1new/get). Обязательные идентификаторы маркировки указаны в поле `requiredMeta`.

Чтобы добавить номер ДТ к сборочному заданию, передайте его в запросе метода [PUT /api/marketplace/v3/orders/{orderId}/meta/customs-declaration](/docs/openapi/orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1%7BorderId%7D~1meta~1customs-declaration/put) в параметре `customsDeclaration`.

Без обязательного номера ДТ невозможно получить стикеры сборочных заданий методом [POST /api/v3/orders/stickers](/docs/openapi/orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1stickers/post) — если хотя бы для одного сборочного не будет указан обязательный номер ДТ, вы получите ошибку `409` `CustomsDeclarationIsRequired`.

Также, если к сборочному заданию не добавлен обязательный номер ДТ, поставку с этим сборочным заданием невозможно перевести в доставку. В ответе метода [PATCH /api/v3/supplies/{supplyId}/deliver](/docs/openapi/orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1deliver/patch) вы получите ошибку `409` `MetaValidationFail`, при этом в поле `decision` для `customsDeclaration` вернётся значение `required`.

Чтобы проверить, добавлен ли обязательный номер ДТ к сборочному заданию, до перевода поставки в доставку, используйте метод [POST /api/marketplace/v3/orders/meta](/docs/openapi/orders-fbs/#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1meta/post). Перевести поставку в доставку можно со статусами `filled` или `optional` в поле `decision` для `customsDeclaration`.

Новое

## 06.08.2026

Аналитика и данные

Лента заказов

Отчёты

Основные отчёты

Лента заказов в WB API

Получить отчёт [Лента заказов](https://seller.wildberries.ru/content-analytics/order-feed) теперь можно с помощью WB API — методом [POST /api/analytics/v1/order-feed](/docs/openapi/analytics#tag/orderFeed). Используйте его в качестве замены методов:

- [GET /api/v1/supplier/orders](/docs/openapi/reports#tag/mainReports/operation/getV1SupplierOrders) — **Заказы**
- [GET /api/v1/supplier/sales](/docs/openapi/reports#tag/mainReports/operation/getV1SupplierSales) — **Продажи**

Делитесь с нами обратной связью в [Сообществе WB API](/forum/topics/2497). На основе ваших комментариев мы сможем сделать переход на новый метод максимально комфортным.

Методы **Заказы** и **Продажи** продолжают работать, но, как мы [сообщали](/forum/topics/1721) ранее, в будущем они будут отключены. О дате отключения сообщим заранее.

Преимущества **Ленты заказов** в сравнении с методами **Заказы** и **Продажи**:

- данные обновляются в режиме реального времени
- нет разделения на заказы и выкупы, данные отдаются в рамках одного метода
- есть статусы заказов и причины отмен
- отчёт содержит заказы с отложенной оплатой
- для каждого заказа определён тип продажи: B2B или B2C
- изменяться могут только статусы
- используется офсетно-курсорная пагинация и товарные фильтры: артикулы WB, бренды, предметы, теги

Метод доступен по [токену](/docs/openapi/api-information#tag/authorization) любого типа для категории **Аналитика**.

Июль
2026

Новое

## 30.07.2026

Заказы FBS

Настройки автовозврата

Настройки автовозврата для заказов FBS

Добавили методы для работы с [автовозвратами FBS](/docs/openapi/orders-fbs#tag/autoreturnSettings) для малогабаритных товаров — `"cargoType":1` — по предложениям пользователей в [Сообществе WB API](/forum/topics/2079/publichnye-idei-i-predlozheniia-wb-api). Теперь с помощью WB API вы можете:

- Получить настройки автовозврата продавца — [GET /api/marketplace/v3/fbs/settings/autoreturns](/docs/openapi/orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturns)
- Обновить настройки автовозврата продавца — [PATCH /api/marketplace/v3/fbs/settings/autoreturns](/docs/openapi/orders-fbs#tag/autoreturnSettings/operation/patchMarketplaceV3FbsSettingsAutoreturns)
- Получить настройки автовозврата товаров — [POST /api/marketplace/v3/fbs/settings/autoreturns/items](/docs/openapi/orders-fbs#tag/autoreturnSettings/operation/postMarketplaceV3FbsSettingsAutoreturnsItems)
- Обновить настройки автовозврата товаров — [PATCH /api/marketplace/v3/fbs/settings/autoreturns/items](/docs/openapi/orders-fbs#tag/autoreturnSettings/operation/patchMarketplaceV3FbsSettingsAutoreturnsItems)
- Получить предметы, которые не хранятся на складах WB — [GET /api/marketplace/v3/fbs/settings/autoreturns/subcategories/restricted](/docs/openapi/orders-fbs#tag/autoreturnSettings/operation/getMarketplaceV3FbsSettingsAutoreturnsSubcategoriesRestricted)

Новое

## 30.07.2026

Критичное изменение

Работа с товарами

Склады продавца

Изменение в методах работы со складами продавца

С **5 августа** с помощью API нельзя будет создавать и редактировать склады продавца для **сверхгабаритных** товаров (СГТ). Данная возможность будет только в [личном кабинете](https://seller.wildberries.ru/marketplace-pass/warehouses).

Что изменится в методах:

- Получить список складов WB — [GET /api/v3/offices](/docs/openapi/work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1offices/get) — в ответе теперь не будут возвращаться СГТ-склады WB
- Создать склад продавца — [POST /api/v3/warehouses](/docs/openapi/work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses/post) — при создании СГТ-склада вы получите ошибку `404`
- Обновить склад продавца — [PUT /api/v3/warehouses/ {warehouseId}](/docs/openapi/work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses~1%7BwarehouseId%7D/put) — при изменении данных СГТ-склада вы получите ошибку `404`

Новое

## 20.07.2026

Маркетинг и продвижение

Управление кампаниями

Изменения в сервисе Продвижения

В ответ метода [GET /api/advert/v1/config](/docs/openapi/promotion/#tag/campaignManagement/operation/getV1Config) добавили информацию о минимальной сумме пополнения бюджета кампании — поле `minTopUp`.

Изменения

## 16.07.2026

Критичное изменение

Аналитика и данные

Оценка товара

Отчёты

Скрытые товары

Новая версия Оценки товара и отключение метода Скрытые из каталога

Добавили новую версию метода получения отчёта **Оценка товара** — [POST /api/analytics/v2/item-rating](/docs/openapi/analytics#tag/itemRating/operation/postV2ItemRating). C её помощью вы можете получать данные отдельно по скрытым из каталога товарам.

В новом методе:

- добавили параметр `onlyShadowedNms`:   укажите `true`, чтобы получить в отчёте только скрытые из каталога товары укажите `false`, чтобы получить в отчёте все товары, если не указаны другие параметры
- добавили поле `isShadowed` — является ли товар скрытым из каталога
- изменили наименование массива ответа `cards` на `items`
- изменили наименование параметра `isNotIncludeNMsWithoutSales` на `isNotIncludeNmsWithoutSales`

Метод доступен по **Персональному** или **Сервисному** [токену](/docs/openapi/api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) для категории **Аналитика**.

Текущие методы **POST /api/analytics/v1/item-rating** и **GET /api/v1/analytics/banned-products/shadowed** будут отключены **30 июля**.

Новое

## 14.07.2026

Маркетинг и продвижение

Кампании

Изменения в сервисе Продвижения

В ответ метода [GET /api/advert/v2/adverts](/docs/openapi/promotion/#tag/campaigns/operation/getV2Adverts) добавили признак возможности изменения списка товаров в кампании поле — `can_change_nms` в объекте `restrictions`.

Новое

## 09.07.2026

Критичное изменение

Общение с покупателями

Вопросы

Отзывы

Новые методы в Песочнице Вопросов и отзывов

Расширили песочницу вопросов и отзывов. Теперь вы можете:

- создавать несколько тестовых отзывов одним запросом — [POST /api/v1/test/make/feedbacks/batch](/docs/openapi-other/sandbox-environment#tag/Voprosy-i-otzyvy/operation/postV1TestMakeFeedbacksBatch)
- удалять тестовые отзывы — [POST /api/v1/test/delete/feedbacks](/docs/openapi-other/sandbox-environment#tag/Voprosy-i-otzyvy/operation/postV1TestDeleteFeedbacks)
- создавать несколько тестовых вопросов одним запросом — [POST /api/v1/test/make/questions/batch](/docs/openapi-other/sandbox-environment#tag/Voprosy-i-otzyvy/operation/postV1TestMakeQuestionsBatch)
- удалять тестовые вопросы — [POST /api/v1/test/delete/questions](/docs/openapi-other/sandbox-environment#tag/Voprosy-i-otzyvy/operation/postV1TestDeleteQuestions)

**27 июля** отключим неактуальные методы:

- **POST /api/v1/test/make/feedbacks**
- **POST /api/v1/test/make/questions**

Новое

## 07.07.2026

Критичное изменение

Маркетинг и продвижение

Кампании

Управление кампаниями

Финансы

Параметры кампаний

Статистика

Поисковые кластеры

Изменения в сервисе Продвижения

API Продвижения уже работает в валюте аккаунта продавца.

Добавили информацию о валюте [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) — поле `currency`— в ответы методов:

- [GET /api/advert/v2/adverts](/docs/openapi/promotion/#tag/campaigns/operation/getV2Adverts)
- [POST /api/advert/v1/bids/min](/docs/openapi/promotion/#tag/creatingCampaigns/operation/postV1BidsMin)
- [PATCH /api/advert/v1/bids](/docs/openapi/promotion/#tag/campaignManagement/operation/patchV1Bids)
- [GET /adv/v1/balance](/docs/openapi/promotion/#tag/finances/operation/getV1Balance)
- [GET /adv/v1/budget](/docs/openapi/promotion/#tag/finances/operation/getV1Budget)
- [POST /adv/v1/budget/deposit](/docs/openapi/promotion/#tag/finances/operation/postV1BudgetDeposit)
- [GET /adv/v1/payments](/docs/openapi/promotion/#tag/finances/operation/getV1Payments)
- [POST /adv/v0/normquery/stats](/docs/openapi/promotion/#tag/statistics/operation/postV0NormqueryStats)
- [GET /adv/v3/fullstats](/docs/openapi/promotion/#tag/statistics/operation/getV3Fullstats)

В ответ метода получения списка ставок поисковых кластеров [POST /adv/v0/normquery/get-bids](/docs/openapi/promotion/#tag/searchClusters/operation/postV0NormqueryBids) добавили поля:

- `id_kopecks` — текущая ставка в разменных денежных единицах — 0,01 от базовой единицы валюты [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances) за тысячу показов.
- `currency` — валюта [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances).

Добавили метод [GET /api/advert/v1/config](/docs/openapi/promotion/#tag/campaignManagement/operation/getV1Config). С его помощью вы можете получить валюту вашего аккаунта и допустимые шаги ставок.

Чтобы установить ставки для поисковых кластеров в валюте вашего аккаунта используйте новый метод [POST /api/advert/v1/normquery/bids](/docs/openapi/promotion/#tag/searchClusters/operation/postV1NormqueryBids)

Новое

## 02.07.2026

Критичное изменение

DBS

Сборочные задания DBS

Идентификаторы маркировки DBS

Самовывоз

Сборочные задания Самовывоз

Идентификаторы маркировки Самовывоз

Изменения в заказах DBS и Самовывоз

С **8 июля** при закреплении за сборочными заданиями номеров деклараций на товары (ДТ) будет обязательно указывать код страны происхождения товара по [Общероссийскому классификатору стран мира](https://esnsi.gosuslugi.ru/classifiers/16269) для B2B-заказов DBS и Самовывоз. Без корректного кода страны закрепить за сборочным заданием номер ДТ станет невозможно.

Мы обновили документацию уже сейчас, чтобы вы заранее внесли изменения в свои интеграции. Обновление методов WB API состоится не ранее 8 июля, мы сообщим об этом дополнительно.

**Чтобы добавить код страны, используйте методы**:

- DBS — [POST /api/marketplace/v3/dbs/orders/meta/customs-declaration](/docs/openapi/orders-dbs/#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaCustomsDeclaration), укажите числовой код страны происхождения товара в параметре `originCountryCode`. Доступно для сборочных заданий в статусах `confirm` или `deliver`. Сборочные задания без корректного кода страны вернутся в ответе `200` с ошибкой `InvalidOriginCountryCode` в массиве `errors`.
- Самовывоз — [POST /api/marketplace/v3/click-collect/orders/meta/customs-declaration](/docs/openapi/in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration), укажите числовой код страны происхождения товара в параметре `originCountryCode`. Доступно для сборочных заданий в статусах`confirm` или `prepare`. Сборочные задания без корректного кода страны вернутся в ответе `200` с ошибкой `InvalidOriginCountryCode` в массиве `errors`.

**Чтобы проверить код страны, используйте методы**:

- DBS — [POST /api/marketplace/v3/dbs/orders/meta/details](/docs/openapi/orders-dbs/#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDetails). Метод доступен для сборочных заданий в статусах `confirm` или `deliver`.
- Самовывоз — [POST /api/marketplace/v3/click-collect/orders/meta/details](/docs/openapi/in-store-pickup/#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDetails). Метод доступен для сборочных заданий в статусах `confirm` или `prepare`.

**Чтобы удалить код страны, используйте методы**:

- DBS — [POST /api/marketplace/v3/dbs/orders/meta/delete](/docs/openapi/orders-dbs/#tag/dbsLabelIdentifiers/operation/postV3DbsOrdersMetaDelete)
- Самовывоз — [POST /api/marketplace/v3/click-collect/orders/meta/delete](/docs/openapi/in-store-pickup/#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaDelete)

Июнь
2026

Новое

## 30.06.2026

Документы и бухгалтерия

Финансовые отчёты

Новoе поле в детализациях к отчётам реализации

Добавили поле `b2bCustomerTin` с информацией об [ИНН B2B-покупателя](https://seller.wildberries.ru/news-v2/news-details?id=12515) в детализации к отчётам реализации — [POST /api/finance/v1/sales-reports/detailed/{reportId}](/docs/openapi/financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) и [POST api/finance/v1/sales-reports/detailed](/docs/openapi/financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed).

Изменения

## 25.06.2026

DBS

Сборочные задания DBS

Аналитика и данные

История остатков

Обновление доступов к методам

Обновили доступы к методам:

- Отчёт об остатках на складах WB [POST /api/analytics/v1/stocks-report/wb-warehouses](/docs/openapi/analytics#tag/stocksReport/operation/postV1StocksReportWbWarehouses)
- Получить стикеры для сборочных заданий с доставкой в ПВЗ [POST /api/marketplace/v3/dbs/orders/stickers](/docs/openapi/orders-dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersStickers)

Теперь эти методы доступны для [зарегистрированных и авторизованных сервисов](/knowledge-base/articles/019dce8b-4233-701b-9318-961cde8b24cd/registratsiia-servisa-na-platforme-wb-api) по базовому токену с секретом.

Изменения

## 25.06.2026

Общее

Управление пользователями продавца

Изменения в методах Управления пользователями продавца

Расширили список разделов личного кабинета, к которым можно настроить доступ сотрудникам:

- `brandzone` — [Бренд-зона. Публикация изменений](https://cmp.wildberries.ru/bz/)
- `brandzoneSubscribe` — [Управление подпиской бренд-зоны](https://cmp.wildberries.ru/bz/)

Указывайте новые разделы в запросах методов:

- Создать приглашение для нового пользователя [POST /api/v1/invite](/docs/openapi/api-information#tag/sellerUserManagement/operation/postV1Invite)
- Изменить права доступа пользователей [PUT /api/v1/users/access](/docs/openapi/api-information#tag/sellerUserManagement/operation/putV1UsersAccess)

Обновлённый список разделов можно получить в ответе метода [GET /api/v1/users](/docs/openapi/api-information#tag/sellerUserManagement/operation/getV1Users).

Изменения

## 25.06.2026

Заказы FBS

Сборочные задания FBS

Изменения в Заказах FBS

С **21 июля** получить сборочные задания, созданные более 3 месяцев назад, вы сможете только методом [GET /api/marketplace/v3/fbs/orders/archive](/docs/openapi/orders-fbs/#tag/Sborochnye-zadaniya-FBS/paths/~1api~1marketplace~1v3~1fbs~1orders~1archive/get).

Метод [GET /api/v3/orders](/docs/openapi/orders-fbs/#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get) будет возвращать информацию только о сборочных заданиях, созданных менее 3 месяцев назад.

Мы используем [cookies](/privacy) для сбора статистики и улучшения сервиса
