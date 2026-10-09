---
title: Журнал изменений WB API
api: wildberries
kind: changelog
source: "https://dev.wildberries.ru/release-notes"
window: последние записи, страница отдаёт не всю историю
fetched_at: "2026-10-09T02:05:22Z"
content_sha: ba6b9dfec8985a89
---

# Журнал изменений WB API

> Страница WB отдаёт в DOM только последние записи (прокрутка остальные не подгружает), поэтому здесь скользящее окно, а не вся история. Полная история накапливается в git: `mpdocs changes`.

# Журнал изменений

2026

Окт

Пн

5

Вт

6

Ср

7

Чт

8

Пт

9

Сб

10

Вс

11

Пн

12

Поиск

Все обновления

Выберите теги

Все обновления

Новое

Изменения

Устарело

Октябрь
2026

Новое

## 08.10.2026

DBS

Сборочные задания DBS

Изменения в песочнице Маркетплейс

Добавили параметр `deliveryType` — тип доставки — в запрос метода [POST /api/v3/test/dbs/orders/make](/docs/openapi-other/sandbox-environment#tag/marketplaceDbs/operation/postV3TestDbsOrdersMake).

Теперь вы можете создавать тестовые сборочные задания моделей DBS в ПВЗ и EDBS.

Изменения

## 07.10.2026

Аналитика и данные

Поисковые запросы по вашим товарам

Изменение времени обновления данных в Поисковых запросах по вашим товарам

С **12 октября** данные по поисковым запросам по вашим товарам будут обновляться 1 раз в 2 часа в отчётах:

- [Основная страница](/docs/openapi/analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportReport)
- [Пагинация по группам](/docs/openapi/analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportTableGroups)
- [Пагинация по товарам в группе](/docs/openapi/analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportTableDetails)
- [Поисковые запросы по товару](/docs/openapi/analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportProductSearchTexts)
- [Заказы и позиции по поисковым запросам товара](/docs/openapi/analytics#tag/searchQueriesForYourItems/operation/postV2SearchReportProductOrders)
- `SEARCH_QUERIES_PREMIUM_REPORT_GROUP` — отчёт по параметрам поиска по предметам, брендам и ярлыкам в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)
- `SEARCH_QUERIES_PREMIUM_REPORT_PRODUCT` — отчёт по параметрам поиска по артикулам WB в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)
- `SEARCH_QUERIES_PREMIUM_REPORT_TEXT` — отчёт по текстам поисковых запросов в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)

Новое

## 06.10.2026

DBS

Сборочные задания DBS

Изменения в сборочных заданиях DBS

В метод [POST /api/v3/dbs/orders/client](/docs/openapi/dbs#tag/dbsAssemblyOrders/operation/postV3DbsOrdersClient) добавили поля с дополнительными номерами телефонов для связи с покупателем:

- `additionalPhones` — дополнительные номера
- `replacementAdditionalPhones` — дополнительные подменные номера

Устарело

## 05.10.2026

Отчёты

Продажи по регионам

Отключение отчёта Продажи по регионам

С **3 ноября** [отключим](https://seller.wildberries.ru/news-v2/news-details?id=14313) метод [GET /api/v1/analytics/region-sale](/docs/openapi/reports#tag/salesByRegions/operation/getV1AnalyticsRegionSale). Чтобы получить статистику продаж по регионам, используйте данные отчёта [Лента заказов](/docs/openapi/analytics#tag/orderFeed/operation/postV1OrderFeed) — подробнее в [инструкции](/knowledge-base/articles/01a09d9e-4f79-7016-b641-0718252e6572/lenta-zakazov#prodazhi-po-regionam).

Новое

## 02.10.2026

Работа с товарами

Создание карточек товаров

Карточки товаров

Дополнительный GTIN в карточках товаров

Добавили параметр `gtin` в методы:

- [POST content/v2/cards/upload](/docs/openapi/item-management#tag/listingItems/operation/postV2CardsUpload)
- [POST content/v2/cards/update](/docs/openapi/item-management#tag/listings/operation/postV2CardsUpdate)
- [POST content/v2/cards/upload/add](/docs/openapi/item-management#tag/listingItems/operation/postV2CardsUploadAdd)

Указывайте дополнительный GTIN в новом параметре только если такое же значение GTIN вы ранее указывали в одной из карточек товара в параметре `skus`. Нельзя указывать один и тот же GTIN в `skus` для разных карточек или размеров товаров

Дополнительный `gtin` теперь также возвращается в ответе метода [POST content/v2/get/cards/list](/docs/openapi/item-management#tag/listings/operation/postV2GetCardsList) — поле `gtin`.

Новое

## 01.10.2026

Критичное изменение

Аналитика и данные

Поисковые запросы по вашим товарам

Изменения в Аналитике продавца CSV

С **12 октября** в отчёте по текстам поисковых запросов по вашим товарам —`SEARCH_QUERIES_PREMIUM_REPORT_TEXT` — метода [GET /api/v2/nm-report/downloads/file/{downloadId}](/docs/openapi/analytics/#tag/sellerAnalyticsCsv/operation/getV2NmReportDownloadsFileDownloadId) отключим поля:

- `OpenCardPercentile` — процент, на который показатель количества открытий карточки товара выше, чем у карточек других продавцов по поисковому запросу
- `AddToCartPercentile` — процент, на который показатель добавлений в корзину выше, чем у карточек других продавцов по поисковому запросу
- `OpenToCartPercentile` — процент, на который показатель конверсии в корзину выше, чем у карточек других продавцов по поисковому запросу
- `OrdersPercentile` — процент, на который показатель заказов выше, чем у карточек других продавцов по поисковому запросу
- `CartToOrderPercentile` — процент, на который показатель конверсии в заказ выше, чем у карточек других продавцов по поисковому запросу

Сентябрь
2026

Новое

## 30.09.2026

Работа с товарами

Категории, предметы и характеристики

Новые методы для работы с товарами

Добавили методы для работы с карточками товаров. Теперь с помощью WB API вы можете получить:

- Список кодов ТН ВЭД — [GET /api/content/v2/directory/tnved/all](/docs/openapi/item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryTnvedAll)
- Код ОКПД2 предмета — [GET /api/content/v2/directory/okpd](/docs/openapi/item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryOkpd)
- Список кодов ОКПД2 — [GET /api/content/v2/directory/okpd/all](/docs/openapi/item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryOkpdAll)

Изменения

## 28.09.2026

Аналитика и данные

Воронка продаж

Аналитика продавца CSV

Изменение времени обновления данных в Воронке продаж и Аналитике продавца CSV

С **24 сентября** данные обновляются 1 раз в 2 часа в следующих отчётах:

- [Статистика карточек товаров за период](/docs/openapi/analytics/#tag/salesFunnel/operation/postV3SalesFunnelProducts)
- [Статистика карточек товаров по дням](/docs/openapi/analytics/#tag/salesFunnel/operation/postV3SalesFunnelProductsHistory)
- [Статистика групп карточек товаров по дням](/docs/openapi/analytics/#tag/salesFunnel/operation/postV3SalesFunnelGroupedHistory)
- DETAIL_HISTORY_REPORT — отчёт воронки продаж по артикулам WB в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)
- GROUPED_HISTORY_REPORT — отчёт воронки продаж по предметам, брендам и ярлыкам в методе [POST /api/v2/nm-report/downloads](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/postV2NmReportDownloads)

Чтобы получить текущие данные без задержки обновления, используйте метод [POST /api/analytics/v1/order-feed](/docs/openapi/analytics/#tag/orderFeed/operation/postV1OrderFeed).

Новое

## 28.09.2026

Документы и бухгалтерия

Финансовые отчёты

Новые поля в детализациях к отчётам реализации

Добавили [новые поля](https://seller.wildberries.ru/news-v2/news-details?id=14226) в детализации к отчётам реализации [POST /api/finance/v1/sales-reports/detailed/{reportId}](/docs/openapi/financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) и [POST api/finance/v1/sales-reports/detailed](/docs/openapi/financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed):

- `buyerTaxRegistrationReasonCode` — КПП B2B-покупателя
- `utdUcdNumber` — номер УПД или УКД
- `utdUcdDate` — дата УПД или УКД

Новое

## 24.09.2026

Критичное изменение

Отчёты

Отчёт о возвратах и перемещении товаров

Новая версия отчёта по возвратам и перемещению товаров

Добавили новую версию метода получения отчёта **Возврат и перемещение товаров** — [GET /api/analytics/v1/goods-return](/docs/openapi/reports#tag/returnsAndItemMovementReport/operation/getV1GoodsReturn). C её помощью вы можете получать данные как по активным, так и по архивным возвратам за любой период времени.

В новом методе:

- добавили параметр `status`:   укажите `active`, чтобы получить в отчёте только активные возвраты укажите `archive`, чтобы получить в отчёте только архивные возвраты
- добавили пагинацию — параметры `limit` и `offset`

Метод доступен по [токену](/docs/openapi/api-information#tag/authorization) любого типа для категории **Аналитика**.

Текущий метод [GET /api/v1/analytics/goods-return](/docs/openapi/reports/#tag/returnsAndItemMovementReport/operation/getV1GoodsReturn) будет отключен **26 октября**.

Новое

## 23.09.2026

Маркетинг и продвижение

Управление кампаниями

Дневные лимиты кампаний в API Продвижения

Добавили методы для работы с дневными лимитами кампаний CPC. Теперь с помощью WB API вы можете:

- Получить настройки дневных лимитов кампаний — [GET /api/advert/v0/daily-limits](/docs/openapi/promotion/#tag/campaignManagement/operation/getV0DailyLimits)
- Управлять дневными лимитами — [PUT /api/advert/v0/daily-limits](/docs/openapi/promotion/#tag/campaignManagement/operation/putV0DailyLimits)

Методы доступны по **Персональному** и **Сервисному** токену категории **Продвижение**.

В ответ метода [GET /api/advert/v1/config](/docs/openapi/promotion/#tag/campaignManagement/operation/getV1Config) добавили поле `minDailyLimit` — минимально допустимый размер дневного лимита, вне зависимости от ставок кампании.

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

Чтобы получить текущие данные по остаткам без задержки обновления, используйте методы [POST /api/analytics/v1/stocks-report/wb-warehouses](/docs/openapi/analytics/#tag/stocksReport/operation/postV1StocksReportWbWarehouses) и [POST /api/analytics/v1/stocks-report/seller-warehouses](/docs/openapi/analytics#tag/stocksReport/operation/postV1StocksReportSellerWarehouses).

Новое

## 16.09.2026

Критичное изменение

Маркетинг и продвижение

Финансы

Изменения в API Продвижения

Добавили новую версию метода получения бюджета кампаний — [POST /api/advert/v2/budget](https://dev.wildberries.ru/docs/openapi/promotion/#tag/finances/operation/postV2Budget). Теперь с помощью WB API вы можете получить остатки бюджетов по нескольким кампаниям одним запросом.

Текущий метод [GET /adv/v1/budget](https://dev.wildberries.ru/docs/openapi/promotion/#tag/finances/operation/getV1Budget) будет отключён **16 ноября**.

Изменения

## 10.09.2026

Отчёты

Отчёты об удержаниях

Изменения в Отчётах об удержании

Добавили новые поля в отчёт об удержаниях за занижение габаритов упаковки [GET /api/analytics/v1/measurement-penalties](/docs/openapi/reports#tag/retentionReports/operation/getV1MeasurementPenalties):

- `dateStart` — дата начала действия коэффициента
- `dateEnd` — дата окончания действия коэффициента

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

Мы используем [cookies](https://legal.wildberries.ru/privacypolicy/country/ru/lang/ru/#anchor-7), чтобы анализировать, как вы пользуетесь сайтом, и улучшать его
