---
title: Работа с товарами — все методы
api: wb-item-management
spec_version: items
operations: 52
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: c8216faf01e6849b
---

# Работа с товарами

С помощью методов этого раздела вы можете:
 - [создавать](./item-management#tag/listingItems) и [редактировать](./item-management#tag/listings) карточки товаров
 - получать [категории, предметы, характеристики и бренды товаров](./item-management#tag/categoriesSubcategoriesAndCharacteristics)
 - загружать [медиафайлы](./item-management#tag/mediaFiles) в карточки товаров
 - настраивать [ярлыки](./item-management#tag/labels) для поиска товаров
 - работать с [рекомендациями](./item-management#tag/recommendations) для товаров
 - устанавливать [цены и скидки](./item-management#tag/pricesAndDiscounts)
 - управлять [остатками товаров](./item-management#tag/sellerWarehousesInventory) и [складами](./item-management#tag/sellerWarehouses), если вы работаете по модели продаж со склада продавца

Вы можете протестировать методы работы с товарами в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/itemManagement) для управления карточками товаров

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

Версия спеки: `items` · методов: **52** · разделов справки: **10**

Источник: https://dev.wildberries.ru/docs/openapi/item-management

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/v3/stocks/{warehouseId}` | sellerWarehousesInventory | [Удалить остатки товаров{{ /api/v3/stocks/{warehouseId} }}](sellerwarehousesinventory/delete-api-v3-stocks-warehouseid.md) |
| `DELETE` | `/api/v3/warehouses/{warehouseId}` | sellerWarehouses | [Удалить склад продавца{{ /api/v3/warehouses/{warehouseId} }}](sellerwarehouses/delete-api-v3-warehouses-warehouseid.md) |
| `DELETE` | `/content/v2/tag/{id}` | labels | [Удаление ярлыка{{ /content/v2/tag/{id} }}](labels/delete-content-v2-tag-id.md) |
| `GET` | `/api/content/v1/brands` | categoriesSubcategoriesAndCharacteristics | [Бренды](categoriessubcategoriesandcharacteristics/get-api-content-v1-brands.md) |
| `GET` | `/api/v2/buffer/goods/task` | pricesAndDiscounts | [Детализация необработанной загрузки](pricesanddiscounts/get-api-v2-buffer-goods-task.md) |
| `GET` | `/api/v2/buffer/tasks` | pricesAndDiscounts | [Состояние необработанной загрузки](pricesanddiscounts/get-api-v2-buffer-tasks.md) |
| `GET` | `/api/v2/history/goods/task` | pricesAndDiscounts | [Детализация обработанной загрузки](pricesanddiscounts/get-api-v2-history-goods-task.md) |
| `GET` | `/api/v2/history/tasks` | pricesAndDiscounts | [Состояние обработанной загрузки](pricesanddiscounts/get-api-v2-history-tasks.md) |
| `GET` | `/api/v2/list/goods/filter` | pricesAndDiscounts | [Получить товары с ценами](pricesanddiscounts/get-api-v2-list-goods-filter.md) |
| `GET` | `/api/v2/list/goods/size/nm` | pricesAndDiscounts | [Получить размеры товара с ценами](pricesanddiscounts/get-api-v2-list-goods-size-nm.md) |
| `GET` | `/api/v2/quarantine/goods` | pricesAndDiscounts | [Получить товары в карантине](pricesanddiscounts/get-api-v2-quarantine-goods.md) |
| `GET` | `/api/v3/dbw/warehouses/{warehouseId}/contacts` | sellerWarehouses | [Список контактов{{ /api/v3/dbw/warehouses/{warehouseId}/contacts }}](sellerwarehouses/get-api-v3-dbw-warehouses-warehouseid-contacts.md) |
| `GET` | `/api/v3/offices` | sellerWarehouses | [Получить список складов WB](sellerwarehouses/get-api-v3-offices.md) |
| `GET` | `/api/v3/warehouses` | sellerWarehouses | [Получить список складов продавца](sellerwarehouses/get-api-v3-warehouses.md) |
| `GET` | `/content/v2/cards/limits` | listingItems | [Лимиты карточек товаров](listingitems/get-content-v2-cards-limits.md) |
| `GET` | `/content/v2/directory/colors` | categoriesSubcategoriesAndCharacteristics | [Цвет](categoriessubcategoriesandcharacteristics/get-content-v2-directory-colors.md) |
| `GET` | `/content/v2/directory/countries` | categoriesSubcategoriesAndCharacteristics | [Страна производства](categoriessubcategoriesandcharacteristics/get-content-v2-directory-countries.md) |
| `GET` | `/content/v2/directory/kinds` | categoriesSubcategoriesAndCharacteristics | [Пол](categoriessubcategoriesandcharacteristics/get-content-v2-directory-kinds.md) |
| `GET` | `/content/v2/directory/seasons` | categoriesSubcategoriesAndCharacteristics | [Сезон](categoriessubcategoriesandcharacteristics/get-content-v2-directory-seasons.md) |
| `GET` | `/content/v2/directory/tnved` | categoriesSubcategoriesAndCharacteristics | [ТНВЭД-код](categoriessubcategoriesandcharacteristics/get-content-v2-directory-tnved.md) |
| `GET` | `/content/v2/directory/vat` | categoriesSubcategoriesAndCharacteristics | [Ставка НДС](categoriessubcategoriesandcharacteristics/get-content-v2-directory-vat.md) |
| `GET` | `/content/v2/object/all` | categoriesSubcategoriesAndCharacteristics | [Список предметов](categoriessubcategoriesandcharacteristics/get-content-v2-object-all.md) |
| `GET` | `/content/v2/object/charcs/{subjectId}` | categoriesSubcategoriesAndCharacteristics | [Характеристики предмета{{ /content/v2/object/charcs/{subjectId} }}](categoriessubcategoriesandcharacteristics/get-content-v2-object-charcs-subjectid.md) |
| `GET` | `/content/v2/object/parent/all` | categoriesSubcategoriesAndCharacteristics | [Родительские категории товаров](categoriessubcategoriesandcharacteristics/get-content-v2-object-parent-all.md) |
| `GET` | `/content/v2/tags` | labels | [Список ярлыков](labels/get-content-v2-tags.md) |
| `PATCH` | `/content/v2/tag/{id}` | labels | [Изменение ярлыка{{ /content/v2/tag/{id} }}](labels/patch-content-v2-tag-id.md) |
| `POST` | `/api/content/v1/recommendations/list` | recommendations | [Список рекомендаций в карточках товаров](recommendations/post-api-content-v1-recommendations-list.md) |
| `POST` | `/api/content/v1/recommendations/set` | recommendations | [Установить рекомендации для товаров](recommendations/post-api-content-v1-recommendations-set.md) |
| `POST` | `/api/discounts-prices/v1/upload/task/b2b/wholesale` | pricesAndDiscounts | [Установить оптовые скидки для B2B-продаж](pricesanddiscounts/post-api-discounts-prices-v1-upload-task-b2b-wholesale.md) |
| `POST` | `/api/v2/list/goods/filter` | pricesAndDiscounts | [Получить товары с ценами по артикулам](pricesanddiscounts/post-api-v2-list-goods-filter.md) |
| `POST` | `/api/v2/upload/task/club-discount` | pricesAndDiscounts | [Установить скидки WB Клуба](pricesanddiscounts/post-api-v2-upload-task-club-discount.md) |
| `POST` | `/api/v2/upload/task/size` | pricesAndDiscounts | [Установить цены для размеров](pricesanddiscounts/post-api-v2-upload-task-size.md) |
| `POST` | `/api/v2/upload/task` | pricesAndDiscounts | [Установить цены и скидки](pricesanddiscounts/post-api-v2-upload-task.md) |
| `POST` | `/api/v3/stocks/{warehouseId}` | sellerWarehousesInventory | [Получить остатки товаров{{ /api/v3/stocks/{warehouseId} }}](sellerwarehousesinventory/post-api-v3-stocks-warehouseid.md) |
| `POST` | `/api/v3/warehouses` | sellerWarehouses | [Создать склад продавца](sellerwarehouses/post-api-v3-warehouses.md) |
| `POST` | `/content/v2/barcodes` | listingItems | [Генерация баркодов](listingitems/post-content-v2-barcodes.md) |
| `POST` | `/content/v2/cards/delete/trash` | listings | [Перенос карточек товаров в корзину](listings/post-content-v2-cards-delete-trash.md) |
| `POST` | `/content/v2/cards/error/list` | listings | [Список несозданных карточек товаров с ошибками](listings/post-content-v2-cards-error-list.md) |
| `POST` | `/content/v2/cards/moveNm` | listings | [Объединение и разъединение карточек товаров](listings/post-content-v2-cards-movenm.md) |
| `POST` | `/content/v2/cards/recover` | listings | [Восстановление карточек товаров из корзины](listings/post-content-v2-cards-recover.md) |
| `POST` | `/content/v2/cards/update` | listings | [Редактирование карточек товаров](listings/post-content-v2-cards-update.md) |
| `POST` | `/content/v2/cards/upload/add` | listingItems | [Создание карточек товаров с присоединением](listingitems/post-content-v2-cards-upload-add.md) |
| `POST` | `/content/v2/cards/upload` | listingItems | [Создание карточек товаров](listingitems/post-content-v2-cards-upload.md) |
| `POST` | `/content/v2/get/cards/list` | listings | [Список карточек товаров](listings/post-content-v2-get-cards-list.md) |
| `POST` | `/content/v2/get/cards/trash` | listings | [Список карточек товаров в корзине](listings/post-content-v2-get-cards-trash.md) |
| `POST` | `/content/v2/tag/nomenclature/link` | labels | [Управление ярлыками в карточке товара](labels/post-content-v2-tag-nomenclature-link.md) |
| `POST` | `/content/v2/tag` | labels | [Создание ярлыка](labels/post-content-v2-tag.md) |
| `POST` | `/content/v3/media/file` | mediaFiles | [Загрузить медиафайл](mediafiles/post-content-v3-media-file.md) |
| `POST` | `/content/v3/media/save` | mediaFiles | [Загрузить медиафайлы по ссылкам](mediafiles/post-content-v3-media-save.md) |
| `PUT` | `/api/v3/dbw/warehouses/{warehouseId}/contacts` | sellerWarehouses | [Обновить список контактов{{ /api/v3/dbw/warehouses/{warehouseId}/contacts }}](sellerwarehouses/put-api-v3-dbw-warehouses-warehouseid-contacts.md) |
| `PUT` | `/api/v3/stocks/{warehouseId}` | sellerWarehousesInventory | [Обновить остатки товаров{{ /api/v3/stocks/{warehouseId} }}](sellerwarehousesinventory/put-api-v3-stocks-warehouseid.md) |
| `PUT` | `/api/v3/warehouses/{warehouseId}` | sellerWarehouses | [Обновить склад продавца{{ /api/v3/warehouses/{warehouseId} }}](sellerwarehouses/put-api-v3-warehouses-warehouseid.md) |
