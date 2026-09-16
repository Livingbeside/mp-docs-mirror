---
title: Общие методы
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md"
fetched_at: "2026-09-16T02:26:59Z"
content_sha: f20bb28139fe2aa2
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/business.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/business.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Общие для всех моделей методы

<!-- source: ru/_auto/methods_summary/business.md -->
## Кабинеты и магазины

#|
|| **Метод** | **Описание метода** ||
||
[GET v2/​campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md)
{style="max-width: 400px"}
|
Список магазинов пользователя
||
||
[POST v2/​businesses/​{businessId}/​settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md)
{style="max-width: 400px"}
|
Настройки кабинета
||
|#

## Товары

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​categories/​tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md)
{style="max-width: 400px"}
|
Дерево категорий
||
||
[POST v2/​category/​{categoryId}/​parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md)
{style="max-width: 400px"}
|
Списки характеристик товаров по категориям
||
||
[POST v2/​businesses/​{businessId}/​offer-mappings/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
{style="max-width: 400px"}
|
Добавление товаров в каталог и изменение информации о них
||
||
[POST v1/​businesses/​{businessId}/​offer-mappings/​barcodes/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/generateOfferBarcodes.md)
{style="max-width: 400px"}
|
Генерация штрихкодов
||
||
[POST v2/​businesses/​{businessId}/​offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)
{style="max-width: 400px"}
|
Получение информации о заполненности карточек магазина
||
||
[POST v2/​businesses/​{businessId}/​offer-cards/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)
{style="max-width: 400px"}
|
Редактирование категорийных характеристик товара
||
||
[POST v1/​businesses/​{businessId}/​offers/​documents/​create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/createDocuments.md)
{style="max-width: 400px"}
|
Создание документов
||
||
[POST v1/​businesses/​{businessId}/​offers/​documents/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/updateDocuments.md)
{style="max-width: 400px"}
|
Обновление документов
||
||
[POST v1/​businesses/​{businessId}/​offers/​documents/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/deleteDocuments.md)
{style="max-width: 400px"}
|
Удаление документов
||
||
[POST v1/​businesses/​{businessId}/​offers/​documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/getDocuments.md)
{style="max-width: 400px"}
|
Получение документов
||
||
[POST v2/​businesses/​{businessId}/​offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md)
{style="max-width: 400px"}
|
Информация о товарах в каталоге
||
||
[POST v2/​businesses/​{businessId}/​offer-mappings/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffers.md)
{style="max-width: 400px"}
|
Удаление товаров из каталога
||
||
[POST v2/​businesses/​{businessId}/​offer-mappings/​archive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/addOffersToArchive.md)
{style="max-width: 400px"}
|
Добавление товаров в архив
||
||
[POST v2/​businesses/​{businessId}/​offer-mappings/​unarchive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffersFromArchive.md)
{style="max-width: 400px"}
|
Удаление товаров из архива
||
|#

## Остатки и оборачиваемость

#|
|| **Метод** | **Описание метода** ||
||
[POST v3/​businesses/​{businessId}/​offers/​stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md)
{style="max-width: 400px"}
|
Информация об остатках
||
||
[POST v3/​businesses/​{businessId}/​offers/​stocks/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md)
{style="max-width: 400px"}
|
Передача информации об остатках
||
|#

## Цены

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​businesses/​{businessId}/​offer-prices/​updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)
{style="max-width: 400px"}
|
Установка цен на товары для всех магазинов
||
||
[POST v2/​businesses/​{businessId}/​offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getDefaultPrices.md)
{style="max-width: 400px"}
|
Просмотр цен на указанные товары во всех магазинах
||
||
[POST v2/​businesses/​{businessId}/​offers/​recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/getOfferRecommendations.md)
{style="max-width: 400px"}
|
Рекомендации Маркета, касающиеся цен
||
||
[POST v2/​businesses/​{businessId}/​price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getBusinessQuarantineOffers.md)
{style="max-width: 400px"}
|
Список товаров, находящихся в карантине по цене в кабинете
||
||
[POST v2/​businesses/​{businessId}/​price-quarantine/​confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmBusinessPrices.md)
{style="max-width: 400px"}
|
Удаление товара из карантина по цене в кабинете
||
|#

## Акции

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​businesses/​{businessId}/​promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md)
{style="max-width: 400px"}
|
Получение списка акций
||
||
[POST v2/​businesses/​{businessId}/​promos/​offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)
{style="max-width: 400px"}
|
Получение списка товаров, которые участвуют или могут участвовать в акции
||
||
[POST v2/​businesses/​{businessId}/​promos/​offers/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)
{style="max-width: 400px"}
|
Добавление товаров в акцию или изменение их цен
||
||
[POST v2/​businesses/​{businessId}/​promos/​offers/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md)
{style="max-width: 400px"}
|
Удаление товаров из акции
||
|#

## Заказы

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/​businesses/​{businessId}/​orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)
{style="max-width: 400px"}
|
Информация о заказах в кабинете
||
||
[POST v1/​businesses/​{businessId}/​operations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/operations/getOperations.md)
{style="max-width: 400px"}
|
Получение статусов операций
||
|#

## Невыкупы и возвраты

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/​businesses/​{businessId}/​returns/​decisions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturnAvailableDecisions.md)
{style="max-width: 400px"}
|
Получение возможных решений по возврату
||
|#

## Отчеты и документы

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​reports/​united-returns/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedReturnsReport.md)
{style="max-width: 400px"}
|
Отчет по невыкупам и возвратам
||
||
[POST v2/​reports/​stocks-on-warehouses/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksOnWarehousesReport.md)
{style="max-width: 400px"}
|
Отчет по остаткам на складах
||
||
[POST v3/​businesses/​{businessId}/​reports/​stocks/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateStocksReport.md)
{style="max-width: 400px"}
|
Отчет по остаткам на складах партнера
||
||
[POST v2/​reports/​united-marketplace-services/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateUnitedMarketplaceServicesReport.md)
{style="max-width: 400px"}
|
Отчет по стоимости услуг
||
||
[POST v2/​reports/​closure-documents/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsReport.md)
{style="max-width: 400px"}
|
Закрывающие документы
||
||
[POST v2/​reports/​closure-documents/​detalization/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md)
{style="max-width: 400px"}
|
Отчет по схождению с закрывающими документами
||
||
[POST v1/​businesses/​{businessId}/​reports/​marketing-detalization/​generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateMarketingDetalizationReport.md)
{style="max-width: 400px"}
|
Отчет по счету маркетинга
||
||
[GET v2/​reports/​info/​{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md)
{style="max-width: 400px"}
|
Получение заданного отчета или документа
||
|#

## Отзывы о товарах

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​businesses/​{businessId}/​goods-feedback](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacks.md)
{style="max-width: 400px"}
|
Получение отзывов о товарах продавца
||
||
[POST v1/​businesses/​{businessId}/​goods-feedback-advertiser](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbacksUrbanads.md)
{style="max-width: 400px"}
|
Получение отзывов о товарах для рекламодателей
||
||
[POST v2/​businesses/​{businessId}/​goods-feedback/​comments](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/getGoodsFeedbackComments.md)
{style="max-width: 400px"}
|
Получение комментариев к отзыву
||
||
[POST v2/​businesses/​{businessId}/​goods-feedback/​comments/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md)
{style="max-width: 400px"}
|
Добавление нового или изменение созданного комментария
||
||
[POST v2/​businesses/​{businessId}/​goods-feedback/​skip-reaction](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/skipGoodsFeedbacksReaction.md)
{style="max-width: 400px"}
|
Пропуск реакции на отзывы
||
||
[POST v2/​businesses/​{businessId}/​goods-feedback/​comments/​delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/deleteGoodsFeedbackComment.md)
{style="max-width: 400px"}
|
Удаление комментария к отзыву
||
|#

## Вопросы и ответы о товарах

#|
|| **Метод** | **Описание метода** ||
||
[POST v1/​businesses/​{businessId}/​goods-questions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestions.md)
{style="max-width: 400px"}
|
Получение вопросов о товарах продавца
||
||
[POST v1/​businesses/​{businessId}/​goods-questions/​answers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/getGoodsQuestionAnswers.md)
{style="max-width: 400px"}
|
Получение ответов на вопрос
||
||
[POST v1/​businesses/​{businessId}/​goods-questions/​update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md)
{style="max-width: 400px"}
|
Создание, изменение и удаление ответа или комментария
||
|#

## Буст продаж

#|
|| **Метод** | **Описание метода** ||
||
[PUT v2/​businesses/​{businessId}/​bids](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/putBidsForBusiness.md)
{style="max-width: 400px"}
|
Включение буста продаж и установка ставок
||
||
[POST v2/​businesses/​{businessId}/​bids/​info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsInfoForBusiness.md)
{style="max-width: 400px"}
|
Информация об установленных ставках
||
||
[POST v2/​businesses/​{businessId}/​bids/​recommendations](https://yandex.ru/dev/market/partner-api/doc/ru/reference/bids/getBidsRecommendations.md)
{style="max-width: 400px"}
|
Рекомендованные ставки для заданных товаров
||
|#

## Индекс качества

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​businesses/​{businessId}/​ratings/​quality](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatings.md)
{style="max-width: 400px"}
|
Индекс качества магазинов
||
|#

## Чаты

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​businesses/​{businessId}/​chats/​history](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatHistory.md)
{style="max-width: 400px"}
|
Получение истории сообщений в чате
||
||
[GET v2/​businesses/​{businessId}/​chat](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChat.md)
{style="max-width: 400px"}
|
Получение чата по идентификатору
||
||
[POST v2/​businesses/​{businessId}/​chats](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChats.md)
{style="max-width: 400px"}
|
Получение доступных чатов
||
||
[GET v2/​businesses/​{businessId}/​chats/​message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md)
{style="max-width: 400px"}
|
Получение сообщения в чате
||
||
[POST v2/​businesses/​{businessId}/​chats/​new](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/createChat.md)
{style="max-width: 400px"}
|
Создание нового чата с покупателем
||
||
[POST v2/​businesses/​{businessId}/​chats/​message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendMessageToChat.md)
{style="max-width: 400px"}
|
Отправка сообщения в чат
||
||
[POST v2/​businesses/​{businessId}/​chats/​file/​send](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendFileToChat.md)
{style="max-width: 400px"}
|
Отправка файла в чат
||
|#

## Склады

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​businesses/​{businessId}/​warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPagedWarehouses.md)
{style="max-width: 400px"}
|
Список складов
||
||
[POST v3/​businesses/​{businessId}/​warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md)
{style="max-width: 400px"}
|
Список складов
||
||
[POST v3/​businesses/​{businessId}/​warehouse/​models/​status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/updateWarehouseModelStatus.md)
{style="max-width: 400px"}
|
Включение/выключение модели работы склада
||
|#

## Справочники

#|
|| **Метод** | **Описание метода** ||
||
[POST v2/​auth/​token](https://yandex.ru/dev/market/partner-api/doc/ru/reference/auth/getAuthTokenInfo.md)
{style="max-width: 400px"}
|
Получение информации о токене авторизации
||
||
[POST v1/​businesses/​{businessId}/​logistics-points](https://yandex.ru/dev/market/partner-api/doc/ru/reference/logistic-points/getLogisticPoints.md)
{style="max-width: 400px"}
|
Получение точек ПВЗ Маркета
||
||
[POST v2/​regions/​countries](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
{style="max-width: 400px"}
|
Список допустимых кодов стран
||
||
[GET v2/​regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md)
{style="max-width: 400px"}
|
Поиск регионов по их имени
||
||
[GET v2/​regions/​{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md)
{style="max-width: 400px"}
|
Информация о регионе
||
||
[GET v2/​regions/​{regionId}/​children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md)
{style="max-width: 400px"}
|
Информация о дочерних регионах
||
|#
<!-- endsource: ru/_auto/methods_summary/business.md -->
