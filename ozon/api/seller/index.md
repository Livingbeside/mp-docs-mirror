---
title: Документация Ozon Seller API — все методы
api: ozon-seller
spec_version: 2.1
operations: 467
source: "https://docs.ozon.ru/api/seller/"
content_sha: 0955e3582908de55
---

# Документация Ozon Seller API

По вопросам работы с Seller API обращайтесь в поддержку через личный кабинет.

Обновляем корневой TLS/SSL-сертификат GlobalSign — вместо него будем использовать [HARICA](https://app.harica.gr/).
[Подробнее о переходе на HARICA на платформе разработчиков Ozon for dev](https://dev.ozon.ru/news/775-Izmeneniia-v-Ozon-API-migratsiia-kornevogo-sertifikata-UTs-Ozon/)

> [Инструкции по работе с маркетплейсом](https://seller-edu.ozon.ru)

> [Информационная платформа и сообщество разработчиков Ozon for dev](https://dev.ozon.ru/)

Версия спеки: `2.1` · методов: **467** · разделов справки: **26**

Источник: https://docs.ozon.ru/api/seller/

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/v1/actions` | Promos | [Список акций](promos/get-v1-actions.md) |
| `GET` | `/v1/cargoes-label/file/{file_guid}` | FboSupplyRequest | [Получить PDF с этикетками грузовых мест](fbosupplyrequest/get-v1-cargoes-label-file-file-guid.md) |
| `GET` | `/v1/product/certificate/accordance-types` | CertificationAPI | [Список типов соответствия требованиям (версия 1)](certificationapi/get-v1-product-certificate-accordance-types.md) |
| `GET` | `/v1/product/certificate/types` | CertificationAPI | [Справочник типов документов](certificationapi/get-v1-product-certificate-types.md) |
| `GET` | `/v1/supplier/available_warehouses` | FBO | [Загруженность складов Ozon](fbo/get-v1-supplier-available-warehouses.md) |
| `GET` | `/v2/product/certificate/accordance-types/list` | CertificationAPI | [Список типов соответствия требованиям (версия 2)](certificationapi/get-v2-product-certificate-accordance-types-list.md) |
| `POST` | `/v1/actions/auto-add/products/candidates` | PromosBeta | [Получить список доступных товаров для автодобавления в акцию](promosbeta/post-v1-actions-auto-add-products-candidates.md) |
| `POST` | `/v1/actions/auto-add/products/delete` | PromosBeta | [Удалить товары из автодобавления в акцию](promosbeta/post-v1-actions-auto-add-products-delete.md) |
| `POST` | `/v1/actions/auto-add/products/list` | PromosBeta | [Получить список товаров из автодобавления в акцию](promosbeta/post-v1-actions-auto-add-products-list.md) |
| `POST` | `/v1/actions/auto-add/products/update` | PromosBeta | [Добавить или обновить товары в автодобавлении в акцию](promosbeta/post-v1-actions-auto-add-products-update.md) |
| `POST` | `/v1/actions/candidates` | Promos | [Список доступных для акции товаров](promos/post-v1-actions-candidates.md) |
| `POST` | `/v1/actions/discounts-task/approve` | Promos | [Согласовать заявку на скидку](promos/post-v1-actions-discounts-task-approve.md) |
| `POST` | `/v1/actions/discounts-task/decline` | Promos | [Отклонить заявку на скидку](promos/post-v1-actions-discounts-task-decline.md) |
| `POST` | `/v1/actions/discounts-task/list` | Promos | [Список заявок на скидку](promos/post-v1-actions-discounts-task-list.md) |
| `POST` | `/v1/actions/products/activate` | Promos | [Добавить товар в акцию](promos/post-v1-actions-products-activate.md) |
| `POST` | `/v1/actions/products/deactivate` | Promos | [Удалить товары из акции](promos/post-v1-actions-products-deactivate.md) |
| `POST` | `/v1/actions/products` | Promos | [Список участвующих в акции товаров](promos/post-v1-actions-products.md) |
| `POST` | `/v1/analytics/data` | Premium | [Данные аналитики](premium/post-v1-analytics-data.md) |
| `POST` | `/v1/analytics/decommissioned-goods` | BetaMethod | [Получить отчёт о списанных товарах](betamethod/post-v1-analytics-decommissioned-goods.md) |
| `POST` | `/v1/analytics/manage/stocks` | BetaMethod | [Управление остатками](betamethod/post-v1-analytics-manage-stocks.md) |
| `POST` | `/v1/analytics/product-queries/details` | Premium | [Получить детализацию запросов по товару](premium/post-v1-analytics-product-queries-details.md) |
| `POST` | `/v1/analytics/product-queries` | Premium | [Получить информацию о запросах моих товаров](premium/post-v1-analytics-product-queries.md) |
| `POST` | `/v1/analytics/stocks` | AnalyticsAPI | [Получить аналитику по остаткам](analyticsapi/post-v1-analytics-stocks.md) |
| `POST` | `/v1/analytics/turnover/stocks` | AnalyticsAPI | [Оборачиваемость товара](analyticsapi/post-v1-analytics-turnover-stocks.md) |
| `POST` | `/v1/assembly/carriage/posting/list` | DeliveryFBS | [Получить список отправлений в отгрузке](deliveryfbs/post-v1-assembly-carriage-posting-list.md) |
| `POST` | `/v1/assembly/carriage/product/list` | DeliveryFBS | [Получить список товаров в отгрузке](deliveryfbs/post-v1-assembly-carriage-product-list.md) |
| `POST` | `/v1/assembly/fbs/posting/list` | DeliveryFBS | [Получить список отправлений](deliveryfbs/post-v1-assembly-fbs-posting-list.md) |
| `POST` | `/v1/assembly/fbs/product/list` | DeliveryFBS | [Получить список товаров в отправлениях](deliveryfbs/post-v1-assembly-fbs-product-list.md) |
| `POST` | `/v1/barcode/add` | BarcodeAPI | [Привязать штрихкод к товару](barcodeapi/post-v1-barcode-add.md) |
| `POST` | `/v1/barcode/generate` | BarcodeAPI | [Создать штрихкод для товара](barcodeapi/post-v1-barcode-generate.md) |
| `POST` | `/v1/brand/company-certification/list` | BrandAPI | [Список сертифицируемых брендов](brandapi/post-v1-brand-company-certification-list.md) |
| `POST` | `/v1/cancel-reason/list-by-order` | CancelReasonAPI | [Причины отмены заказа](cancelreasonapi/post-v1-cancel-reason-list-by-order.md) |
| `POST` | `/v1/cancel-reason/list-by-posting` | CancelReasonAPI | [Причины отмены отправления](cancelreasonapi/post-v1-cancel-reason-list-by-posting.md) |
| `POST` | `/v1/cancel-reason/list` | CancelReasonAPI | [Причины отмены отправлений](cancelreasonapi/post-v1-cancel-reason-list.md) |
| `POST` | `/v1/cargoes-label/create` | FboSupplyRequest | [Сгенерировать этикетки для грузомест](fbosupplyrequest/post-v1-cargoes-label-create.md) |
| `POST` | `/v1/cargoes-label/get` | FboSupplyRequest | [Получить идентификатор этикетки для грузомест](fbosupplyrequest/post-v1-cargoes-label-get.md) |
| `POST` | `/v1/cargoes/create` | FboSupplyRequest | [Установка грузомест](fbosupplyrequest/post-v1-cargoes-create.md) |
| `POST` | `/v1/cargoes/delete/status` | FboSupplyRequest | [Информация о статусе удаления грузоместа](fbosupplyrequest/post-v1-cargoes-delete-status.md) |
| `POST` | `/v1/cargoes/delete` | FboSupplyRequest | [Удалить грузоместо в заявке на поставку](fbosupplyrequest/post-v1-cargoes-delete.md) |
| `POST` | `/v1/cargoes/get` | FboSupplyRequest | [Получить информацию о грузоместах](fbosupplyrequest/post-v1-cargoes-get.md) |
| `POST` | `/v1/cargoes/label/transport-by-order/create` | FBOTransport | [Сгенерировать этикетки для транспортных грузомест по идентификатору поставки](fbotransport/post-v1-cargoes-label-transport-by-order-create.md) |
| `POST` | `/v1/cargoes/label/transport-by-order/status` | FBOTransport | [Получить статус генерации этикеток для транспортных грузомеcт по идентификатору поставки](fbotransport/post-v1-cargoes-label-transport-by-order-status.md) |
| `POST` | `/v1/cargoes/label/transport/create` | FBOTransport | [Сгенерировать этикетки транспортных грузомест по идентификатору грузоместа](fbotransport/post-v1-cargoes-label-transport-create.md) |
| `POST` | `/v1/cargoes/label/transport/status` | FBOTransport | [Получить статус генерации этикеток транспортных грузомест по идентификатору грузоместа](fbotransport/post-v1-cargoes-label-transport-status.md) |
| `POST` | `/v1/cargoes/rules/get` | FboSupplyRequest | [Чек-лист по установке грузомест FBO](fbosupplyrequest/post-v1-cargoes-rules-get.md) |
| `POST` | `/v1/cargoes/supplies/get` | FBOTransport | [Получить информацию о грузоместах в поставках](fbotransport/post-v1-cargoes-supplies-get.md) |
| `POST` | `/v1/cargoes/transport/activate/status` | FBOTransport | [Получить статус включения или отключения транспортных грузомест](fbotransport/post-v1-cargoes-transport-activate-status.md) |
| `POST` | `/v1/cargoes/transport/activate` | FBOTransport | [Включить или отключить транспортные грузоместа в поставке](fbotransport/post-v1-cargoes-transport-activate.md) |
| `POST` | `/v1/cargoes/transport/bind/status` | FBOTransport | [Получить статус связывания или отвязывания грузомест и транспортных грузомест](fbotransport/post-v1-cargoes-transport-bind-status.md) |
| `POST` | `/v1/cargoes/transport/bind` | FBOTransport | [Связать или отвязать грузоместа и транспортные грузоместа](fbotransport/post-v1-cargoes-transport-bind.md) |
| `POST` | `/v1/cargoes/transport/create/status` | FBOTransport | [Получить статус создания транспортного грузоместа](fbotransport/post-v1-cargoes-transport-create-status.md) |
| `POST` | `/v1/cargoes/transport/create` | FBOTransport | [Создать транспортное грузоместо](fbotransport/post-v1-cargoes-transport-create.md) |
| `POST` | `/v1/carriage/act-discrepancy/pdf` | DeliveryFBS | [Получить акт о расхождениях по отгрузке FBS](deliveryfbs/post-v1-carriage-act-discrepancy-pdf.md) |
| `POST` | `/v1/carriage/approve` | DeliveryFBS | [Подтверждение отгрузки](deliveryfbs/post-v1-carriage-approve.md) |
| `POST` | `/v1/carriage/cancel` | DeliveryFBS | [Удаление отгрузки](deliveryfbs/post-v1-carriage-cancel.md) |
| `POST` | `/v1/carriage/container/approve` | CarriageAPI | [Подтвердить состав грузоместа](carriageapi/post-v1-carriage-container-approve.md) |
| `POST` | `/v1/carriage/container/cancel` | CarriageAPI | [Отменить грузоместо](carriageapi/post-v1-carriage-container-cancel.md) |
| `POST` | `/v1/carriage/container/create` | CarriageAPI | [Создать грузоместо](carriageapi/post-v1-carriage-container-create.md) |
| `POST` | `/v1/carriage/container/document/get` | CarriageAPI | [Получить документы по грузоместам — ТрН и лист отгрузки](carriageapi/post-v1-carriage-container-document-get.md) |
| `POST` | `/v1/carriage/container/fill` | CarriageAPI | [Наполнить грузоместо отправлениями](carriageapi/post-v1-carriage-container-fill.md) |
| `POST` | `/v1/carriage/container/get` | CarriageAPI | [Получить информацию о грузоместах](carriageapi/post-v1-carriage-container-get.md) |
| `POST` | `/v1/carriage/container/label/get` | CarriageAPI | [Получить этикетку по грузоместам](carriageapi/post-v1-carriage-container-label-get.md) |
| `POST` | `/v1/carriage/container/list` | CarriageAPI | [Получить список грузомест](carriageapi/post-v1-carriage-container-list.md) |
| `POST` | `/v1/carriage/container/place-into` | CarriageAPI | [Разместить коробки на палете](carriageapi/post-v1-carriage-container-place-into.md) |
| `POST` | `/v1/carriage/container/remove-from` | CarriageAPI | [Убрать коробки с палеты](carriageapi/post-v1-carriage-container-remove-from.md) |
| `POST` | `/v1/carriage/container/remove-postings` | CarriageAPI | [Убрать отправления из грузоместа](carriageapi/post-v1-carriage-container-remove-postings.md) |
| `POST` | `/v1/carriage/container/status/get` | CarriageAPI | [Получить статус грузомест FBS](carriageapi/post-v1-carriage-container-status-get.md) |
| `POST` | `/v1/carriage/container/task/info` | CarriageAPI | [Получить статус задачи грузового места](carriageapi/post-v1-carriage-container-task-info.md) |
| `POST` | `/v1/carriage/courier-contact/get` | DeliveryFBS | [Получить контактные данные продавца для курьера](deliveryfbs/post-v1-carriage-courier-contact-get.md) |
| `POST` | `/v1/carriage/courier-contact/set` | DeliveryFBS | [Добавить или обновить контактные данные продавца для курьера](deliveryfbs/post-v1-carriage-courier-contact-set.md) |
| `POST` | `/v1/carriage/create` | DeliveryFBS | [Создание отгрузки](deliveryfbs/post-v1-carriage-create.md) |
| `POST` | `/v1/carriage/delivery/list` | DeliveryFBS | [Список методов доставки и отгрузок](deliveryfbs/post-v1-carriage-delivery-list.md) |
| `POST` | `/v1/carriage/ettn/status` | DeliveryFBS | [Получить статус проверки электронной ТТН на прослеживаемой перевозке FBS](deliveryfbs/post-v1-carriage-ettn-status.md) |
| `POST` | `/v1/carriage/get` | DeliveryFBS | [Информация о перевозке](deliveryfbs/post-v1-carriage-get.md) |
| `POST` | `/v1/carriage/pass/create` | Pass | [Создать пропуск](pass/post-v1-carriage-pass-create.md) |
| `POST` | `/v1/carriage/pass/delete` | Pass | [Удалить пропуск](pass/post-v1-carriage-pass-delete.md) |
| `POST` | `/v1/carriage/pass/update` | Pass | [Обновить пропуск](pass/post-v1-carriage-pass-update.md) |
| `POST` | `/v1/carriage/set-postings` | DeliveryFBS | [Изменение состава отгрузки](deliveryfbs/post-v1-carriage-set-postings.md) |
| `POST` | `/v1/chat/send/file` | ChatAPI | [Отправить файл](chatapi/post-v1-chat-send-file.md) |
| `POST` | `/v1/chat/send/message` | Premium | [Отправить сообщение](premium/post-v1-chat-send-message.md) |
| `POST` | `/v1/chat/start` | Premium | [Создать новый чат](premium/post-v1-chat-start.md) |
| `POST` | `/v1/cluster/list` | FboSupplyRequest | [Информация о кластерах и их складах](fbosupplyrequest/post-v1-cluster-list.md) |
| `POST` | `/v1/delivery-method/list` | WarehouseAPI | [Список методов доставки склада](warehouseapi/post-v1-delivery-method-list.md) |
| `POST` | `/v1/delivery-method/return/settings/get` | WarehouseAPI | [Получить информацию по возвратным настройкам rFBS и rFBS Express](warehouseapi/post-v1-delivery-method-return-settings-get.md) |
| `POST` | `/v1/delivery/check` | DeliveryAPI | [Проверить доступность доставки для покупателя](deliveryapi/post-v1-delivery-check.md) |
| `POST` | `/v1/delivery/map` | DeliveryAPI | [Отрисовать точки на карте](deliveryapi/post-v1-delivery-map.md) |
| `POST` | `/v1/delivery/point/info` | DeliveryAPI | [Получить информацию о точке самовывоза](deliveryapi/post-v1-delivery-point-info.md) |
| `POST` | `/v1/delivery/point/list` | DeliveryAPI | [Получить список точек самовывоза](deliveryapi/post-v1-delivery-point-list.md) |
| `POST` | `/v1/description-category/attribute/values/search` | CategoryAPI | [Поиск по справочным значениям характеристики](categoryapi/post-v1-description-category-attribute-values-search.md) |
| `POST` | `/v1/description-category/attribute/values` | CategoryAPI | [Справочник значений характеристики](categoryapi/post-v1-description-category-attribute-values.md) |
| `POST` | `/v1/description-category/attribute` | CategoryAPI | [Список характеристик категории](categoryapi/post-v1-description-category-attribute.md) |
| `POST` | `/v1/description-category/dependent-attributes/values` | BetaMethod | [Получить возможные значения дочерней характеристики](betamethod/post-v1-description-category-dependent-attributes-values.md) |
| `POST` | `/v1/description-category/dependent-attributes` | BetaMethod | [Получить зависимые характеристики](betamethod/post-v1-description-category-dependent-attributes.md) |
| `POST` | `/v1/description-category/tree` | CategoryAPI | [Дерево категорий и типов товаров](categoryapi/post-v1-description-category-tree.md) |
| `POST` | `/v1/draft/crossdock/create` | FboSupplyRequest | [Создать черновик заявки на поставку кросс-докингом](fbosupplyrequest/post-v1-draft-crossdock-create.md) |
| `POST` | `/v1/draft/direct/create` | FboSupplyRequest | [Создать черновик заявки на прямую поставку](fbosupplyrequest/post-v1-draft-direct-create.md) |
| `POST` | `/v1/draft/multi-cluster/create` | FboSupplyRequest | [Создать черновик заявки на поставку для нескольких кластеров](fbosupplyrequest/post-v1-draft-multi-cluster-create.md) |
| `POST` | `/v1/fbp/act-from/create` | DeliveryFBP | [Сгенерировать акт приёмки](deliveryfbp/post-v1-fbp-act-from-create.md) |
| `POST` | `/v1/fbp/act-from/get` | DeliveryFBP | [Получить статус генерации акта приёмки](deliveryfbp/post-v1-fbp-act-from-get.md) |
| `POST` | `/v1/fbp/act-to/create` | DeliveryFBP | [Сгенерировать транспортную накладную](deliveryfbp/post-v1-fbp-act-to-create.md) |
| `POST` | `/v1/fbp/act-to/get` | DeliveryFBP | [Получить статус генерации транспортной накладной](deliveryfbp/post-v1-fbp-act-to-get.md) |
| `POST` | `/v1/fbp/archive/get` | DeliveryFBP | [Получить информацию о завершённой поставке](deliveryfbp/post-v1-fbp-archive-get.md) |
| `POST` | `/v1/fbp/archive/list` | DeliveryFBP | [Получить список завершённых поставок](deliveryfbp/post-v1-fbp-archive-list.md) |
| `POST` | `/v1/fbp/draft/direct/create` | DraftDirectFBP | [Создать черновик заявки на поставку без указания способа доставки](draftdirectfbp/post-v1-fbp-draft-direct-create.md) |
| `POST` | `/v1/fbp/draft/direct/delete` | DraftDirectFBP | [Удалить черновик заявки на поставку](draftdirectfbp/post-v1-fbp-draft-direct-delete.md) |
| `POST` | `/v1/fbp/draft/direct/product/validate` | DraftDirectFBP | [Проверить список товаров для склада партнёра](draftdirectfbp/post-v1-fbp-draft-direct-product-validate.md) |
| `POST` | `/v1/fbp/draft/direct/registrate` | DraftDirectFBP | [Перевести черновик в действующую поставку](draftdirectfbp/post-v1-fbp-draft-direct-registrate.md) |
| `POST` | `/v1/fbp/draft/direct/seller-dlv/create` | DraftDirectFBP | [Создать черновик с доставкой силами продавца](draftdirectfbp/post-v1-fbp-draft-direct-seller-dlv-create.md) |
| `POST` | `/v1/fbp/draft/direct/seller-dlv/edit` | DraftDirectFBP | [Обновить информацию о доставке силами продавца в черновике](draftdirectfbp/post-v1-fbp-draft-direct-seller-dlv-edit.md) |
| `POST` | `/v1/fbp/draft/direct/timeslot/edit` | DraftDirectFBP | [Отредактировать таймслот в черновике](draftdirectfbp/post-v1-fbp-draft-direct-timeslot-edit.md) |
| `POST` | `/v1/fbp/draft/direct/timeslot/get` | DraftDirectFBP | [Получить список таймслотов для прямой поставки](draftdirectfbp/post-v1-fbp-draft-direct-timeslot-get.md) |
| `POST` | `/v1/fbp/draft/direct/tpl-dlv/create` | DraftDirectFBP | [Создать черновик заявки на доставку сторонней транспортной компанией](draftdirectfbp/post-v1-fbp-draft-direct-tpl-dlv-create.md) |
| `POST` | `/v1/fbp/draft/direct/tpl-dlv/edit` | DraftDirectFBP | [Редактировать черновик поставки со способом доставки сторонней транспортной компанией](draftdirectfbp/post-v1-fbp-draft-direct-tpl-dlv-edit.md) |
| `POST` | `/v1/fbp/draft/drop-off/create` | DraftDropOffFBP | [Создать черновик для доставки в drop-off пункт](draftdropofffbp/post-v1-fbp-draft-drop-off-create.md) |
| `POST` | `/v1/fbp/draft/drop-off/delete` | DraftDropOffFBP | [Удалить черновик для доставки в drop-off пункт](draftdropofffbp/post-v1-fbp-draft-drop-off-delete.md) |
| `POST` | `/v1/fbp/draft/drop-off/dlv/edit` | DraftDropOffFBP | [Отредактировать детали доставки для drop-off черновика](draftdropofffbp/post-v1-fbp-draft-drop-off-dlv-edit.md) |
| `POST` | `/v1/fbp/draft/drop-off/point/list` | DraftDropOffFBP | [Получить список drop-off пунктов в провинции](draftdropofffbp/post-v1-fbp-draft-drop-off-point-list.md) |
| `POST` | `/v1/fbp/draft/drop-off/point/timetable` | DraftDropOffFBP | [Получить расписание работы drop-off пункта](draftdropofffbp/post-v1-fbp-draft-drop-off-point-timetable.md) |
| `POST` | `/v1/fbp/draft/drop-off/product/validate` | DraftDropOffFBP | [Проверить список товаров, которые склад партнёра может принять](draftdropofffbp/post-v1-fbp-draft-drop-off-product-validate.md) |
| `POST` | `/v1/fbp/draft/drop-off/province/list` | DraftDropOffFBP | [Получить список провинций](draftdropofffbp/post-v1-fbp-draft-drop-off-province-list.md) |
| `POST` | `/v1/fbp/draft/drop-off/registrate` | DraftDropOffFBP | [Перевести черновик в действующую поставку](draftdropofffbp/post-v1-fbp-draft-drop-off-registrate.md) |
| `POST` | `/v1/fbp/draft/get` | DeliveryFBPDraft | [Получить информацию о черновике поставки](deliveryfbpdraft/post-v1-fbp-draft-get.md) |
| `POST` | `/v1/fbp/draft/list` | DeliveryFBPDraft | [Список черновиков поставки](deliveryfbpdraft/post-v1-fbp-draft-list.md) |
| `POST` | `/v1/fbp/draft/pick-up/create` | DraftPickupFBP | [Создать черновик заявки на pick-up поставку](draftpickupfbp/post-v1-fbp-draft-pick-up-create.md) |
| `POST` | `/v1/fbp/draft/pick-up/delete` | DraftPickupFBP | [Отменить черновик заявки на pick-up поставку](draftpickupfbp/post-v1-fbp-draft-pick-up-delete.md) |
| `POST` | `/v1/fbp/draft/pick-up/dlv/edit` | DraftPickupFBP | [Изменить черновик заявки на pick-up поставку](draftpickupfbp/post-v1-fbp-draft-pick-up-dlv-edit.md) |
| `POST` | `/v1/fbp/draft/pick-up/product/validate` | DraftPickupFBP | [Провалидировать список товаров для pick-up поставки](draftpickupfbp/post-v1-fbp-draft-pick-up-product-validate.md) |
| `POST` | `/v1/fbp/draft/pick-up/registrate` | DraftPickupFBP | [Перевести черновик в действующую поставку](draftpickupfbp/post-v1-fbp-draft-pick-up-registrate.md) |
| `POST` | `/v1/fbp/label/create` | DeliveryFBP | [Cоздать задание на генерацию этикеток](deliveryfbp/post-v1-fbp-label-create.md) |
| `POST` | `/v1/fbp/label/get` | DeliveryFBP | [Получить статус задания на генерацию этикеток](deliveryfbp/post-v1-fbp-label-get.md) |
| `POST` | `/v1/fbp/order/direct/cancel` | OrderDirectFBP | [Отменить поставку](orderdirectfbp/post-v1-fbp-order-direct-cancel.md) |
| `POST` | `/v1/fbp/order/direct/seller-dlv/edit` | OrderDirectFBP | [Обновить информацию о доставке силами продавца](orderdirectfbp/post-v1-fbp-order-direct-seller-dlv-edit.md) |
| `POST` | `/v1/fbp/order/direct/timeslot/edit` | OrderDirectFBP | [Отредактировать таймслот в заявке на поставку](orderdirectfbp/post-v1-fbp-order-direct-timeslot-edit.md) |
| `POST` | `/v1/fbp/order/direct/timeslot/list` | OrderDirectFBP | [Получить список таймслотов для поставки](orderdirectfbp/post-v1-fbp-order-direct-timeslot-list.md) |
| `POST` | `/v1/fbp/order/drop-off/cancel` | OrderDropOffFBP | [Отменить поставку drop-off](orderdropofffbp/post-v1-fbp-order-drop-off-cancel.md) |
| `POST` | `/v1/fbp/order/drop-off/dlv/edit` | OrderDropOffFBP | [Отредактировать информацию о поставке на drop-off пункт](orderdropofffbp/post-v1-fbp-order-drop-off-dlv-edit.md) |
| `POST` | `/v1/fbp/order/drop-off/timetable` | OrderDropOffFBP | [Получить график работы drop-off пункта](orderdropofffbp/post-v1-fbp-order-drop-off-timetable.md) |
| `POST` | `/v1/fbp/order/get` | DeliveryFBP | [Получить информацию о конкретной поставке](deliveryfbp/post-v1-fbp-order-get.md) |
| `POST` | `/v1/fbp/order/list` | DeliveryFBP | [Получить список поставок](deliveryfbp/post-v1-fbp-order-list.md) |
| `POST` | `/v1/fbp/order/pick-up/cancel` | OrderPickupFBP | [Отменить pick-up поставку](orderpickupfbp/post-v1-fbp-order-pick-up-cancel.md) |
| `POST` | `/v1/fbp/order/pick-up/dlv/edit` | OrderPickupFBP | [Изменить данные о точке забора](orderpickupfbp/post-v1-fbp-order-pick-up-dlv-edit.md) |
| `POST` | `/v1/fbp/warehouse/list` | DeliveryFBPDraft | [Получить список партнёрских складов](deliveryfbpdraft/post-v1-fbp-warehouse-list.md) |
| `POST` | `/v1/fbs/posting/product/exemplar/update` | FBS&rFBSMarks | [Обновить данные экземпляров](fbs-rfbsmarks/post-v1-fbs-posting-product-exemplar-update.md) |
| `POST` | `/v1/finance/accrual/by-day` | BetaMethod | [Получить начисления за день](betamethod/post-v1-finance-accrual-by-day.md) |
| `POST` | `/v1/finance/accrual/postings` | BetaMethod | [Получить начисления по отправлениям](betamethod/post-v1-finance-accrual-postings.md) |
| `POST` | `/v1/finance/accrual/types` | BetaMethod | [Получить справочник начислений](betamethod/post-v1-finance-accrual-types.md) |
| `POST` | `/v1/finance/balance` | BetaMethod | [Получить отчёт о балансе](betamethod/post-v1-finance-balance.md) |
| `POST` | `/v1/finance/cash-flow-statement/list` | ReportAPI | [Финансовый отчёт](reportapi/post-v1-finance-cash-flow-statement-list.md) |
| `POST` | `/v1/finance/compensation` | FinanceAPI | [Отчёт о компенсациях](financeapi/post-v1-finance-compensation.md) |
| `POST` | `/v1/finance/decompensation` | FinanceAPI | [Отчёт о декомпенсациях](financeapi/post-v1-finance-decompensation.md) |
| `POST` | `/v1/finance/document-b2b-sales/json` | FinanceAPI | [Реестр продаж юридическим лицам в JSON-формате](financeapi/post-v1-finance-document-b2b-sales-json.md) |
| `POST` | `/v1/finance/document-b2b-sales` | FinanceAPI | [Реестр продаж юридическим лицам](financeapi/post-v1-finance-document-b2b-sales.md) |
| `POST` | `/v1/finance/mutual-settlement` | FinanceAPI | [Отчёт о взаиморасчётах](financeapi/post-v1-finance-mutual-settlement.md) |
| `POST` | `/v1/finance/products/buyout` | FinanceAPI | [Отчёт о выкупленных товарах](financeapi/post-v1-finance-products-buyout.md) |
| `POST` | `/v1/finance/realization/by-day` | Premium | [Отчёт о реализации товаров за день](premium/post-v1-finance-realization-by-day.md) |
| `POST` | `/v1/finance/realization/posting` | FinanceAPI | [Позаказный отчёт о реализации товаров](financeapi/post-v1-finance-realization-posting.md) |
| `POST` | `/v1/invoice/delete` | SupplierAPI | [Удалить ссылку на счёт-фактуру](supplierapi/post-v1-invoice-delete.md) |
| `POST` | `/v1/invoice/file/upload` | SupplierAPI | [Загрузка счёта-фактуры](supplierapi/post-v1-invoice-file-upload.md) |
| `POST` | `/v1/notification/check` | Notification | [Проверить URL-адрес для уведомлений](notification/post-v1-notification-check.md) |
| `POST` | `/v1/notification/delete` | Notification | [Удалить URL-адрес для уведомлений](notification/post-v1-notification-delete.md) |
| `POST` | `/v1/notification/enable` | Notification | [Включить или выключить уведомления на URL-адрес](notification/post-v1-notification-enable.md) |
| `POST` | `/v1/notification/list` | Notification | [Получить информацию по подключённым URL-адресам](notification/post-v1-notification-list.md) |
| `POST` | `/v1/notification/push-type/list` | Notification | [Получить типы пуш-уведомлений](notification/post-v1-notification-push-type-list.md) |
| `POST` | `/v1/notification/set` | Notification | [Подключить URL-адрес для уведомлений](notification/post-v1-notification-set.md) |
| `POST` | `/v1/notification/update` | Notification | [Изменить URL-адрес для уведомлений](notification/post-v1-notification-update.md) |
| `POST` | `/v1/order/cancel/check` | OrderAPI | [Проверить возможность отмены заказа](orderapi/post-v1-order-cancel-check.md) |
| `POST` | `/v1/order/cancel/status` | OrderAPI | [Получить статус отмены заказа](orderapi/post-v1-order-cancel-status.md) |
| `POST` | `/v1/order/cancel` | OrderAPI | [Отменить заказ](orderapi/post-v1-order-cancel.md) |
| `POST` | `/v1/pass/list` | Pass | [Список пропусков](pass/post-v1-pass-list.md) |
| `POST` | `/v1/polygon/bind` | PolygonAPI | [Свяжите метод доставки с полигоном доставки](polygonapi/post-v1-polygon-bind.md) |
| `POST` | `/v1/polygon/create` | PolygonAPI | [Создайте полигон доставки](polygonapi/post-v1-polygon-create.md) |
| `POST` | `/v1/polygon/delete` | PolygonAPI | [Удалить полигон из области доставки](polygonapi/post-v1-polygon-delete.md) |
| `POST` | `/v1/polygon/list` | PolygonAPI | [Получить список установленных полигонов на метод доставки](polygonapi/post-v1-polygon-list.md) |
| `POST` | `/v1/polygon/time/coordinates/update` | PolygonAPI | [Обновить координаты полигона доставки](polygonapi/post-v1-polygon-time-coordinates-update.md) |
| `POST` | `/v1/polygon/time/set` | PolygonAPI | [Установить новое время доставки в полигоне](polygonapi/post-v1-polygon-time-set.md) |
| `POST` | `/v1/posting/cancel/status` | FboPostingAPI | [Проверить статус отмены отправления](fbopostingapi/post-v1-posting-cancel-status.md) |
| `POST` | `/v1/posting/cancel` | FboPostingAPI | [Отменить отправление из заказа](fbopostingapi/post-v1-posting-cancel.md) |
| `POST` | `/v1/posting/carriage-available/list` | DeliveryFBS | [Список доступных перевозок](deliveryfbs/post-v1-posting-carriage-available-list.md) |
| `POST` | `/v1/posting/cutoff/set` | DeliveryrFBS | [Уточнить дату отгрузки отправления](deliveryrfbs/post-v1-posting-cutoff-set.md) |
| `POST` | `/v1/posting/digital/codes/upload` | Digital | [Загрузить коды цифровых товаров для отправления](digital/post-v1-posting-digital-codes-upload.md) |
| `POST` | `/v1/posting/digital/list` | Digital | [Получить список отправлений](digital/post-v1-posting-digital-list.md) |
| `POST` | `/v1/posting/fbo/cancel-reason/list` | FBO | [Причины отмены отправлений по схеме FBO](fbo/post-v1-posting-fbo-cancel-reason-list.md) |
| `POST` | `/v1/posting/fbp/get` | BetaMethod | [Получить информацию об отправлении по идентификатору](betamethod/post-v1-posting-fbp-get.md) |
| `POST` | `/v1/posting/fbp/list` | DeliveryFBP | [Получить список отправлений](deliveryfbp/post-v1-posting-fbp-list.md) |
| `POST` | `/v1/posting/fbs/cancel-reason` | FBS | [Причины отмены отправления](fbs/post-v1-posting-fbs-cancel-reason.md) |
| `POST` | `/v1/posting/fbs/package-label/create` | FBS | [Создать задание на выгрузку этикеток](fbs/post-v1-posting-fbs-package-label-create.md) |
| `POST` | `/v1/posting/fbs/package-label/get` | FBS | [Получить файл с этикетками](fbs/post-v1-posting-fbs-package-label-get.md) |
| `POST` | `/v1/posting/fbs/pick-up-code/verify` | FBS | [Проверить код курьера](fbs/post-v1-posting-fbs-pick-up-code-verify.md) |
| `POST` | `/v1/posting/fbs/product/traceable/attribute` | DeliveryFBS | [Получить список незаполненных атрибутов для прослеживаемых товаров](deliveryfbs/post-v1-posting-fbs-product-traceable-attribute.md) |
| `POST` | `/v1/posting/fbs/restrictions` | FBS | [Получить ограничения пункта приёма](fbs/post-v1-posting-fbs-restrictions.md) |
| `POST` | `/v1/posting/fbs/split` | DeliveryFBS | [Разделить заказ на отправления без сборки](deliveryfbs/post-v1-posting-fbs-split.md) |
| `POST` | `/v1/posting/fbs/timeslot/change-restrictions` | DeliveryrFBS | [Доступные даты для переноса доставки](deliveryrfbs/post-v1-posting-fbs-timeslot-change-restrictions.md) |
| `POST` | `/v1/posting/fbs/timeslot/set` | DeliveryrFBS | [Перенести дату доставки](deliveryrfbs/post-v1-posting-fbs-timeslot-set.md) |
| `POST` | `/v1/posting/fbs/traceable/split` | DeliveryFBS | [Разделить отправление с прослеживаемыми товарами](deliveryfbs/post-v1-posting-fbs-traceable-split.md) |
| `POST` | `/v1/posting/global/etgb` | FBS | [Таможенные декларации ETGB](fbs/post-v1-posting-global-etgb.md) |
| `POST` | `/v1/posting/marks` | FboPostingAPI | [Получить маркировки экземпляров из отправления](fbopostingapi/post-v1-posting-marks.md) |
| `POST` | `/v1/posting/unpaid-legal/product/list` | FBS | [Список неоплаченных товаров, заказанных юридическими лицами](fbs/post-v1-posting-unpaid-legal-product-list.md) |
| `POST` | `/v1/pricing-strategy/competitors/list` | PricingStrategyAPI | [Список конкурентов](pricingstrategyapi/post-v1-pricing-strategy-competitors-list.md) |
| `POST` | `/v1/pricing-strategy/create` | PricingStrategyAPI | [Создать стратегию](pricingstrategyapi/post-v1-pricing-strategy-create.md) |
| `POST` | `/v1/pricing-strategy/delete` | PricingStrategyAPI | [Удалить стратегию](pricingstrategyapi/post-v1-pricing-strategy-delete.md) |
| `POST` | `/v1/pricing-strategy/info` | PricingStrategyAPI | [Информация о стратегии](pricingstrategyapi/post-v1-pricing-strategy-info.md) |
| `POST` | `/v1/pricing-strategy/list` | PricingStrategyAPI | [Список стратегий](pricingstrategyapi/post-v1-pricing-strategy-list.md) |
| `POST` | `/v1/pricing-strategy/product/info` | PricingStrategyAPI | [Цена товара у конкурента](pricingstrategyapi/post-v1-pricing-strategy-product-info.md) |
| `POST` | `/v1/pricing-strategy/products/add` | PricingStrategyAPI | [Добавить товары в стратегию](pricingstrategyapi/post-v1-pricing-strategy-products-add.md) |
| `POST` | `/v1/pricing-strategy/products/delete` | PricingStrategyAPI | [Удалить товары из стратегии](pricingstrategyapi/post-v1-pricing-strategy-products-delete.md) |
| `POST` | `/v1/pricing-strategy/products/list` | PricingStrategyAPI | [Список товаров в стратегии](pricingstrategyapi/post-v1-pricing-strategy-products-list.md) |
| `POST` | `/v1/pricing-strategy/status` | PricingStrategyAPI | [Изменить статус стратегии](pricingstrategyapi/post-v1-pricing-strategy-status.md) |
| `POST` | `/v1/pricing-strategy/strategy-ids-by-product-ids` | PricingStrategyAPI | [Список идентификаторов стратегий](pricingstrategyapi/post-v1-pricing-strategy-strategy-ids-by-product-ids.md) |
| `POST` | `/v1/pricing-strategy/update` | PricingStrategyAPI | [Обновить стратегию](pricingstrategyapi/post-v1-pricing-strategy-update.md) |
| `POST` | `/v1/product/action/timer/status` | Prices&StocksAPI | [Получить статус установленного таймера](prices-stocksapi/post-v1-product-action-timer-status.md) |
| `POST` | `/v1/product/action/timer/update` | Prices&StocksAPI | [Обновление таймера актуальности минимальной цены](prices-stocksapi/post-v1-product-action-timer-update.md) |
| `POST` | `/v1/product/archive` | ProductAPI | [Перенести товар в архив](productapi/post-v1-product-archive.md) |
| `POST` | `/v1/product/attributes/update` | ProductAPI | [Обновить характеристики товара](productapi/post-v1-product-attributes-update.md) |
| `POST` | `/v1/product/certificate/bind` | CertificationAPI | [Привязать сертификат к товару](certificationapi/post-v1-product-certificate-bind.md) |
| `POST` | `/v1/product/certificate/create` | CertificationAPI | [Добавить сертификаты для товаров](certificationapi/post-v1-product-certificate-create.md) |
| `POST` | `/v1/product/certificate/delete` | CertificationAPI | [Удалить сертификат](certificationapi/post-v1-product-certificate-delete.md) |
| `POST` | `/v1/product/certificate/info` | CertificationAPI | [Информация о сертификате](certificationapi/post-v1-product-certificate-info.md) |
| `POST` | `/v1/product/certificate/list` | CertificationAPI | [Список сертификатов](certificationapi/post-v1-product-certificate-list.md) |
| `POST` | `/v1/product/certificate/product_status/list` | CertificationAPI | [Список возможных статусов товаров](certificationapi/post-v1-product-certificate-product-status-list.md) |
| `POST` | `/v1/product/certificate/products/list` | CertificationAPI | [Список товаров, привязанных к сертификату](certificationapi/post-v1-product-certificate-products-list.md) |
| `POST` | `/v1/product/certificate/rejection_reasons/list` | CertificationAPI | [Возможные причины отклонения сертификата](certificationapi/post-v1-product-certificate-rejection-reasons-list.md) |
| `POST` | `/v1/product/certificate/status/list` | CertificationAPI | [Возможные статусы сертификатов](certificationapi/post-v1-product-certificate-status-list.md) |
| `POST` | `/v1/product/certificate/unbind` | CertificationAPI | [Отвязать товар от сертификата](certificationapi/post-v1-product-certificate-unbind.md) |
| `POST` | `/v1/product/certification/list` | CertificationAPI | [Список сертифицируемых категорий](certificationapi/post-v1-product-certification-list.md) |
| `POST` | `/v1/product/digital/stocks/import` | Digital | [Обновить количество цифровых товаров](digital/post-v1-product-digital-stocks-import.md) |
| `POST` | `/v1/product/import-by-sku` | ProductAPI | [Создать товар по SKU](productapi/post-v1-product-import-by-sku.md) |
| `POST` | `/v1/product/import/info` | ProductAPI | [Узнать статус добавления или обновления товара](productapi/post-v1-product-import-info.md) |
| `POST` | `/v1/product/import/prices` | Prices&StocksAPI | [Обновить цену](prices-stocksapi/post-v1-product-import-prices.md) |
| `POST` | `/v1/product/info/description` | ProductAPI | [Получить описание товара](productapi/post-v1-product-info-description.md) |
| `POST` | `/v1/product/info/discounted` | Prices&StocksAPI | [Узнать информацию об уценке и основном товаре по SKU уценённого товара](prices-stocksapi/post-v1-product-info-discounted.md) |
| `POST` | `/v1/product/info/stocks-by-warehouse/fbo` | ProductAPI | [Получить информацию о стоках на складах FBO](productapi/post-v1-product-info-stocks-by-warehouse-fbo.md) |
| `POST` | `/v1/product/info/stocks-by-warehouse/fbs` | Prices&StocksAPI | [Информация об остатках на складах продавца (FBS и rFBS)](prices-stocksapi/post-v1-product-info-stocks-by-warehouse-fbs.md) |
| `POST` | `/v1/product/info/subscription` | ProductAPI | [Количество подписавшихся на товар пользователей](productapi/post-v1-product-info-subscription.md) |
| `POST` | `/v1/product/info/warehouse/stocks` | Prices&StocksAPI | [Получить информацию по остаткам на складе FBS и rFBS](prices-stocksapi/post-v1-product-info-warehouse-stocks.md) |
| `POST` | `/v1/product/info/wrong-volume` | ProductAPI | [Список товаров с некорректными ОВХ](productapi/post-v1-product-info-wrong-volume.md) |
| `POST` | `/v1/product/pictures/import` | ProductAPI | [Загрузить или обновить изображения товара](productapi/post-v1-product-pictures-import.md) |
| `POST` | `/v1/product/placement-zone/info` | CategoryAPI | [Получить зоны размещения товаров по SKU перед поставкой](categoryapi/post-v1-product-placement-zone-info.md) |
| `POST` | `/v1/product/prices/details` | Premium | [Получить подробную информацию о ценах товаров](premium/post-v1-product-prices-details.md) |
| `POST` | `/v1/product/quant/info` | Quants | [Информация об эконом-товаре](quants/post-v1-product-quant-info.md) |
| `POST` | `/v1/product/quant/list` | Quants | [Список эконом-товаров](quants/post-v1-product-quant-list.md) |
| `POST` | `/v1/product/rating-by-sku` | ProductAPI | [Получить контент-рейтинг товаров по SKU](productapi/post-v1-product-rating-by-sku.md) |
| `POST` | `/v1/product/related-sku/get` | ProductAPI | [Получить связанные SKU](productapi/post-v1-product-related-sku-get.md) |
| `POST` | `/v1/product/stairway-discount/by-quantity/get` | BetaMethod | [Получить информацию о скидке от количества](betamethod/post-v1-product-stairway-discount-by-quantity-get.md) |
| `POST` | `/v1/product/stairway-discount/by-quantity/set` | BetaMethod | [Управлять скидкой от количества](betamethod/post-v1-product-stairway-discount-by-quantity-set.md) |
| `POST` | `/v1/product/unarchive` | ProductAPI | [Вернуть товар из архива](productapi/post-v1-product-unarchive.md) |
| `POST` | `/v1/product/update/discount` | Prices&StocksAPI | [Установить скидку на уценённый товар](prices-stocksapi/post-v1-product-update-discount.md) |
| `POST` | `/v1/product/update/offer-id` | ProductAPI | [Изменить артикулы товаров из системы продавца](productapi/post-v1-product-update-offer-id.md) |
| `POST` | `/v1/product/visibility/info` | BetaMethod | [Получить информацию о видимости товара](betamethod/post-v1-product-visibility-info.md) |
| `POST` | `/v1/product/visibility/set` | BetaMethod | [Настроить видимость товара на витрине Ozon и Ozon Селект](betamethod/post-v1-product-visibility-set.md) |
| `POST` | `/v1/question/answer/create` | Questions&Answers | [Создать ответ на вопрос](questions-answers/post-v1-question-answer-create.md) |
| `POST` | `/v1/question/answer/delete` | Questions&Answers | [Удалить ответ на вопрос](questions-answers/post-v1-question-answer-delete.md) |
| `POST` | `/v1/question/answer/list` | Questions&Answers | [Список ответов на вопрос](questions-answers/post-v1-question-answer-list.md) |
| `POST` | `/v1/question/change-status` | Questions&Answers | [Изменить статус вопросов](questions-answers/post-v1-question-change-status.md) |
| `POST` | `/v1/question/count` | Questions&Answers | [Количество вопросов по статусам](questions-answers/post-v1-question-count.md) |
| `POST` | `/v1/question/info` | Questions&Answers | [Информация о вопросе](questions-answers/post-v1-question-info.md) |
| `POST` | `/v1/question/list` | Questions&Answers | [Список вопросов](questions-answers/post-v1-question-list.md) |
| `POST` | `/v1/question/top-sku` | Questions&Answers | [Товары с наибольшим количеством вопросов](questions-answers/post-v1-question-top-sku.md) |
| `POST` | `/v1/rating/history` | SellerRating | [Получить информацию о рейтингах продавца за период](sellerrating/post-v1-rating-history.md) |
| `POST` | `/v1/rating/index/fbs/info` | SellerRating | [Получить индекс ошибок FBS и rFBS](sellerrating/post-v1-rating-index-fbs-info.md) |
| `POST` | `/v1/rating/index/fbs/posting/list` | SellerRating | [Список отправлений, которые повлияли на индекс ошибок FBS и rFBS](sellerrating/post-v1-rating-index-fbs-posting-list.md) |
| `POST` | `/v1/rating/summary` | SellerRating | [Получить информацию о текущих рейтингах продавца](sellerrating/post-v1-rating-summary.md) |
| `POST` | `/v1/receipts/get` | Receipt | [Получить чек в формате PDF](receipt/post-v1-receipts-get.md) |
| `POST` | `/v1/receipts/seller/list` | Receipt | [Получить список чеков продавца](receipt/post-v1-receipts-seller-list.md) |
| `POST` | `/v1/receipts/upload` | Receipt | [Загрузить чек](receipt/post-v1-receipts-upload.md) |
| `POST` | `/v1/removal/from-stock/list` | BetaMethod | [Отчёт по вывозу и утилизации со стока FBO](betamethod/post-v1-removal-from-stock-list.md) |
| `POST` | `/v1/removal/from-supply/list` | BetaMethod | [Отчёт по вывозу и утилизации с поставки FBO](betamethod/post-v1-removal-from-supply-list.md) |
| `POST` | `/v1/report/discounted/create` | ReportAPI | [Отчёт об уценённых товарах](reportapi/post-v1-report-discounted-create.md) |
| `POST` | `/v1/report/info` | ReportAPI | [Информация об отчёте](reportapi/post-v1-report-info.md) |
| `POST` | `/v1/report/list` | ReportAPI | [Список отчётов](reportapi/post-v1-report-list.md) |
| `POST` | `/v1/report/marked-products-sales/create` | ReportAPI | [Сгенерировать отчёт по продажам товаров с маркировкой](reportapi/post-v1-report-marked-products-sales-create.md) |
| `POST` | `/v1/report/placement/by-products/create` | ReportAPI | [Получить отчёт о стоимости размещения по товарам](reportapi/post-v1-report-placement-by-products-create.md) |
| `POST` | `/v1/report/placement/by-supplies/create` | ReportAPI | [Получить отчёт о стоимости размещения по поставкам](reportapi/post-v1-report-placement-by-supplies-create.md) |
| `POST` | `/v1/report/postings/create` | ReportAPI | [Отчёт об отправлениях](reportapi/post-v1-report-postings-create.md) |
| `POST` | `/v1/report/products/create` | ReportAPI | [Отчёт по товарам](reportapi/post-v1-report-products-create.md) |
| `POST` | `/v1/report/realization/posting/create` | BetaMethod | [Получить позаказный отчёт о реализации товаров](betamethod/post-v1-report-realization-posting-create.md) |
| `POST` | `/v1/report/warehouse/stock` | ReportAPI | [Отчёт об остатках на FBS-складе](reportapi/post-v1-report-warehouse-stock.md) |
| `POST` | `/v1/return/giveout/barcode-reset` | ReturnAPI | [Сгенерировать новый штрихкод](returnapi/post-v1-return-giveout-barcode-reset.md) |
| `POST` | `/v1/return/giveout/barcode` | ReturnAPI | [Значение штрихкода для возвратных отгрузок](returnapi/post-v1-return-giveout-barcode.md) |
| `POST` | `/v1/return/giveout/get-pdf` | ReturnAPI | [Штрихкод для получения возвратной отгрузки в формате PDF](returnapi/post-v1-return-giveout-get-pdf.md) |
| `POST` | `/v1/return/giveout/get-png` | ReturnAPI | [Штрихкод для получения возвратной отгрузки в формате PNG](returnapi/post-v1-return-giveout-get-png.md) |
| `POST` | `/v1/return/giveout/info` | ReturnAPI | [Информация о возвратной отгрузке](returnapi/post-v1-return-giveout-info.md) |
| `POST` | `/v1/return/giveout/is-enabled` | ReturnAPI | [Проверить возможность получения возвратных отгрузок по штрихкоду](returnapi/post-v1-return-giveout-is-enabled.md) |
| `POST` | `/v1/return/giveout/list` | ReturnAPI | [Список возвратных отгрузок](returnapi/post-v1-return-giveout-list.md) |
| `POST` | `/v1/return/pass/create` | Pass | [Создать пропуск для возврата](pass/post-v1-return-pass-create.md) |
| `POST` | `/v1/return/pass/delete` | Pass | [Удалить пропуск для возврата](pass/post-v1-return-pass-delete.md) |
| `POST` | `/v1/return/pass/update` | Pass | [Обновить пропуск для возврата](pass/post-v1-return-pass-update.md) |
| `POST` | `/v1/returns/company/fbs/info` | ReturnAPI | [Количество возвратов FBS](returnapi/post-v1-returns-company-fbs-info.md) |
| `POST` | `/v1/returns/list` | ReturnsAPI | [Информация о возвратах FBO и FBS](returnsapi/post-v1-returns-list.md) |
| `POST` | `/v1/returns/rfbs/action/set` | RFBSReturnsAPI | [Передать доступные действия для rFBS возвратов](rfbsreturnsapi/post-v1-returns-rfbs-action-set.md) |
| `POST` | `/v1/returns/settings/utilization/history` | ReturnsAPI | [Получить историю изменений автоутилизации](returnsapi/post-v1-returns-settings-utilization-history.md) |
| `POST` | `/v1/returns/settings/utilization/info` | ReturnsAPI | [Получить настройки автоутилизации](returnsapi/post-v1-returns-settings-utilization-info.md) |
| `POST` | `/v1/returns/settings/utilization/update` | ReturnsAPI | [Обновить настройки автоутилизации](returnsapi/post-v1-returns-settings-utilization-update.md) |
| `POST` | `/v1/review/change-status` | ReviewAPI | [Изменить статус отзывов](reviewapi/post-v1-review-change-status.md) |
| `POST` | `/v1/review/comment/create` | ReviewAPI | [Оставить комментарий на отзыв](reviewapi/post-v1-review-comment-create.md) |
| `POST` | `/v1/review/comment/delete` | ReviewAPI | [Удалить комментарий на отзыв](reviewapi/post-v1-review-comment-delete.md) |
| `POST` | `/v1/review/comment/list` | ReviewAPI | [Получить список комментариев на отзыв](reviewapi/post-v1-review-comment-list.md) |
| `POST` | `/v1/review/count` | ReviewAPI | [Количество отзывов по статусам](reviewapi/post-v1-review-count.md) |
| `POST` | `/v1/review/info` | ReviewAPI | [Получить информацию об отзыве](reviewapi/post-v1-review-info.md) |
| `POST` | `/v1/review/list` | ReviewAPI | [Получить список отзывов](reviewapi/post-v1-review-list.md) |
| `POST` | `/v1/roles` | APIkey | [Получить список ролей и методов по API-ключу](apikey/post-v1-roles.md) |
| `POST` | `/v1/search-queries/text` | Premium | [Получить список поисковых запросов по тексту](premium/post-v1-search-queries-text.md) |
| `POST` | `/v1/search-queries/top` | Premium | [Получить список популярных поисковых запросов](premium/post-v1-search-queries-top.md) |
| `POST` | `/v1/seller-actions/archive` | SellerActions | [Перенести акцию в архив](selleractions/post-v1-seller-actions-archive.md) |
| `POST` | `/v1/seller-actions/change-activity` | SellerActions | [Включить или выключить акцию](selleractions/post-v1-seller-actions-change-activity.md) |
| `POST` | `/v1/seller-actions/create/discount-with-condition` | SellerActions | [Создать акцию с механикой «Скидка от суммы заказа»](selleractions/post-v1-seller-actions-create-discount-with-condition.md) |
| `POST` | `/v1/seller-actions/create/discount` | SellerActions | [Создать акцию с механикой «Скидка»](selleractions/post-v1-seller-actions-create-discount.md) |
| `POST` | `/v1/seller-actions/create/installment` | SellerActions | [Создать акцию с механикой «Беспроцентная рассрочка»](selleractions/post-v1-seller-actions-create-installment.md) |
| `POST` | `/v1/seller-actions/create/multi-level-discount` | SellerActions | [Создать акцию с механикой «Многоуровневая скидка от суммы»](selleractions/post-v1-seller-actions-create-multi-level-discount.md) |
| `POST` | `/v1/seller-actions/create/voucher` | SellerActions | [Создать акцию с механикой «Скидка по промокоду»](selleractions/post-v1-seller-actions-create-voucher.md) |
| `POST` | `/v1/seller-actions/list` | SellerActions | [Получить список акций](selleractions/post-v1-seller-actions-list.md) |
| `POST` | `/v1/seller-actions/products/add` | SellerActions | [Добавить товары в акцию](selleractions/post-v1-seller-actions-products-add.md) |
| `POST` | `/v1/seller-actions/products/candidates` | SellerActions | [Получить список доступных для акции товаров](selleractions/post-v1-seller-actions-products-candidates.md) |
| `POST` | `/v1/seller-actions/products/delete` | SellerActions | [Удалить товары из акции](selleractions/post-v1-seller-actions-products-delete.md) |
| `POST` | `/v1/seller-actions/products/list` | SellerActions | [Получить список участвующих в акции товаров](selleractions/post-v1-seller-actions-products-list.md) |
| `POST` | `/v1/seller-actions/update/discount-with-condition` | SellerActions | [Обновить акцию с механикой «Скидка от суммы заказа»](selleractions/post-v1-seller-actions-update-discount-with-condition.md) |
| `POST` | `/v1/seller-actions/update/discount` | SellerActions | [Обновить акцию с механикой «Скидка»](selleractions/post-v1-seller-actions-update-discount.md) |
| `POST` | `/v1/seller-actions/update/installment` | SellerActions | [Обновить акцию с механикой «Беспроцентная рассрочка»](selleractions/post-v1-seller-actions-update-installment.md) |
| `POST` | `/v1/seller-actions/update/multi-level-discount` | SellerActions | [Обновить акцию с механикой «Многоуровневая скидка от суммы»](selleractions/post-v1-seller-actions-update-multi-level-discount.md) |
| `POST` | `/v1/seller-actions/update/voucher` | SellerActions | [Обновить акцию с механикой «Скидка по промокоду»](selleractions/post-v1-seller-actions-update-voucher.md) |
| `POST` | `/v1/seller-actions/voucher/get` | SellerActions | [Получить файл с промокодами в формате CSV](selleractions/post-v1-seller-actions-voucher-get.md) |
| `POST` | `/v1/seller/info` | SellerInfo | [Информация о кабинете продавца](sellerinfo/post-v1-seller-info.md) |
| `POST` | `/v1/seller/ozon-logistics/info` | SellerInfo | [Информация о подключении Ozon Доставки](sellerinfo/post-v1-seller-ozon-logistics-info.md) |
| `POST` | `/v1/supply-order/act/accept/status` | SupplyOrderAPI | [Получить статус согласования акта](supplyorderapi/post-v1-supply-order-act-accept-status.md) |
| `POST` | `/v1/supply-order/act/accept` | SupplyOrderAPI | [Согласовать акт](supplyorderapi/post-v1-supply-order-act-accept.md) |
| `POST` | `/v1/supply-order/act/product/get` | SupplyOrderAPI | [Получить информацию о товарах в акте](supplyorderapi/post-v1-supply-order-act-product-get.md) |
| `POST` | `/v1/supply-order/act/summary/get` | SupplyOrderAPI | [Получить информацию об акте](supplyorderapi/post-v1-supply-order-act-summary-get.md) |
| `POST` | `/v1/supply-order/bundle` | FBO | [Состав поставки или заявки на поставку](fbo/post-v1-supply-order-bundle.md) |
| `POST` | `/v1/supply-order/cancel/status` | FboSupplyRequest | [Получить статус отмены заявки на поставку](fbosupplyrequest/post-v1-supply-order-cancel-status.md) |
| `POST` | `/v1/supply-order/cancel` | FboSupplyRequest | [Отменить заявку на поставку](fbosupplyrequest/post-v1-supply-order-cancel.md) |
| `POST` | `/v1/supply-order/content/update/status` | FboSupplyRequest | [Информация о статусе редактирования товарного состава](fbosupplyrequest/post-v1-supply-order-content-update-status.md) |
| `POST` | `/v1/supply-order/content/update/validation` | FboSupplyRequest | [Проверить новый товарный состав](fbosupplyrequest/post-v1-supply-order-content-update-validation.md) |
| `POST` | `/v1/supply-order/content/update` | FboSupplyRequest | [Редактирование товарного состава](fbosupplyrequest/post-v1-supply-order-content-update.md) |
| `POST` | `/v1/supply-order/details` | FBO | [Получить подробную информацию о заявке на поставку](fbo/post-v1-supply-order-details.md) |
| `POST` | `/v1/supply-order/pass/create` | FBO | [Указать данные о водителе и автомобиле](fbo/post-v1-supply-order-pass-create.md) |
| `POST` | `/v1/supply-order/pass/status` | FBO | [Статус ввода данных о водителе и автомобиле](fbo/post-v1-supply-order-pass-status.md) |
| `POST` | `/v1/supply-order/status/counter` | FBO | [Количество заявок по статусам](fbo/post-v1-supply-order-status-counter.md) |
| `POST` | `/v1/supply-order/timeslot/get` | FBO | [Интервалы поставки](fbo/post-v1-supply-order-timeslot-get.md) |
| `POST` | `/v1/supply-order/timeslot/status` | FBO | [Статус интервала поставки](fbo/post-v1-supply-order-timeslot-status.md) |
| `POST` | `/v1/supply-order/timeslot/update` | FBO | [Обновить интервал поставки](fbo/post-v1-supply-order-timeslot-update.md) |
| `POST` | `/v1/warehouse/archive` | WarehouseAPI | [Перенести склад в архив](warehouseapi/post-v1-warehouse-archive.md) |
| `POST` | `/v1/warehouse/erfbs/aggregator/create` | rFBSWarehouseSetup | [Создать склад с методом доставки «Партнёры Ozon»](rfbswarehousesetup/post-v1-warehouse-erfbs-aggregator-create.md) |
| `POST` | `/v1/warehouse/erfbs/aggregator/delivery-method/update` | rFBSWarehouseSetup | [Обновить метод доставки «Партнёры Ozon»](rfbswarehousesetup/post-v1-warehouse-erfbs-aggregator-delivery-method-update.md) |
| `POST` | `/v1/warehouse/erfbs/non-integrated/create` | rFBSWarehouseSetup | [Создать склад с методом доставки «Вы или сторонняя служба»](rfbswarehousesetup/post-v1-warehouse-erfbs-non-integrated-create.md) |
| `POST` | `/v1/warehouse/erfbs/non-integrated/delivery-method/update` | rFBSWarehouseSetup | [Обновить метод доставки «Вы или сторонняя служба»](rfbswarehousesetup/post-v1-warehouse-erfbs-non-integrated-delivery-method-update.md) |
| `POST` | `/v1/warehouse/erfbs/update` | rFBSWarehouseSetup | [Обновить склад](rfbswarehousesetup/post-v1-warehouse-erfbs-update.md) |
| `POST` | `/v1/warehouse/fbo/list` | FboSupplyRequest | [Поиск точек для отгрузки поставки](fbosupplyrequest/post-v1-warehouse-fbo-list.md) |
| `POST` | `/v1/warehouse/fbo/seller/list` | FboSupplyRequest | [Получить список складов продавца](fbosupplyrequest/post-v1-warehouse-fbo-seller-list.md) |
| `POST` | `/v1/warehouse/fbs/create/drop-off/list` | FBSWarehouseSetup | [Получить список drop-off пунктов для создания склада](fbswarehousesetup/post-v1-warehouse-fbs-create-drop-off-list.md) |
| `POST` | `/v1/warehouse/fbs/create/drop-off/timeslot/list` | FBSWarehouseSetup | [Получить список таймслотов для создания склада с отгрузкой drop-off](fbswarehousesetup/post-v1-warehouse-fbs-create-drop-off-timeslot-list.md) |
| `POST` | `/v1/warehouse/fbs/create/pick-up/timeslot/list` | FBSWarehouseSetup | [Получить список таймслотов для создания склада с отгрузкой pick-up](fbswarehousesetup/post-v1-warehouse-fbs-create-pick-up-timeslot-list.md) |
| `POST` | `/v1/warehouse/fbs/create/return-point/list` | FBSWarehouseSetup | [Получить список пунктов возврата для создания склада](fbswarehousesetup/post-v1-warehouse-fbs-create-return-point-list.md) |
| `POST` | `/v1/warehouse/fbs/create` | FBSWarehouseSetup | [Создать склад](fbswarehousesetup/post-v1-warehouse-fbs-create.md) |
| `POST` | `/v1/warehouse/fbs/first-mile/update` | FBSWarehouseSetup | [Обновить первую милю](fbswarehousesetup/post-v1-warehouse-fbs-first-mile-update.md) |
| `POST` | `/v1/warehouse/fbs/pickup/courier/cancel` | FBSWarehouseSetup | [Отменить вызов курьера на забор отгрузки pick-up](fbswarehousesetup/post-v1-warehouse-fbs-pickup-courier-cancel.md) |
| `POST` | `/v1/warehouse/fbs/pickup/courier/create` | FBSWarehouseSetup | [Создать вызов курьера на забор отгрузки pick-up](fbswarehousesetup/post-v1-warehouse-fbs-pickup-courier-create.md) |
| `POST` | `/v1/warehouse/fbs/pickup/history/list` | FBSWarehouseSetup | [Получить историю отгрузок курьерам](fbswarehousesetup/post-v1-warehouse-fbs-pickup-history-list.md) |
| `POST` | `/v1/warehouse/fbs/pickup/planning/list` | FBSWarehouseSetup | [Получить список складов для планирования отгрузок курьеру](fbswarehousesetup/post-v1-warehouse-fbs-pickup-planning-list.md) |
| `POST` | `/v1/warehouse/fbs/return-mile/check` | FBSWarehouseSetup | [Проверить необходимость установки возвратной мили на склад](fbswarehousesetup/post-v1-warehouse-fbs-return-mile-check.md) |
| `POST` | `/v1/warehouse/fbs/return-mile/info` | FBSWarehouseSetup | [Получить информацию о возвратной миле](fbswarehousesetup/post-v1-warehouse-fbs-return-mile-info.md) |
| `POST` | `/v1/warehouse/fbs/update/drop-off/list` | FBSWarehouseSetup | [Получить список drop-off пунктов для изменения информации склада](fbswarehousesetup/post-v1-warehouse-fbs-update-drop-off-list.md) |
| `POST` | `/v1/warehouse/fbs/update/drop-off/timeslot/list` | FBSWarehouseSetup | [Получить список таймслотов для обновления склада с отгрузкой drop-off](fbswarehousesetup/post-v1-warehouse-fbs-update-drop-off-timeslot-list.md) |
| `POST` | `/v1/warehouse/fbs/update/pick-up/timeslot/list` | FBSWarehouseSetup | [Получить список таймслотов для обновления склада с отгрузкой pick-up](fbswarehousesetup/post-v1-warehouse-fbs-update-pick-up-timeslot-list.md) |
| `POST` | `/v1/warehouse/fbs/update/return-point/list` | FBSWarehouseSetup | [Получить список пунктов возврата для обновления склада](fbswarehousesetup/post-v1-warehouse-fbs-update-return-point-list.md) |
| `POST` | `/v1/warehouse/fbs/update` | FBSWarehouseSetup | [Обновить склад](fbswarehousesetup/post-v1-warehouse-fbs-update.md) |
| `POST` | `/v1/warehouse/invalid-products/get` | WarehouseAPI | [Получить список товаров с ограничениями по доставке](warehouseapi/post-v1-warehouse-invalid-products-get.md) |
| `POST` | `/v1/warehouse/list` | WarehouseAPI | [Список складов](warehouseapi/post-v1-warehouse-list.md) |
| `POST` | `/v1/warehouse/operation/status` | WarehouseAPI | [Получить статус операции](warehouseapi/post-v1-warehouse-operation-status.md) |
| `POST` | `/v1/warehouse/ozon/list` | FBOWarehouse | [Получить список складов Ozon](fbowarehouse/post-v1-warehouse-ozon-list.md) |
| `POST` | `/v1/warehouse/rfbs/pause` | rFBSWarehouseSetup | [Поставить rFBS-склад на паузу](rfbswarehousesetup/post-v1-warehouse-rfbs-pause.md) |
| `POST` | `/v1/warehouse/rfbs/unpause` | rFBSWarehouseSetup | [Снять rFBS-склад с паузы](rfbswarehousesetup/post-v1-warehouse-rfbs-unpause.md) |
| `POST` | `/v1/warehouse/unarchive` | WarehouseAPI | [Перенести склад из архива](warehouseapi/post-v1-warehouse-unarchive.md) |
| `POST` | `/v1/warehouse/warehouses-with-invalid-products` | WarehouseAPI | [Получить список складов с ограниченными для доставки товарами](warehouseapi/post-v1-warehouse-warehouses-with-invalid-products.md) |
| `POST` | `/v2/actions/discounts-task/list` | BetaMethod | [Получить список заявок на скидку](betamethod/post-v2-actions-discounts-task-list.md) |
| `POST` | `/v2/analytics/stock_on_warehouses` | AnalyticsAPI | [Отчёт по остаткам и товарам](analyticsapi/post-v2-analytics-stock-on-warehouses.md) |
| `POST` | `/v2/cargoes/create/info` | FboSupplyRequest | [Получить информацию по установке грузомест](fbosupplyrequest/post-v2-cargoes-create-info.md) |
| `POST` | `/v2/cargoes/delete/status` | FBOTransport | [Получить информацию о статусе удаления грузомест и транспортных грузомест](fbotransport/post-v2-cargoes-delete-status.md) |
| `POST` | `/v2/cargoes/delete` | FBOTransport | [Удалить грузоместа и транспортные грузоместа в заявке на поставку](fbotransport/post-v2-cargoes-delete.md) |
| `POST` | `/v2/cargoes/get` | FBOTransport | [Получить информацию о грузоместах](fbotransport/post-v2-cargoes-get.md) |
| `POST` | `/v2/carriage/delivery/list` | DeliveryFBS | [Список методов доставки и отгрузок](deliveryfbs/post-v2-carriage-delivery-list.md) |
| `POST` | `/v2/chat/read` | Premium | [Отметить сообщения как прочитанные](premium/post-v2-chat-read.md) |
| `POST` | `/v2/cluster/list` | FboSupplyRequest | [Получить информацию о макролокальных кластерах](fbosupplyrequest/post-v2-cluster-list.md) |
| `POST` | `/v2/conditional-cancellation/approve` | CancellationAPI | [Подтвердить заявку на отмену rFBS](cancellationapi/post-v2-conditional-cancellation-approve.md) |
| `POST` | `/v2/conditional-cancellation/list` | CancellationAPI | [Получить список заявок на отмену rFBS](cancellationapi/post-v2-conditional-cancellation-list.md) |
| `POST` | `/v2/conditional-cancellation/reject` | CancellationAPI | [Отклонить заявку на отмену rFBS](cancellationapi/post-v2-conditional-cancellation-reject.md) |
| `POST` | `/v2/delivery-method/list` | WarehouseAPI | [Список методов доставки realFBS-склада](warehouseapi/post-v2-delivery-method-list.md) |
| `POST` | `/v2/delivery/checkout` | DeliveryAPI | [Получить доступные варианты доставки](deliveryapi/post-v2-delivery-checkout.md) |
| `POST` | `/v2/draft/create/info` | FboSupplyRequest | [Получить информацию о черновике заявки на поставку](fbosupplyrequest/post-v2-draft-create-info.md) |
| `POST` | `/v2/draft/supply/create/status` | FboSupplyRequest | [Получить информацию о создании заявки на поставку](fbosupplyrequest/post-v2-draft-supply-create-status.md) |
| `POST` | `/v2/draft/supply/create` | FboSupplyRequest | [Создать заявку на поставку по черновику](fbosupplyrequest/post-v2-draft-supply-create.md) |
| `POST` | `/v2/draft/timeslot/info` | FboSupplyRequest | [Получить список доступных таймслотов](fbosupplyrequest/post-v2-draft-timeslot-info.md) |
| `POST` | `/v2/fbs/posting/delivered` | DeliveryrFBS | [Изменить статус на «Доставлено»](deliveryrfbs/post-v2-fbs-posting-delivered.md) |
| `POST` | `/v2/fbs/posting/delivering` | DeliveryrFBS | [Изменить статус на «Доставляется»](deliveryrfbs/post-v2-fbs-posting-delivering.md) |
| `POST` | `/v2/fbs/posting/last-mile` | DeliveryrFBS | [Изменить статус на «Последняя миля»](deliveryrfbs/post-v2-fbs-posting-last-mile.md) |
| `POST` | `/v2/fbs/posting/tracking-number/set` | DeliveryrFBS | [Добавить трек-номера](deliveryrfbs/post-v2-fbs-posting-tracking-number-set.md) |
| `POST` | `/v2/finance/realization` | FinanceAPI | [Отчёт о реализации товаров (версия 2)](financeapi/post-v2-finance-realization.md) |
| `POST` | `/v2/invoice/create-or-update` | SupplierAPI | [Создать или изменить счёт-фактуру](supplierapi/post-v2-invoice-create-or-update.md) |
| `POST` | `/v2/invoice/get` | SupplierAPI | [Получить информацию о счёте-фактуре](supplierapi/post-v2-invoice-get.md) |
| `POST` | `/v2/order/create` | OrderAPI | [Создать заказ](orderapi/post-v2-order-create.md) |
| `POST` | `/v2/polygon/bind` | PolygonAPI | [Связать метод доставки с полигоном](polygonapi/post-v2-polygon-bind.md) |
| `POST` | `/v2/posting/digital/list` | BetaMethod | [Получить список отправлений](betamethod/post-v2-posting-digital-list.md) |
| `POST` | `/v2/posting/fbo/get` | FBO | [Информация об отправлении](fbo/post-v2-posting-fbo-get.md) |
| `POST` | `/v2/posting/fbo/list` | FBO | [Список отправлений](fbo/post-v2-posting-fbo-list.md) |
| `POST` | `/v2/posting/fbs/act/check-status` | DeliveryFBS | [Статус отгрузки и документов](deliveryfbs/post-v2-posting-fbs-act-check-status.md) |
| `POST` | `/v2/posting/fbs/act/create` | DeliveryFBS | [Подтвердить отгрузку и создать документы](deliveryfbs/post-v2-posting-fbs-act-create.md) |
| `POST` | `/v2/posting/fbs/act/get-barcode/text` | DeliveryFBS | [Значение штрихкода для отгрузки отправления](deliveryfbs/post-v2-posting-fbs-act-get-barcode-text.md) |
| `POST` | `/v2/posting/fbs/act/get-barcode` | DeliveryFBS | [Штрихкод для отгрузки отправления](deliveryfbs/post-v2-posting-fbs-act-get-barcode.md) |
| `POST` | `/v2/posting/fbs/act/get-container-labels` | DeliveryFBS | [Этикетки для грузового места](deliveryfbs/post-v2-posting-fbs-act-get-container-labels.md) |
| `POST` | `/v2/posting/fbs/act/get-pdf` | DeliveryFBS | [Получить PDF c документами](deliveryfbs/post-v2-posting-fbs-act-get-pdf.md) |
| `POST` | `/v2/posting/fbs/act/get-postings` | DeliveryFBS | [Список отправлений в акте](deliveryfbs/post-v2-posting-fbs-act-get-postings.md) |
| `POST` | `/v2/posting/fbs/act/list` | DeliveryFBS | [Список актов по отгрузкам](deliveryfbs/post-v2-posting-fbs-act-list.md) |
| `POST` | `/v2/posting/fbs/arbitration` | FBS | [Открыть спор по отправлению](fbs/post-v2-posting-fbs-arbitration.md) |
| `POST` | `/v2/posting/fbs/awaiting-delivery` | FBS | [Передать отправление к отгрузке](fbs/post-v2-posting-fbs-awaiting-delivery.md) |
| `POST` | `/v2/posting/fbs/cancel-reason/list` | FBS | [Причины отмены отправлений](fbs/post-v2-posting-fbs-cancel-reason-list.md) |
| `POST` | `/v2/posting/fbs/cancel` | FBS | [Отменить отправление](fbs/post-v2-posting-fbs-cancel.md) |
| `POST` | `/v2/posting/fbs/digital/act/check-status` | DeliveryFBS | [Статус формирования накладной](deliveryfbs/post-v2-posting-fbs-digital-act-check-status.md) |
| `POST` | `/v2/posting/fbs/digital/act/get-pdf` | DeliveryFBS | [Получить лист отгрузки по перевозке](deliveryfbs/post-v2-posting-fbs-digital-act-get-pdf.md) |
| `POST` | `/v2/posting/fbs/get-by-barcode` | FBS | [Получить информацию об отправлении по штрихкоду](fbs/post-v2-posting-fbs-get-by-barcode.md) |
| `POST` | `/v2/posting/fbs/package-label/create` | FBS | [Создать задание на формирование этикеток](fbs/post-v2-posting-fbs-package-label-create.md) |
| `POST` | `/v2/posting/fbs/package-label` | FBS | [Напечатать этикетку](fbs/post-v2-posting-fbs-package-label.md) |
| `POST` | `/v2/posting/fbs/product/cancel` | FBS | [Отменить отправку некоторых товаров в отправлении](fbs/post-v2-posting-fbs-product-cancel.md) |
| `POST` | `/v2/posting/fbs/product/country/list` | FBS | [Список доступных стран-изготовителей](fbs/post-v2-posting-fbs-product-country-list.md) |
| `POST` | `/v2/posting/fbs/product/country/set` | FBS | [Добавить информацию о стране-изготовителе товара](fbs/post-v2-posting-fbs-product-country-set.md) |
| `POST` | `/v2/product/certificate/create` | BetaMethod | [Создать сертификат качества](betamethod/post-v2-product-certificate-create.md) |
| `POST` | `/v2/product/certification/list` | CertificationAPI | [Список сертифицируемых категорий](certificationapi/post-v2-product-certification-list.md) |
| `POST` | `/v2/product/certification/options` | BetaMethod | [Получить параметры для создания сертификата качества](betamethod/post-v2-product-certification-options.md) |
| `POST` | `/v2/product/certification/params` | BetaMethod | [Получить обязательные параметры для создания сертификата качества](betamethod/post-v2-product-certification-params.md) |
| `POST` | `/v2/product/info/stocks-by-warehouse/fbs` | Prices&StocksAPI | [Получить информацию об остатках на складах продавца](prices-stocksapi/post-v2-product-info-stocks-by-warehouse-fbs.md) |
| `POST` | `/v2/product/pictures/import` | ProductAPI | [Загрузить или обновить изображения товара](productapi/post-v2-product-pictures-import.md) |
| `POST` | `/v2/product/pictures/info` | ProductAPI | [Получить изображения товаров](productapi/post-v2-product-pictures-info.md) |
| `POST` | `/v2/products/delete` | ProductAPI | [Удалить товар без SKU из архива](productapi/post-v2-products-delete.md) |
| `POST` | `/v2/products/stocks` | Prices&StocksAPI | [Обновить количество товаров на складах](prices-stocksapi/post-v2-products-stocks.md) |
| `POST` | `/v2/report/returns/create` | ReportAPI | [Отчёт о возвратах](reportapi/post-v2-report-returns-create.md) |
| `POST` | `/v2/returns/rfbs/get` | RFBSReturnsAPI | [Информация о заявке на возврат](rfbsreturnsapi/post-v2-returns-rfbs-get.md) |
| `POST` | `/v2/returns/rfbs/list` | RFBSReturnsAPI | [Список заявок на возврат](rfbsreturnsapi/post-v2-returns-rfbs-list.md) |
| `POST` | `/v2/review/change-status` | ReviewAPI | [Изменить статус отзывов](reviewapi/post-v2-review-change-status.md) |
| `POST` | `/v2/review/comment/delete` | ReviewAPI | [Удалить комментарий на отзыв](reviewapi/post-v2-review-comment-delete.md) |
| `POST` | `/v2/review/count` | ReviewAPI | [Получить количество отзывов по статусам](reviewapi/post-v2-review-count.md) |
| `POST` | `/v2/review/info` | ReviewAPI | [Получить информацию по отзыву](reviewapi/post-v2-review-info.md) |
| `POST` | `/v2/review/list` | ReviewAPI | [Получить список отзывов](reviewapi/post-v2-review-list.md) |
| `POST` | `/v2/supply-order/timeslot/list` | FBO | [Получить список доступных интервалов поставки](fbo/post-v2-supply-order-timeslot-list.md) |
| `POST` | `/v2/warehouse/list` | WarehouseAPI | [Список складов](warehouseapi/post-v2-warehouse-list.md) |
| `POST` | `/v3/chat/history` | ChatAPI | [История чата](chatapi/post-v3-chat-history.md) |
| `POST` | `/v3/chat/list` | ChatAPI | [Список чатов](chatapi/post-v3-chat-list.md) |
| `POST` | `/v3/finance/transaction/list` | FinanceAPI | [Список транзакций](financeapi/post-v3-finance-transaction-list.md) |
| `POST` | `/v3/finance/transaction/totals` | FinanceAPI | [Суммы транзакций](financeapi/post-v3-finance-transaction-totals.md) |
| `POST` | `/v3/posting/fbo/list` | FBO | [Получить список отправлений](fbo/post-v3-posting-fbo-list.md) |
| `POST` | `/v3/posting/fbs/get` | FBS | [Получить информацию об отправлении по идентификатору](fbs/post-v3-posting-fbs-get.md) |
| `POST` | `/v3/posting/fbs/list` | FBS | [Список отправлений](fbs/post-v3-posting-fbs-list.md) |
| `POST` | `/v3/posting/fbs/unfulfilled/list` | FBS | [Список необработанных отправлений](fbs/post-v3-posting-fbs-unfulfilled-list.md) |
| `POST` | `/v3/posting/multiboxqty/set` | FBS | [Указать количество коробок для многокоробочных отправлений](fbs/post-v3-posting-multiboxqty-set.md) |
| `POST` | `/v3/product/import` | ProductAPI | [Создать или обновить товар](productapi/post-v3-product-import.md) |
| `POST` | `/v3/product/info/list` | ProductAPI | [Получить информацию о товарах по идентификаторам](productapi/post-v3-product-info-list.md) |
| `POST` | `/v3/product/list` | ProductAPI | [Список товаров](productapi/post-v3-product-list.md) |
| `POST` | `/v3/supply-order/get` | FBO | [Информация о заявке на поставку](fbo/post-v3-supply-order-get.md) |
| `POST` | `/v3/supply-order/list` | FBO | [Список заявок на поставку на склад Ozon](fbo/post-v3-supply-order-list.md) |
| `POST` | `/v4/posting/fbs/list` | FBS | [Получить список отправлений](fbs/post-v4-posting-fbs-list.md) |
| `POST` | `/v4/posting/fbs/ship/package` | FBS&rFBSMarks | [Частичная сборка отправления (версия 4)](fbs-rfbsmarks/post-v4-posting-fbs-ship-package.md) |
| `POST` | `/v4/posting/fbs/ship` | FBS&rFBSMarks | [Собрать заказ (версия 4)](fbs-rfbsmarks/post-v4-posting-fbs-ship.md) |
| `POST` | `/v4/posting/fbs/unfulfilled/list` | FBS | [Получить список необработанных отправлений](fbs/post-v4-posting-fbs-unfulfilled-list.md) |
| `POST` | `/v4/product/info/attributes` | ProductAPI | [Получить описание характеристик товара](productapi/post-v4-product-info-attributes.md) |
| `POST` | `/v4/product/info/limit` | ProductAPI | [Лимиты на ассортимент, создание и обновление товаров](productapi/post-v4-product-info-limit.md) |
| `POST` | `/v4/product/info/stocks` | Prices&StocksAPI | [Информация о количестве товаров](prices-stocksapi/post-v4-product-info-stocks.md) |
| `POST` | `/v5/fbs/posting/product/exemplar/status` | FBS&rFBSMarks | [Получить статус добавления экземпляров](fbs-rfbsmarks/post-v5-fbs-posting-product-exemplar-status.md) |
| `POST` | `/v5/fbs/posting/product/exemplar/validate` | FBS&rFBSMarks | [Валидация кодов маркировки](fbs-rfbsmarks/post-v5-fbs-posting-product-exemplar-validate.md) |
| `POST` | `/v5/product/info/prices` | Prices&StocksAPI | [Получить информацию о цене товара](prices-stocksapi/post-v5-product-info-prices.md) |
| `POST` | `/v6/fbs/posting/product/exemplar/create-or-get` | FBS&rFBSMarks | [Получить данные созданных экземпляров](fbs-rfbsmarks/post-v6-fbs-posting-product-exemplar-create-or-get.md) |
| `POST` | `/v6/fbs/posting/product/exemplar/set` | FBS&rFBSMarks | [Проверить и сохранить данные экземпляров](fbs-rfbsmarks/post-v6-fbs-posting-product-exemplar-set.md) |
