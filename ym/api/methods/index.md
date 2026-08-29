---
title: API Яндекс Маркета для продавцов — все методы
api: yandex-market
spec_version: LATEST
operations: 165
source: "https://yandex.ru/dev/market/partner-api/"
content_sha: bde8c1c7145ad7c0
---

# API Яндекс Маркета для продавцов

API Яндекс Маркета помогает продавцам автоматизировать и упростить работу с маркетплейсом.

В числе возможностей интеграции:

* управление каталогом товаров и витриной,

* обработка заказов,

* изменение настроек магазина,

* получение отчетов.

Версия спеки: `LATEST` · методов: **165** · разделов справки: **0**

Источник: https://yandex.ru/dev/market/partner-api/

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/v2/campaigns/{campaignId}/outlets/licenses` | outlet-licenses | [Удаление лицензий для точек продаж](outlet-licenses/delete-v2-campaigns-campaignid-outlets-licenses.md) |
| `DELETE` | `/v2/campaigns/{campaignId}/outlets/{outletId}` | outlets | [Удаление точки продаж](outlets/delete-v2-campaigns-campaignid-outlets-outletid.md) |
| `GET` | `/v2/businesses/{businessId}/chat` | chats | [Получение чата по идентификатору](chats/get-v2-businesses-businessid-chat.md) |
| `GET` | `/v2/businesses/{businessId}/chats/message` | chats | [Получение сообщения в чате](chats/get-v2-businesses-businessid-chats-message.md) |
| `GET` | `/v2/businesses/{businessId}/warehouses` | warehouses | [Список складов и групп складов](warehouses/get-v2-businesses-businessid-warehouses.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/act` | shipments | [Получение акта приема-передачи](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid-act.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/discrepancy-act` | shipments | [Получение акта расхождений](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid-discrepancy-act.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/inbound-act` | shipments | [Получение фактического акта приема-передачи](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid-inbound-act.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/info` | shipments | [Получение информации о возможности печати ярлыков](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid-orders-info.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallet/labels` | shipments | [Ярлыки для доверительной приемки](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid-pallet-labels.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/transportation-waybill` | shipments | [Получение транспортной накладной](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid-transportation-waybill.md) |
| `GET` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}` | shipments | [Получение информации об одной отгрузке](shipments/get-v2-campaigns-campaignid-first-mile-shipments-shipmentid.md) |
| `GET` | `/v2/campaigns/{campaignId}/hidden-offers` | hidden-offers | [Информация о скрытых вами товарах](hidden-offers/get-v2-campaigns-campaignid-hidden-offers.md) |
| `GET` | `/v2/campaigns/{campaignId}/offer-prices` | prices | [Список цен](prices/get-v2-campaigns-campaignid-offer-prices.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/buyer` | order-delivery | [Информация о покупателе — физическом лице](order-delivery/get-v2-campaigns-campaignid-orders-orderid-buyer.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data` | order-labels | [Данные для самостоятельного изготовления ярлыков](order-labels/get-v2-campaigns-campaignid-orders-orderid-delivery-labels-data.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels` | order-labels | [Готовые ярлыки‑наклейки на все коробки в одном заказе](order-labels/get-v2-campaigns-campaignid-orders-orderid-delivery-labels.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label` | order-labels | [Готовый ярлык‑наклейка для коробки в заказе](order-labels/get-v2-campaigns-campaignid-orders-orderid-delivery-shipments-shipmentid-boxes-boxid.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/application` | returns | [Получение заявления на возврат](returns/get-v2-campaigns-campaignid-orders-orderid-returns-returnid-application.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/{itemId}/image/{imageHash}` | returns | [Получение фотографий товаров в возврате](returns/get-v2-campaigns-campaignid-orders-orderid-returns-returnid-decision-itemid-image-im.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}` | returns | [Информация о невыкупе или возврате](returns/get-v2-campaigns-campaignid-orders-orderid-returns-returnid.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders/{orderId}` | orders | [Информация об одном заказе в магазине](orders/get-v2-campaigns-campaignid-orders-orderid.md) |
| `GET` | `/v2/campaigns/{campaignId}/orders` | orders | [Информация о заказах в магазине](orders/get-v2-campaigns-campaignid-orders.md) |
| `GET` | `/v2/campaigns/{campaignId}/outlets/licenses` | outlet-licenses | [Информация о лицензиях для точек продаж](outlet-licenses/get-v2-campaigns-campaignid-outlets-licenses.md) |
| `GET` | `/v2/campaigns/{campaignId}/outlets/{outletId}` | outlets | [Информация об одной точке продаж](outlets/get-v2-campaigns-campaignid-outlets-outletid.md) |
| `GET` | `/v2/campaigns/{campaignId}/outlets` | outlets | [Информация о нескольких точках продаж](outlets/get-v2-campaigns-campaignid-outlets.md) |
| `GET` | `/v2/campaigns/{campaignId}/returns` | returns | [Список невыкупов и возвратов](returns/get-v2-campaigns-campaignid-returns.md) |
| `GET` | `/v2/campaigns/{campaignId}/settings` | campaigns | [Настройки магазина](campaigns/get-v2-campaigns-campaignid-settings.md) |
| `GET` | `/v2/campaigns/{campaignId}/shipments/reception-transfer-act` | shipments | [Подтверждение ближайшей отгрузки и получение акта приема-передачи для нее](shipments/get-v2-campaigns-campaignid-shipments-reception-transfer-act.md) |
| `GET` | `/v2/campaigns/{campaignId}` | campaigns | [Информация о магазине](campaigns/get-v2-campaigns-campaignid.md) |
| `GET` | `/v2/campaigns` | campaigns | [Список магазинов пользователя](campaigns/get-v2-campaigns.md) |
| `GET` | `/v2/delivery/services` | delivery-services | [Справочник служб доставки](delivery-services/get-v2-delivery-services.md) |
| `GET` | `/v2/regions/{regionId}/children` | regions | [Информация о дочерних регионах](regions/get-v2-regions-regionid-children.md) |
| `GET` | `/v2/regions/{regionId}` | regions | [Информация о регионе](regions/get-v2-regions-regionid.md) |
| `GET` | `/v2/regions` | regions | [Поиск регионов по их имени](regions/get-v2-regions.md) |
| `GET` | `/v2/reports/info/{reportId}` | reports | [Получение заданного отчета или документа](reports/get-v2-reports-info-reportid.md) |
| `GET` | `/v2/warehouses` | warehouses | [Идентификаторы фулфилмент-складов Маркета](warehouses/get-v2-warehouses.md) |
| `POST` | `/v1/businesses/{businessId}/goods-feedback-advertiser` | goods-feedback | [Получение отзывов о товарах для рекламодателей](goods-feedback/post-v1-businesses-businessid-goods-feedback-advertiser.md) |
| `POST` | `/v1/businesses/{businessId}/goods-questions/answers` | goods-questions | [Получение ответов на вопрос](goods-questions/post-v1-businesses-businessid-goods-questions-answers.md) |
| `POST` | `/v1/businesses/{businessId}/goods-questions/update` | goods-questions | [Создание, изменение и удаление ответа или комментария](goods-questions/post-v1-businesses-businessid-goods-questions-update.md) |
| `POST` | `/v1/businesses/{businessId}/goods-questions` | goods-questions | [Получение вопросов о товарах продавца](goods-questions/post-v1-businesses-businessid-goods-questions.md) |
| `POST` | `/v1/businesses/{businessId}/logistics-points` | logistic-points | [Получение точек ПВЗ Маркета](logistic-points/post-v1-businesses-businessid-logistics-points.md) |
| `POST` | `/v1/businesses/{businessId}/offer-mappings/barcodes/generate` | business-offer-mappings | [Генерация штрихкодов](business-offer-mappings/post-v1-businesses-businessid-offer-mappings-barcodes-generate.md) |
| `POST` | `/v1/businesses/{businessId}/operations` | operations | [Получение статусов операций](operations/post-v1-businesses-businessid-operations.md) |
| `POST` | `/v1/businesses/{businessId}/orders` | orders | [Информация о заказах в кабинете](orders/post-v1-businesses-businessid-orders.md) |
| `POST` | `/v1/businesses/{businessId}/reports/marketing-detalization/generate` | reports | [Отчет по счету маркетинга](reports/post-v1-businesses-businessid-reports-marketing-detalization-generate.md) |
| `POST` | `/v1/businesses/{businessId}/returns/decisions` | returns | [Получение возможных решений по возврату](returns/post-v1-businesses-businessid-returns-decisions.md) |
| `POST` | `/v1/campaigns/{campaignId}/delivery-options` | delivery-options | [Получение доступных вариантов доставки заказов](delivery-options/post-v1-campaigns-campaignid-delivery-options.md) |
| `POST` | `/v1/campaigns/{campaignId}/orders/create` | orders | [Создание заказа](orders/post-v1-campaigns-campaignid-orders-create.md) |
| `POST` | `/v1/campaigns/{campaignId}/orders/update-options` | orders | [Получение временных интервалов для изменения заказа](orders/post-v1-campaigns-campaignid-orders-update-options.md) |
| `POST` | `/v1/campaigns/{campaignId}/orders/update` | orders | [Изменение заказа](orders/post-v1-campaigns-campaignid-orders-update.md) |
| `POST` | `/v1/campaigns/{campaignId}/return-delivery-options` | delivery-options | [Получение подходящих для возврата пунктов выдачи](delivery-options/post-v1-campaigns-campaignid-return-delivery-options.md) |
| `POST` | `/v1/campaigns/{campaignId}/returns/cancel` | returns | [Отмена возврата](returns/post-v1-campaigns-campaignid-returns-cancel.md) |
| `POST` | `/v1/campaigns/{campaignId}/returns/create` | returns | [Создание возврата](returns/post-v1-campaigns-campaignid-returns-create.md) |
| `POST` | `/v1/reports/documents/barcodes/generate` | reports | [Получение файла со штрихкодами](reports/post-v1-reports-documents-barcodes-generate.md) |
| `POST` | `/v2/auth/token` | auth | [Получение информации о токене авторизации](auth/post-v2-auth-token.md) |
| `POST` | `/v2/businesses/{businessId}/bids/info` | bids | [Информация об установленных ставках](bids/post-v2-businesses-businessid-bids-info.md) |
| `POST` | `/v2/businesses/{businessId}/bids/recommendations` | bids | [Рекомендованные ставки для заданных товаров](bids/post-v2-businesses-businessid-bids-recommendations.md) |
| `POST` | `/v2/businesses/{businessId}/chats/file/send` | chats | [Отправка файла в чат](chats/post-v2-businesses-businessid-chats-file-send.md) |
| `POST` | `/v2/businesses/{businessId}/chats/history` | chats | [Получение истории сообщений в чате](chats/post-v2-businesses-businessid-chats-history.md) |
| `POST` | `/v2/businesses/{businessId}/chats/message` | chats | [Отправка сообщения в чат](chats/post-v2-businesses-businessid-chats-message.md) |
| `POST` | `/v2/businesses/{businessId}/chats/new` | chats | [Создание нового чата с покупателем](chats/post-v2-businesses-businessid-chats-new.md) |
| `POST` | `/v2/businesses/{businessId}/chats` | chats | [Получение доступных чатов](chats/post-v2-businesses-businessid-chats.md) |
| `POST` | `/v2/businesses/{businessId}/goods-feedback/comments/delete` | goods-feedback | [Удаление комментария к отзыву](goods-feedback/post-v2-businesses-businessid-goods-feedback-comments-delete.md) |
| `POST` | `/v2/businesses/{businessId}/goods-feedback/comments/update` | goods-feedback | [Добавление нового или изменение созданного комментария](goods-feedback/post-v2-businesses-businessid-goods-feedback-comments-update.md) |
| `POST` | `/v2/businesses/{businessId}/goods-feedback/comments` | goods-feedback | [Получение комментариев к отзыву](goods-feedback/post-v2-businesses-businessid-goods-feedback-comments.md) |
| `POST` | `/v2/businesses/{businessId}/goods-feedback/skip-reaction` | goods-feedback | [Пропуск реакции на отзывы](goods-feedback/post-v2-businesses-businessid-goods-feedback-skip-reaction.md) |
| `POST` | `/v2/businesses/{businessId}/goods-feedback` | goods-feedback | [Получение отзывов о товарах продавца](goods-feedback/post-v2-businesses-businessid-goods-feedback.md) |
| `POST` | `/v2/businesses/{businessId}/offer-cards/update` | content | [Редактирование категорийных характеристик товара](content/post-v2-businesses-businessid-offer-cards-update.md) |
| `POST` | `/v2/businesses/{businessId}/offer-cards` | content | [Получение информации о заполненности карточек магазина](content/post-v2-businesses-businessid-offer-cards.md) |
| `POST` | `/v2/businesses/{businessId}/offer-mappings/archive` | business-offer-mappings | [Добавление товаров в архив](business-offer-mappings/post-v2-businesses-businessid-offer-mappings-archive.md) |
| `POST` | `/v2/businesses/{businessId}/offer-mappings/delete` | business-offer-mappings | [Удаление товаров из каталога](business-offer-mappings/post-v2-businesses-businessid-offer-mappings-delete.md) |
| `POST` | `/v2/businesses/{businessId}/offer-mappings/unarchive` | business-offer-mappings | [Удаление товаров из архива](business-offer-mappings/post-v2-businesses-businessid-offer-mappings-unarchive.md) |
| `POST` | `/v2/businesses/{businessId}/offer-mappings/update` | business-offer-mappings | [Добавление товаров в каталог и изменение информации о них](business-offer-mappings/post-v2-businesses-businessid-offer-mappings-update.md) |
| `POST` | `/v2/businesses/{businessId}/offer-mappings` | business-offer-mappings | [Информация о товарах в каталоге](business-offer-mappings/post-v2-businesses-businessid-offer-mappings.md) |
| `POST` | `/v2/businesses/{businessId}/offer-prices/updates` | prices | [Установка цен на товары для всех магазинов](prices/post-v2-businesses-businessid-offer-prices-updates.md) |
| `POST` | `/v2/businesses/{businessId}/offer-prices` | prices | [Просмотр цен на указанные товары во всех магазинах](prices/post-v2-businesses-businessid-offer-prices.md) |
| `POST` | `/v2/businesses/{businessId}/offers/recommendations` | offers | [Рекомендации Маркета, касающиеся цен](offers/post-v2-businesses-businessid-offers-recommendations.md) |
| `POST` | `/v2/businesses/{businessId}/price-quarantine/confirm` | price-quarantine | [Удаление товара из карантина по цене в кабинете](price-quarantine/post-v2-businesses-businessid-price-quarantine-confirm.md) |
| `POST` | `/v2/businesses/{businessId}/price-quarantine` | price-quarantine | [Список товаров, находящихся в карантине по цене в кабинете](price-quarantine/post-v2-businesses-businessid-price-quarantine.md) |
| `POST` | `/v2/businesses/{businessId}/promos/offers/delete` | promos | [Удаление товаров из акции](promos/post-v2-businesses-businessid-promos-offers-delete.md) |
| `POST` | `/v2/businesses/{businessId}/promos/offers/update` | promos | [Добавление товаров в акцию или изменение их цен](promos/post-v2-businesses-businessid-promos-offers-update.md) |
| `POST` | `/v2/businesses/{businessId}/promos/offers` | promos | [Получение списка товаров, которые участвуют или могут участвовать в акции](promos/post-v2-businesses-businessid-promos-offers.md) |
| `POST` | `/v2/businesses/{businessId}/promos` | promos | [Получение списка акций](promos/post-v2-businesses-businessid-promos.md) |
| `POST` | `/v2/businesses/{businessId}/ratings/quality` | ratings | [Индекс качества магазинов](ratings/post-v2-businesses-businessid-ratings-quality.md) |
| `POST` | `/v2/businesses/{businessId}/settings` | businesses | [Настройки кабинета](businesses/post-v2-businesses-businessid-settings.md) |
| `POST` | `/v2/businesses/{businessId}/warehouses` | warehouses | [Список складов](warehouses/post-v2-businesses-businessid-warehouses.md) |
| `POST` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm` | shipments | [Подтверждение отгрузки](shipments/post-v2-campaigns-campaignid-first-mile-shipments-shipmentid-confirm.md) |
| `POST` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/transfer` | shipments | [Перенос заказов в следующую отгрузку](shipments/post-v2-campaigns-campaignid-first-mile-shipments-shipmentid-orders-transfer.md) |
| `POST` | `/v2/campaigns/{campaignId}/hidden-offers/delete` | hidden-offers | [Возобновление показа товаров](hidden-offers/post-v2-campaigns-campaignid-hidden-offers-delete.md) |
| `POST` | `/v2/campaigns/{campaignId}/hidden-offers` | hidden-offers | [Скрытие товаров и настройки скрытия](hidden-offers/post-v2-campaigns-campaignid-hidden-offers.md) |
| `POST` | `/v2/campaigns/{campaignId}/offer-prices/updates` | prices | [Установка цен на товары в конкретном магазине](prices/post-v2-campaigns-campaignid-offer-prices-updates.md) |
| `POST` | `/v2/campaigns/{campaignId}/offer-prices` | prices | [Просмотр цен на указанные товары в конкретном магазине](prices/post-v2-campaigns-campaignid-offer-prices.md) |
| `POST` | `/v2/campaigns/{campaignId}/offers/delete` | offers | [Удаление товаров из ассортимента магазина](offers/post-v2-campaigns-campaignid-offers-delete.md) |
| `POST` | `/v2/campaigns/{campaignId}/offers/stocks` | stocks | [Информация об остатках и оборачиваемости](stocks/post-v2-campaigns-campaignid-offers-stocks.md) |
| `POST` | `/v2/campaigns/{campaignId}/offers/update` | offers | [Изменение условий продажи товаров в магазине](offers/post-v2-campaigns-campaignid-offers-update.md) |
| `POST` | `/v2/campaigns/{campaignId}/offers` | offers | [Информация о товарах, которые размещены в заданном магазине](offers/post-v2-campaigns-campaignid-offers.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/status-update` | orders | [Изменение статусов нескольких заказов](orders/post-v2-campaigns-campaignid-orders-status-update.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/business-buyer` | order-business-information | [Информация о покупателе — юридическом лице](order-business-information/post-v2-campaigns-campaignid-orders-orderid-business-buyer.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods` | orders | [Передача ключей цифровых товаров](orders/post-v2-campaigns-campaignid-orders-orderid-deliverdigitalgoods.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/track` | order-delivery | [Передача трек‑номера посылки](order-delivery/post-v2-campaigns-campaignid-orders-orderid-delivery-track.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/documents` | order-business-information | [Информация о документах](order-business-information/post-v2-campaigns-campaignid-orders-orderid-documents.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/external-id` | orders | [Передача внешнего идентификатора заказа](orders/post-v2-campaigns-campaignid-orders-orderid-external-id.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status` | orders | [Статусы проверки кодов маркировки](orders/post-v2-campaigns-campaignid-orders-orderid-identifiers-status.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit` | returns | [Передача решения по возврату](returns/post-v2-campaigns-campaignid-orders-orderid-returns-returnid-decision-submit.md) |
| `POST` | `/v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision` | returns | [Принятие или изменение решения по возврату](returns/post-v2-campaigns-campaignid-orders-orderid-returns-returnid-decision.md) |
| `POST` | `/v2/campaigns/{campaignId}/outlets/licenses` | outlet-licenses | [Создание и изменение лицензий для точек продаж](outlet-licenses/post-v2-campaigns-campaignid-outlets-licenses.md) |
| `POST` | `/v2/campaigns/{campaignId}/outlets` | outlets | [Создание точки продаж](outlets/post-v2-campaigns-campaignid-outlets.md) |
| `POST` | `/v2/campaigns/{campaignId}/price-quarantine/confirm` | price-quarantine | [Удаление товара из карантина по цене в магазине](price-quarantine/post-v2-campaigns-campaignid-price-quarantine-confirm.md) |
| `POST` | `/v2/campaigns/{campaignId}/price-quarantine` | price-quarantine | [Список товаров, находящихся в карантине по цене в магазине](price-quarantine/post-v2-campaigns-campaignid-price-quarantine.md) |
| `POST` | `/v2/campaigns/{campaignId}/ratings/quality/details` | ratings | [Заказы, которые повлияли на индекс качества](ratings/post-v2-campaigns-campaignid-ratings-quality-details.md) |
| `POST` | `/v2/campaigns/{campaignId}/stats/orders` | orders-stats | [Детальная информация по заказам](orders-stats/post-v2-campaigns-campaignid-stats-orders.md) |
| `POST` | `/v2/campaigns/{campaignId}/stats/skus` | goods-stats | [Отчет по товарам](goods-stats/post-v2-campaigns-campaignid-stats-skus.md) |
| `POST` | `/v2/campaigns/{campaignId}/supply-requests/documents` | supply-requests | [Получение документов по заявке на поставку, вывоз или утилизацию](supply-requests/post-v2-campaigns-campaignid-supply-requests-documents.md) |
| `POST` | `/v2/campaigns/{campaignId}/supply-requests/items` | supply-requests | [Получение товаров в заявке на поставку, вывоз или утилизацию](supply-requests/post-v2-campaigns-campaignid-supply-requests-items.md) |
| `POST` | `/v2/campaigns/{campaignId}/supply-requests` | supply-requests | [Получение информации о заявках на поставку, вывоз и утилизацию](supply-requests/post-v2-campaigns-campaignid-supply-requests.md) |
| `POST` | `/v2/campaigns/{campaignId}/warehouse/status` | warehouses | [Изменение статуса склада](warehouses/post-v2-campaigns-campaignid-warehouse-status.md) |
| `POST` | `/v2/categories/max-sale-quantum` | categories | [Лимит на установку кванта продажи и минимального количества товаров в заказе](categories/post-v2-categories-max-sale-quantum.md) |
| `POST` | `/v2/categories/tree` | categories | [Дерево категорий](categories/post-v2-categories-tree.md) |
| `POST` | `/v2/category/{categoryId}/parameters` | content | [Списки характеристик товаров по категориям](content/post-v2-category-categoryid-parameters.md) |
| `POST` | `/v2/regions/countries` | regions | [Список допустимых кодов стран](regions/post-v2-regions-countries.md) |
| `POST` | `/v2/reports/banners-statistics/generate` | reports | [Отчет по охватному продвижению](reports/post-v2-reports-banners-statistics-generate.md) |
| `POST` | `/v2/reports/boost-consolidated/generate` | reports | [Отчет по бусту продаж](reports/post-v2-reports-boost-consolidated-generate.md) |
| `POST` | `/v2/reports/closure-documents/detalization/generate` | reports | [Отчет по схождению с закрывающими документами](reports/post-v2-reports-closure-documents-detalization-generate.md) |
| `POST` | `/v2/reports/closure-documents/generate` | reports | [Закрывающие документы](reports/post-v2-reports-closure-documents-generate.md) |
| `POST` | `/v2/reports/competitors-position/generate` | reports | [Отчет «Конкурентная позиция»](reports/post-v2-reports-competitors-position-generate.md) |
| `POST` | `/v2/reports/documents/labels/generate` | reports | [Готовые ярлыки‑наклейки на все коробки в нескольких заказах](reports/post-v2-reports-documents-labels-generate.md) |
| `POST` | `/v2/reports/documents/shipment-list/generate` | reports | [Получение листа сборки](reports/post-v2-reports-documents-shipment-list-generate.md) |
| `POST` | `/v2/reports/goods-feedback/generate` | reports | [Отчет по отзывам о товарах](reports/post-v2-reports-goods-feedback-generate.md) |
| `POST` | `/v2/reports/goods-movement/generate` | reports | [Отчет по движению товаров](reports/post-v2-reports-goods-movement-generate.md) |
| `POST` | `/v2/reports/goods-prices/generate` | reports | [Отчет «Цены»](reports/post-v2-reports-goods-prices-generate.md) |
| `POST` | `/v2/reports/goods-realization/generate` | reports | [Отчет по реализации](reports/post-v2-reports-goods-realization-generate.md) |
| `POST` | `/v2/reports/goods-turnover/generate` | reports | [Отчет по оборачиваемости](reports/post-v2-reports-goods-turnover-generate.md) |
| `POST` | `/v2/reports/jewelry-fiscal/generate` | reports | [Отчет по заказам с ювелирными изделиями](reports/post-v2-reports-jewelry-fiscal-generate.md) |
| `POST` | `/v2/reports/key-indicators/generate` | reports | [Отчет по ключевым показателям](reports/post-v2-reports-key-indicators-generate.md) |
| `POST` | `/v2/reports/sales-geography/generate` | reports | [Отчет по географии продаж](reports/post-v2-reports-sales-geography-generate.md) |
| `POST` | `/v2/reports/shelf-statistics/generate` | reports | [Отчет по полкам](reports/post-v2-reports-shelf-statistics-generate.md) |
| `POST` | `/v2/reports/shows-boost/generate` | reports | [Отчет по бусту показов](reports/post-v2-reports-shows-boost-generate.md) |
| `POST` | `/v2/reports/shows-sales/generate` | reports | [Отчет «Аналитика продаж»](reports/post-v2-reports-shows-sales-generate.md) |
| `POST` | `/v2/reports/stocks-on-warehouses/generate` | reports | [Отчет по остаткам на складах](reports/post-v2-reports-stocks-on-warehouses-generate.md) |
| `POST` | `/v2/reports/united-marketplace-services/generate` | reports | [Отчет по стоимости услуг](reports/post-v2-reports-united-marketplace-services-generate.md) |
| `POST` | `/v2/reports/united-netting/generate` | reports | [Отчет по платежам](reports/post-v2-reports-united-netting-generate.md) |
| `POST` | `/v2/reports/united-orders/generate` | reports | [Отчет по заказам](reports/post-v2-reports-united-orders-generate.md) |
| `POST` | `/v2/reports/united-returns/generate` | reports | [Отчет по невыкупам и возвратам](reports/post-v2-reports-united-returns-generate.md) |
| `POST` | `/v2/tariffs/calculate` | tariffs | [Калькулятор стоимости услуг](tariffs/post-v2-tariffs-calculate.md) |
| `POST` | `/v3/businesses/{businessId}/offers/stocks/update` | stocks | [Передача информации об остатках](stocks/post-v3-businesses-businessid-offers-stocks-update.md) |
| `POST` | `/v3/businesses/{businessId}/offers/stocks` | stocks | [Информация об остатках](stocks/post-v3-businesses-businessid-offers-stocks.md) |
| `POST` | `/v3/businesses/{businessId}/reports/stocks/generate` | reports | [Отчет по остаткам на складах партнера](reports/post-v3-businesses-businessid-reports-stocks-generate.md) |
| `POST` | `/v3/businesses/{businessId}/warehouse/models/status` | warehouses | [Включение/выключение модели работы склада](warehouses/post-v3-businesses-businessid-warehouse-models-status.md) |
| `POST` | `/v3/businesses/{businessId}/warehouses` | warehouses | [Список складов](warehouses/post-v3-businesses-businessid-warehouses.md) |
| `PUT` | `/v2/businesses/{businessId}/bids` | bids | [Включение буста продаж и установка ставок](bids/put-v2-businesses-businessid-bids.md) |
| `PUT` | `/v2/campaigns/{campaignId}/bids` | bids | [Включение буста продаж и установка ставок для магазина](bids/put-v2-campaigns-campaignid-bids.md) |
| `PUT` | `/v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallets` | shipments | [Передача количества упаковок для доверительной приемки](shipments/put-v2-campaigns-campaignid-first-mile-shipments-shipmentid-pallets.md) |
| `PUT` | `/v2/campaigns/{campaignId}/first-mile/shipments` | shipments | [Получение информации о нескольких отгрузках](shipments/put-v2-campaigns-campaignid-first-mile-shipments.md) |
| `PUT` | `/v2/campaigns/{campaignId}/offers/stocks` | stocks | [Передача информации об остатках](stocks/put-v2-campaigns-campaignid-offers-stocks.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/boxes` | orders | [Подготовка заказа](orders/put-v2-campaigns-campaignid-orders-orderid-boxes.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept` | orders | [Отмена заказа покупателем](orders/put-v2-campaigns-campaignid-orders-orderid-cancellation-accept.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/date` | order-delivery | [Изменение даты доставки заказа](order-delivery/put-v2-campaigns-campaignid-orders-orderid-delivery-date.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes` | orders | [Передача количества грузовых мест в заказе](orders/put-v2-campaigns-campaignid-orders-orderid-delivery-shipments-shipmentid-boxes.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit` | order-delivery | [Продление срока хранения заказа](order-delivery/put-v2-campaigns-campaignid-orders-orderid-delivery-storage-limit.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/identifiers` | orders | [Передача кодов маркировки единиц товара](orders/put-v2-campaigns-campaignid-orders-orderid-identifiers.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/items` | orders | [Удаление товаров из заказа или уменьшение их числа](orders/put-v2-campaigns-campaignid-orders-orderid-items.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/status` | orders | [Изменение статуса одного заказа](orders/put-v2-campaigns-campaignid-orders-orderid-status.md) |
| `PUT` | `/v2/campaigns/{campaignId}/orders/{orderId}/verifyEac` | order-delivery | [Передача кода подтверждения](order-delivery/put-v2-campaigns-campaignid-orders-orderid-verifyeac.md) |
| `PUT` | `/v2/campaigns/{campaignId}/outlets/{outletId}` | outlets | [Изменение информации о точке продаж](outlets/put-v2-campaigns-campaignid-outlets-outletid.md) |
