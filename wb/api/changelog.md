---
title: Журнал изменений WB API
api: wildberries
kind: changelog
source: "https://dev.wildberries.ru/release-notes"
window: последние записи, страница отдаёт не всю историю
fetched_at: "2026-09-23T02:22:50Z"
content_sha: 08e2546a526d7fff
---

# Журнал изменений WB API

> Страница WB отдаёт в DOM только последние записи (прокрутка остальные не подгружает), поэтому здесь скользящее окно, а не вся история. Полная история накапливается в git: `mpdocs changes`.

# Журнал изменений

2026

Сен

Пн

21

Вт

22

Ср

23

Чт

24

Пт

25

Сб

26

Вс

27

Пн

28

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

## 22.09.2026

Поставки FBW

Информация о поставках

Расхождения в поставках FBW

Добавили метод [GET /api/supplies/v1/discrepancies/{supplyId}](./docs/openapi/orders-fbw#tag/suppliesInformation/operation/getV1SuppliesSupplyIdDiscrepanciesQuantity). С его помощь вы можете получить расхождения между заявленным и фактическим количеством товара, выявленные при приёмке поставки.

В ответ метода получения деталей поставки — [GET /api/v1/supplies/{ID}](/docs/openapi/orders-fbw#tag/suppliesInformation/operation/getV1SuppliesId) добавили поле `discrepancies` — расхождения между заявленным и фактическим количеством товара в поставке.

Изменения

## 17.09.2026

Аналитика и данные

История остатков

Изменение времени обновления данных в Истории остатков

С **17 сентября** данные по остаткам будут обновляться 1 раз в 2 часа в следующих отчётах:

- [Данные по группам](/docs/openapi/analytics#tag/stocksReport/operation/postV2StocksReportProductsGroups)
- [Данные по товарам](/docs/openapi/analytics#tag/stocksReport/operation/postV2StocksReportProductsProducts)
- [Данные по размерам](/docs/openapi/analytics#tag/stocksReport/operation/postV2StocksReportProductsSizes)
- [Данные по складам](/docs/openapi/analytics#tag/stocksReport/operation/postV2StocksReportOffices)
- `STOCK_HISTORY_REPORT_CSV` — отчёт по статистике остатков в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)
- `STOCK_HISTORY_DAILY_CSV` — отчёт по истории остатков в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)

Чтобы получить текущие данные по остаткам без задержки обновления, используйте методы [POST /api/analytics/v1/stocks-report/wb-warehouses](/docs/openapi/analytics/#tag/stocksReport/operation/postV1StocksReportWbWarehouses) и [POST /api/analytics/v1/stocks-report/seller-warehouses](/docs/openapi/analytics#tag/stocksReport/operation/postAnalyticsV1StocksReportSellerWarehouses).

Новое

## 16.09.2026

Критичное изменение

Маркетинг и продвижение

Финансы

Изменения в API Продвижения

Добавили новую версию метода получения бюджета кампаний — [POST /api/advert/v2/budget](https://dev.wildberries.ru/docs/openapi/promotion/#tag/finances/operation/postV2Budget). Теперь с помощью WB API вы можете получить остатки бюджетов по нескольким кампаниям одним запросом.

Текущий метод [GET /adv/v1/budget](https://dev.wildberries.ru/docs/openapi/promotion/#tag/finances/operation/getV1Budget) будет отключён **16 ноября**.

Новое

## 10.09.2026

Поставки FBW

Черновики поставок

Черновики поставок FBW

Добавили методы для работы с [черновиками поставок](./docs/openapi/orders-fbw#tag/supplyDrafts) FBW. Теперь с помощью WB API вы можете:

- Создать черновик — [POST /api/supplies/v1/drafts](./docs/openapi/orders-fbw#tag/supplyDrafts/operation/postV1Drafts)
- Добавить товары в черновик — [POST /api/supplies/v1/drafts/{draftId}/items](./docs/openapi/orders-fbw#tag/supplyDrafts/operation/postV1DraftsDraftIdItems)
- Получить список черновиков — [GET /api/supplies/v1/drafts](./docs/openapi/orders-fbw#tag/supplyDrafts/operation/getV1Drafts)
- Получить список товаров в черновике — [GET /api/supplies/v1/drafts/{draftId}/items](./docs/openapi/orders-fbw#tag/supplyDrafts/operation/getV1DraftsDraftIdItems)
- Удалить товары из черновика — [DELETE /api/supplies/v1/drafts/{draftId}/items](./docs/openapi/orders-fbw#tag/supplyDrafts/operation/deleteV1DraftsDraftIdItems)
- Удалить черновик — [DELETE /api/supplies/v1/drafts/{draftId}](./docs/openapi/orders-fbw#tag/supplyDrafts/operation/deleteV1DraftsDraftId)

Методы доступны по **Персональному** и **Сервисному** токену категории **Поставки**.

Изменения

## 10.09.2026

Работа с товарами

Создание карточек товаров

Карточки товаров

Корректировка описания объекта B2B-продажи в методах карточек товаров

Исправили описание объекта `wholesale` в запросах и ответах методов:

- Создание карточек товаров — [POST /content/v2/cards/upload](/docs/openapi/item-management#tag/listingItems/operation/postV2CardsUpload)
- Создание карточек товаров с присоединением — [POST /content/v2/cards/upload/add](/docs/openapi/item-management#tag/listingItems/operation/postV2CardsUploadAdd)
- Список карточек товаров — [POST /content/v2/get/cards/list](/docs/openapi/item-management#tag/listings/operation/postV2GetCardsList)
- Список карточек товаров в корзине — [POST /content/v2/get/cards/trash](/docs/openapi/item-management#tag/listings/operation/postV2GetCardsTrash)

В предыдущей версии описания объекта `wholesale` было некорректно указано, что при `"enabled":true` товар предназначен для оптовой продажи.
 В исправленной версии описания объекта `wholesale` указано, что при `"enabled":true` товар предназначен для любой [B2B-продажи](https://seller.wildberries.ru/instructions/ru/ru/material/wholesale-of-goods), не только оптовой.

Изменения

## 10.09.2026

Отчёты

Отчёты об удержаниях

Изменения в Отчётах об удержании

Добавили новые поля в отчёт об удержаниях за занижение габаритов упаковки [GET /api/analytics/v1/measurement-penalties](/docs/openapi/reports#tag/retentionReports/operation/getV1MeasurementPenalties):

- `dateStart` — дата начала действия коэффициента
- `dateEnd` — дата окончания действия коэффициента

Изменения

## 08.09.2026

Критичное изменение

Работа с товарами

Создание карточек товаров

Карточки товаров

Документы в методах Работы с товарами

Теперь с помощью WB API вы можете указать документы в карточке товара:

- Сертификат соответствия
- Декларация о соответствии
- Свидетельство о государственной регистрации (СГР)
- Регистрационное удостоверение (РУ) на медицинские изделия
- Регистрационное удостоверение республики Беларусь
- Данные о регистрации пестицида
- Данные о регистрации агрохимиката
- Регистрационное удостоверение (РУ) на лекарственные препараты

Чтобы указать документы в карточке товара, используйте объект `documents` в запросах методов:

- Создание карточек товаров — [POST /content/v2/cards/upload](/docs/openapi/item-management#tag/listingItems/operation/postV2CardsUpload)
- Создание карточек товаров с присоединением — [POST /content/v2/cards/upload/add](/docs/openapi/item-management#tag/listingItems/operation/postV2CardsUploadAdd)
- Редактирование карточек товаров — [POST /content/v2/cards/update](/docs/openapi/item-management#tag/listings/operation/postV2CardsUpdate)

Чтобы получить информацию о документах, указанных в карточке товара, используйте объект `documents` в ответах метода Список карточек товаров — [POST /content/v2/get/cards/list](/docs/openapi/item-management#tag/listings/operation/postV2GetCardsList).

Передавать документы в массиве `characteristics` теперь можно только:

- если вы ещё ни разу не указывали в запросах объект `documents`
- если вы не указывали документы в личном кабинете в [обновлённом блоке Документы](https://seller.wildberries.ru/news-v2/news-details?id=13738) в карточке товара

Рекомендуем передавать документы только с помощью объекта `documents`, поскольку, если вы передаёте документы в массиве `characteristics`, эти документы могут быть обработаны некорректно для любых карточек.

Документы, которые уже были в карточках товаров, будут автоматически продублированы в объекте `documents` в ответах метода [POST /content/v2/get/cards/list](/docs/openapi/item-management#tag/listings/operation/postV2GetCardsList).

Напоминаем, что карточки товаров перезаписываются при обновлении. Поэтому передавайте в запросах метода [POST /content/v2/cards/update](/docs/openapi/item-management#tag/listings/operation/postV2CardsUpdate) в том числе те документы, которые вы не собираетесь обновлять.

Изменения

## 04.09.2026

Критичное изменение

Заказы FBS

Поставки FBS

Изменения в Поставках FBS

Обновили описание метода [POST /api/v3/supplies/{supplyId}/trbx](./docs/openapi/orders-fbs#tag/fbsSupplies/operation/postV3SuppliesSupplyIdTrbx) — Добавить грузоместа к поставке в соответствии с [инструкцией](https://seller.wildberries.ru/instructions/ru/ru/material/step-three-b-fbs-shipment-delivery-to-pick-up-point?goBackOption=prevRoute&categoryId=48c727fd-ad27-45f5-a0fb-3e62e9b853e8) на портале продавца:

В одном грузоместе может быть несколько заказов. Например, если в поставке 10 заказов, распределите их по коробам: система позволит создать не больше 5 грузомест. Для 20 заказов — не больше 10 грузомест, для 100 — не больше 50.

Новое

## 03.09.2026

Заказы FBS

Поставки FBS

Новые методы Поставок FBS

Добавили методы для работы с данными [СПОТ](https://www.nalog.gov.ru/rn77/related_activities/spot/) — системы ввоза товаров автомобильным транспортом из стран ЕАЭС. Заполнять данные СПОТ обязательно для всех поставок из ЕАЭС в РФ.

С помощью новых методов вы можете:

- Получать список стран ОКСМ — [GET /api/marketplace/v3/fbs/dictionaries/countries/oksm](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3FbsDictionariesCountriesOksm)
- Добавлять данные СПОТ в поставку — [PUT /api/marketplace/v3/fbs/supplies/{supplyId}/spot](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/putV3FbsSuppliesSupplyIdSpot)
- Получать данные СПОТ для списка поставок — [POST /api/marketplace/v3/fbs/supplies/spot/list](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/postV3FbsSuppliesSpotList)
- Получать сформированные QR-коды СПОТ — [GET /api/marketplace/v3/fbs/supplies/{supplyId}/stickers/spot](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3FbsSuppliesSupplyIdStickersSpot)

Также добавили поле `spotAvailable` — доступен ли СПОТ для данной поставки — в методы:

- Получить список поставок — [GET /api/v3/supplies](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3Supplies)
- Получить информацию о поставке — [GET /api/v3/supplies/{supplyId}](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3SuppliesSupplyId)

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

- Получить список мест отгрузки поставок — [GET /api/marketplace/v3/fbs/shipping-points](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3FbsShippingPoints)
- Установить параметры отгрузки поставок — [PATCH /api/marketplace/v3/fbs/supplies/shipping-method](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesShippingMethod)

Для доставки транспортной компанией можно будет указывать ID ЭТрН — электронной транспортной накладной. Чтобы добавить ID ЭТрН в поставку, нужно будет использовать метод [PATCH /api/marketplace/v3/fbs/supplies/waybill](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesWaybill). Пока метод находится в доработке, о его доступности сообщим дополнительно.

С **1 октября** добавление параметров отгрузки и ID ЭТрН станет обязательным. Без этого нельзя будет перевести поставку в доставку — вы получите ошибку `409` в методе [PATCH /api/v3/supplies/ {supplyId} /deliver](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/patchV3SuppliesSupplyIdDeliver).

Новое

## 24.08.2026

Аналитика и данные

История остатков

Новый отчёт по остаткам на складах продавца

Добавили отчёт по остаткам на складах продавца — [POST /api/analytics/v1/stocks-report/seller-warehouses](/docs/openapi/analytics#tag/stocksReport/operation/postAnalyticsV1StocksReportSellerWarehouses).

Используйте новый отчёт вместо метода [POST /api/v3/stocks/{warehouseId}](/docs/openapi/work-with-products#tag/sellerWarehousesInventory/operation/postV3StocksWarehouseId), чтобы получить остатки без указания ID складов продавца и ID размеров в запросе.

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

С **18 августа** добавить номер декларации на товары (ДТ) можно будет только к сборочным заданиям в [статусе](https://dev.wildberries.ru/docs/openapi/orders-fbs/#tag/fbsAssemblyOrders/operation/postV3OrdersStatus) `confirm`.

Также с **18 августа** продавцам из Армении будет обязательно указывать номер ДТ для товаров, произведённых вне ЕАЭС, если заказ из Армении доставляется в РФ.

Чтобы проверить, обязательно ли закреплять номер ДТ за сборочным заданием, используйте метод [GET /api/v3/orders/new](/docs/openapi/orders-fbs#tag/fbsAssemblyOrders/operation/getV3OrdersNew). Обязательные идентификаторы маркировки указаны в поле `requiredMeta`.

Чтобы добавить номер ДТ к сборочному заданию, передайте его в запросе метода [PUT /api/marketplace/v3/orders/{orderId}/meta/customs-declaration](/docs/openapi/orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaCustomsDeclaration) в параметре `customsDeclaration`.

Без обязательного номера ДТ невозможно получить стикеры сборочных заданий методом [POST /api/v3/orders/stickers](/docs/openapi/orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStickers) — если хотя бы для одного сборочного не будет указан обязательный номер ДТ, вы получите ошибку `409` `CustomsDeclarationIsRequired`.

Также, если к сборочному заданию не добавлен обязательный номер ДТ, поставку с этим сборочным заданием невозможно перевести в доставку. В ответе метода [PATCH /api/v3/supplies/{supplyId}/deliver](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/patchV3SuppliesSupplyIdDeliver) вы получите ошибку `409` `MetaValidationFail`, при этом в поле `decision` для `customsDeclaration` вернётся значение `required`.

Чтобы проверить, добавлен ли обязательный номер ДТ к сборочному заданию, до перевода поставки в доставку, используйте метод [POST /api/marketplace/v3/orders/meta](/docs/openapi/orders-fbs/#tag/fbsLabelIdentifiers/operation/postV3OrdersMeta). Перевести поставку в доставку можно со статусами `filled` или `optional` в поле `decision` для `customsDeclaration`.

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

- Получить список складов WB — [GET /api/v3/offices](/docs/openapi/work-with-products#tag/sellerWarehouses/operation/getV3Offices) — в ответе теперь не будут возвращаться СГТ-склады WB
- Создать склад продавца — [POST /api/v3/warehouses](/docs/openapi/work-with-products#tag/sellerWarehouses/operation/postV3Warehouses) — при создании СГТ-склада вы получите ошибку `404`
- Обновить склад продавца — [PUT /api/v3/warehouses/ {warehouseId}](/docs/openapi/work-with-products#tag/sellerWarehouses/operation/putV3WarehousesWarehouseId) — при изменении данных СГТ-склада вы получите ошибку `404`

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

Заблокированные карточки

Новая версия Оценки товара и отключение метода Скрытые из каталога

Добавили новую версию метода получения отчёта **Оценка товара** — [POST /api/analytics/v2/item-rating](/docs/openapi/analytics#tag/itemRating/operation/postV2ItemRating). C её помощью вы можете получать данные отдельно по скрытым из каталога товарам.

В новом методе:

- добавили параметр `onlyShadowedNms`:   укажите `true`, чтобы получить в отчёте только скрытые из каталога товары укажите `false`, чтобы получить в отчёте все товары, если не указаны другие параметры
- добавили поле `isShadowed` — является ли товар скрытым из каталога
- изменили наименование массива ответа `cards` на `items`
- изменили наименование параметра `isNotIncludeNMsWithoutSales` на `isNotIncludeNmsWithoutSales`

Метод доступен по **Персональному** или **Сервисному** [токену](/docs/openapi/api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) для категории **Аналитика**.

Текущие методы **POST /api/analytics/v1/item-rating** и **GET /api/v1/analytics/banned-products/shadowed** будут отключены **30 июля**.

Мы используем [cookies](/privacy) для сбора статистики и улучшения сервиса
