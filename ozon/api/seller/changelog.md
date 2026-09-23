---
title: Обновления
api: ozon-seller
tag: News
group: Обновления
kind: changelog
source: "https://docs.ozon.ru/api/seller/"
content_sha: 4652175565a73fdb
---

# Обновления

Следите за обновлениями документации на платформе для разработчиков [Ozon for dev](https://dev.ozon.ru/).

## 22 сентября 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/actions/products/update](#operation/ActionsProductsUpdate)<br>[/v2/actions/products/deactivate](#operation/ActionsProductsDeactivate)<br>[/v2/actions/products](#operation/ActionsProducts)<br>[/v2/actions/candidates](#operation/ActionsCandidates)<br>[/v2/actions/auto-add/products/candidates](#operation/ActionsAutoAddProductsCandidatesV2)<br>[/v2/actions/auto-add/products/update](#operation/ActionsAutoAddProductsUpdateV2)<br>[/v2/actions/auto-add/products/list](#operation/ActionsAutoAddProductsListV2)<br>[/v2/actions/auto-add/products/delete](#operation/ActionsAutoAddProductsDeleteV2) | Добавили новые версии методов для работы с акциями Ozon. |
| [/v1/actions/candidates](#operation/PromosCandidates) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/candidates](#operation/ActionsCandidates). |
| [/v1/actions/products](#operation/PromosProducts) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/products](#operation/ActionsProducts). |
| [/v1/actions/products/activate](#operation/PromosProductsActivate) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v1/actions/products/update](#operation/ActionsProductsUpdate). |
| [/v1/actions/products/deactivate](#operation/PromosProductsDeactivate) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/products/deactivate](#operation/ActionsProductsDeactivate). |
| [/v1/actions/auto-add/products/list](#operation/ActionsAutoAddProductsList) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/auto-add/products/list](#operation/ActionsAutoAddProductsListV2). |
| [/v1/actions/auto-add/products/candidates](#operation/ActionsAutoAddProductsCandidates) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/auto-add/products/candidates](#operation/ActionsAutoAddProductsCandidatesV2). |
| [/v1/actions/auto-add/products/delete](#operation/ActionsAutoAddProductsDelete) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/auto-add/products/delete](#operation/ActionsAutoAddProductsDeleteV2). |
| [/v1/actions/auto-add/products/update](#operation/ActionsAutoAddProductsUpdate) | Метод устаревает и будет отключён 13 октября 2026 года. Переключитесь на [/v2/actions/auto-add/products/update](#operation/ActionsAutoAddProductsUpdateV2). |
| [/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList)<br>[/v4/posting/fbs/list](#operation/PostingFbsList) | Добавили параметр `postings.scanit` в ответ методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.scanit` в ответ метода. |
| [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode) | Обновили описание параметра `barcode` в запросе метода. |
| [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel) | Метод устаревает и будет отключён 2 ноября 2026 года. Переключитесь на [/v3/posting/fbs/package-label/create](#operation/PostingFbsPackageLabelCreate) и [/v2/posting/fbs/package-label/get](#operation/PostingFbsPackageLabelGet). |
| [/v3/posting/fbs/package-label/create](#operation/PostingFbsPackageLabelCreate) | Добавили новую версию метода для создания задания на формирование этикеток. |
| [/v2/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatchV2)<br>[/v1/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatch) | Методы устаревают и будут отключены 2 ноября 2026 года. Переключитесь на [/v3/posting/fbs/package-label/create](#operation/PostingFbsPackageLabelCreate). |
| [/v2/posting/fbs/package-label/get](#operation/PostingFbsPackageLabelGet) | Добавили новую версию метода для получения файла с этикетками. |
| [/v1/posting/fbs/package-label/get](#operation/PostingAPI_GetLabelBatch) | Метод устаревает и будет отключён 2 ноября 2026 года. Переключитесь на [/v2/posting/fbs/package-label/get](#operation/PostingFbsPackageLabelGet). |
| — | В разделе [**Порядок работы с методами**](#tag/Process) обновили методы для работы с этикетками. |

## 17 сентября 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/draft/create/info](#operation/DraftCreateInfo) | В ответе метода:обновили описание параметра `errors.error_message`;
добавили параметры `errors.items_validation.limit` и `errors.items_validation.supply_id`.
 |
| [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) | Добавили параметр `error_details` в ответ метода. |

## 16 сентября 2026

| Метод | Изменение |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| [/v1/analytics/local-sale/total](#operation/AnalyticsLocalSaleTotal)<br>[/v1/analytics/local-sale/clusters-items/info](#operation/AnalyticsLocalSaleClustersItemsInfo)<br>[/v1/analytics/local-sale/items-clusters/info](#operation/AnalyticsLocalSaleItemsClustersInfo) | Добавили бета-методы для работы с локальностью продаж. |
| [/v1/analytics/data](#operation/AnalyticsAPI_AnalyticsGetData) | Обновили описание метода. |

## 14 сентября 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3)<br>[/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU) | Обновили описание параметров `items.old_price` и `items.price` в запросе методов. |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Обновили описание параметров `items.min_price`, `items.old_price` и `items.price` в ответе метода. |
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Обновили описание параметров `prices.min_price`, `prices.min_price_for_auto_actions_enabled`, `prices.old_price`, `prices.price` и `prices.price_strategy_enabled` в запросе метода. |
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Обновили описание параметров `items.price.marketing_seller_price`, `items.price.min_price`, `items.price.old_price` и `items.price.price` в ответе метода. |
| [/v1/product/prices/details](#operation/ProductPricesDetails) | Обновили описание параметров `prices.customer_price`, `prices.price` и `prices.price_indexes` в ответе метода. |
| [/v1/analytics/category/comparison](#operation/AnalyticsCategoryComparison) | Добавили бета-метод для получения информации о сравнении категорий. |

## 11 сентября 2026

| Метод | Изменение |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Отметили устаревшими параметры `prices.auto_action_enabled` и `prices.manage_elastic_boosting_through_price` в запросе метода. |
| [/v1/fbp/order/direct/tpl-dlv/edit](#operation/FbpOrderDirectTplDlvEdit) | Добавили бета-метод для обновления информации о доставке сторонней транспортной компанией. |
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Добавили параметры `items.inbound_replenishment`, `items.outbound_pending_delivery`, `items.outbound_returns_picking`, `items.outbound_returns_ready_to_ship`, `items.outbound_returns_return_to_seller` и `items.stock_not_being_sold` в ответ метода. |

## 10 сентября 2026

| Метод | Изменение |
|--------------------------------------------------------------|------------------------------------------------------------------|
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Отметили устаревшим параметр `items.geo_names` в запросе метода. |

## 8 сентября 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/review/list](#operation/ReviewListV2) | Обновили пример запроса и ответа метода. |
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Обновили описание метода. |
| [/v2/product/certification/options](#operation/ProductCertificateOptions) | Обновили описание параметра `option.name` в ответе метода. |
| [/v2/product/certification/params](#operation/ProductCertificateParams)<br>[/v2/product/certificate/create](#operation/ProductCertificateCreate) | Обновили описание параметра `params.accordance_type` в запросе методов.<br>Обновили описание параметра `params.name` в ответе методов. |
| /v1/product/quant/list<br>/v1/product/quant/info | Тариф «Эконом» отключён, удалили методы из документации. |
| [/v1/product/pictures/import](#operation/ProductAPI_ProductImportPictures) | Обновили описание параметра `images` в запросе метода.<br>Обновили описание метода. |
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3)<br>[/v2/product/pictures/import](#operation/ProductImportPicturesV2) | Обновили описание параметра `items.images` в запросе методов.<br>Обновили описание методов. |

## 7 сентября 2026

| Метод | Изменение |
|---------------------------------------------------------------|---------------------------------------------------------|
| [/v1/product/prices/details](#operation/ProductPricesDetails) | Добавили параметр `prices.weight_index` в ответ метода. |

## 4 сентября 2026

| Метод | Изменение |
|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/seller-actions/products/add](#operation/SellerActionsProductsAdd) | Добавили параметр `products.action_price` в запрос метода. <br> Обновили описание параметра `products.discount_percent` в запросе метода. |

## 3 сентября 2026

| Метод | Изменение |
|-------|-----------|
| [/v2/product/pictures/import](#operation/ProductImportPicturesV2) | Добавили новую версию метода для загрузки или обновления изображений товара. |
| [/v1/product/pictures/import](#operation/ProductAPI_ProductImportPictures) | Метод устаревает и будет отключён 1 октября 2026 года. Переключитесь на [/v2/product/pictures/import](#operation/ProductImportPicturesV2). |
| [/v1/analytics/decommissioned-goods](#operation/AnalyticsDecommissionedGoods) | Добавили бета-метод для получения отчёта о списанных товарах. |
| [/v2/product/certification/params](#operation/ProductCertificateParams)<br>[/v2/product/certificate/create](#operation/ProductCertificateCreate) | Обновили описание параметра `params.files.name` в запросе методов. |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибки `file extension is not available` для метода [/v2/product/certificate/create](#operation/ProductCertificateCreate). |

## 2 сентября 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/product/certificate/products/list](#operation/CertificateProductsList) | 28 сентября 2026 года отключим параметры `page` и `page_size` в запросе метода. Используйте параметры `last_id` и `limit`.<br>Обновили описание параметра `last_id` в запросе метода. |
| [/v1/notification/list](#operation/NotificationList) | Добавили параметры `availability_statuses`, `limit`, `offset` и `sort_dir` в запрос метода.<br>Добавили параметры `availability_status_thresholds`, `total_count`, `urls.availability_status`, `urls.availability_status_date`, `urls.disable_reason`, `urls.problematic_type` и `urls.reason_details` в ответ метода. |
| — | В разделе [**Авторизация через API-ключ → Как получить API-ключ**](#section/Kak-poluchit-API-klyuch) обновили срок действия API-ключа. |

## 1 сентября 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| [/v1/description-category/dependent-attributes](#operation/DescriptionCategoryDependentAttributes)<br>[/v1/description-category/dependent-attributes/values](#operation/DescriptionCategoryDependentAttributesValues) | Добавили бета-методы для работы с зависимыми характеристиками. |

## 27 августа 2026

| Метод | Изменение |
|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| — | Добавили раздел [**Пуш-уведомления → Мониторинг доступности уведомлений**](#tag/push_monitoring).<br> В раздел [**Пуш-уведомления → Как подключить**](#tag/push_start) добавили информацию о просмотре статуса и повторном подключении пуш-уведомлений. |

## 19 августа 2026

| Метод | Изменение |
|---|---|
| [/v2/posting/fbs/act/get-container-labels](#operation/PostingAPI_PostingFBSActGetContainerLabels) | Обновили описание параметра `id` в запросе метода. |
| [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) | Обновили описание метода. |

## 18 августа 2026

| Метод | Изменение |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Обновили описание параметра `chats.chat.chat_type` в ответе метода. |
| — | В разделе [**Пуш-уведомления → Новое сообщение в чате, Сообщение в чате изменено, Ваше сообщение прочитано** и **Чат закрыт**](#section/Novoe-soobshenie-v-chate) обновили значения параметра `chat_type`. |

## 14 августа 2026

| Метод | Изменение |
|-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/carriage/courier-contact/set](#operation/CarriageCourierContactSet)<br> [/v1/carriage/courier-contact/get](#operation/CarriageCourierContactGet) | Добавили методы для работы с контактными данными продавца для курьера. |

## 13 августа 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | В запросе метода:добавили параметры `placement_zone` и `unmarked_stocks_only`;
обновили описание параметра `item_tags`.
В ответе метода:добавили параметры `items.waiting_docs_to_export_stock_count` и `items.placement_zone`;
обновили описание параметра `items.item_tags`.
 |
| [/v2/delivery/checkout](#operation/DeliveryCheckout) | Добавили параметр `splits.commissions` в ответ метода. |
| [/v1/product/certificate/bind](#operation/ProductAPI_ProductCertificateBind)<br>[/v1/product/certificate/unbind](#operation/CertificateUnbind) | В запросе методов:пометили устаревшим параметр `product_id`;
добавили параметр `skus`.
 |
| [/v1/product/certificate/products/list](#operation/CertificateProductsList) | В запросе метода:пометили устаревшим параметры `page` и `page_size`;
добавили параметры `last_id` и `limit`.
Добавили параметр `result.items.sku` в ответ метода. |
| [/v1/product/certificate/create](#operation/ProductAPI_ProductCertificateCreate) | Метод устаревает и будет отключён 31 августа 2026 года. |
| [/v2/product/certification/options](#operation/ProductCertificateOptions)<br>[/v2/product/certification/params](#operation/ProductCertificateParams)<br>[/v2/product/certificate/create](#operation/ProductCertificateCreate) | Добавили бета-методы для создания сертификатов. |

## 11 августа 2026

| Метод | Изменение |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| [/v1/supply-order/act/summary/get](#operation/SupplyOrderActSummaryGet)<br>[/v1/supply-order/act/product/get](#operation/SupplyOrderActProductGet)<br>[/v1/supply-order/act/accept](#operation/SupplyOrderActAccept)<br>[/v1/supply-order/act/accept/status](#operation/SupplyOrderActAcceptStatus) | Добавили бета-методы для работы с актами FBO. |
| [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2) | Отметили устаревшим параметр `returns.return_method_description` в ответе метода. |
| /v2/returns/rfbs/reject<br>/v2/returns/rfbs/compensate<br>/v2/returns/rfbs/verify<br>/v2/returns/rfbs/receive-return<br>/v2/returns/rfbs/return-money | Методы устарели, удалили их из документации. Используйте [/v1/returns/rfbs/action/set](#operation/ReturnsAPI_ReturnsRfbsActionSet). |

## 6 августа 2026

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------|-------------------------|
| [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate) <br> [/v1/draft/direct/create](#operation/DraftDirectCreate) <br> [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate) | Пометили обязательным параметр `deletion_sku_mode` в запросе метода. |

## 4 августа 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/notification/set](#operation/SetNotification)<br>[/v1/notification/update](#operation/UpdateNotification) | Обновили описание параметра `types` в запросе методов. |
| [/v1/notification/list](#operation/NotificationList) | Обновили описание параметра `urls.types.type` в ответе метода. |
| [/v1/notification/push-type/list](#operation/GetNotificationPushTypeList) | Обновили описание параметра `types.type` в ответе метода. |
| [/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList)<br>[/v4/posting/fbs/list](#operation/PostingFbsList)<br>[/v3/posting/fbo/list](#operation/PostingFboList) | Обновили описание параметра `postings.products.is_marketplace_buyout` в ответе методов. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)<br>[/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Обновили описание параметра `result.postings.products.is_marketplace_buyout` в ответе методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting)<br>[/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Обновили описание параметра `result.products.is_marketplace_buyout` в ответе методов. |
| [/v1/finance/products/buyout](#operation/GetFinanceProductsBuyout) | Обновили описание метода. |
| — | В раздел [**Пуш-уведомления → Уведомления, которые отправляет Ozon**](#tag/push_types) добавили уведомления `TYPE_FBO_POSTING_NEW`, `TYPE_FBO_POSTING_CANCELLED`, `TYPE_FBO_POSTING_STATE_CHANGED`, `TYPE_FBO_POSTING_DELIVERY_DATE_CHANGED`, `TYPE_FBO_STOCKS_CHANGED`, `TYPE_ORDER_NEW`, `TYPE_ORDER_CANCELLED` и `TYPE_ORDER_STATE_CHANGED`. |

## 30 июля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay) | Обновили описание параметров `date` и `last_id` в запросе метода. <br> В ответе метода:добавили параметр `accruals.container_fees`;
обновили описание параметров `accruals.accrued_category` и `last_id`.
 |

## 28 июля 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| [/v1/report/info](#operation/ReportAPI_ReportInfo) | Добавили параметр `result.additional_data` в ответ метода. |
| [/v1/report/list](#operation/ReportAPI_ReportList) | Добавили параметр `result.reports.additional_data` в ответ метода. |
| [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1) | Обновили описание параметра `message` в теле ошибки `400` метода. |
| [/v1/report/realization/posting/create](#operation/CreateCompanyFinanceRealizationPostingReport) | Добавили бета-метод для получения позаказного отчёта о реализации товаров. |

## 22 июля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Добавили параметр `filter.integration_type_flow` в запрос метода. <br> Добавили параметры `result.postings.integration_type_flow` и `result.postings.sorting_center` в ответ метода. |
| [/v4/posting/fbs/list](#operation/PostingFbsList) | Добавили параметр `filter.integration_type_flow` в запрос метода. <br> Добавили параметры `postings.integration_type_flow` и `postings.sorting_center` в ответ метода. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметры `result.integration_type_flow` и `result.sorting_center` в ответ метода. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметры `result.postings.integration_type_flow` и `result.postings.sorting_center` в ответ метода. |
| [/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList) | Добавили параметры `postings.integration_type_flow` и `postings.sorting_center` в ответ метода. |
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | С 17 августа 2026 года метод возвращает информацию об остатках в реальном времени. |

## 21 июля 2026

| Метод | Изменение |
|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay) | Обновили описание параметра `accruals.posting.products.delivery.services` в ответе метода. |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибки `PRODUCT_IS_ARCHIVED` для метода [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2). |

## 16 июля 2026

| Метод | Изменение |
|-----------------------------------------------------------------|-------------------------------------------------------------|
| [/v1/product/unarchive](#operation/ProductAPI_ProductUnarchive) | Обновили описание метода. <br> Обновили тело ошибки метода. |

## 14 июля 2026

| Метод | Изменение |
|---|---|
| [/v3/finance/transaction/list](#operation/FinanceAPI_FinanceTransactionListV3)<br>[/v3/finance/transaction/totals](#operation/FinanceAPI_FinanceTransactionTotalV3) | Методы устаревают и будут отключены 8 сентября 2026 года. Переключитесь на [/v1/finance/accrual/postings](#operation/GetFinanceAccrualPostings), [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes), [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay). |

## 10 июля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Удалили параметр `items.images360` из запроса метода.<br>Пометили обязательным параметр `items.offer_id` в запросе метода.<br>Обновили описание метода. |
| [/v1/product/pictures/import](#operation/ProductAPI_ProductImportPictures) | Удалили параметр `images360` из запроса метода.<br>Удалили параметр `result.pictures.is_360` из ответа метода.<br>Обновили описание метода. |
| [/v2/product/pictures/info](#operation/ProductAPI_ProductInfoPicturesV2) | Удалили параметр `items.photo_360` из ответа метода. |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Удалили параметр `items.images360` из ответа метода. |
| [/v1/product/attributes/update](#operation/ProductAPI_ProductUpdateAttributes) <br>[/v1/product/unarchive](#operation/ProductAPI_ProductUnarchive) <br>[/v1/product/update/offer-id](#operation/ProductAPI_ProductUpdateOfferID) <br>[/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU) <br>[/v4/product/info/limit](#operation/ProductAPI_GetUploadQuota) | Обновили описание методов. |
| [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Метод устаревает и будет отключён 31 августа 2026 года. Переключитесь на [/v3/posting/fbo/list](#operation/PostingFboList). |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Метод устаревает и будет отключён 31 августа 2026 года. Переключитесь на [/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList). |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Метод устаревает и будет отключён 31 августа 2026 года. Переключитесь на [/v4/posting/fbs/list](#operation/PostingFbsList). |
| [/v1/posting/digital/list](#operation/ListPostingCodes) | Метод устаревает и будет отключён 31 августа 2026 года. Переключитесь на [/v2/posting/digital/list](#operation/PostingDigitalList). |

## 9 июля 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| [/v3/product/list](#operation/ProductAPI_GetProductList) | Добавили параметр `filter.skus` в запрос метода. <br> Добавили параметр `result.items.sku` в ответ метода. |
| [/v1/order/cancel/status](#operation/OrderAPI_OrderCancelStatus)<br>[/v1/posting/cancel/status](#operation/PostingAPI_PostingCancelStatus) | Обновили описание параметра `state` в ответе методов. |
| [/v2/delivery/checkout](#operation/DeliveryCheckout) | Обновили тело ошибки метода. |
| — | В разделе [**Порядок работы с методами → Управляйте заказами FBO, FBS и rFBS → Схема FBO**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBO) добавили информацию о распределении товаров по транспортным грузоместам FBO. |

## 8 июля 2026

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| [/v2/supply-order/timeslot/list](#operation/SupplyOrderTimeslotList) <br> [/v1/review/comment/create](#operation/ReviewAPI_CommentCreate) <br> [/v1/review/comment/delete](#operation/ReviewAPI_CommentDelete) <br> [/v1/review/comment/list](#operation/ReviewAPI_CommentList) <br> [/v1/review/change-status](#operation/ReviewAPI_ReviewChangeStatus) <br> [/v1/review/count](#operation/ReviewAPI_ReviewCount) <br> [/v1/review/info](#operation/ReviewAPI_ReviewInfo) <br> [/v1/review/list](#operation/ReviewAPI_ReviewList) <br> [/v2/review/change-status](#operation/ReviewChangeStatusV2) <br> [/v2/review/comment/delete](#operation/ReviewCommentDeleteV2) <br> [/v2/review/count](#operation/ReviewCountV2) <br> [/v2/review/info](#operation/ReviewInfoV2) <br> [/v2/review/list](#operation/ReviewListV2) <br> [/v1/question/answer/create](#operation/QuestionAnswer_Create) <br> [/v1/question/answer/delete](#operation/QuestionAnswer_Delete) <br> [/v1/question/answer/list](#operation/QuestionAnswer_List) <br> [/v1/question/change-status](#operation/Question_ChangeStatus) <br> [/v1/question/count](#operation/Question_Count) <br> [/v1/question/info](#operation/Question_Info) <br> [/v1/question/list](#operation/Question_List) <br> [/v1/question/top-sku](#operation/Question_TopSku) | Перенесли методы из бета-раздела в основной. |

## 7 июля 2026

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) <br> [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.external_order` в ответ методов. |
| [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) | Метод устаревает и будет отключён 7 сентября 2026. Переключитесь на [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) и [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove). |

## 2 июля 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| [/v1/product/info/stocks-by-warehouse/fbo](#operation/GetProductInfoStocksByWarehouseFbo) | Добавили новый метод для для получения информации о стоках на складах FBO. |

## 1 июля 2026

| Метод | Изменение |
|---|---|
| [/v1/posting/fbp/get](#operation/GetFbpPosting) | Добавили бета-метод для получения информации об отправлении FBP по идентификатору. |

## 30 июня 2026

| Метод | Изменение |
|------------------------------------------------|---------------------------------------------------------------------|
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Обновили описание параметра `chats.chat.chat_type` в ответе метода. |
| [/v1/warehouse/erfbs/aggregator/create](#operation/WarehouseERFBSAggregatorCreate) | Добавили параметр `delivery_method.is_courier_phone_same_as_warehouse` в запрос метода. |
| [/v1/warehouse/erfbs/aggregator/delivery-method/update](#operation/WarehouseERFBSAggregatorDeliveryMethodUpdate) | Добавили параметр `is_courier_phone_same_as_warehouse` в запрос метода. |
| [/v1/posting/fbp/list](#operation/PostingFbpList) | Добавили параметры `postings.financial_data.products.posting_commission` и `postings.financial_data.products.return_commission` в ответ метода. |

## 25 июня 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------|-----------------------------------------------------------|
| [/v1/product/certificate/products/list](#operation/CertificateProductsList) | Обновили описание параметра `page_size` в запросе метода. |
| — | Обновляем корневой TLS/SSL-сертификат GlobalSign — вместо него будем использовать [HARICA](https://app.harica.gr/).<br>[Подробнее о переходе на HARICA на платформе разработчиков Ozon for dev](https://dev.ozon.ru/news/775-Izmeneniia-v-Ozon-API-migratsiia-kornevogo-sertifikata-UTs-Ozon/) |

## 22 июня 2026

| Метод | Изменение |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| [/v1/product/visibility/set](#operation/ProductVisibilitySet) | Обновили описание метода. <br> Обновили описание параметра `item_placement.placement` в запросе метода. |

## 19 июня 2026

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/supply-order/timeslot/get](#operation/SupplyOrderAPI_GetSupplyOrderTimeslots) | Метод устаревает и будет отключён 19 августа 2026 года. Переключитесь на [/v2/supply-order/timeslot/list](#operation/SupplyOrderTimeslotList). |
| [/v1/supply-order/timeslot/update](#operation/SupplyOrderAPI_UpdateSupplyOrderTimeslot)<br>[/v1/supply-order/timeslot/status](#operation/SupplyOrderAPI_GetSupplyOrderTimeslotStatus) | Обновили описание параметра `errors` в ответе методов. |
| [/v2/supply-order/timeslot/list](#operation/SupplyOrderTimeslotList) | Добавили новую версию метода для получения списка доступных интервалов поставки. |
| — | Добавили раздел [**Пуш-уведомления → Уведомления, которые отправляет Ozon → Изменение дерева категорий**](#section/Izmenenie-dereva-kategorij). <br> Добавили тип уведомления `TYPE_DESCRIPTION_CATEGORY_TREE_CHANGED` в раздел [**Пуш-уведомления → Уведомления, которые отправляет Ozon**](#tag/push_types). |

## 18 июня 2026

| Метод | Изменение |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/draft/create | Метод устарел, удалили его из документации. Используйте [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate), [/v1/draft/direct/create](#operation/DraftDirectCreate) или [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate). |
| /v1/draft/create/info | Метод устарел, удалили его из документации. Используйте [/v2/draft/create/info](#operation/DraftCreateInfo). |
| /v1/draft/timeslot/info | Метод устарел, удалили его из документации. Используйте [/v2/draft/timeslot/info](#operation/DraftTimeslotInfo). |
| /v1/draft/supply/create | Метод устарел, удалили его из документации. Используйте [/v2/draft/supply/create](#operation/DraftSupplyCreate). |
| /v1/draft/supply/create/status | Метод устарел, удалили его из документации. Используйте [/v2/draft/supply/create/status](#operation/DraftSupplyCreateStatus). |

## 11 июня 2026

| Метод | Изменение |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [/v2/cargoes/get](#operation/CargoesGetV2) <br> [/v2/cargoes/delete](#operation/CargoesDeleteV2) <br> [/v2/cargoes/delete/status](#operation/CargoesDeleteStatusV2) <br> [/v1/cargoes/transport/activate](#operation/CargoesTransportActivate)<br>[/v1/cargoes/transport/activate/status](#operation/CargoesTransportActivateStatus)<br>[/v1/cargoes/transport/create](#operation/CargoesTransportCreate)<br>[/v1/cargoes/transport/create/status](#operation/CargoesTransportCreateStatus)<br>[/v1/cargoes/transport/bind](#operation/CargoesTransportBind) <br> [/v1/cargoes/transport/bind/status](#operation/CargoesTransportBindStatus)<br>[/v1/cargoes/supplies/get](#operation/CargoesSuppliesGet)<br>[/v1/cargoes/label/transport-by-order/create](#operation/CargoesLabelTransportByOrderCreate)<br>[/v1/cargoes/label/transport-by-order/status](#operation/CargoesLabelTransportByOrderStatus)<br>[/v1/cargoes/label/transport/create](#operation/CargoesLabelTransportCreate)<br>[/v1/cargoes/label/transport/status](#operation/CargoesLabelTransportStatus) | Добавили бета-методы для работы с транспортными грузоместами FBO. |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибок: `method is not allowed` — для всех методов;
 `token must be issued for seller, not oauth-client` и `method is not allowed: OZON logistic is disabled` — для метода [/v1/delivery/point/list](#operation/DeliveryAPI_DeliveryPointList); 
 `not available with existing subscription` — для метода [/v2/review/list](#operation/ReviewListV2). 
 |

## 9 июня 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v4/product/info/limit](#operation/ProductAPI_GetUploadQuota) | Добавили параметр `operation_limits` в ответ метода. |
| /v2/chat/list | Метод устарел, удалили его из документации. Используйте [/v3/chat/list](#operation/ChatAPI_ChatListV3). |
| [/v1/product/placement-zone/info](#operation/ProductAPI_GetProductPlacementZoneInfo) | Перенесли метод из раздела [**Загрузка и обновление товаров**](#tag/ProductAPI) в раздел [**Атрибуты и характеристики Ozon**](#tag/CategoryAPI). |
| [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay) | Изменили название параметра `accruals.type_id` на `accruals.accrual_id` в ответе метода. |

## 4 июня 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/warehouse/erfbs/aggregator/create](#operation/WarehouseERFBSAggregatorCreate) | Добавили параметры `delivery_method.delivery_costs.min_weight`, `delivery_method.delivery_costs.max_weight`, `delivery_method.delivery_costs.min_order_price`, `delivery_method.delivery_costs.max_order_price` и `delivery_method.delivery_costs.seller_payment` в запрос метода. <br> Удалили параметры `delivery_method.delivery_costs.max_amount`, `delivery_method.delivery_costs.min_amount` и `delivery_method.delivery_costs.percent`. |
| [/v1/warehouse/erfbs/aggregator/delivery-method/update](#operation/WarehouseERFBSAggregatorDeliveryMethodUpdate)| Добавили параметры `delivery_costs.min_weight`, `delivery_costs.max_weight`, `delivery_costs.min_order_price`, `delivery_costs.max_order_price` и `delivery_costs.seller_payment` в запрос метода. <br> Удалили параметры `delivery_costs.max_amount`, `delivery_costs.min_amount` и `delivery_costs.percent`. |

## 3 июня 2026

| Метод | Изменение |
|-----------------------------------------------------------|-----------------------------------------------------------------|
| [/v2/posting/fbs/act/get-postings](#operation/PostingAPI_ActPostingList) | Обновили описание параметра `id` в запросе метода. |

## 2 июня 2026

| Метод | Изменение |
|-----------------------------------------------------------|-----------------------------------------------------------------|
| [/v1/seller/info](#operation/SellerAPI_SellerInfo) | Обновили описание параметра `company.currency` в ответе метода. | 
| [/v1/polygon/create](#operation/PolygonAPI_CreatePolygon) | Обновили описание метода. |

## 1 июня 2026

| Метод | Изменение |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/draft/supply/create](#operation/DraftSupplyCreate) | Добавили описание метода. |
| [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate) <br> [/v1/draft/direct/create](#operation/DraftDirectCreate) <br> [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate) | Обновили описание методов. |
|[/v2/cluster/list](#operation/DraftClusterList) | Перенесли метод из бета-раздела в основной. |
| — | В разделе [**Порядок работы с методами → Управляйте заказами FBO, FBS и rFBS → Схема FBO → Создать заявку на поставку**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBO) обновили информацию о создании заявки на поставку по схеме FBO.|

## 28 мая 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Обновили описание параметров `items.marketing_actions`, `items.marketing_actions.actions`, `items.marketing_actions.actions.date_from`, `items.marketing_actions.actions.date_to`, `items.marketing_actions.actions.title` и `items.marketing_actions.actions.value` в ответе метода. |
| [/v1/fbp/draft/get](#operation/FbpAPI_FbpDraftGet)<br>[/v1/fbp/archive/get](#operation/FbpAPI_FbpArchiveGet)<br>[/v1/fbp/order/get](#operation/FbpAPI_FbpOrderGet) | Обновили описание параметров `delivery_details.direct_details.timeslot_details.timeslot.timeslot_end`, `delivery_details.direct_details.timeslot_details.timeslot.timeslot_start`, `delivery_details.drop_off_point.timeslot.timeslot_end` и `delivery_details.drop_off_point.timeslot.timeslot_start` в ответе методов. |
| [/v1/fbp/draft/list](#operation/FbpAPI_FbpDraftList)<br>[/v1/fbp/archive/list](#operation/FbpAPI_FbpArchiveList)<br>[/v1/fbp/order/list](#operation/FbpAPI_FbpOrderList) | Обновили описание параметров `items.delivery_details.direct_details.timeslot_details.timeslot.timeslot_end`, `items.delivery_details.direct_details.timeslot_details.timeslot.timeslot_start`, `items.delivery_details.drop_off_point.timeslot.timeslot_end` и `items.delivery_details.drop_off_point.timeslot.timeslot_start` в ответе методов. |

## 26 мая 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/supply-order/get](#operation/SupplyOrderGet) | Обновили описание параметров `orders.supplies.storage_warehouse` и `orders.supplies.storage_warehouse.warehouse_id` в ответе метода. |
| [/v1/supply-order/details](#operation/SupplyOrderAPI_SupplyOrderDetails) | Обновили описание параметров `supplies.storage_warehouse` и `supplies.storage_warehouse.warehouse_id` в ответе метода. |
| [/v1/carriage/act-discrepancy/pdf](#operation/CarriageActDiscrepancyPDF) <br> [/v1/warehouse/ozon/list](#operation/WarehouseOZONList) <br> [/v1/warehouse/rfbs/pause](#operation/WarehouseRfbsPause) <br> [/v1/warehouse/rfbs/unpause](#operation/WarehouseRfbsUnpause) | Перенесли методы из бета-раздела в основной. |
| [/v1/return/giveout/get-pdf](#operation/ReturnAPI_GiveoutGetPDF) <br> [/v1/return/giveout/get-png](#operation/ReturnAPI_GiveoutGetPNG) | Обновили описание параметра `file_content` в ответе методов. |
| — | В разделе [**Частые ошибки**](#tag/Errors) обновили описание ошибки `FLAMMABLE_ONLY_ON_SELF_OR_PROVIDER_DELIVERY` для метода [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2). |

## 22 мая 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| [/v1/product/visibility/set](#operation/ProductVisibilitySet) | Обновили описание параметров `item_placement` в запросе метода и `items.seller_item_placement` в ответе метода. |
| [/v1/supply-order/content/update](#operation/SupplyOrderAPI_SupplyOrderContentUpdate) <br> [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) | Обновили описание параметра `errors` в ответе методов. |
| [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2) | Добавили параметр `delivery_methods.tpl_dropoff_point` в ответ метода. |
| /v1/cargoes/create/info | Метод устарел, удалили его из документации. Используйте [/v2/cargoes/create/info](#operation/CargoesCreateInfoV2). |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибок `SELLER_NO_CONTRACT_FAILED`, `error_attribute_values_empty`, `error_attribute_values_out_of_range`, `missing_dimension`, `VALUE_MAX_LIMIT`, `EMPTY_REQUIRED`, `description_category_invalid`, `description_category_has_no_description_type`, `description_category_is_legacy`, `levels_category_not_found`, `description_category_is_empty`, `description_type_is_empty`, `vat_invalid`, `name_too_long`, `all_image_failed`, `invalid_rich_content_json`, `all_image_unprocessed`, `price_out_of_range`, `old_price_less_than_price`, `min_auto_price_too_big`, `min_auto_price_too_small` и `price_less_than_min_auto_price` для метода [/v3/product/import](#operation/ProductAPI_ImportProductsV3). |

## 21 мая 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/finance/realization](#operation/FinanceAPI_GetRealizationReportV2) | Обновили описание метода. | 
| [/v1/warehouse/erfbs/aggregator/create](#operation/WarehouseERFBSAggregatorCreate)<br>[/v1/warehouse/erfbs/non-integrated/create](#operation/WarehouseERFBSNonIntegratedCreate)<br>[/v1/warehouse/erfbs/update](#operation/WarehouseERFBSUpdate) | Добавили параметр `is_auto_assembly` в запрос методов. | 
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибок `IsAutoAssembly property is not available for c&c delivery method` для метода [/v1/warehouse/erfbs/update](#operation/WarehouseERFBSUpdate) и `label not allowed for delivered postings` для метода [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel). |

## 20 мая 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| [/v1/seller-actions/products/delete](#operation/SellerActionsProductsDelete) | Обновили описание параметра `skus` в запросе метода. |
| [/v1/finance/balance](#operation/GetFinanceBalanceV1) | Обновили пример запроса. |

## 19 мая 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| [/v1/analytics/data](#operation/AnalyticsAPI_AnalyticsGetData) | Обновили описание параметра `dimension` в запросе метода. |
| [/v2/invoice/create-or-update](#operation/InvoiceAPI_InvoiceCreateOrUpdateV2) <br> [/v2/order/create](#operation/OrderAPI_OrderCreate) | Обновили описание методов. |
| /v1/analytics/average-delivery-time/details <br> /v1/analytics/average-delivery-time <br> /v1/analytics/average-delivery-time/summary | Методы устарели, удалили их из документации. |

## 15 мая 2026

| Метод | Изменение |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/barcode/add](#operation/add-barcode) | Обновили описание метода. |

## 14 мая 2026

| Метод | Изменение |
|------------------------------------------------------------------|----------------------------------------------------------------------|
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Обновили описание параметра `items.promotions.type` в ответе метода. |
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Обновили описание параметра `items.promotions.type` в запросе метода. |
| [/v1/product/placement-zone/info](#operation/ProductAPI_GetProductPlacementZoneInfo) | Добавили описание метода. |
| [/v1/supply-order/content/update](#operation/SupplyOrderAPI_SupplyOrderContentUpdate) | Обновили описание параметра `order_id` в запросе метода. |
| [/v1/finance/cash-flow-statement/list](#operation/FinanceAPI_FinanceCashFlowStatementList) | Обновили описание метода. |

## 12 мая 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| [/v1/actions](#operation/Promos) | Добавили параметр `result.auto_add_dates` в ответ метода. |
| [/v1/actions/auto-add/products/list](#operation/ActionsAutoAddProductsList)<br>[/v1/actions/auto-add/products/candidates](#operation/ActionsAutoAddProductsCandidates)<br>[/v1/actions/auto-add/products/delete](#operation/ActionsAutoAddProductsDelete)<br>[/v1/actions/auto-add/products/update](#operation/ActionsAutoAddProductsUpdate) | Добавили бета-методы для работы с автодобавлением товаров в акции. |
| [/v1/product/visibility/info](#operation/ProductVisibilityInfo) | Добавили бета-метод для получения информации о видимости товаров. |
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Добавили описание метода. |
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Обновили описание параметра `prices.min_price` в запросе метода. |
| [/v1/product/action/timer/status](#operation/ProductAPI_ActionTimerStatus) | Обновили описание параметра `statuses.expired_at` в ответе метода. |

## 6 мая 2026

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/finance/accrual/postings](#operation/GetFinanceAccrualPostings) | Добавили бета-метод для получения начислений по отправлениям. |
| [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes) | Добавили бета-метод для получения справочника начислений по отправлениям. |
| [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay) | Добавили бета-метод для получения начислений по отправлению за день. |
| [/v3/finance/transaction/list](#operation/FinanceAPI_FinanceTransactionListV3) | Метод устаревает и будет отключён 6 июля 2026 года. Переключитесь на [/v1/finance/accrual/postings](#operation/GetFinanceAccrualPostings), [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes), [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay). |
| [/v3/finance/transaction/totals](#operation/FinanceAPI_FinanceTransactionTotalV3) | Метод устаревает и будет отключён 6 июля 2026 года. Переключитесь на [/v1/finance/accrual/postings](#operation/GetFinanceAccrualPostings), [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes), [/v1/finance/accrual/by-day](#operation/GetFinanceAccrualByDay). |

## 5 мая 2026

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| [/v3/product/list](#operation/ProductAPI_GetProductList)<br>[/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks)<br>[/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Обновили описание параметра `filter.visibility` в запросе методов. |
| [/v1/carriage/container/create](#operation/CarriageContainerCreate) <br> [/v1/carriage/container/fill](#operation/CarriageContainerFill) <br> [/v1/carriage/container/approve](#operation/CarriageContainerApprove) <br> [/v1/carriage/container/place-into](#operation/CarriageContainerPlaceInto) <br> [/v1/carriage/container/remove-postings](#operation/CarriageContainerRemovePostings) <br> [/v1/carriage/container/remove-from](#operation/CarriageContainerRemoveFrom) <br> [/v1/carriage/container/cancel](#operation/CarriageContainerCancel) <br> [/v1/carriage/container/list](#operation/CarriageContainerList) <br> [/v1/carriage/container/get](#operation/CarriageContainerGet) <br> [/v1/carriage/container/status/get](#operation/CarriageContainerStatusGet) <br> [/v1/carriage/container/task/info](#operation/CarriageContainerTaskInfo) <br> [/v1/carriage/container/document/get](#operation/CarriageContainerDocumentGet) <br> [/v1/carriage/container/label/get](#operation/CarriageContainerLabelGet) | Добавили бета-методы для работы с грузоместами FBS. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[ /v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметры `result.postings.container` и `result.postings.container_sort_type` в ответ методов. |
| [/v4/posting/fbs/list](#operation/PostingFbsList)<br>[/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList) | Добавили параметры `postings.container` и `postings.container_sort_type` в ответ методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметры `result.container` и `result.container_sort_type` в ответ метода. |
| [/v1/brand/company-certification/list](#operation/BrandAPI_BrandCompanyCertificationList) <br> [/v3/product/import](#operation/ProductAPI_ImportProductsV3) <br> [/v1/product/pictures/import](#operation/ProductAPI_ProductImportPictures) <br> [/v1/product/archive](#operation/ProductAPI_ProductArchive) <br> [/v1/product/unarchive](#operation/ProductAPI_ProductUnarchive) <br> [/v1/product/info/wrong-volume](#operation/ProductAPI_ProductInfoWrongVolume)| Обновили описание методов. |

## 30 апреля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/posting/fbo/list](#operation/PostingFboList) | Добавили новую версию метода для получения списка отправлений FBO. | 
| [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Метод устаревает и будет отключён 1 июня 2026 года. Переключитесь на [/v3/posting/fbo/list](#operation/PostingFboList). |
| [/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList) | Добавили новую версию метода для получения списка необработанных отправлений FBS. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Метод устаревает и будет отключён 1 июня 2026 года. Переключитесь на [/v4/posting/fbs/unfulfilled/list](#operation/PostingFbsUnfulfilledList). |
| [/v4/posting/fbs/list](#operation/PostingFbsList) | Добавили новую версию метода для получения списка отправлений FBS. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Метод устаревает и будет отключён 1 июня 2026 года. Переключитесь на [/v4/posting/fbs/list](#operation/PostingFbsList). |
| [/v2/posting/digital/list](#operation/PostingDigitalList) | Добавили новую версию метода для получения списка отправлений, по которым нужно загрузить коды цифровых товаров. |
| [/v1/posting/digital/list](#operation/ListPostingCodes) | Метод устаревает. Переключитесь на [/v2/posting/digital/list](#operation/PostingDigitalList). |
| [/v1/posting/fbp/list](#operation/PostingFbpList) | Добавили новый бета-метод для получения списка отправлений FBP. |
| [/v1/carriage/get](#operation/CarriageGet) | Обновили описание параметра `available_actions` в ответе метода. |
| [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList) | Добавили параметр `with.able_to_set_price` в запрос метода.<br>Добавили параметры `result.is_able_to_set_price` и `result.is_presorted` в ответ метода. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `filter.last_changed_status_date` в запрос метода.<br>Добавили параметры `result.postings.is_presortable`, `result.postings.destination_place_id`, `result.postings.destination_place_name` и `result.postings.customer.customer_email` в ответ метода. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Добавили параметры `result.postings.is_presortable`, `result.postings.destination_place_id`, `result.postings.destination_place_name` и `result.postings.customer.customer_email` в ответ метода. |
| [/v3/supply-order/get](#operation/SupplyOrderGet) | Изменили название параметров `orders.data_filling_deadline` на `orders.data_filling_deadline_utc` и `orders.drop_off_warehouse` на `orders.dropoff_warehouse` в ответе метода. |

## 29 апреля 2026

| Метод | Изменение |
|-------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/product/prices/details](#operation/ProductPricesDetails) | В ответе метода: добавили параметр `prices.price_indexes`; 
 пометили устаревшим параметр `prices.discount_percent`; 
 обновили описание параметра `prices.customer_price`. |

## 28 апреля 2026

| Метод | Изменение |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/warehouse/erfbs/non-integrated/create](#operation/WarehouseERFBSNonIntegratedCreate) | Обновили описание параметра `min_order_value` в запросе метода. |

## 24 апреля 2026

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| [/v1/fbp/draft/drop-off/product/validate](#operation/FbpDraftDropOffProductValidate)<br>[/v1/fbp/draft/direct/product/validate](#operation/FbpDraftDirectProductValidate)<br>[/v1/fbp/draft/pick-up/product/validate](#operation/FbpAPI_FbpDraftPickUpProductValidate)| Добавили значения `NO_SALES`, `SURPLUS` и `AVAILABILITY_IS_EMPTY` параметра `rejected_items.rejection_reasons` в ответе методов. |
| [/v1/fbp/draft/drop-off/registrate](#operation/FbpDraftDropOffRegistrate)<br>[/v1/fbp/draft/direct/registrate](#operation/FbpDraftDirectRegistrate)<br>[/v1/fbp/draft/pick-up/registrate](#operation/FbpDraftPickUpRegistrate)| Добавили значения `NO_SALES`, `SURPLUS` и `AVAILABILITY_IS_EMPTY` параметра `error.bundle_errors.errors` в ответе методов. |

## 20 апреля 2026

| Метод | Изменение |
|---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/review/comment/list](#operation/ReviewAPI_CommentList) | Обновили название метода.<br>Добавили параметр `filter` в запрос метода.<br>Добавили параметры `comments.deviation_reason`, `comments.dislikes_amount`, `comments.is_published`, `comments.is_rejected` и `comments.likes_amount` в ответ метода. |
| [/v2/review/comment/delete](#operation/ReviewCommentDeleteV2) | Добавили новую версию метода для удаления комментария на отзыв. |
| [/v1/review/comment/delete](#operation/ReviewAPI_CommentDelete) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/review/comment/delete](#operation/ReviewCommentDeleteV2). |
| [/v2/review/change-status](#operation/ReviewChangeStatusV2) | Добавили новую версию метода для изменения статуса отзывов. |
| [/v1/review/change-status](#operation/ReviewAPI_ReviewChangeStatus) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/review/change-status](#operation/ReviewChangeStatusV2). |
| [/v2/review/count](#operation/ReviewCountV2) | Добавили новую версию метода для получения количества отзывов по статусам. |
| [/v1/review/count](#operation/ReviewAPI_ReviewCount) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/review/count](#operation/ReviewCountV2). |
| [/v2/review/info](#operation/ReviewInfoV2) | Добавили новую версию метода для получения информации об отзыве. |
| [/v1/review/info](#operation/ReviewAPI_ReviewInfo) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/review/info](#operation/ReviewInfoV2). |
| [/v2/review/list](#operation/ReviewListV2) | Добавили новую версию метода для получения списка отзывов. |
| [/v1/review/list](#operation/ReviewAPI_ReviewList) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/review/list](#operation/ReviewListV2). |
| [/v1/question/answer/list](#operation/QuestionAnswer_List) | Добавили параметр `answers.status_publication` в ответ метода. |
| [/v1/question/list](#operation/Question_List) | Добавили параметры `sort_dir` и `limit` в запрос метода.<br>Добавили параметр `has_next` в ответ метода. |

## 17 апреля 2026

| Метод | Изменение |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| — | В разделе [**Пуш-уведомления → Новое сообщение в чате, Сообщение в чате изменено, Ваше сообщение прочитано** и **Чат закрыт**](#section/Novoe-soobshenie-v-chate) обновили значения параметра `chat_type`. |

## 15 апреля 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/seller/ozon-logistics/info](#operation/SellerAPI_SellerOzonLogisticsInfo) | Обновили название метода.<br>Обновили описание параметра `ozon_logistics_enabled` в ответе метода. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList)<br>[/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) | Обновили описание параметров `result.analytics_data.client_delivery_date_begin` и `result.analytics_data.client_delivery_date_end` в ответе методов. | 
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Обновили описание параметров `result.postings.analytics_data.client_delivery_date_begin` и `result.postings.analytics_data.client_delivery_date_end` в ответе методов. |
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Обновили описание параметра `chats.chat.chat_type` в ответе метода. |
| — | Изменили название раздела **Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Ozon Логистика** на [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Ozon Доставка**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Ozon-Dostavka).<br>Изменили название раздела **Ozon Логистика** на [**Ozon Доставка**](#tag/OzonLogistics). |

## 14 апреля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| /v1/seller-actions/create/ozon-card-discount<br>/v1/seller-actions/update/ozon-card-discount | Акция недоступна для использования, удалили методы из документации. |

## 8 апреля 2026

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| [/v1/notification/set](#operation/SetNotification)<br>[/v1/notification/update](#operation/UpdateNotification)<br>[/v1/notification/check](#operation/CheckNotification)<br>[/v1/notification/delete](#operation/DeleteNotification)<br>[/v1/notification/enable](#operation/EnableNotification)<br>[/v1/notification/list](#operation/NotificationList)<br>[/v1/notification/push-type/list](#operation/GetNotificationPushTypeList) | Добавили бета-методы для работы с пуш-уведомлениями. |

## 7 апреля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| [/v2/warehouse/list](#operation/WarehouseListV2) | Добавили параметр `warehouses.pause_at` в ответ метода. | 
| [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) | Обновили значение параметра `type` в ответе метода. |
| [/v1/warehouse/rfbs/pause](#operation/WarehouseRfbsPause)<br>[/v1/warehouse/rfbs/unpause](#operation/WarehouseRfbsUnpause) | Добавили бета-методы для включения и выключения паузы на rFBS-складе. |

## 6 апреля 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| [/v1/product/visibility/set](#operation/ProductVisibilitySet) | Добавили бета-метод для настройки видимости товара на витрине Ozon и Ozon Селект. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.tariffication_steps` в ответ метода. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.tariffication_steps` в ответ методов. | 

## 31 марта 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| [/v1/review/comment/create](#operation/ReviewAPI_CommentCreate)<br>[/v1/review/comment/delete](#operation/ReviewAPI_CommentDelete)<br>[/v1/review/comment/list](#operation/ReviewAPI_CommentList)<br>[/v1/review/change-status](#operation/ReviewAPI_ReviewChangeStatus)<br>[/v1/review/count](#operation/ReviewAPI_ReviewCount)<br>[/v1/review/info](#operation/ReviewAPI_ReviewInfo)<br>[/v1/review/list](#operation/ReviewAPI_ReviewList) | Обновили описание методов. |

## 26 марта 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3)<br>[/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU)<br>[/v1/product/attributes/update](#operation/ProductAPI_ProductUpdateAttributes)<br>[/v1/product/pictures/import](#operation/ProductAPI_ProductImportPictures)<br>[/v1/product/update/offer-id](#operation/ProductAPI_ProductUpdateOfferID) | Обновили описание методов. | 

## 24 марта 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_ProductStocksByWarehouseFbs) | Метод устаревает и будет отключён 7 апреля 2026 года. Переключитесь на [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2). |
| [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList) | Метод устаревает и будет отключён 7 апреля 2026 года. Переключитесь на [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2). |
| [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList) | Метод устаревает и будет отключён 7 апреля 2026 года. Переключитесь на [/v2/warehouse/list](#operation/WarehouseListV2). |
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Перенесли метод из бета-раздела в основной.<br>Обновили описание метода. |
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | В описание метода добавили информацию о загрузке главного изображения для Ozon Селект. |

## 17 марта 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/analytics/average-delivery-time<br>/v1/analytics/average-delivery-time/details<br>/v1/analytics/average-delivery-time/summary | Обновили описание методов. |
| [/v1/product/update/offer-id](#operation/ProductAPI_ProductUpdateOfferID) | Обновили описание метода. Добавили лимиты для параметра `update_offer_id` в запрос метода. |
| [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList)<br>[/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) | Обновили описание параметров `result.analytics_data.client_delivery_date_begin` и `result.analytics_data.client_delivery_date_end` в ответе методов. | 
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Обновили описание параметров `result.analytics_data.client_delivery_date_begin` и `result.analytics_data.client_delivery_date_end` в ответе метода. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Обновили описание параметров `result.postings.analytics_data.client_delivery_date_begin` и `result.postings.analytics_data.client_delivery_date_end` в ответе методов. | 

## 13 марта 2026

| Метод | Изменение |
|------------------------------------------------------|---------------------------------------------------------------------|
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Обновили описание параметра `chats.chat.chat_type` в ответе метода. |
| [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3) | Обновили описание параметра `messages.user.type` в ответе метода. |

## 12 марта 2026

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| [/v1/warehouse/ozon/list](#operation/WarehouseOZONList) | Добавили бета-метод для получения списка складов Ozon. |

## 11 марта 2026

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Обновили описание параметра `chats.chat.chat_type` в ответе метода. |

## 10 марта 2026

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/warehouse/fbs/create/return-point/list](#operation/WarehouseFBSCreateReturnPointList)<br>[/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList) | Обновили описание параметров `search.types` в запросе и `points.type` в ответе методов.<br> |
| [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo) | Обновили описание параметра `return_mile_settings.return_point.type` в ответе метода. |
| [/v2/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatchV2) | Обновили описание метода. |
|[/v1/cargoes-label/get](#operation/CargoesAPI_CargoesLabelGet) | В ответе метода:<br>• добавили параметр `result.file_url`; <br>• пометили устаревшим параметр `result.file_guid`. |
| [/v1/cargoes-label/file/{file_guid}](#operation/CargoesAPI_CargoesLabelFile) | Метод устаревает и будет отключён 10 апреля 2026 года. Переключитесь на [/v1/cargoes-label/get](#operation/CargoesAPI_CargoesLabelGet). |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибки `INCORRECT_OVH_FOR_POSTING` для метода [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). |
| [/v2/order/create](#operation/OrderAPI_OrderCreate) | Добавили параметр `splits.items.offer_id` в запрос метода. |
| [/v2/delivery/checkout](#operation/DeliveryCheckout) | Добавили параметр `items.offer_id` в запрос метода и `splits.items.offer_id` в ответ метода. |
| [/v2/cluster/list](#operation/DraftClusterList) | Добавили бета-метод для получения информации о макролокальных кластерах. |
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Добавили параметр `macrolocal_cluster_ids` в запрос метода.<br>Добавили параметр `items.macrolocal_cluster_id` в ответ метода. |

## 6 марта 2026

| Метод | Изменение |
|-------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| — | Изменили название раздела **Порядок работы с методами → Участвуйте в акциях** на [**Порядок работы с методами → Участвуйте в акциях Ozon**](#section/Uchastvujte-v-akciyah-Ozon).<br>Изменили название раздела **Акции** на [**Акции Ozon**](#tag/Promos).<br>Добавили раздел [**Порядок работы с методами → Работа с акциями продавца**](#section/Rabota-s-akciyami-prodavca).<br>Добавили описание раздела [**Акции продавца**](#tag/SellerActions). |

## 4 марта 2026

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| [/v1/returns/settings/utilization/history](#operation/UtilizationHistory) <br> [/v1/returns/settings/utilization/info](#operation/UtilizationInfo) <br> [/v1/returns/settings/utilization/update](#operation/UtilizationUpdate) <br> [/v1/cargoes/get](#operation/CargoesGet) <br> [/v1/product/prices/details](#operation/ProductPricesDetails) | Перенесли методы из бета-раздела в основной. |

## 2 марта 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/seller-actions/create/discount](#operation/SellerActionsCreateDiscount) <br> [/v1/seller-actions/create/discount-with-condition](#operation/SellerActionsCreateDiscountWithCondition) <br> [/v1/seller-actions/create/installment](#operation/SellerActionsCreateInstallment) <br> [/v1/seller-actions/create/multi-level-discount](#operation/SellerActionsCreateMultiLevelDiscount) <br> /v1/seller-actions/create/ozon-card-discount <br> [/v1/seller-actions/create/voucher](#operation/SellerActionsCreateVoucher) <br> [/v1/seller-actions/update/discount](#operation/SellerActionsUpdateDiscount) <br> [/v1/seller-actions/update/discount-with-condition](#operation/SellerActionsUpdateDiscountWithCondition) <br> [/v1/seller-actions/update/installment](#operation/SellerActionsUpdateInstallment) <br> [/v1/seller-actions/update/multi-level-discount](#operation/SellerActionsUpdateMultiLevelDiscount) <br> /v1/seller-actions/update/ozon-card-discount <br> [/v1/seller-actions/update/voucher](#operation/SellerActionsUpdateVoucher) <br> [/v1/seller-actions/products/add](#operation/SellerActionsProductsAdd) <br> [/v1/seller-actions/products/candidates](#operation/SellerActionsProductsCandidates) <br> [/v1/seller-actions/products/delete](#operation/SellerActionsProductsDelete) <br> [/v1/seller-actions/products/list](#operation/SellerActionsProductsList) <br> [/v1/seller-actions/archive](#operation/SellerActionsArchive) <br> [/v1/seller-actions/change-activity](#operation/SellerActionsChangeActivity) <br> [/v1/seller-actions/list](#operation/SellerActionsList) <br> [/v1/seller-actions/voucher/get](#operation/SellerActionsVoucherGet) | Добавили бета-методы для работы с акциями продавца. |
| /v1/draft/create<br>/v1/draft/create/info<br>/v1/draft/timeslot/info<br>/v1/draft/supply/create<br>/v1/draft/supply/create/status | Методы устаревают и будут отключены 16 марта 2026 года. |
| [/v2/draft/create/info](#operation/DraftCreateInfo) | • Добавили параметр `clusters.supply_type` в ответ метода.<br>• Добавили значение `MINIMUM_VOLUME_IN_LITRES_INVALID` параметра `errors.error_reasons` в ответе метода.<br>• Обновили описание параметров `clusters.warehouses.storage_warehouse` и `clusters.warehouses.total_rank` в ответе метода. |
| [/v2/draft/timeslot/info](#operation/DraftTimeslotInfo) | • Добавили параметр `supply_type` в запрос метода.<br>• Добавили значение `INVALID_REQUESTED_CLUSTER_IDS` параметра `error_reason` в ответе метода.<br>• Обновили описание параметров `selected_cluster_warehouses` и `selected_cluster_warehouses.storage_warehouse_id` в запросе метода. |
| [/v2/draft/supply/create](#operation/DraftSupplyCreate) | • Добавили параметр `supply_type` в запрос метода.<br>• Добавили значение `MINIMUM_VOLUME_IN_LITRES_INVALID` параметра `error_reasons` в ответе метода.<br>• Обновили описание параметра `selected_cluster_warehouses.storage_warehouse_id` в запросе метода. |
| [/v3/supply-order/get](#operation/SupplyOrderGet) | Добавили параметр `supplies.macrolocal_cluster_id` в ответ метода. |
| [/v1/supply-order/details](#operation/SupplyOrderAPI_SupplyOrderDetails) | • Добавили параметр `supplies.macrolocal_cluster_id` в ответ метода.<br>• Обновили описание параметра `vehicle.value` в ответ метода. |
| [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate) <br> [/v1/draft/direct/create](#operation/DraftDirectCreate) <br> [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate) <br> [/v2/draft/create/info](#operation/DraftCreateInfo) <br> [/v2/draft/timeslot/info](#operation/DraftTimeslotInfo) <br> [/v2/draft/supply/create](#operation/DraftSupplyCreate) <br> [/v2/draft/supply/create/status](#operation/DraftSupplyCreateStatus) <br> [/v1/warehouse/fbo/seller/list](#operation/WarehouseFboSellerList) | Перенесли методы из бета-раздела в основной. |

## 26 февраля 2026

| Метод | Изменение |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Обновили описание параметра `items.is_kgt` в ответе метода. | 
| [/v1/carriage/act-discrepancy/pdf](#operation/CarriageActDiscrepancyPDF) | Добавили бета-метод для получения акта о расхождениях по отгрузке FBS. | 
| — | В разделах [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема FBS Стандарт**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBS-Standart) и [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема FBS PickUp с доверительной приёмкой**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBS-PickUp-s-doveritelnoj-priyomkoj) обновили порядок работы с PDF-документами. |
| — | В разделе [**Порядок работы с методами → Получите информацию о складах**](#section/Poluchite-informaciyu-o-skladah) обновили описание работы с методами. |

## 24 февраля 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate) <br> [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate)| Обновили описание параметра `delivery_info.drop_off_warehouse.warehouse_type` в запросе методов.|

## 20 февраля 2026

| Метод | Изменение |
|------------------------------------------------|--------------------------------------------------------------------------------------------------|
| — | В разделе [**Авторизация через API-ключ**](#tag/Auth) обновили информацию о работе с API-ключом. |
| [/v1/roles](#operation/AccessAPI_RolesByToken) | Добавили параметр `expires_at` в ответ метода. |
| /v2/chat/history | Метод устарел, удалили его из документации. Используйте [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3). |

## 17 февраля 2026

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/fbp/draft/direct/seller-dlv/create](#operation/FbpDraftDirectSellerDlvCreate) | Пометили обязательными параметры `bundle_id`, `delivery_details`, `delivery_details.driver_name`, `delivery_details.timeslot_start`, `delivery_details.vehicle_number`, `delivery_details.vehicle_type`, `package_units_count` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/direct/seller-dlv/edit](#operation/FbpDraftDirectSellerDlvEdit) | Пометили обязательными параметры `driver_name`, `row_version`, `supply_id`, `vehicle_number` и `vehicle_type` в запросе метода. |
| [/v1/fbp/draft/direct/timeslot/edit](#operation/FbpDraftDirectTimeslotEdit) | Пометили обязательными параметры `row_version`, `supply_id` и `timeslot_start` в запросе метода. |
| [/v1/fbp/draft/direct/timeslot/get](#operation/FbpDraftDirectGetTimeslot) | Пометили обязательными параметры `bundle_id`, `interval_end`, `interval_start` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/direct/create](#operation/FbpDraftDirectCreate) | Пометили обязательными параметры `bundle_id`, `delivery_details`, `delivery_details.timeslot_start`, `package_units_count` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/direct/delete](#operation/FbpDraftDirectDelete)<br>[/v1/fbp/draft/drop-off/delete](#operation/FbpDraftDropOffDelete)<br>[/v1/fbp/draft/pick-up/delete](#operation/FbpAPI_FbpDraftPickUpDelete)<br>[/v1/fbp/order/direct/cancel](#operation/FbpAPI_FbpOrderDirectCancel) | Пометили обязательным параметр `supply_id` в запросе методов. |
| [/v1/fbp/draft/direct/product/validate](#operation/FbpDraftDirectProductValidate)<br>[/v1/fbp/draft/drop-off/product/validate](#operation/FbpDraftDropOffProductValidate)<br>[/v1/fbp/draft/pick-up/product/validate](#operation/FbpAPI_FbpDraftPickUpProductValidate) | Пометили обязательными параметры `skus`, `skus.count`, `skus.sku` и `warehouse_id` в запросе методов. |
| [/v1/fbp/draft/direct/registrate](#operation/FbpDraftDirectRegistrate)<br>[/v1/fbp/draft/drop-off/registrate](#operation/FbpDraftDropOffRegistrate)<br>[/v1/fbp/draft/pick-up/registrate](#operation/FbpDraftPickUpRegistrate) | Пометили обязательными параметры `row_version` и `supply_id` в запросе методов. |
| [/v1/fbp/draft/direct/tpl-dlv/create](#operation/FbpAPI_FbpDraftDirectTplDlvCreate) | Пометили обязательными параметры `bundle_id`, `delivery_details`, `delivery_details.timeslot_start`, `delivery_details.tracking_number`, `delivery_details.transport_company_name`, `package_units_count` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/direct/tpl-dlv/edit](#operation/FbpAPI_FbpDraftDirectTplDlvEdit) | Пометили обязательными параметры `row_version`, `supply_id`, `tracking_number` и `transport_company_name` в запросе метода. |
| [/v1/fbp/draft/drop-off/create](#operation/FbpDraftDropOffCreate) | Пометили обязательными параметры `bundle_id`, `delivery_details`, `delivery_details.drop_off_date`, `delivery_details.drop_off_point_id`, `delivery_details.drop_off_province_uuid`, `package_units_count` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/drop-off/dlv/edit](#operation/FbpDraftDropOffDlvEdit) | Пометили обязательными параметры `drop_off_date`, `drop_off_point_id`, `drop_off_province_uuid`, `row_version` и `supply_id` в запросе метода. |
| [/v1/fbp/draft/drop-off/province/list](#operation/FbpDraftDropOffProvinceList) | Пометили обязательным параметр `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/drop-off/point/list](#operation/FbpDraftDropOffPointList) | Пометили обязательными параметры `page_size`, `province_uuid` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/drop-off/point/timetable](#operation/FbpDraftDropOffPointTimetable) | Пометили обязательными параметры `drop_off_point_id`, `province_uuid` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/pick-up/create](#operation/FbpAPI_FbpDraftPickupCreate) | Пометили обязательными параметры `bundle_id`, `delivery_details`, `delivery_details.address`, `delivery_details.comment`, `delivery_details.date`, `delivery_details.sender_name`, `delivery_details.sender_phone`, `package_units_count` и `warehouse_id` в запросе метода. |
| [/v1/fbp/draft/pick-up/dlv/edit](#operation/FbpAPI_FbpDraftPickupDlvEdit) | Пометили обязательными параметры `row_version`, `supply_id`, `pickup_details`, `pickup_details.address`, `pickup_details.comment`, `pickup_details.date`, `pickup_details.sender_name` и `pickup_details.sender_phone` в запросе метода. |

## 16 февраля 2026

| Метод | Изменение |
|---|---|
| [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList) | Метод устаревает и будет отключён 20 марта 2026 года. Переключитесь на [/v2/warehouse/list](#operation/WarehouseListV2). |
| [/v1/posting/carriage-available/list](#operation/PostingAPI_GetCarriageAvailableList)<br>[/v1/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryList) | Методы устаревают и будут отключены 20 марта 2026 года. Переключитесь на [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2). |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.addressee.pin` в ответ метода. |

## 12 февраля 2026

| Метод | Изменение |
|---|---|
| [/v1/returns/rfbs/action/set](#operation/ReturnsAPI_ReturnsRfbsActionSet) | Пометили обязательным параметр `return_id` в запросе метода. |
| [/v1/chat/send/file](#operation/ChatAPI_ChatSendFile) | Пометили обязательными параметры `base64_content` и `name` в запросе метода. |
| [/v2/report/returns/create](#operation/ReportAPI_ReportReturnsCreate) | Пометили обязательным параметр `filter` в запросе метода. |
| [/v1/report/postings/create](#operation/ReportAPI_CreateCompanyPostingsReport) | Пометили обязательными параметры `filter.processed_at_from` и `filter.processed_at_to` в запросе метода. |
| [/v1/report/marked-products-sales/create](#operation/CreateCompanyMarkedProductsSalesReport) | Пометили обязательными параметры `date.from` и `date.to` в запросе метода. |
| [/v1/finance/document-b2b-sales](#operation/ReportAPI_CreateDocumentB2BSalesReport)<br>[/v1/finance/document-b2b-sales/json](#operation/ReportAPI_CreateDocumentB2BSalesJSONReport)<br>[/v1/finance/mutual-settlement](#operation/ReportAPI_CreateMutualSettlementReport) | Пометили обязательным параметр `date` в запросе методов. |
| [/v1/product/info/wrong-volume](#operation/ProductAPI_ProductInfoWrongVolume)<br>/v1/product/quant/list<br>[/v1/warehouse/fbs/pickup/history/list](#operation/WarehouseFbsPickUpHistoryList) | Пометили обязательным параметр `limit` в запросе методов. |
| [/v1/product/stairway-discount/by-quantity/set](#operation/ProductAPI_SetProductStairwayDiscountByQuantity) | Пометили обязательными параметры `stairways`, `stairways.enabled`, `stairways.sku`, `stairways.stairway`, `stairways.stairway.steps`, `stairways.stairway.steps.discount`, `stairways.stairway.steps.quantity` и `stairways.stairway.steps.step` в запросе метода. |
| [/v1/product/stairway-discount/by-quantity/get](#operation/ProductAPI_GetProductStairwayDiscountByQuantity)<br>[/v1/product/placement-zone/info](#operation/ProductAPI_GetProductPlacementZoneInfo)<br>[/v1/product/prices/details](#operation/ProductPricesDetails) | Пометили обязательным параметр `skus` в запросе методов. |
| [/v2/draft/supply/create](#operation/DraftSupplyCreate) | Пометили обязательными параметры `timeslot`, `timeslot.from_in_timezone` и `timeslot.to_in_timezone` в запросе метода. |
| [/v1/warehouse/fbs/update](#operation/UpdateWarehouseFBS) | Пометили обязательным параметр `address_coordinates` в запросе метода. |
| [/v1/warehouse/fbs/pickup/courier/create](#operation/WarehouseFbsPickUpCourierCreate)<br>[/v1/warehouse/fbs/pickup/courier/cancel](#operation/WarehouseFbsPickUpCourierCancel) | Пометили обязательным параметр `warehouse_id` в запросе методов. |
| [/v1/actions/discounts-task/list](#operation/promos_task_list) | Пометили обязательным параметр `page` в запросе метода. |
| [/v1/fbp/draft/get](#operation/FbpAPI_FbpDraftGet) | Пометили обязательным параметр `supply_id` в запросе метода. |
| [/v1/fbp/draft/list](#operation/FbpAPI_FbpDraftList) | Пометили обязательным параметр `count` в запросе метода. |
| [/v1/fbp/order/direct/seller-dlv/edit](#operation/FbpAPI_FbpOrderDirectSellerDlvEdit) | Пометили обязательными параметры `driver_name`, `row_version`, `supply_id`, `vehicle_number` и `vehicle_type` в запросе метода. |
| [/v1/fbp/order/direct/timeslot/edit](#operation/FbpAPI_FbpEditTimeslot) | Пометили обязательными параметры `row_version`, `supply_id` и `timeslot_start` в запросе метода. |
| [/v1/fbp/order/direct/timeslot/list](#operation/FbpAPI_FbpAvailableTimeslotList) | Пометили обязательными параметры `interval_end`, `interval_start` и `supply_id` в запросе метода. |
| [/v1/fbp/order/drop-off/cancel](#operation/FbpAPI_FbpOrderDropOffCancel) <br> [/v1/fbp/order/pick-up/cancel](#operation/FbpAPI_FbpOrderPickUpCancel) <br> [/v1/fbp/act-from/create](#operation/FbpAPI_FbpCreateAct) <br> [/v1/fbp/act-to/create](#operation/FbpAPI_FbpCreateConsignmentNote) <br> [/v1/fbp/order/get](#operation/FbpAPI_FbpOrderGet) | Пометили обязательным параметр `supply_id` в запросе методов. |
| [/v1/fbp/order/drop-off/dlv/edit](#operation/FbpAPI_FbpOrderDropOffDlvEdit) | Пометили обязательными параметры `drop_off_date`, `row_version` и `supply_id` в запросе метода. |
| [/v1/fbp/order/drop-off/timetable](#operation/FbpAPI_FbpOrderDropOffTimetable) | Пометили обязательными параметры `drop_off_point_id`, `province_uuid` и `warehouse_id` в запросе метода. |
| [/v1/fbp/order/pick-up/dlv/edit](#operation/FbpAPI_FbpOrderPickUpDlvEdit) | Пометили обязательными параметры `pickup_details`, `pickup_details.sender_name`, `pickup_details.sender_phone`, `row_version` и `supply_id` в запросе метода. |
| [/v1/fbp/act-from/get](#operation/FbpAPI_FbpCheckActState) | Пометили обязательным параметр `file_uuid` в запросе метода. |
| [/v1/fbp/act-to/get](#operation/FbpAPI_FbpCheckConsignmentNoteState) | Пометили обязательными параметры `code` и `supply_id` в запросе метода. |
| [/v1/fbp/order/list](#operation/FbpAPI_FbpOrderList) | Пометили обязательным параметр `count` в запросе метода. |
| [/v1/cancel-reason/list-by-order](#operation/CancelReasonListByOrder) | Пометили обязательным параметр `order_number` в запросе метода. |
| [/v1/cancel-reason/list-by-posting](#operation/CancelReasonAPI_CancelReasonListByPosting) | Пометили обязательным параметр `posting_number` в запросе метода. |
| [/v1/delivery/check](#operation/DeliveryCheck) | Пометили обязательным параметр `client_phone` в запросе метода. |
| [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2) | Пометили обязательным параметр `limit` в запросе метода. |
| [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate)<br>[/v1/draft/direct/create](#operation/DraftDirectCreate)<br>[/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate) | Обновили описание методов. |
| [/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU) | Обновили описание метода. |
| [/v2/draft/timeslot/info](#operation/DraftTimeslotInfo)<br>[/v2/draft/create/info](#operation/DraftCreateInfo) | Обновили описание методов.<br>Обновили описание параметра `draft_id` в запросе методов. |
| [/v2/draft/supply/create](#operation/DraftSupplyCreate) | Обновили описание параметра `draft_id` в запросе метода. |

## 10 февраля 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| [/v3/product/list](#operation/ProductAPI_GetProductList)<br>[/v4/product/info/attributes](#operation/ProductAPI_GetProductAttributesV4)<br>[/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks)<br>[/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Обновили описание параметра `filter.visibility` в запросе методов. |

## 9 февраля 2026

| Метод | Изменение |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| [/v3/supply-order/get](#operation/SupplyOrderGet) | Отметили устаревшим параметр `orders.supplies.storage_warehouse.arrival_date` в ответе метода. |
| [/v1/supply-order/details](#operation/SupplyOrderAPI_SupplyOrderDetails) | Отметили устаревшим параметр `supplies.storage_warehouse.arrival_date` в ответе метода. |
| [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) | Обновили описание параметра `delivery_method_id` в запросе метода. |
| [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2) | Обновили описание параметра `filter.delivery_method_id` в запросе метода. |
| [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2) | Изменили название метода. |
| [/v2/order/create](#operation/OrderAPI_OrderCreate) | Пометили обязательными параметры `delivery_schema`, `splits.delivery_method`, `splits.delivery_method.delivery_method_id`, `splits.delivery_method.delivery_type`, `splits.delivery_method.timeslot_id`, `splits.delivery_method.logistic_date_range`, `splits.delivery_method.logistic_date_range.from`, `splits.delivery_method.logistic_date_range.to`, `splits.items`, `items.price`, `items.quantity`, `items.sku`, `splits.warehouse_id`, `delivery.courier.city`, `delivery.courier.country`, `delivery.courier.house_number` и `delivery.pick_up.map_point_id` в запросе метода. |

## 5 февраля 2026

| Метод | Изменение |
|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [/v1/product/certificate/bind](#operation/ProductAPI_ProductCertificateBind) | Пометили обязательными параметры `product_id` и `certificate_id` в запросе метода. |
| [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode) | Пометили обязательным параметр `barcode` в запросе метода. |
| [/v2/posting/fbs/cancel](#operation/PostingAPI_CancelFbsPosting) | Пометили обязательными параметры `cancel_reason_id` и `posting_number` в запросе метода. |
| [/v1/posting/unpaid-legal/product/list](#operation/PostingAPI_UnpaidLegalProductList) | Пометили обязательным параметр `limit` в запросе метода. |
| [/v1/cargoes/delete](#operation/CargoesAPI_CargoesDelete) | Пометили обязательными параметры `cargo_ids` и `supply_id` в запросе метода. |
| [/v1/cargoes/delete/status](#operation/CargoesAPI_CargoesDeleteStatus) | Пометили обязательным параметр `operation_id` в запросе метода. |
| [/v1/cargoes/rules/get](#operation/CargoesAPI_CargoesRulesGet) | Пометили обязательным параметр `supply_ids` в запросе метода. |
| [/v1/supply-order/content/update](#operation/SupplyOrderAPI_SupplyOrderContentUpdate) | Пометили обязательными параметры `order_id`, `supply_id`, `items`, `items.quant`, `items.quantity` и `items.sku` в запросе метода. |
| [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) | Пометили обязательным параметр `operation_id` в запросе метода. |
| [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) | Пометили обязательными параметры `posting_number`, `products`, `products.product_id`, `products.exemplars` и `products.exemplars.exemplar_id` в запросе метода. |
| [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) <br> [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) <br> [/v1/fbs/posting/product/exemplar/update](#operation/PostingAPI_FbsPostingProductExemplarUpdate)| Пометили обязательным параметр `posting_number` в запросе методов. |
| [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5) | Пометили обязательными параметры `posting_number`, `products.product_id` и `products.exemplars` в запросе метода. |
| [/v1/carriage/set-postings](#operation/CarriageAPI_SetPostings) | Пометили обязательными параметры `carriage_id` и `posting_numbers` в запросе метода. |
| [/v1/carriage/cancel](#operation/CarriageAPI_CarriageCancel) | Пометили обязательным параметр `carriage_id` в запросе метода. |
| [/v1/assembly/carriage/posting/list](#operation/AssemblyCarriagePostingList) <br> [/v1/assembly/carriage/product/list](#operation/AssemblyCarriageProductList) | Пометили обязательным параметр `filter.carriage_id` в запросе методов. |
| [/v1/assembly/fbs/posting/list](#operation/AssemblyFbsPostingList) | Пометили обязательными параметры `sort_dir`, `filter.cutoff_from` и `filter.cutoff_to` в запросе метода. |
| [/v1/assembly/fbs/product/list](#operation/AssemblyFbsProductList) | Пометили обязательными параметры `filter.cutoff_from` и `filter.cutoff_to` в запросе метода. |

## 3 февраля 2026

| Метод | Изменение |
|----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/report/info](#operation/ReportAPI_ReportInfo) | Обновили описание параметра `result.report_type` в ответе метода. |
| [/v1/report/list](#operation/ReportAPI_ReportList) | Обновили описание параметра `report_type` в запросе метода.<br>Обновили описание параметра `result.reports.report_type` в ответе метода. |

## 2 февраля 2026

| Метод | Изменение |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [/v1/rating/index/fbs/info](#operation/RatingAPI_GetFBSRatingIndexInfoV1) <br> [/v1/rating/index/fbs/posting/list](#operation/RatingAPI_ListFBSRatingIndexPostingsV1) <br> [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2) <br> [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2) <br> [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2) <br> [/v1/delivery-method/return/settings/get](#operation/GetDeliveryMethodReturnSettingsV1) <br> [/v1/supply-order/details](#operation/SupplyOrderAPI_SupplyOrderDetails) <br> [/v1/product/placement-zone/info](#operation/ProductAPI_GetProductPlacementZoneInfo) <br> [/v2/warehouse/list](#operation/WarehouseListV2) <br> [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) <br> [/v1/warehouse/archive](#operation/ArchiveWarehouseFBS) <br> [/v1/warehouse/unarchive](#operation/UnarchiveWarehouseFBS) <br> [/v1/warehouse/invalid-products/get](#operation/WarehouseInvalidProductsGet) <br> [/v1/warehouse/warehouses-with-invalid-products](#operation/WarehouseWithInvalidProducts) <br> [/v1/warehouse/fbs/create/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForCreateFBSWarehouse) <br> [/v1/warehouse/fbs/create/drop-off/timeslot/list](#operation/WarehouseFbsCreateDropOffTimeslotList) <br> [/v1/warehouse/fbs/create/pick-up/timeslot/list](#operation/WarehouseFbsCreatePickUpTimeslotList) <br>[/v1/warehouse/fbs/create/return-point/list](#operation/WarehouseFBSCreateReturnPointList) <br> [/v1/warehouse/fbs/create](#operation/WarehouseAPI_CreateWarehouseFBS) <br> [/v1/warehouse/fbs/first-mile/update](#operation/UpdateWarehouseFBSFirstMile) <br> [/v1/warehouse/fbs/pickup/courier/cancel](#operation/WarehouseFbsPickUpCourierCancel) <br> [/v1/warehouse/fbs/pickup/courier/create](#operation/WarehouseFbsPickUpCourierCreate) <br> [/v1/warehouse/fbs/pickup/history/list](#operation/WarehouseFbsPickUpHistoryList) <br> [/v1/warehouse/fbs/pickup/planning/list](#operation/WarehouseFbsPickUpPlanningList) <br> [/v1/warehouse/fbs/return-mile/check](#operation/WarehouseFbsReturnMileCheck) <br> [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo) <br> [/v1/warehouse/fbs/update/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForUpdateFBSWarehouse) <br> [/v1/warehouse/fbs/update/drop-off/timeslot/list](#operation/WarehouseFbsUpdateDropOffTimeslotList) <br> [/v1/warehouse/fbs/update/pick-up/timeslot/list](#operation/WarehouseFbsUpdatePickUpTimeslotList) <br> [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList) <br> [/v1/warehouse/fbs/update](#operation/UpdateWarehouseFBS) <br> [/v1/polygon/delete](#operation/PolygonDelete) <br> [/v1/polygon/list](#operation/PolygonList) <br> [/v1/polygon/time/coordinates/update](#operation/PolygonTimeCoordinatesUpdate) <br> [/v1/polygon/time/set](#operation/PolygonTimeSet) <br> [/v1/warehouse/erfbs/aggregator/create](#operation/WarehouseERFBSAggregatorCreate) <br> [/v1/warehouse/erfbs/aggregator/delivery-method/update](#operation/WarehouseERFBSAggregatorDeliveryMethodUpdate) <br> [/v1/warehouse/erfbs/non-integrated/create](#operation/WarehouseERFBSNonIntegratedCreate) <br> [/v1/warehouse/erfbs/non-integrated/delivery-method/update](#operation/WarehouseERFBSNonIntegratedDeliveryMethodUpdate) <br> [/v1/warehouse/erfbs/update](#operation/WarehouseERFBSUpdate) <br> [/v2/polygon/bind](#operation/PolygonBind) | Перенесли методы из бета-раздела в основной. |
| [/v2/posting/fbs/act/create](#operation/PostingAPI_PostingFBSActCreate) <br> [/v1/posting/carriage-available/list](#operation/PostingAPI_GetCarriageAvailableList) | Обновили описание параметра `delivery_method_id` в запросе методов. |

## 27 января 2026

| Метод | Изменение |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| — | В разделах [**Порядок работы с методами → Обновите цены и остатки товаров**](#section/Obnovite-ceny-i-ostatki-tovarov) и [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBP) обновили описание работы с методами. |
| [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) | Обновили описание метода. |

## 26 января 2026

| Метод | Изменение |
|---------------------------------------------------------------|------------------------------------------------------------------------|
| [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) <br> [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)| Добавили параметры `result.fact_delivery_date` и `result.financial_data.products.customer_currency_code` в ответ методов. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) <br> [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.financial_data.products.customer_currency_code` в ответ методов. |

## 23 января 2026

| Метод | Изменение |
|---------------------------------------------------------------|------------------------------------------------------------------------|
| [/v1/returns/settings/utilization/history](#operation/UtilizationHistory) <br> [/v1/returns/settings/utilization/info](#operation/UtilizationInfo) <br> [/v1/returns/settings/utilization/update](#operation/UtilizationUpdate) | Добавили бета-методы для работы с автоутилизацией. |
| [/v2/actions/discounts-task/list](#operation/GetDiscountTaskListV2) | Добавили бета-метод для получения списка заявок на скидку. |
| [/v1/actions/discounts-task/list](#operation/promos_task_list) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/actions/discounts-task/list](#operation/GetDiscountTaskListV2). |

## 22 января 2026

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/report/products/create](#operation/ReportAPI_CreateCompanyProductsReport) | Обновили описание параметра `visibility` в запросе метода. |
| [/v1/report/placement/by-products/create](#operation/CreatePlacementByProductsReport)<br>[/v1/report/placement/by-supplies/create](#operation/CreatePlacementBySuppliesReport) | Обновили описание методов. |
| [/v2/order/create](#operation/OrderAPI_OrderCreate) | В запросе метода: обновили описание параметра `splits.items.price`;
пометили обязательными параметры `splits.items.price`, `splits.items.price.currency_code` и `splits.items.price.units`.
 |
| [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove) | Обновили описание метода. |
| [/v1/carriage/get](#operation/CarriageGet) | Обновили описание параметра `available_actions` в ответе метода. |
| [/v2/posting/fbs/digital/act/check-status](#operation/PostingAPI_PostingFBSDigitalActCheckStatus) | Метод устаревает и будет отключён 22 марта 2026 года. Переключитесь на [/v2/posting/fbs/act/check-status](#operation/PostingAPI_PostingFBSActCheckStatus). |
| [/v2/posting/fbs/act/get-pdf](#operation/PostingAPI_PostingFBSGetAct) | Обновили описание метода.<br>Обновили описание параметра `id` в запросе метода. |
| [/v2/posting/fbs/digital/act/get-pdf](#operation/PostingAPI_PostingFBSGetDigitalAct) | Метод устаревает и будет отключён 22 марта 2026 года. Переключитесь на [/v2/posting/fbs/act/get-pdf](#operation/PostingAPI_PostingFBSGetAct). |
| [/v2/posting/fbs/act/check-status](#operation/PostingAPI_PostingFBSActCheckStatus) | Обновили описание параметра `result.act_type` в ответе метода. |
| — | В разделах [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема FBS Стандарт**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBS-Standart) и [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема FBS PickUp с доверительной приёмкой**](#section/Upravlyajte-zakazami-FBO-FBS-rFBS-i-FBP/Shema-FBS-PickUp-s-doveritelnoj-priyomkoj) обновили порядок работы с файлами. |

## 20 января 2026

| Метод | Изменение |
|---------------------------------------------------------------|------------------------------------------------------------------------|
| /v2/fbs/posting/sent-by-seller | Метод устарел, удалили его из документации. |
| — | В разделах [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема rFBS Crossborder**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Shema-rFBS-Crossborder) и [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема rFBS Crossborder с интегрированной службой доставки**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Shema-rFBS-Crossborder-s-integrirovannoj-sluzhboj-dostavki) обновили описание работы с методами. | 

## 16 января 2026

| Метод | Изменение |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate) <br> [/v1/draft/direct/create](#operation/DraftDirectCreate) <br> [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate) <br> [/v2/draft/create/info](#operation/DraftCreateInfo) <br> [/v2/draft/timeslot/info](#operation/DraftTimeslotInfo) <br> [/v2/draft/supply/create](#operation/DraftSupplyCreate) <br> [/v2/draft/supply/create/status](#operation/DraftSupplyCreateStatus) <br> [/v1/warehouse/fbo/seller/list](#operation/WarehouseFboSellerList)| Добавили бета-методы для работы с заявками на поставку FBO. |
| [/v1/cargoes/get](#operation/CargoesGet) | Добавили бета-метод для получения информации о грузоместах. | 
| [/v3/supply-order/get](#operation/SupplyOrderGet) | Добавили параметры `orders.order_tags.is_pickup` и `orders.order_tags.seller_warehouse_id` в ответ метода. |
| [/v1/supply-order/timeslot/update](#operation/SupplyOrderAPI_UpdateSupplyOrderTimeslot) <br> [/v1/supply-order/timeslot/status](#operation/SupplyOrderAPI_GetSupplyOrderTimeslotStatus)| Обновили описание параметра `errors` в ответе методов. |
| [/v1/report/info](#operation/ReportAPI_ReportInfo) | Обновили описание параметра `result.report_type` в ответе метода. |
| [/v1/report/list](#operation/ReportAPI_ReportList) | Обновили описания параметров `report_type` в запросе метода и `result.reports.report_type` в ответе метода. |

## 15 января 2026

| Метод | Изменение |
|---------------------------------------------------------------|------------------------------------------------------------------------|
| [/v1/product/prices/details](#operation/ProductPricesDetails) | Добавили бета-метод для получения подробной информации о цене товаров. |

## 13 января 2026

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| /v5/fbs/posting/product/exemplar/create-or-get<br>/v4/fbs/posting/product/exemplar/set<br>/v5/fbs/posting/product/exemplar/set<br>/v4/fbs/posting/product/exemplar/status<br>/v4/fbs/posting/product/exemplar/validate<br>/v2/supply-order/list<br>/v2/supply-order/get | Методы устарели, удалили их из документации. |

## 30 декабря 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
| [/v1/report/marked-products-sales/create](#operation/CreateCompanyMarkedProductsSalesReport) <br>[/v1/posting/fbs/traceable/split](#operation/PostingFbsTraceableSplit) <br>[/v1/posting/fbs/product/traceable/attribute](#operation/PostingFbsProductTraceableAttribute) <br>[/v1/carriage/ettn/status](#operation/CarriageEttnStatus) <br>[/v1/assembly/carriage/posting/list](#operation/AssemblyCarriagePostingList) <br>[/v1/assembly/carriage/product/list](#operation/AssemblyCarriageProductList) <br>[/v1/assembly/fbs/posting/list](#operation/AssemblyFbsPostingList) <br>[/v1/assembly/fbs/product/list](#operation/AssemblyFbsProductList) <br>[/v1/seller/info](#operation/SellerAPI_SellerInfo) <br>[/v1/seller/ozon-logistics/info](#operation/SellerAPI_SellerOzonLogisticsInfo) | Перенесли методы из бета-раздела в основной. |
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Обновили описание параметра `prices.vat` в запросе метода. |
| [/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU) <br>[/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Обновили описание параметра `items.vat` в запросе методов. |

## 26 декабря 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| [/v2/returns/rfbs/list](#operation/RFBSReturnsAPI_ReturnsRfbsListV2) <br>[/v2/returns/rfbs/list](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2) | Параметр `returns.client_name` в ответе метода устаревает, отключим его 2 февраля 2026 года. |

## 25 декабря 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [/v1/report/placement/by-products/create](#operation/CreatePlacementByProductsReport) | Добавили метод для получения отчёта о стоимости размещения по товарам.| 
| [/v1/report/placement/by-supplies/create](#operation/CreatePlacementBySuppliesReport) | Добавили метод для получения отчёта о стоимости размещения по поставкам.|
| [/v1/product/placement-zone/info](#operation/ProductAPI_GetProductPlacementZoneInfo) | Добавили бета-метод для получения информации о зонах размещения товаров по их SKU перед поставкой. |
|[/v1/report/info](#operation/ReportAPI_ReportInfo)| Обновили описание параметра `result.report_type` в ответе метода.|
|[/v1/report/list](#operation/ReportAPI_ReportList) | Обновили описание параметра `report_type` в запросе метода. <br> Обновили описание параметра `result.reports.report_type` в ответе метода. |
| [/v2/finance/realization](#operation/FinanceAPI_GetRealizationReportV2) | Удалили параметры `result.header.doc_amount` и `result.header.vat_amount` из ответа метода. | 
| [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1) | Удалили параметры `header.doc_amount` и `header.vat_amount` из ответа метода. |
| [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) | Обновили описание параметра `products.exemplars.marks.check_status` в ответе метода. |
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Обновили описание параметра `items.price.retail_price` в ответе метода. |
| [/v3/product/list](#operation/ProductAPI_GetProductList) | Обновили описание параметра `result.items.quants` в ответе метода. |
| /v2/posting/fbs/product/change | Метод устарел, удалили его из документации. |

## 23 декабря 2025

| Метод | Изменение |
|-----------------------------------------------------------------|------------------------------------------------------------|
| [/v1/product/unarchive](#operation/ProductAPI_ProductUnarchive) | Обновили описание параметра `product_id` в запросе метода. | 

## 18 декабря 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [/v1/warehouse/fbs/pickup/courier/create](#operation/WarehouseFbsPickUpCourierCreate) | Добавили бета-метод для вызова курьера на забор отгрузки pick-up со склада FBS. | 
| [/v1/warehouse/fbs/pickup/courier/cancel](#operation/WarehouseFbsPickUpCourierCancel) | Добавили бета-метод для отмены вызова курьера на забор отгрузки pick-up со склада FBS. | 
| [/v1/warehouse/fbs/pickup/planning/list](#operation/WarehouseFbsPickUpPlanningList) | Добавили бета-метод для получения списка складов для планирования отгрузок курьеру. | 
| [/v1/receipts/get](#operation/GetReceipt) <br> [/v1/receipts/seller/list](#operation/ReceiptsSellerList) <br> [/v1/receipts/upload](#operation/UploadReceipt) | Добавили методы для работы с чеками. |

## 16 декабря 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| [/v1/warehouse/fbs/pickup/history/list](#operation/WarehouseFbsPickUpHistoryList) | Добавили бета-метод для работы с историей отгрузок курьерам. | 
| [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) | Обновили описание параметра `status` в ответе метода. | 
| [/v2/warehouse/list](#operation/WarehouseListV2) | Добавили параметр `has_next` в ответ метода. | 

## 15 декабря 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------|-----------------------------------------------------|
| [/v1/warehouse/warehouses-with-invalid-products](#operation/WarehouseWithInvalidProducts) | Добавили бета-метод для получения списка складов, на которых есть товары с ограничениями по доставке rFBS.| 
| [/v1/warehouse/invalid-products/get](#operation/WarehouseInvalidProductsGet) | Добавили бета-метод для получения списка товаров с ограничениями по доставке rFBS. | 

## 12 декабря 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------|-----------------------------------------------------|
| [/v1/finance/balance](#operation/GetFinanceBalanceV1) | Добавили бета-метод для получения отчёта о балансе. |
| [/v1/finance/cash-flow-statement/list](#operation/FinanceAPI_FinanceCashFlowStatementList) | Обновили описание метода. |
| [/v1/returns/list](#operation/returnsList) | Удалили значение `ReturnCompensated` параметра `filter.visual_status_name` в запросе метода. | 

## 11 декабря 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes)<br>[/v1/posting/digital/list](#operation/ListPostingCodes)<br>[/v1/product/digital/stocks/import](#operation/DigitalProductAPI_StocksImport) | Перенесли методы из бета-раздела в основной. | 

## 9 декабря 2025

| Метод | Изменение |
|------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| [/v1/rating/history](#operation/RatingAPI_RatingHistoryV1) | Обновили описание параметра `ratings` в запросе метода. | 
| — | Добавили описание раздела [**Управление кодами маркировки и сборкой заказов для FBS/rFBS**](#tag/FBSandrFBSMarks). | 

## 5 декабря 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| [/v1/delivery-method/return/settings/get](#operation/GetDeliveryMethodReturnSettingsV1) | Добавили бета-метод для получения информации по возвратным настройкам rFBS и rFBS Express. | 
| — | В разделах [**Работа со складами rFBS Express → Доставка «Партнёры Ozon**](#section/Rabota-so-skladami-rFBS-Express/Dostavka-Partnyory-Ozon) и [**Работа со складами rFBS Express → Доставка «Вы или сторонняя служба»**](#section/Rabota-so-skladami-rFBS-Express/Dostavka-Vy-ili-storonnyaya-sluzhba) обновили порядок работы со складами rFBS Express.|

## 4 декабря 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) | Добавили параметр `clusters.macrolocal_cluster_id` в ответ метода. | 
| [/v1/supply-order/details](#operation/SupplyOrderAPI_SupplyOrderDetails) | Добавили бета-метод для получения подробной информации о заявке на поставку. | 
| [/v1/warehouse/fbs/create/return-point/list](#operation/WarehouseFBSCreateReturnPointList) <br> [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList) <br> [/v1/warehouse/fbs/return-mile/info](#operation/WarehouseFBSReturnMileInfo) <br> [/v1/warehouse/fbs/return-mile/check](#operation/WarehouseFbsReturnMileCheck) | Добавили бета-методы для работы с FBS-складами. |
| [/v1/warehouse/fbs/create](#operation/WarehouseAPI_CreateWarehouseFBS) <br> [/v1/warehouse/unarchive](#operation/UnarchiveWarehouseFBS) <br> [/v1/warehouse/archive](#operation/ArchiveWarehouseFBS) <br> [/v1/warehouse/fbs/first-mile/update](#operation/UpdateWarehouseFBSFirstMile)| Добавили параметр `return_point_id` в запрос метода. |
| [/v1/analytics/manage/stocks](#operation/AnalyticsAPI_ManageStocks) | Метод устаревает и будет отключён 22 декабря 2025 года. Переключитесь на [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks). | 
| — | В разделе [**Порядок работы с методами → Работа с FBS-складами**](#section/Rabota-s-FBS-skladami) обновили порядок работы с с FBS-складами. |

## 2 декабря 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2) | Добавили бета-метод для работы с остатками на складах продавца. | 
| [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2) | Добавили бета-метод для получения методов доставки на складе. |
| [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2) | Добавили бета-метод для получения методов доставки и отгрузок. |
| [/v1/posting/carriage-available/list](#operation/PostingAPI_GetCarriageAvailableList)<br>[/v1/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryList) | Методы устаревают и будут отключены с 2 февраля 2026 года. Переключитесь на [/v2/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryListV2). |
| [/v1/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_ProductStocksByWarehouseFbs) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_GetProductInfoStocksByWarehouseFbsV2). |
| [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList) | Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2). |

## 27 ноября 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/actions/candidates](#operation/PromosCandidates)<br>[/v1/actions/products](#operation/PromosProducts) | Добавили параметры `result.products.current_boost`, `result.products.price_min_elastic`, `result.products.price_max_elastic`, `result.products.min_boost` и `result.products.max_boost`. | 
| [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList)<br>[/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) | В ответе методов:обновили описание параметра `result.analytics_data.payment_type_group_name`;
добавили параметры `result.analytics_data.client_delivery_date_begin`, `result.analytics_data.client_delivery_date_end` и `result.substatus`.
 | 
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | В ответе метода:обновили описание параметра `result.analytics_data.payment_type_group_name`;
добавили параметры `result.analytics_data.client_delivery_date_begin` и `result.analytics_data.client_delivery_date_end`.
 |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | В ответе методов:обновили описание параметра `result.postings.analytics_data.payment_type_group_name`;
добавили параметры `result.postings.analytics_data.client_delivery_date_begin` и `result.postings.analytics_data.client_delivery_date_end`.
 | 
| [/v2/warehouse/list](#operation/WarehouseListV2) | Добавили параметры `limit` и `cursor` в запрос метода.<br>Добавили параметр `cursor` в ответ метода. | 
| [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList) | Добавили параметры `limit` и `offset` в запрос метода. | 
| [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) | Пометили устаревшим параметр `items.stocks.warehouse_ids` в ответе метода. | 
| [/v1/report/warehouse/stock](#operation/ReportAPI_CreateStockByWarehouseReport) | Обновили описание параметра `warehouseId` в запросе метода. | 
| [/v1/cancel-reason/list](#operation/CancelReasonList)<br>[/v1/cancel-reason/list-by-order](#operation/CancelReasonListByOrder)<br>[/v1/cancel-reason/list-by-posting](#operation/CancelReasonAPI_CancelReasonListByPosting) | Добавили описание методов.<br>Обновили описание параметра `reasons.id` в ответе методов. | 
| [/v1/delivery/check](#operation/DeliveryCheck) | Добавили описание метода.<br>Обновили описание параметра `client_phone` в запросе метода. |
| [/v2/delivery/checkout](#operation/DeliveryCheckout)<br>[/v1/delivery/map](#operation/DeliveryMap)<br>[/v1/delivery/point/info](#operation/DeliveryPointInfo)<br>[/v1/delivery/point/list](#operation/DeliveryAPI_DeliveryPointList)<br>[/v1/order/cancel](#operation/OrderAPI_OrderCancel)<br>[/v1/order/cancel/check](#operation/OrderAPI_OrderCancelCheck)<br>[/v2/order/create](#operation/OrderAPI_OrderCreate)<br>[/v1/posting/cancel](#operation/PostingAPI_PostingCancel)<br>[/v1/posting/marks](#operation/PostingAPI_PostingMarks) | Добавили описание методов. |
| — | В разделе [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Ozon Логистика**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Ozon-Logistika) обновили порядок работы с возвратами. |

## 25 ноября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| [/v1/product/attributes/update](#operation/ProductAPI_ProductUpdateAttributes) | Обновили описание метода. | 
| — | Добавили раздел [**Порядок работы с методами → Работа со складами rFBS Express**](#section/Rabota-so-skladami-rFBS-Express). | 

## 21 ноября 2025

| Метод | Изменение |
|------------------------------------------------------------------------|----------------------------------------------------------------------------|
| — | Добавили [бета-методы](#tag/DeliveryFBPDraft) для работы с FBP поставками. |
| [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) | Обновили описание параметра `items.stocks.type` в ответе метода. | 

## 20 ноября 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/rating/index/fbs/info](#operation/RatingAPI_GetFBSRatingIndexInfoV1)<br>[/v1/rating/index/fbs/posting/list](#operation/RatingAPI_ListFBSRatingIndexPostingsV1) | Добавили бета-методы для работы с индексом ошибок FBS и rFBS. | 
| [/v1/returns/list](#operation/returnsList) | Добавили параметр `filter.compensation_status_id` в запрос метода.<br>Добавили параметр `returns.compensation_status` в ответ метода. | 

## 18 ноября 2025

| Метод | Изменение |
|-----------------------------------------------------|--------------------------|
| [/v3/supply-order/list](#operation/SupplyOrderList) | Обновили пример запроса. | 
| [/v1/report/info](#operation/ReportAPI_ReportInfo) | Добавили параметр `result.expires_at` в ответ метода. | 
| [/v1/report/list](#operation/ReportAPI_ReportList) | Добавили параметр `result.reports.expires_at` в ответ метода. | 
| [/v1/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryList) | Обновили описание метода. |
| [/v1/supply-order/content/update/validation](#operation/SupplyOrderContentUpdateValidation) | Обновили описание параметра `editing_errors` в ответе метода. | 

## 13 ноября 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| /v1/analytics/average-delivery-time <br> /v1/analytics/average-delivery-time/details <br> /v1/analytics/average-delivery-time/summary | Перенесли методы из бета-раздела в основной. | 

## 12 ноября 2025

| Метод | Изменение |
|------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Параметр `items.marketing_price` в ответе метода устарел, удалили его из документации. | 
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Параметр `price.marketing_price` в ответе метода устарел, удалили его из документации. |

## 11 ноября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| [/v1/seller/info](#operation/SellerAPI_SellerInfo) | Добавили бета-метод для получения информации о кабинете продавца. | 
| [/v1/seller/ozon-logistics/info](#operation/SellerAPI_SellerOzonLogisticsInfo) | Добавили бета-метод для получения информации о подключении продавца к Ozon Логистике. |

## 7 ноября 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/carriage/ettn/status](#operation/CarriageEttnStatus) | Добавили бета-метод для получения статуса проверки электронной ТТН на прослеживаемой перевозке FBS. | 
| [/v1/posting/fbs/product/traceable/attribute](#operation/PostingFbsProductTraceableAttribute) | Добавили бета-метод для получения списка незаполненных атрибутов для прослеживаемых товаров. |
| [/v1/posting/fbs/traceable/split](#operation/PostingFbsTraceableSplit) | Добавили бета-метод для разделения заказа на прослеживаемые отправления. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) <br> [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.require_blr_traceable_attrs` в ответ метода. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.require_blr_traceable_attrs` в ответ метода. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Добавили параметр `filter.is_blr_traceable` в запрос метода. |
| [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) | Добавили параметр `all_blr_traceable` в запрос метода. |
|[/v1/carriage/get](#operation/CarriageGet) | Добавили параметр `all_blr_traceable` в ответ метода. |
| — | Добавили раздел [**Порядок работы с методами → Схема FBS с электронными ТТН**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Shema-FBS-s-elektronnymi-TTN). |

## 6 ноября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| [/v1/warehouse/erfbs/aggregator/create](#operation/WarehouseERFBSAggregatorCreate) <br> [/v1/warehouse/erfbs/aggregator/delivery-method/update](#operation/WarehouseERFBSAggregatorDeliveryMethodUpdate) <br> [/v1/warehouse/erfbs/non-integrated/create](#operation/WarehouseERFBSNonIntegratedCreate) <br> [/v1/warehouse/erfbs/non-integrated/delivery-method/update](#operation/WarehouseERFBSNonIntegratedDeliveryMethodUpdate) <br> [/v1/warehouse/erfbs/update](#operation/WarehouseERFBSUpdate) <br> [/v2/polygon/bind](#operation/PolygonBind) <br> [/v1/polygon/delete](#operation/PolygonDelete) <br> [/v1/polygon/list](#operation/PolygonList) <br> [/v1/polygon/time/coordinates/update](#operation/PolygonTimeCoordinatesUpdate) <br> [/v1/polygon/time/set](#operation/PolygonTimeSet) | Добавили бета-методы для работы со складами rFBS Express. | 

## 5 ноября 2025

| Метод | Изменение |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------|
| [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Удалили параметр `result.financial_data.products.customer_price` из ответа метода. | 
| — | Добавили раздел с методами [Ozon Логистика](#tag/OzonLogistics). |

## 30 октября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/assembly/carriage/posting/list](#operation/AssemblyCarriagePostingList) <br> [/v1/assembly/carriage/product/list](#operation/AssemblyCarriageProductList) <br> [/v1/assembly/fbs/posting/list](#operation/AssemblyFbsPostingList) <br> [/v1/assembly/fbs/product/list](#operation/AssemblyFbsProductList) | Добавили бета-методы для работы с листами подбора FBS. |
| [/v3/supply-order/list](#operation/SupplyOrderList) <br> [/v3/supply-order/get](#operation/SupplyOrderGet) <br> [/v1/supply-order/content/update/validation](#operation/SupplyOrderContentUpdateValidation) <br> [/v1/product/info/warehouse/stocks](#operation/ProductInfoWarehouseStocks) | Перенесли методы из бета-раздела в основной. | 
| /v2/supply-order/list <br> /v2/supply-order/get | Методы устаревают и будут отключены 11 декабря 2025 года. Переключитесь на новые версии — [/v3/supply-order/list](#operation/SupplyOrderList) и [/v3/supply-order/get](#operation/SupplyOrderGet). | 
| — | Добавили описание работы с [OAuth-токеном](#tag/OAuth-token). |

## 28 октября 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------|
| [/v1/report/postings/create](#operation/ReportAPI_CreateCompanyPostingsReport) | Обновили описание параметра `filter.is_express` в запросе метода. | 

## 23 октября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| [/v1/product/certificate/create](#operation/ProductAPI_ProductCertificateCreate) | Обновили описание параметра `accordance_type_code` и добавили возможные значения параметра `type_code` в запросе метода. |
| [/v1/product/certificate/types](#operation/ProductAPI_ProductCertificateTypes) | Обновили пример ответа метода. |
| [/v1/product/info/stocks-by-warehouse/fbs](#operation/ProductAPI_ProductStocksByWarehouseFbs) | Добавили параметр `offer_id` в запрос и параметр `results.offer_id` в ответ метода. |
| [/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate) | Обновили пример метода. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Обновили описание параметра `result.substatus` в ответе метода. | 
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)<br>[/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Обновили описание параметра `result.postings.substatus` в ответе методов. |
| [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4)<br>[/v4/posting/fbs/ship/package](#operation/PostingAPI_ShipFbsPostingPackage) | Обновили описание методов. |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описания ошибок `POSTING_NOT_FOUND` для метода [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) и `error limiting: acquire limit per item: items limit: limit exceeded` для метода [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices). |

## 22 октября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Добавили параметр `prices.manage_elastic_boosting_through_price` в запрос метода. | 

## 21 октября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/report/marked-products-sales/create](#operation/CreateCompanyMarkedProductsSalesReport) | Добавили бета-метод для получения отчёта по продажам товаров с маркировкой. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.shipment_date_without_delay` в ответ методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.shipment_date_without_delay` в ответ метода. |
| — | В разделе [**Уведомления, которые отправляет Ozon → Новое отправление**](#section/Novoe-otpravlenie) обновили пример уведомления для нового отправления. |

## 17 октября 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| /v1/draft/create<br>/v1/draft/create/info | Обновили описание методов. |
| [/v1/product/stairway-discount/by-quantity/set](#operation/ProductAPI_SetProductStairwayDiscountByQuantity) | Добавили бета-метод для управления скидкой от количества товаров. |
| [/v1/product/stairway-discount/by-quantity/get](#operation/ProductAPI_GetProductStairwayDiscountByQuantity) | Добавили бета-метод для получения информации о скидке от количества товаров. |
| /v2/supply-order/list | Обновили описание параметра `filter.states` в запросе метода. |
| /v2/supply-order/get | Обновили описание параметра `order.state` в ответе метода. |

## 16 октября 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting)<br>[/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList)<br>[/v1/posting/digital/list](#operation/ListPostingCodes) | Обновили описание параметра `result.financial_data.products.product_id` в ответе метода. | 
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Обновили описание параметра `result.postings.financial_data.products.product_id` в ответе метода. |
| [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5) | Обновили описание параметра `products.exemplars.marks` в ответе метода. |
| [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) | Обновили описание параметра `products.exemplars.marks` в запросе метода. |
| [/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode) | Удалили параметры `result.analytics_data` и `result.financial_data` из ответа метода. |
| [/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList) | Обновили описание параметра `search` в запросе метода. |
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Обновили описание параметра `limit` в запросе метода. |

## 14 октября 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| [/v2/finance/realization](#operation/FinanceAPI_GetRealizationReportV2) | Параметры `result.header.doc_amount` и `result.header.vat_amount` устаревают, отключим их с 14 декабря 2025 года. | 
| [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1) | Параметры `header.doc_amount` и `header.vat_amount` устаревают, отключим их с 14 декабря 2025 года. |

## 13 октября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/warehouse/fbs/create/drop-off/timeslot/list](#operation/WarehouseFbsCreateDropOffTimeslotList) <br> [/v1/warehouse/fbs/update/drop-off/timeslot/list](#operation/WarehouseFbsUpdateDropOffTimeslotList) <br> [/v1/warehouse/fbs/create/pick-up/timeslot/list](#operation/WarehouseFbsCreatePickUpTimeslotList) <br> [/v1/warehouse/fbs/update/pick-up/timeslot/list](#operation/WarehouseFbsUpdatePickUpTimeslotList)| Добавили бета-методы для работы с таймслотами. |
|[/v2/warehouse/list](#operation/WarehouseListV2) | Добавили параметры `warehouses.cut_in_time`, `warehouses.warehouse_type`, `warehouses.is_comfort` и `warehouses.is_express` в ответ метода. |
| [/v1/warehouse/fbs/create](#operation/WarehouseAPI_CreateWarehouseFBS) <br> [/v1/warehouse/fbs/first-mile/update](#operation/UpdateWarehouseFBSFirstMile)| Добавили параметры `сut_in_time` и `timeslot_id` в запрос методов. | 

## 10 октября 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Добавили параметры `items.comissions.sales_percent_fbp` и `items.comissions.sales_percent_rfbs` в ответ метода.<br>Добавили возможное значение `SUPER` параметра `items.price_indexes.color_index` в ответе метода. |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Добавили возможное значение `COLOR_INDEX_SUPER` параметра `items.price_indexes.color_index` в ответе метода. |

## 8 октября 2025

| Метод | Изменение |
|----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| [/v2/cargoes/create/info](#operation/CargoesCreateInfoV2) | Добавили новую версию метода для получения информации по установке грузомест. |
| /v1/cargoes/create/info | Метод устаревает и будет отключён в будущем. Переключитесь на новую версию [/v2/cargoes/create/info](#operation/CargoesCreateInfoV2). |
| [/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate) | Добавили параметр `cargoes.value.items.offer_id` в запрос метода.|
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Обновили описание параметра `items.images` в запросе метода.<br>Обновили описание метода. |
| [/v1/product/pictures/import](#operation/ProductAPI_ProductImportPictures) | Обновили описание параметра `images` в запросе метода.<br>Обновили описание метода. |

## 7 октября 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [v1/removal/from-stock/list](#operation/GetSupplierReturnsSummaryReport)<br>[v1/removal/from-supply/list](#operation/GetSupplyReturnsSummaryReport) | Обновили примеры ответов. |
| [/v1/question/info](#operation/Question_Info) | Обновили название метода.<br>Обновили описание и пример ответа метода. |
| [/v1/question/top-sku](#operation/Question_TopSku) | Обновили описание ответа метода.<br>Обновили описание параметра `sku` в ответе метода. |
| — | Добавили описания разделов [**Чаты с покупателями**](#tag/ChatAPI), [**Аналитические отчёты**](#tag/AnalyticsAPI) и [**Финансовые отчёты**](#tag/FinanceAPI). |
| [/v1/search-queries/text](#operation/SearchQueriesAPI_SearchQueriesText)<br>[/v1/search-queries/top](#operation/SearchQueriesAPI_SearchQueriesTop) | Добавили методы для работы с поисковыми запросами. |
| [/v1/analytics/data](#operation/AnalyticsAPI_AnalyticsGetData)<br>[/v1/chat/send/message](#operation/ChatAPI_ChatSendMessage)<br>[/v1/chat/send/file](#operation/ChatAPI_ChatSendFile)<br>[/v1/chat/start](#operation/ChatAPI_ChatStart)<br>[/v3/chat/history](#operation/ChatAPI_ChatHistoryV3)<br>[/v2/chat/read](#operation/ChatAPI_ChatReadV2)<br>[/v1/finance/realization/by-day](#operation/FinanceAPI_GetRealizationByDayReportV1)<br>[/v1/review/comment/create](#operation/ReviewAPI_CommentCreate)<br>[/v1/review/comment/delete](#operation/ReviewAPI_CommentDelete)<br>[/v1/review/comment/list](#operation/ReviewAPI_CommentList)<br>[/v1/review/change-status](#operation/ReviewAPI_ReviewChangeStatus)<br>[/v1/review/count](#operation/ReviewAPI_ReviewCount)<br>[/v1/review/info](#operation/ReviewAPI_ReviewInfo)<br>[/v1/review/list](#operation/ReviewAPI_ReviewList) | Обновили описание методов. |

## 6 октября 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------|------------------------------------------------------------------|
| /v5/fbs/posting/product/exemplar/create-or-get<br>/v4/fbs/posting/product/exemplar/set<br>/v5/fbs/posting/product/exemplar/set<br>/v4/fbs/posting/product/exemplar/status<br>/v4/fbs/posting/product/exemplar/validate | Методы устаревают и будут отключены 3 декабря 2025 года. Переключитесь на новые версии. |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Параметр `items.marketing_price` устаревает, отключим его 12 ноября 2025 года.| 
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Добавили параметр `items.availabilities` в ответ метода. |

## 3 октября 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| [/v1/posting/fbs/package-label/get](#operation/PostingAPI_GetLabelBatch) | Добавили параметры `result.printed_postings_count`, `result.unprinted_postings.msg`, `result.unprinted_postings.posting_number` и `result.unprinted_postings_count` в ответ метода. |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Параметр `items.marketing_price` устаревает, отключим его 12 ноября 2025 года. |

## 2 октября 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------|------------------------------------------------------------------|
| [/v1/product/info/warehouse/stocks](#operation/ProductInfoWarehouseStocks) | Добавили бета-метод для получения остатков на складе FBS и rFBS. |

## 29 сентября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/report/postings/create](#operation/ReportAPI_CreateCompanyPostingsReport) | Добавили параметры `filter.warehouse_id`, `filter.delivery_method_id`, `filter.is_express`, `with.additional_data`, `with.analytics_data`, `with.customer_data` и `with.jewelry_codes` в запрос метода. |
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Параметр `items.price.marketing_price` устаревает, отключим его 12 ноября 2025 года. |

## 24 сентября 2025

| Метод | Изменение |
|---|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/returns/rfbs/list](#operation/RFBSReturnsAPI_ReturnsRfbsListV2) | Обновили описание параметра `last_id` в запросе метода.<br>Обновили пример ответа. |
| [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2)<br>[/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) | Обновили примеры ответов. |
| [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) | Добавили пример запроса. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)<br>[/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Обновили описание параметров `result.postings.status`, `result.postings.substatus` в ответе методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | В ответе метода: <br> • добавили параметр `result.financial_data.products.customer_price`; <br> • обновили описание параметров `result.requirements.products_requiring_gtd`, `result.requirements.products_requiring_mandatory_mark`, `result.requirements.products_requiring_jw_uin`, `result.requirements.products_requiring_rnpt`, `result.status`, `result.substatus` и `result.previous_substatus`, `result.financial_data.products.price`, `result.financial_data.products.old_price`, `result.customer.phone`, `result.addressee.phone` и `result.products.is_marketplace_buyout`. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | В ответе метода: <br> • добавили параметр `result.postings.financial_data.products.customer_price`; <br> • обновили описание параметров `result.postings.requirements.products_requiring_gtd`, `result.postings.requirements.products_requiring_mandatory_mark`, `result.postings.requirements.products_requiring_jw_uin`, `result.postings.requirements.products_requiring_rnpt`, `result.postings.financial_data.products.price`, `result.postings.financial_data.products.old_price`, `result.postings.customer.phone`, `result.postings.addressee.phone`, `result.postings.products.is_marketplace_buyout` и `result.postings.products.is_marketplace_buyout`. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)| Обновили описание параметров `result.postings.customer.phone`, `result.postings.addressee.phone`, `result.postings.products.is_marketplace_buyout` и `result.products.is_marketplace_buyout` в ответе метода. |
| [/v2/finance/realization](#operation/FinanceAPI_GetRealizationReportV2) | Обновили описание параметров `result.rows.delivery_commission.commission`, `result.rows.delivery_commission.compensation`, `result.rows.return_commission.commission` и `result.rows.return_commission.compensation` в ответе метода. |
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Обновили описание параметров `items.available_stock_count` и `items.valid_stock_count` в ответе метода. |
| [/v4/product/info/limit](#operation/ProductAPI_GetUploadQuota) | Обновили описание параметров `total.limit`, `daily_create.limit` и `daily_update.limit` в ответе метода. |
| /v2/chat/history<br>[/v3/chat/history](#operation/ChatAPI_ChatHistoryV3) | Обновили описание параметра `from_message_id` в запросе методов. |
| [/v1/rating/history](#operation/RatingAPI_RatingHistoryV1) | Обновили описание параметров `ratings = rating_reaction_time` и `ratings = rating_average_response_time` в запросе метода. |
| [/v1/analytics/product-queries](#operation/AnalyticsAPI_AnalyticsProductQueries)<br>[/v1/analytics/product-queries/details](#operation/AnalyticsAPI_AnalyticsProductQueriesDetails) | Обновили описание параметров `page` и `page_size` в запросе методов. Обновили пример запроса. |
| /v1/draft/create | Обновили описание параметра `cluster_ids` в запросе метода. |
| /v1/draft/create/info | Добавили описание метода. Обновили описание параметров `clusters.warehouses` и `errors.items_validation.reasons` в ответе метода. |
| /v1/draft/timeslot/info | Обновили описание метода. Обновили описание параметров `draft_id` и `warehouse_ids` в запросе метода. Добавили предупреждение в описание метода. |
| [/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate)<br>/v1/cargoes/create/info | Обновили описание параметра `items.value.barcode` в запросе методов. |
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Пометили параметр `items.price` как обязательный в запросе метода. <br> Обновили описание параметра `result.task_id` в ответе метода. <br> Обновили описание параметра `items.name` в запросе метода. |
| [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2) | Обновили описание параметра `return_id` в запросе метода. |
| [/v2/fbs/posting/delivering](#operation/PostingAPI_FbsPostingDelivering)<br>[/v2/fbs/posting/last-mile](#operation/PostingAPI_FbsPostingLastMile)<br>[/v2/fbs/posting/delivered](#operation/PostingAPI_FbsPostingDelivered) <br> [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel)<br>[/v2/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatchV2) <br> [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes)| Обновили описание методов. |
| /v4/fbs/posting/product/exemplar/status | Обновили описание параметра `status` в ответе метода. |
| [/v1/actions/products/activate](#operation/PromosProductsActivate) | Добавили лимиты для параметра `products` в запрос метода. |
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описания ошибок `POSTING_NUMBERS_IS_INCORRECT_FOR_COMPANY` для метода [/v2/posting/fbs/package-label/create](#operation/PostingAPI_CreateLabelBatchV2), `CREATE_ORDER_ERROR_REASON_INVALID_STORAGE_WAREHOUSE` для метода /v1/draft/supply/create, `WAREHOUSE_SCORING_INVALID_REASON_NOT_AVAILABLE_MATRIX`, `ITEM_REJECTION_REASON_OUT_OF_ASSORTMENT` для метода /v1/draft/timeslot/info и `price_is_negative` для метода [/v3/product/import](#operation/ProductAPI_ImportProductsV3). Обновили описание ошибки `TRANSITION_IS_NOT_POSSIBLE` для метода [/v4/posting/fbs/ship](#operation/PostingAPI_ShipFbsPostingV4). |

## 23 сентября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| [/v1/supply-order/content/update/validation](#operation/SupplyOrderContentUpdateValidation) | Добавили бета-метод для проверки нового товарного состава. |
| [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) | В ответе метода: <br> • добавили параметр `new_bundle_id`; <br> • обновили описание параметра `errors`. |

## 18 сентября 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| [/v2/posting/fbs/digital/act/get-pdf](#operation/PostingAPI_PostingFBSGetDigitalAct) | Добавили значение `waybill` для параметра `doc_type` в запросе метода. |
| [/v1/question/list](#operation/Question_List) | Обновили описание параметра `questions` в ответе метода. |

## 17 сентября 2025

| Метод | Изменение |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/supply-order/list](#operation/SupplyOrderList) | Добавили бета-метод для получения списка заявок на поставку. |
| [/v3/supply-order/get](#operation/SupplyOrderGet) | Добавили бета-метод для получения информации о заявке на поставку. |
| — | Удалили раздел **Пуш-уведомления → Уведомления, которые отправляет Ozon → Изменение ценового индекса товара**.<br>Удалили уведомление `TYPE_PRICE_INDEX_CHANGED` из раздела [**Пуш-уведомления → Уведомления, которые отправляет Ozon**](#tag/push_types). |

## 15 сентября 2025

| Метод | Изменение |
|----------------------------------------------------------------|--------------------------|
| [/v1/question/answer/create](#operation/QuestionAnswer_Create) | Обновили пример запроса. |

## 12 сентября 2025

| Метод | Изменение |
|------------------------------------------------|-------------------------------------------------------------|
| — | Добавили раздел [**Информация по API-ключу**](#tag/APIkey). |
| [/v1/roles](#operation/AccessAPI_RolesByToken) | Перенесли метод из бета-раздела в основной. |

## 10 сентября 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)<br>[v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Добавили параметры `result.postings.products.imei` и `result.postings.requirements.products_requiring_imei` в ответ метода. |
| [v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметры `result.products.has_imei`, `result.product_exemplars.products.exemplars.imei` и `result.requirements.products_requiring_imei` в ответ метода. |
| [v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) | Обновили описание параметра `products.exemplars.marks` и добавили параметр `products.has_imei` в ответ метода. |
| [v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5) | Обновили описание параметра `products.exemplars.marks` в запросе и ответе метода. |
| [v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) | Обновили описание параметра `products.exemplars.marks` в запросе метода. |
| [v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) | Обновили описание параметра `products.exemplars.marks` в ответе метода. |

## 3 сентября 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/conditional-cancellation/get<br>/v1/conditional-cancellation/list | Методы устарели, удалили их из документации. Используйте [/v2/conditional-cancellation/list](#operation/CancellationAPI_GetConditionalCancellationListV2). |
| /v1/conditional-cancellation/approve | Метод устарел, удалили его из документации. Используйте [/v2/conditional-cancellation/approve](#operation/CancellationAPI_ConditionalCancellationApproveV2). |
| /v1/conditional-cancellation/reject | Метод устарел, удалили его из документации. Используйте [/v2/conditional-cancellation/reject](#operation/CancellationAPI_ConditionalCancellationRejectV2). |
| [/v1/supply-order/content/update](#operation/SupplyOrderAPI_SupplyOrderContentUpdate) <br> [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) | Обновили описание параметра `errors` в ответе методов. |

## 2 сентября 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.requirements.products_requiring_weight` в ответ методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметры `result.product_exemplars.products.exemplars.weight`, `result.products.is_weight_needed`, `result.products.weight_max`, `result.products.weight_min`, `result.related_weight_postings` и `result.requirements.products_requiring_weight` в ответ метода. |
| [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5) | Добавили параметр `products.exemplars.weight` в запрос и ответ метода. |
| [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) | Добавили параметры `products.exemplars.weight`, `products.exemplars.weight_check_status` и `products.exemplars.weight_error_codes` в ответ метода. |
| [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6) | Добавили параметр `products.exemplars.weight` в запрос метода. |
| [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) | Добавили параметры `products.exemplars.weight`, `products.is_weight_needed`, `products.weight_max` и `products.weight_min` в ответ метода. |
| — | В разделах [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Схема rFBS Стандарт**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Shema-rFBS-Standart) и [**Порядок работы с методами → Управляйте заказами FBO, FBS, rFBS и FBP → Как работать с заказами с весовыми товарами (rFBS)**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Kak-rabotat-s-zakazami-s-vesovymi-tovarami-(rFBS)) обновили описание работы с методами. |

## 27 августа 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| — | В разделе [**Порядок работы с методами → Работа с FBS-складами**](#section/Rabota-s-FBS-skladami) описали порядок работы с FBS-складами. |
| [/v1/warehouse/fbs/create/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForCreateFBSWarehouse)<br>[/v1/warehouse/fbs/update/drop-off/list](#operation/WarehouseAPI_ListDropOffPointsForUpdateFBSWarehouse)<br>[/v1/warehouse/fbs/create](#operation/WarehouseAPI_CreateWarehouseFBS) <br> [/v1/warehouse/fbs/update](#operation/UpdateWarehouseFBS) <br> [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus) <br> [/v2/warehouse/list](#operation/WarehouseListV2) <br> [/v1/warehouse/fbs/first-mile/update](#operation/UpdateWarehouseFBSFirstMile) <br> [/v1/warehouse/archive](#operation/ArchiveWarehouseFBS) <br> [/v1/warehouse/unarchive](#operation/UnarchiveWarehouseFBS) | Добавили бета-методы для работы с FBS-складами. |
| [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList) | Обновили описание метода. |

## 15 августа 2025

| Метод | Изменение |
|------|-------------------------------------------------------------------------------------------------------------------|
| — | Добавили раздел [**Premium-методы**](#tag/Premium) и перенесли в него методы, доступные с подпиской Premium. |

## 14 августа 2025

| Метод | Изменение |
|-------|----------------|
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Добавили параметры `items.promotions`, `items.promotions.is_enabled`, `items.promotions.type` и `items.sku` в ответ метода. |

## 8 августа 2025

| Метод | Изменение |
|-------|----------------|
| [/v1/finance/products/buyout](#operation/GetFinanceProductsBuyout) | Обновили описание метода. |

## 6 августа 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [/v1/carriage/set-postings](#operation/CarriageAPI_SetPostings) <br> [/v1/carriage/cancel](#operation/CarriageAPI_CarriageCancel) <br> [/v1/product/action/timer/status](#operation/ProductAPI_ActionTimerStatus) <br> [/v1/product/action/timer/update](#operation/ProductAPI_ActionTimerUpdate) | Перенесли методы из бета-раздела в основной. |

## 5 августа 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [/v1/chat/send/file](#operation/ChatAPI_ChatSendFile) <br> [/v1/chat/send/message](#operation/ChatAPI_ChatSendMessage) | Обновили описание методов. |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Пометили параметр `items.is_prepayment_allowed` в ответе метода как устаревший. |

## 1 августа 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| [/v1/finance/cash-flow-statement/list](#operation/FinanceAPI_FinanceCashFlowStatementList) <br>[/v3/finance/transaction/list](#operation/FinanceAPI_FinanceTransactionListV3) <br> [/v3/finance/transaction/totals](#operation/FinanceAPI_FinanceTransactionTotalV3) | Обновили описания методов. |

## 30 июля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------|
| /v1/analytics/average-delivery-time/summary | Добавили бета-метод для получения общей аналитики по среднему времени доставки. |

## 28 июля 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/chat/list](#operation/ChatAPI_ChatListV3) | Добавили новую версию метода для получения информации о чатах по указанным фильтрам. |
| /v2/chat/list | Метод устаревает и будет отключён в будущем. Переключитесь на новую версию [/v3/chat/list](#operation/ChatAPI_ChatListV3). |
| [/v1/finance/document-b2b-sales/json](#operation/ReportAPI_CreateDocumentB2BSalesJSONReport) | Добавили параметр `invoices.buyer_info.name` в ответ метода. |
| [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2) | Обновили описание метода. |
| [/v1/posting/digital/list](#operation/ListPostingCodes) | В ответе метода: обновили описание параметра `result.status`;
удалили параметры `result.products.digital_codes` и `result.products.quantity`.
 |

## 24 июля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------|
| [/v1/removal/from-supply/list](#operation/GetSupplyReturnsSummaryReport) | Добавили бета-метод для получения отчёта по вывозу и утилизации с поставки FBO. |
| [/v1/removal/from-stock/list](#operation/GetSupplierReturnsSummaryReport) | Добавили бета-метод для получения отчёта по вывозу и утилизации со стока FBO. |
| [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1)<br>[/v2/finance/realization](#operation/FinanceAPI_GetRealizationReportV2) | Обновили описание методов. |

## 23 июля 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|
| [/v1/analytics/product-queries](#operation/AnalyticsAPI_AnalyticsProductQueries)<br>[/v1/analytics/product-queries/details](#operation/AnalyticsAPI_AnalyticsProductQueriesDetails)<br>[/v1/finance/compensation](#operation/ReportAPI_GetCompensationReport)<br>[/v1/finance/decompensation](#operation/ReportAPI_GetDecompensationReport) | Перенесли методы из бета-раздела в основной. |

## 22 июля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes) | Обновили описание параметра `result.id` в ответе метода. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Обновили описание параметра `result.requirements.products_requiring_change_country` в ответе метода. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Обновили описание параметров `result.postings.requirements.products_requiring_change_country` и `result.postings.financial_data.products.actions` в ответе методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br> [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) <br> [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Обновили описание параметра `result.financial_data.products.actions` в ответе методов. |

## 21 июля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------|
| [/v1/finance/products/buyout](#operation/GetFinanceProductsBuyout) <br> [/v1/finance/document-b2b-sales/json](#operation/ReportAPI_CreateDocumentB2BSalesJSONReport)| Перенесли методы из бета-раздела в основной. |

## 15 июля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------|
| [/v1/finance/realization/by-day](#operation/FinanceAPI_GetRealizationByDayReportV1) | Перенесли метод из бета-раздела в основной. |

## 14 июля 2025

| Метод | Изменение |
|----------------------------------------------------|------------------------------------------------------------------------|
| [/v1/roles](#operation/AccessAPI_RolesByToken) | Добавили бета-метод для получения списка ролей и методов по API-ключу. |

## 2 июля 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.requirements.products_requiring_change_country` в ответ метода. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)<br>[/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Добавили параметр `result.postings.requirements.products_requiring_change_country` в ответ метода. |
| [/v1/analytics/data](#operation/AnalyticsAPI_AnalyticsGetData) | Обновили описание метода. Обновили описание параметров `dimension` и `metrics` в запросе метода. |

## 1 июля 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/finance/products/buyout](#operation/GetFinanceProductsBuyout) | Добавили бета-метод для получения отчёта по выкупленным товарам. |
| [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) <br> [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) <br> [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.products.is_marketplace_buyout` в ответы методов. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) <br> [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.products.is_marketplace_buyout` в ответы методов. |
| /v2/chat/history <br> [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3) <br> [/v2/chat/read](#operation/ChatAPI_ChatReadV2) <br> [/v1/chat/start](#operation/ChatAPI_ChatStart) <br> [/v1/chat/send/file](#operation/ChatAPI_ChatSendFile) <br> [/v1/chat/send/message](#operation/ChatAPI_ChatSendMessage) | Обновили описания методов. |
| [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes) | Добавили бета-метод для загрузки кодов цифровых товаров. |
| [/v1/posting/digital/list](#operation/ListPostingCodes) | Добавили бета-метод для получения списка отправлений, по которым нужно загрузить коды цифровых товаров. |
| [/v1/product/digital/stocks/import](#operation/DigitalProductAPI_StocksImport) | Добавили бета-метод для обновления количества цифровых товаров. |
| /v1/product/upload_digital_codes<br>/v1/product/upload_digital_codes/info | Методы устарели, удалили их из документации. Используйте методы [/v1/posting/digital/list](#operation/ListPostingCodes), [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes) и [/v1/product/digital/stocks/import](#operation/DigitalProductAPI_StocksImport). |
| — | В разделе [**Порядок работы с методами → Загрузите и обновите товары**](#section/Zagruzite-i-obnovite-tovary) обновили описание работы с методами. |

## 26 июня 2025

| Метод | Изменение |
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/quant/list<br>/v1/quant/get<br>/v1/quant/ship<br>/v1/quant/status | Методы устарели, удалили их из документации. |
| [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2) | Удалили параметры `stocks.quant_size` из запроса и `result.quant_size` из ответа метода. |
| — | В разделе [**Схема FBS Стандарт**](#section/Upravlyajte-zakazami-FBO-FBS-i-rFBS/Shema-FBS-Standart) обновили порядок работы с эконом-товарами. |

## 25 июня 2025

| Метод | Изменение |
|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| — | В разделе [**Частые ошибки**](#tag/Errors) добавили описание ошибок `restore limit exceeded` и `total limit exceeded` для метода [/v1/product/unarchive](#operation/ProductAPI_ProductUnarchive). |

## 23 июня 2025

| Метод | Изменение |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Обновили описание параметра `result.shipment_date` в ответе метода. |
| [Частые ошибки](#tag/Errors) | Добавили описание ошибки `Stock is updated too frequently` и обновили описание ошибки `TOO_MANY_REQUESTS` для метода [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2). |
| [v1/carriage/create](#operation/CarriageAPI_CarriageCreate) | Обновили описание метода. |

## 20 июня 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList) | Обновили описание метода. |
| /v1/draft/create | Обновили описание параметров `cluster_ids` и `drop_off_point_warehouse_id` в запросе метода. | 
| /v1/draft/supply/create | Обновили описание параметра `warehouse_id` в запросе метода. |
| [/v1/cargoes/rules/get](#operation/CargoesAPI_CargoesRulesGet) <br> [/v1/cargoes/delete](#operation/CargoesAPI_CargoesDelete) <br> [/v1/cargoes/delete/status](#operation/CargoesAPI_CargoesDeleteStatus) <br> [/v1/supply-order/content/update](#operation/SupplyOrderAPI_SupplyOrderContentUpdate) <br> [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) <br> [/v1/returns/rfbs/action/set](#operation/ReturnsAPI_ReturnsRfbsActionSet) | Перенесли методы из бета-раздела в основной. |
| — | В разделе [**Порядок работы с методами → Управляйте заявками на возврат rFBS-заказов**](#section/Upravlyajte-zayavkami-na-vozvrat-rFBS-zakazov) обновили описание работы с методами. |
| /v1/draft/create/info | Обновили описание параметра `operation_id` в запросе метода.<br>Удалили параметры `clusters.warehouses.warehouse_id`, `clusters.warehouses.address` и `clusters.warehouses.name` из ответа метода. |
| [/v1/question/answer/list](#operation/QuestionAnswer_List)<br>[/v1/brand/company-certification/list](#operation/BrandAPI_BrandCompanyCertificationList)<br>[/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v1/report/list](#operation/ReportAPI_ReportList)<br>[/v1/supply-order/bundle](#operation/SupplyOrderBundle)<br>[/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList)<br>[/v1/description-category/attribute/values/search](#operation/DescriptionCategoryAPI_SearchAttributeValues)<br>[/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks)<br>[/v1/actions/discounts-task/list](#operation/promos_task_list)<br>[/v2/product/certification/list](#operation/ProductAPI_ProductCertificationList)<br>[/v1/product/certificate/list](#operation/CertificateList)<br>[/v1/product/certificate/products/list](#operation/CertificateProductsList)<br>[/v1/pass/list](#operation/PassList)<br>[/v2/returns/rfbs/list](#operation/RFBSReturnsAPI_ReturnsRfbsListV2)<br>[/v1/returns/company/fbs/info](#operation/returnsCompanyFBSInfo)<br>[/v1/return/giveout/list](#operation/ReturnAPI_GiveoutList)<br>[/v1/analytics/product-queries](#operation/AnalyticsAPI_AnalyticsProductQueries)<br>[/v1/analytics/product-queries/details](#operation/AnalyticsAPI_AnalyticsProductQueriesDetails)<br>[/v1/product/info/wrong-volume](#operation/ProductAPI_ProductInfoWrongVolume)<br>/v1/product/quant/list<br>/v1/quant/list<br>[/v1/review/comment/list](#operation/ReviewAPI_CommentList)<br>[/v1/review/list](#operation/ReviewAPI_ReviewList)<br>[/v1/question/list](#operation/Question_List)<br>/v2/supply-order/list | Обновили примеры запросов. |

## 19 июня 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/pricing-strategy/product/info](#operation/pricing_items-info) | Пометили устаревшим параметр `result.strategy_competitor_id` в ответе метода. |
| /v1/conditional-cancellation/get | Метод устаревает и будет отключён 3 августа 2025 года. Переключитесь на [/v2/conditional-cancellation/list](#operation/CancellationAPI_GetConditionalCancellationListV2). |
| — | В разделе [**Управляйте заявками на отмену**](#section/Upravlyajte-zayavkami-na-otmenu) обновили метод для получения заявок на отмену rFBS. |

## 18 июня 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/analytics/average-delivery-time | Добавили параметры `data.metrics.exact_impact_share` и `total.exact_impact_share` в ответ метода. <br>Пометили устаревшими параметры `data.metrics.impact_share` и `total.impact_share`. |
| /v1/analytics/average-delivery-time/details | Добавили параметр `data.metrics.exact_impact_share` и пометили устаревшим параметр `data.metrics.impact_share` в ответе метода. |

## 17 июня 2025

| Метод | Изменение |
|-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Добавили параметры `items.ads_cluster`, `items.days_without_sales_cluster`, `items.idc_cluster` и `items.turnover_grade_cluster` в ответ метода.<br>Обновили описание параметров `items.ads`, `items.days_without_sales`, `items.idc` и `items.turnover_grade` в ответе метода. |

## 16 июня 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/quant/list<br>/v1/quant/get<br>/v1/quant/ship<br>/v1/quant/status | Методы устаревают и будут отключены 26 июня 2025 года. |
| [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2) | Пометили устаревшими параметры `stocks.quant_size` в запросе метода и `result.quant_size` в ответе метода. 26 июня 2025 они будут отключены. |

## 11 июня 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) | Добавили параметр `items.stocks.warehouse_ids` в ответ метода. |

## 5 июня 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) <br> [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Добавили параметры `with.legal_info` в запрос метода и `result.legal_info` в ответ метода. |
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) <br> [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Добавили параметры `with.legal_info` в запрос метода и `result.postings.legal_info` в ответ метода. | |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметры `with.legal_info` в запрос метода и `result.legal_info` в ответ метода. |
| [Частые ошибки](#tag/Errors) | Добавили описание ошибки `You have reached request rate limit per second` для всех методов. |
| [/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate) | Обновили описание параметра `supply_id` в запросе метода. |
| [/v2/posting/fbs/act/get-postings](#operation/PostingAPI_ActPostingList) | Обновили описание параметра `id` в запросе метода. |
| [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1) | Перенесли метод из бета-раздела в основной. |

## 3 июня 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/conditional-cancellation/list](#operation/CancellationAPI_GetConditionalCancellationListV2) <br> [/v2/conditional-cancellation/approve](#operation/CancellationAPI_ConditionalCancellationApproveV2) <br> [/v2/conditional-cancellation/reject](#operation/CancellationAPI_ConditionalCancellationRejectV2) | Перенесли методы из бета-раздела в основной. |
| /v1/conditional-cancellation/list | Метод устаревает и будет отключён 3 августа 2025 года. Переключитесь на новую версию [/v2/conditional-cancellation/list](#operation/CancellationAPI_GetConditionalCancellationListV2). |
| /v1/conditional-cancellation/approve | Метод устаревает и будет отключён 3 августа 2025 года. Переключитесь на новую версию [/v2/conditional-cancellation/approve](#operation/CancellationAPI_ConditionalCancellationApproveV2). |
| /v1/conditional-cancellation/reject | Метод устаревает и будет отключён 3 августа 2025 года. Переключитесь на новую версию [/v2/conditional-cancellation/reject](#operation/CancellationAPI_ConditionalCancellationRejectV2). |
| [Частые ошибки](#tag/Errors) | Обновили описание ошибки `INVALID_ARGUMENT` для метода [/v2/posting/fbs/package-label](#operation/PostingAPI_PostingFBSPackageLabel). |

## 30 мая 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [/v1/finance/document-b2b-sales/json](#operation/ReportAPI_CreateDocumentB2BSalesJSONReport) | Добавили бета-метод для получения отчёта по продажам юридическим лицам в JSON-формате. |
| [/v4/product/info/attributes](#operation/ProductAPI_GetProductAttributesV4) | Добавили параметр `result.attributes_with_defaults` в ответ метода. |

## 27 мая 2025

| Метод | Изменение |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------|
| /v1/product/import/stocks | Метод устарел, удалили его из документации. Используйте [/v2/products/stock](#operation/ProductAPI_ProductsStocksV2). |

## 26 мая 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Обновили описание параметра `turnover_grades` в запросе метода. <br> Обновили описание параметров `items.turnover_grades` и `items.valid_stock_count` в ответе метода. |
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Пометили обязательным параметр `items.type_id` в запросе метода. |

## 23 мая 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Добавили параметр `items.price.net_price` в ответ метода. |
| [/v2/product/pictures/info](#operation/ProductAPI_ProductInfoPicturesV2) | Добавили параметр `items.errors` в ответ метода. |

## 22 мая 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /v1/analytics/average-delivery-time | Добавили бета-метод для получения аналитики по среднему времени доставки. |
| /v1/analytics/average-delivery-time/details | Добавили бета-метод для получения детальной аналитики по среднему времени доставки по кластеру. |
| — | В разделе [**Порядок работы с методами**](#tag/Process) увеличили лимит запросов — теперь вы можете отправить не больше 50 запросов в секунду на все методы с одного Client ID. Раньше — не больше 10. |
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Добавили параметр `items.promotions` в запрос метода. |

## 20 мая 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| [/v1/supply-order/bundle](#operation/SupplyOrderBundle) | Добавили параметр `items.placement_zone` в ответ метода. |
| [/v1/cargoes/rules/get](#operation/CargoesAPI_CargoesRulesGet) | Добавили бета-метод для получения чек-листа с правилами по установке грузомест. |
| [/v1/cargoes/delete](#operation/CargoesAPI_CargoesDelete)<br>[/v1/cargoes/delete/status](#operation/CargoesAPI_CargoesDeleteStatus) | Добавили бета-методы для удаления грузомест в заявке на поставку. |
| [/v1/supply-order/content/update](#operation/SupplyOrderAPI_SupplyOrderContentUpdate)<br>[/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) | Добавили бета-методы для редактирования товарного состава в заявке на поставку. |

## 15 мая 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| [/v1/actions/candidates](#operation/PromosCandidates) <br> [/v1/actions/products](#operation/PromosProducts) | Добавили параметры `result.products.alert_max_action_price_failed` и `result.products.alert_max_action_price` в ответ методов. |

## 13 мая 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3) | Перенесли метод из бета-раздела в основной. |
| /v2/chat/history | Метод устаревает и будет отключён 13 июля 2025 года. Переключитесь на новую версию [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3). |
| — | В разделе [**Порядок работы с методами → Управляйте чатами**](#section/Upravlyajte-chatami) указали новый метод для получения истории чата. |
| [/v1/returns/rfbs/action/set](#operation/ReturnsAPI_ReturnsRfbsActionSet) | Добавили бета-метод для передачи действий для возврата rFBS. |
| /v2/returns/rfbs/reject<br>/v2/returns/rfbs/compensate<br>/v2/returns/rfbs/verify<br>/v2/returns/rfbs/receive-return<br>/v2/returns/rfbs/return-money | Методы будут отключены в будущем. Переключитесь на метод [/v1/returns/rfbs/action/set](#operation/ReturnsAPI_ReturnsRfbsActionSet). |

## 6 мая 2025

| Метод | Изменение |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| /v1/product/import/stocks | Метод будет отключён 27 мая 2025 года. Переключитесь на [/v2/products/stocks](#operation/ProductAPI_ProductsStocksV2). |

## 30 апреля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| [/v2/conditional-cancellation/approve](#operation/CancellationAPI_ConditionalCancellationApproveV2) | Добавили бета-метод для подтверждения заявки на отмену rFBS-заказов. |
| [/v2/conditional-cancellation/list](#operation/CancellationAPI_GetConditionalCancellationListV2) | Добавили бета-метод для получения списка заявок на отмену rFBS-заказов. |
| [/v2/conditional-cancellation/reject](#operation/CancellationAPI_ConditionalCancellationRejectV2) | Добавили бета-метод для отклонения заявки на отмену rFBS-заказов. |

## 28 апреля 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Удалили параметры `items.image_group_id` и `items.premium_price` из запроса метода. |
| [/v1/product/import/info](#operation/ProductAPI_GetImportProductsInfo) | Удалили параметр `result.items.errors.optional_description_elements` из ответа метода. |
| [/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU) | Удалили параметр `items.premium_price` из запроса метода. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Удалили параметры `result.postings.financial_data.products.client_price`, `result.postings.financial_data.products.picking` и `result.postings.products.mandatory_mark` из ответа методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode) | Удалили параметры `result.financial_data.products.client_price`, `result.financial_data.products.picking` и `result.products.mandatory_mark` из ответа методов. |
| [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting)<br>[/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) | Удалили параметры `result.analytics_data.region`, `result.financial_data.products.client_price` и `result.financial_data.products.picking` из ответа методов. |
| /v2/supply-order/get | Удалили параметр `orders.creation_flow` из ответа метода. |
| [/v2/analytics/stock_on_warehouses](#operation/AnalyticsAPI_AnalyticsGetStockOnWarehousesV2) | Удалили параметр `result.rows.idc` из ответа метода. |
| /v1/finance/realization | Метод устарел, удалили его из документации. Используйте [/v2/finance/realization](#operation/FinanceAPI_GetRealizationReportV2). |

## 23 апреля 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------|
| [/v1/finance/compensation](#operation/ReportAPI_GetCompensationReport) | Добавили бета-метод для получения отчёта о компенсациях. |
| [/v1/finance/decompensation](#operation/ReportAPI_GetDecompensationReport) | Добавили бета-метод для получения отчёта о декомпенсациях. |
| [/v1/report/info](#operation/ReportAPI_ReportInfo) | Обновили описание параметра `report_type` в ответе метода. |
| [/v1/report/list](#operation/ReportAPI_ReportList) | Обновили описание параметра `report_type` в ответе и запросе метода. |

## 17 апреля 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1) | Добавили бета-метод для получения позаказного отчёта о реализации товаров. |

## 16 апреля 2025

| Метод | Изменение |
|---------------------------------------------------------------------|--------------------------------------------------------------------|
| [/v1/analytics/manage/stocks](#operation/AnalyticsAPI_ManageStocks) | Обновили описание параметра `filter.stock_types` в запросе метода. |

## 11 апреля 2025

| Метод | Изменение |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting)<br>[/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList)<br>[/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v2/posting/fbs/get-by-barcode](#operation/PostingAPI_GetFbsPostingByBarcode) | Удалили устаревшие параметры `result.financial_data.posting_services` и `result.financial_data.products.item_services` из ответа методов. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Удалили устаревшие параметры `result.postings.financial_data.posting_services` и `result.postings.financial_data.products.item_services` из ответа методов. |

## 10 апреля 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------|------------------------------------------------------------------------|
| [/v1/finance/realization/by-day](#operation/FinanceAPI_GetRealizationByDayReportV1) | Добавили бета-метод для получения отчёта о реализации товаров за день. |

## 9 апреля 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks) | Добавили метод для получения аналитики по остаткам на складах. |

## 4 апреля 2025

| Метод | Изменение |
|-------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Добавили параметр `items.price.auto_add_to_ozon_actions_list_enabled` в ответ метода. |

## 3 апреля 2025

| Метод | Изменение |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Добавили параметр `prices.auto_add_to_ozon_actions_list_enabled` в запрос метода. Обновили описание параметра `prices.auto_action_enabled` в запросе метода. |

## 1 апреля 2025

| Метод | Изменение |
|-----------------------------------------------------------------|-----------------------------------------------------------------------------|
| [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) | Удалили параметр `clusters.logistic_clusters.is_archived` из ответа метода. |

## 31 марта 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) <br> [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove) <br> [/v1/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryList) | Перенесли метод из бета-раздела в основной. |

## 27 марта 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) <br> [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) <br> [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `is_blr_traceable` в ответы методов. |
| /v2/supply-order/get | Добавили параметры `is_traceable` и `is_ettn_required` в ответ метода. |
| [/v1/supply-order/bundle](#operation/SupplyOrderBundle) | Добавили параметр `item_tags_calculation` в запрос метода и параметр `tags` в ответ метода. |

## 26 марта 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| [/v1/product/info/wrong-volume](#operation/ProductAPI_ProductInfoWrongVolume) | Добавили бета-метод для получения списка товаров с некорректными объёмно-весовыми характеристиками. |

## 20 марта 2025

| Метод | Изменение |
|--------------------------------------------------------------|---------------------------------------------------|
| [/v1/rating/summary](#operation/RatingAPI_RatingSummaryV1) | Добавили параметр `premium_plus` в ответ метода. |
| [/v1/analytics/product-queries/details](#operation/AnalyticsAPI_AnalyticsProductQueriesDetails) | Обновили описание параметров `limit_by_sku`, `page` и `page_size` в запросе метода. |

## 19 марта 2025

| Метод | Изменение |
|-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| [/v1/product/import/info](#operation/ProductAPI_GetImportProductsInfo) | Обновили описание метода.<br> Добавили возможное значение `skipped` параметра `result.items.status` в ответе метода. |
| [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes) | Добавили параметр `result.complex_is_collection` в ответ метода. |

## 18 марта 2025

| Метод | Изменение |
|--------|------------------------------------------------|
| [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList)<br>[/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList)<br>/v1/draft/create<br>/v1/draft/create/info<br>/v1/draft/timeslot/info<br>/v1/draft/supply/create<br>/v1/draft/supply/create/status<br>[/v1/cargoes/create](#operation/CargoesAPI_CargoesCreate)<br>/v1/cargoes/create/info<br>[/v1/cargoes-label/create](#operation/CargoesAPI_CargoesLabelCreate)<br>[/v1/cargoes-label/get](#operation/CargoesAPI_CargoesLabelGet)<br>[/v1/cargoes-label/file/{file_guid}](#operation/CargoesAPI_CargoesLabelFile)<br>[/v1/supply-order/cancel](#operation/SupplyOrderAPI_SupplyOrderCancel)<br>[/v1/supply-order/cancel/status](#operation/SupplyOrderAPI_SupplyOrderCancelStatus)<br>[/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6)<br>[/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6)<br>[/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5)<br>[/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5)<br>[/v1/fbs/posting/product/exemplar/update](#operation/PostingAPI_FbsPostingProductExemplarUpdate) | Перенесли методы из бета-раздела в основной. |

## 14 марта 2025

| Метод | Изменение |
|---------------------------------------|---------------------------------------------------------------------|
| [/v1/analytics/product-queries/details](#operation/AnalyticsAPI_AnalyticsProductQueriesDetails) | Добавили метод для получения данных по запросам конкретного товара. |

## 13 марта 2025

| Метод | Изменение |
|---------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| [/v1/actions/candidates](#operation/PromosCandidates)<br>[/v1/actions/products](#operation/PromosProducts) | Пометили параметр `offset` в запросе методов как устаревший и добавили параметр пагинации `last_id`. |

## 11 марта 2025

| Метод | Изменение |
|------------------------------------------------------------------------------|----------------------------------------------------------|
| [/v3/chat/history](#operation/ChatAPI_ChatHistoryV3) | Добавили новую версию метода для просмотра истории чата. |
| /v1/actions/hotsales/activate <br>/v1/actions/hotsales/deactivate <br>/v1/actions/hotsales/list <br>/v1/actions/hotsales/products | Методы устарели, удалили их из документации. |

## 10 марта 2025

| Метод | Изменение |
|------------------|---------------------------------------------------------------------------------------|
| /v2/product/info | Метод устарел, удалили его из документации. Используйте [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList). |

## 5 марта 2025

| Метод | Изменение |
|-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| [/v2/report/returns/create](#operation/ReportAPI_ReportReturnsCreate) | Добавили параметр `result` в ответ метода. <br> Пометили обязательными параметры `filter.date_from`, `filter.date_to` и `filter.status` в запросе метода. |

## 3 марта 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | В ответе метода:<br>• добавили параметр `result.optional.products_with_possible_mandatory_mark`,<br>• пометили устаревшим параметр `result.products.mandatory_mark`. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | В ответе методов:<br>• добавили параметр `result.postings.optional.products_with_possible_mandatory_mark`,<br>• пометили устаревшим параметр `result.postings.products.mandatory_mark`. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3)<br>[/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Значения кодов маркировки можно получить через метод [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) c `with.product_exemplars: true` в запросе или метод [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6). |

## 28 февраля 2025

| Метод | Изменение |
|------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v4/product/info/attributes](#operation/ProductAPI_GetProductAttributesV4) | Добавили возможные значения параметра `sort_by` в запросе метода и добавили описания параметров `result.barcodes` и `result.sku` в ответ метода. |
| [v2/supply-order/get](#operation/SupplyOrderAPI_GetSupplyOrdersV2) | Пометили параметр `creation_flow` как устаревший. |

## 27 февраля 2025

| Метод | Изменение |
|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| [/v2/analytics/stock_on_warehouses](#operation/AnalyticsAPI_AnalyticsGetStockOnWarehousesV2) | Обновили описание метода и отметили параметр `result.rows.idc` как устаревший, удалили его из примера. |
| [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList)<br>[/v1/actions](#operation/Promos) | Обновили описание метода. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.previous_substatus` в ответ метода. |
| [/v3/finance/transaction/list](#operation/FinanceAPI_FinanceTransactionListV3) | Обновили описание параметра `result.operations.posting.delivery_schema` в ответе метода. |
| [/v1/analytics/product-queries](#operation/AnalyticsAPI_AnalyticsProductQueries) | Добавили бета-метод для получения данных о запросах ваших товаров. |

## 26 февраля 2025

| Метод | Изменение |
|------------|-----------------|
| [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList)<br> [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) | Обновили описание параметра `result.postings.analytics_data.city` в ответе методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3)<br>[/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList)<br>[/v2/posting/fbo/get](#operation/PostingAPI_GetFboPosting) | Обновили описание параметра `result.analytics_data.city` в ответе методов.|

## 24 февраля 2025

| Метод | Изменение |
|-------------------------------------------------------------------------|--------------------------------------------------------|
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Добавили параметр `prices.net_price` в запрос метода для указания себестоимости товара. |

## 18 февраля 2025

| Метод | Изменение |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices) | Перенесли метод из бета-раздела в основной. |
| /v4/product/info/prices | Метод устарел, удалили его из документации. |
| /v3/returns/company/fbo <br>/v3/returns/company/fbs | Методы устарели, удалили их из документации. Переключитесь на новую версию [/v1/returns/list](#operation/returnsList). |
| /v1/report/returns/create | Метод устарел, удалили его из документации. Переключитесь на новую версию [/v2/report/returns/create](#operation/ReportAPI_ReportReturnsCreate). |

## 17 февраля 2025

| Метод | Изменение |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| /v2/product/info/list | Метод устарел, удалили его из документации. Переключитесь на новую версию [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList). |
| [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6 ) <br> [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6) <br> [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5) <br> [/v5/fbs/posting/product/exemplar/validate](#operation/PostingAPI_FbsPostingProductExemplarValidateV5) <br> [/v1/fbs/posting/product/exemplar/update](#operation/PostingAPI_FbsPostingProductExemplarUpdate) | Добавили бета-методы для управления кодами маркировки. |

## 14 февраля 2025

| Метод | Изменение |
|------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [v2/supply-order/get](#operation/SupplyOrderAPI_GetSupplyOrdersV2) | Добавили параметры `orders.can_cancel`, `orders.is_econom`, `orders.is_virtual`, `orders.is_super_fbo`, `orders.product_super_fbo`, `orders.supplies.supply_state`, `orders.supplies.supply_tags.is_evsd_required`, `orders.supplies.supply_tags.is_jewelry`, `orders.supplies.supply_tags.is_marking_possible`, `orders.supplies.supply_tags.is_marking_required` в ответ метода. |
| [/v2/product/certification/list](#operation/ProductAPI_ProductCertificationList) | Перенесли метод из бета-раздела в основной. |
| [/v1/product/certification/list](#operation/ProductAPI_V1ProductCertificationList) | Метод устаревает и будет отключён 14 апреля 2025 года. Переключитесь на новую версию [/v2/product/certification/list](#operation/ProductAPI_ProductCertificationList). |

## 11 февраля 2025

| Метод | Изменение |
|------------------------------------------------------------|----------------------------------------------|
| [/v3/product/list](#operation/ProductAPI_GetProductList) | Перенесли метод из бета-раздела в основной. |
| /v2/product/list | Метод устарел, удалили его из документации. |

## 10 февраля 2025

| Метод | Изменение |
|-----------------------------------------------------------------------|---------------------------------------------|
| [/v4/product/info/stocks](#operation/ProductAPI_GetProductInfoStocks) | Перенесли метод из бета-раздела в основной. |
| /v3/product/info/stocks | Метод устарел, удалили его из документации. |
| /v1/product/pictures/info | Метод устарел, удалили его из документации. Переключитесь на новую версию [/v2/product/pictures/info](#operation/ProductAPI_ProductInfoPicturesV2). | 
| /v3/product/info/attributes | Метод устарел, удалили его из документации. Переключитесь на новую версию [/v4/product/info/attributes](#operation/ProductAPI_GetProductAttributesV4). |

## 6 февраля 2025

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| [/v2/posting/fbs/awaiting-delivery](#operation/PostingAPI_MoveFbsPostingToAwaitingDelivery) | Обновили описание параметра `posting_number` в запросе метода. |
| [/v4/product/info/attributes](#operation/ProductAPI_GetProductAttributesV4)<br>[/v1/finance/document-b2b-sales](#operation/ReportAPI_CreateDocumentB2BSalesReport)<br>[/v1/finance/mutual-settlement](#operation/ReportAPI_CreateMutualSettlementReport) | Перенесли методы из бета-раздела в основной. |

## 30 января 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| [/v1/supply-order/cancel](#operation/SupplyOrderAPI_SupplyOrderCancel) | Добавили бета-метод для отмены заявки на поставку. |
| [/v1/supply-order/cancel/status](#operation/SupplyOrderAPI_SupplyOrderCancelStatus) | Добавили бета-метод для получения статуса отмены заявки на поставку. |

## 22 января 2025

| Метод | Изменение |
|-------------------------------------------------------------------|---------------------------------------------|
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Перенесли метод из бета-раздела в основной. |

## 17 января 2025

| Метод | Изменение |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| [/v1/posting/fbs/pick-up-code/verify](#operation/PostingAPI_PostingFBSPickupCodeVerify) | Добавили метод для проверки кода курьера. |
| [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) <br> [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) | Добавили параметр `result.postings.pickup_code_verified_at` в ответы методов. |
| [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) | Добавили параметр `result.pickup_code_verified_at` в ответ метода. |

## 15 января 2025

| Метод | Изменение |
|----------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Добавили параметр `prices.min_price_for_auto_actions_enabled` в запрос метода. |
| [/v1/product/action/timer/update](#operation/ProductAPI_ActionTimerUpdate) | Добавили бета-метод для обновления таймера актуальности минимальной цены. |
| [/v1/product/action/timer/status](#operation/ProductAPI_ActionTimerStatus) | Добавили бета-метод для получения статуса установленного таймера. | 

## 14 января 2025

| Метод | Изменение |
|---------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| [/v1/returns/list](#operation/returnsList) | Обновили описание параметров `filter` и `filter.posting_numbers` в запросе метода. |
| [/v2/product/pictures/info](#operation/ProductAPI_ProductInfoPicturesV2) | Перенесли метод из бета-раздела в основной. |

## 13 января 2025

| Метод | Изменение |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| /v2/posting/fbs/digital/act/document-sign | Метод устарел, удалили его из документации. |

## 28 декабря 2024

| Метод | Изменение |
|-----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| [/v1/supply-order/bundle](#operation/SupplyOrderBundle) | Добавили описание метода, изменили описания параметров `bundle_ids`, `last_id` и `limit` в запросе метода. |
| [/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList) | Изменили название и описание метода, изменили описание параметра `search` в запросе метода. |
| /v1/draft/create/info | Обновили описание параметров `clusters.warehouses.bundle_ids.bundle_id` и `clusters.warehouses.restricted_bundle_id` в ответе метода. |
| [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) | Обновили описание параметра `cluster_type` в запросе метода. |
| [/v1/warehouse/fbo/list](#operation/SupplyDraftAPI_DraftGetWarehouseFboList) | Обновили описание параметра `filter_by_supply_type` в запросе метода. |
| [/v1/question/answer/create](#operation/QuestionAnswer_Create)<br>[/v1/question/answer/delete](#operation/QuestionAnswer_Delete)<br>[/v1/question/answer/list](#operation/QuestionAnswer_List)<br>[/v1/question/change-status](#operation/Question_ChangeStatus)<br>[/v1/question/count](#operation/Question_Count)<br>[/v1/question/info](#operation/Question_Info)<br>[/v1/question/list](#operation/Question_List)<br>[/v1/question/top-sku](#operation/Question_TopSku) | Добавили бета-методы для работы с вопросами и ответами. |

## 27 декабря 2024

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| [/v1/review/comment/create](#operation/ReviewAPI_CommentCreate)<br>[/v1/review/comment/delete](#operation/ReviewAPI_CommentDelete)<br>[/v1/review/comment/list](#operation/ReviewAPI_CommentList)<br>[/v1/review/change-status](#operation/ReviewAPI_ReviewChangeStatus)<br>[/v1/review/count](#operation/ReviewAPI_ReviewCount)<br>[/v1/review/info](#operation/ReviewAPI_ReviewInfo)<br>[/v1/review/list](#operation/ReviewAPI_ReviewList) | Добавили бета-методы для работы с отзывами. |
| [/v1/carriage/create](#operation/CarriageAPI_CarriageCreate) | Добавили бета-метод для создания отгрузки. |
| [/v1/carriage/approve](#operation/CarriageAPI_CarriageApprove) | Добавили бета-метод для подтверждения отгрузки. |
| [/v1/carriage/delivery/list](#operation/CarriageAPI_CarriageDeliveryList) | Добавили бета-метод для получения списка методов доставки и отгрузок. |
| [/v1/carriage/get](#operation/CarriageGet) | Добавили параметры `result.is_waybill_enabled` и `result.is_econom` в ответ метода. |

## 26 декабря 2024

| Метод | Изменение |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList) | Добавили параметр `result.sla_cut_in` в ответ метода. |
| /v1/supply-order/get | Метод устарел, удалили его из документации. Используйте [/v3/supply-order/get](#operation/SupplyOrderGet). |
| /v1/supply-order/list | Метод устарел, удалили его из документации. Используйте [/v3/supply-order/list](#operation/SupplyOrderList). |
| /v1/supply-order/items | Метод устарел, удалили его из документации. Используйте [/v1/supply-order/bundle](#operation/SupplyOrderBundle). |
| /v4/product/info/prices | Метод устаревает и будет отключён 17 февраля 2025 года. Переключитесь на новую версию [/v5/product/info/prices](#operation/ProductAPI_GetProductInfoPrices). |
| [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList) | Добавили параметр `items.is_super` в ответ метода. |

## 24 декабря 2024

| Метод | Изменение |
|----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
| [/v1/product/import/prices](#operation/ProductAPI_ImportProductsPrices) | Добавили параметр `prices.vat` в запрос метода. |
| [/v1/product/import-by-sku](#operation/ProductAPI_ImportProductsBySKU)<br>[/v3/product/import](#operation/ProductAPI_ImportProductsV3) | Обновили описание параметра `items.vat` в запросе методов. |
