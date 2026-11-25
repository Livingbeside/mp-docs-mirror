---
title: Журнал изменений WB API
api: wildberries
kind: changelog
source: "https://dev.wildberries.ru/release-notes"
window: последние записи, страница отдаёт не всю историю
fetched_at: "2026-11-25T05:10:44Z"
content_sha: 6fe47b22d99d6a79
---

# Журнал изменений WB API

> Страница WB отдаёт в DOM только последние записи (прокрутка остальные не подгружает), поэтому здесь скользящее окно, а не вся история. Полная история накапливается в git: `mpdocs changes`.

# Журнал изменений

2026

Ноя

Пн

23

Вт

24

Ср

25

Чт

26

Пт

27

Сб

28

Вс

29

Пн

30

Поиск

Все обновления

Выберите теги

Все обновления

Новое

Изменения

Устарело

Ноябрь
2026

Изменения

## 24.11.2026

Аналитика и данные

Лента заказов

Изменения в отображении складов WB в Ленте заказов

C **24 ноября** по-новому отображаем склады WB в строках [Ленты заказов](/docs/openapi/analytics#tag/orderFeed):

Список значений

Изменения

## 19.11.2026

Заказы FBS

Сборочные задания FBS

Новый статус сборочных заданий для трансграничных поставок

В ответ метода [POST /api/v3/orders/status](/docs/openapi/orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus) добавили новый статус для трансграничных поставок — `delivering_by_carrier`. Статус означает, что заказ передан перевозчику и находится в пути на склад WB.

Новый статус будет возвращаться в поле `wbStatus` вместо устаревших статусов `accepted_by_carrier` и `sent_to_carrier`. Устаревшие статусы останутся в ответе для сборочных заданий, созданных до **12 ноября**.

Новое

## 18.11.2026

Маркетинг и продвижение

Статистика

Изменения в API Продвижения

Добавили методы в API Продвижения:

- [GET /api/advert/v4/fullstats](/en/docs/openapi/promotion#tag/statistics/operation/getV4Fullstats) — новая версия статистики по кампаниям. Используйте, чтобы получать статистику кампаний в плоском формате с разделением по зонам показов и типам конверсии.
- [GET /api/advert/v0/positions](/en/docs/openapi/promotion#tag/statistics/operation/getV0Positions) — метод получения позиций карточек товаров в поисковой выдаче. Используйте, чтобы получать медианные позиции карточек товаров в поисковой выдаче и распределение показов по фиксированным диапазонам позиций.

Об отключении текущего метода [GET /adv/v3/fullstats](/en/docs/openapi/promotion#tag/statistics/operation/getV3Fullstats) сообщим дополнительно.

Устарело

## 16.11.2026

Критичное изменение

Маркетинг и продвижение

Финансы

Изменения в API Продвижения

Напоминаем, что сегодня мы начинаем [отключать](https://dev.wildberries.ru/release-notes?id=582) устаревший метод получения бюджета кампаний [GET /adv/v1/budget](/docs/openapi/promotion/#tag/finances/operation/getV1Budget).

Изменения

## 16.11.2026

Общее

Управление пользователями продавца

Изменения в Управлении пользователями продавца

Теперь с помощью WB API вы можете настроить доступ к получению отчёта [Оценка товара](https://seller.wildberries.ru/content-ratings) для пользователей профиля продавца.

Чтобы добавить пользователю право получать отчёт на Портале продавцов, укажите для этого пользователя `"code":"reportRating"` в массиве `access` в запросах методов:

- [POST /api/v1/invite](/docs/openapi/api-information#tag/sellerUserManagement/operation/postV1Invite)
- [PUT /api/v1/users/access](/docs/openapi/api-information#tag/sellerUserManagement/operation/putV1UsersAccess)

Новое

## 12.11.2026

Поставки FBW

Информация о поставках

Изменения в поставках FBW

В метод [GET /api/v1/supplies/{ID}/package](/docs/openapi/orders-fbw#tag/suppliesInformation/operation/getV1SuppliesIdPackage) добавили поле `packageId` — ID QR-стикера упаковки.

В поле `packageCode` теперь возвращается только закодированное значение QR-стикера упаковки.

Новое

## 09.11.2026

Критичное изменение

Маркетинг и продвижение

Кампании

Новая версия Информации о кампаниях

Добавили новую версию метода получения информации о кампаниях — [GET /api/advert/v3/adverts](/docs/openapi/promotion#tag/campaigns/operation/getV3Adverts).

Теперь с помощью WB API вы можете получить информацию не только по списку ID кампаний, но и по всем рекламным кампаниям — для этого используйте параметры пагинации limit и next.

Текущий метод [GET /api/advert/v2/adverts](/docs/openapi/promotion#tag/campaigns/operation/getV2Adverts) будет отключен **10 января**.

Изменения

## 03.11.2026

Аналитика и данные

Аналитика продавца CSV

История остатков

Отчёты

Основные отчёты

Изменения в отображении складов в WB API с 9 ноября

C **9 ноября** будем по-новому отображать склады:

- в строках отчёта [Остатки на складах WB](/docs/openapi/analytics#tag/stocksReport/operation/postV1StocksReportWbWarehouses):

Список значений

- в строках отчёта [Данные по размерам](/docs/openapi/analytics#tag/stocksReport/operation/postV2StocksReportProductsSizes):

Список значений

- в строках отчёта [Данные по складам](/docs/openapi/analytics#tag/stocksReport/operation/postV2StocksReportOffices):

Список значений

- в строках отчётов по остаткам [Аналитики продавца CSV](/docs/openapi/analytics#tag/sellerAnalyticsCsv/operation/getV2NmReportDownloadsFileDownloadId):

Список значений

- в строках отчётов [Заказы](/docs/openapi/reports#tag/mainReports/operation/getV1SupplierOrders) и [Продажи](/docs/openapi/reports#tag/mainReports/operation/getV1SupplierSales): выделим СГТ-склады отгрузки в РФ с помощью значения поля `warehouseName` — `Склад WB СГТ РФ`. Будет доступно для заказов и продаж со значением `date` от 9 ноября

Октябрь
2026

Новое

## 27.10.2026

Общее

API коммуникаций

Новый метод API коммуникаций

Добавили метод [GET /api/communications/v1/notifications](/docs/openapi/api-information#tag/newsApi/operation/getV1Notifications). С его помощью вы можете получать уведомления [WB Partners](https://seller.wildberries.ru/) на русском языке.

Метод доступен только для продавцов из РФ.

Устарело

## 21.10.2026

Поставки FBW

Маркетинг и продвижение

Отчёты

Отключение песочниц Статистика, Поставки FBW, Продвижение

C **5 ноября** отключим [песочницы](https://dev.wildberries.ru/sandbox) на следующих адресах:

- https://statistics-api-sandbox.wildberries.ru
- https://supplies-api-sandbox.wildberries.ru
- https://advert-api-sandbox.wildberries.ru

Новое

## 20.10.2026

Заказы FBS

Поставки FBS

Новый метод получения пунктов отгрузки

Добавили новую версию метода получения списка пунктов отгрузки — [GET /api/marketplace/v3/fbs/supplies/{supplyId}/shipping-points](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3FbsSuppliesSupplyIdShippingPoints). Теперь с помощью WB API вы можете получить список пунктов, доступных для отгрузки указанной в запросе поставки. Используйте эту информацию, чтобы устанавливать параметры отгрузки поставок методом [PATCH /api/marketplace/v3/fbs/supplies/shipping-method](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesShippingMethod).

Текущую версию метода — [GET /api/marketplace/v3/fbs/shipping-points](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/getV3FbsShippingPoints) — отключим **20** **ноября**.

Новое

## 15.10.2026

Заказы FBS

Поставки FBS

Трек-номер для трансграничных поставок

В ответ метода [GET /api/v3/orders](/docs/openapi/orders-fbs#tag/fbsAssemblyOrders/operation/getV3Orders) добавили поле `trackNumber` с информацией о трек-номере для трансграничных поставок.

Изменения

## 14.10.2026

Общее

Информация о продавце

Изменения в методе Получить информацию о продавце

В метод [GET /api/v1/seller-info](/docs/openapi/api-information#tag/sellerInformation/operation/getV1SellerInfo) добавили поле `country` — информацию о стране регистрации профиля продавца.

Новое

## 14.10.2026

Заказы FBS

Поставки FBS

Перевод сборочных заданий с доставки на сборку

Добавили метод перевода сборочного задания с доставки на сборку — [PATCH /api/marketplace/v3/fbs/supplies/{supplyId}/orders/transfer](https://dev.wildberries.ru/docs/openapi/orders-fbs/#tag/fbsSupplies/operation/patchV3FbsSuppliesSupplyIdOrdersTransfer). Используйте метод, чтобы переместить сборочное задание из закрытой поставки в открытую.

Сборочное задание можно перевести из доставки на сборку, если выполняются все условия:

- сборочное задание находится в статусе `complete` — в доставке
- поставка, в которую нужно перенести сборочное задание, [не передана в доставку](/docs/openapi/orders-fbs#tag/fbsSupplies/operation/patchV3SuppliesSupplyIdDeliver)
- сборочное задание ранее не переносили из закрытой поставки в открытую

Чтобы проверить, можно ли перевести сборочное задание из доставки на сборку, используйте метод [получения статусов сборочных заданий](/docs/openapi/orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStatus), поле `isTransferable`.

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

Мы используем [cookies](https://legal.wildberries.ru/global-confidentiality-policy/country/ru/lang/ru/#anchor-4.4), чтобы анализировать, как вы пользуетесь сайтом, и улучшать его
