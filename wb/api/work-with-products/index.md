---
title: Работа с товарами — все методы
api: wb-work-with-products
spec_version: items
operations: 52
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
content_sha: 1f528465195a56d9
---

# Работа с товарами

С помощью методов этого раздела вы можете: - [создавать](./work-with-products#tag/listingItems) и [редактировать](./work-with-products#tag/listings) карточки товаров - получать [категории, предметы, характеристики и бренды товаров](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics) - загружать [медиафайлы](./work-with-products#tag/mediaFiles) в карточки товаров - настраивать [ярлыки](./work-with-products#tag/labels) для поиска товаров - работать с [рекомендациями](./work-with-products#tag/recommendations) для товаров - устанавливать [цены и скидки](./work-with-products#tag/Ceny-i-skidki) - управлять [остатками товаров](./work-with-products#tag/Ostatki-na-skladah-prodavca) и [складами](./work-with-products#tag/Sklady-prodavca), если вы работаете по модели продаж со склада продавца Вы можете протестировать методы работы с товарами в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Rabota-s-tovarami) для управления карточками товаров Узнать, как использовать методы в бизнес-кейсах, можно в инструкции по работе с товарами

Версия спеки: `items` · методов: **52**

Источник: https://dev.wildberries.ru/docs/openapi/work-with-products

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/v3/stocks/{warehouseId}` | Остатки на складах продавца | [Удалить остатки товаров{{ /api/v3/stocks/{warehouseId} }}](ostatki-na-skladah-prodavca/delete-api-v3-stocks-warehouseid.md) |
| `DELETE` | `/api/v3/warehouses/{warehouseId}` | Склады продавца | [Удалить склад продавца{{ /api/v3/warehouses/{warehouseId} }}](sklady-prodavca/delete-api-v3-warehouses-warehouseid.md) |
| `DELETE` | `/content/v2/tag/{id}` | labels | [Удаление ярлыка{{ /content/v2/tag/{id} }}](labels/delete-content-v2-tag-id.md) |
| `GET` | `/api/content/v1/brands` | categoriesSubcategoriesAndCharacteristics | [Бренды{{ /api/content/v1/brands }}](categoriessubcategoriesandcharacteristics/get-api-content-v1-brands.md) |
| `GET` | `/api/v2/buffer/goods/task` | Цены и скидки | [Детализация необработанной загрузки{{ /api/v2/buffer/goods/task }}](ceny-i-skidki/get-api-v2-buffer-goods-task.md) |
| `GET` | `/api/v2/buffer/tasks` | Цены и скидки | [Состояние необработанной загрузки{{ /api/v2/buffer/tasks }}](ceny-i-skidki/get-api-v2-buffer-tasks.md) |
| `GET` | `/api/v2/history/goods/task` | Цены и скидки | [Детализация обработанной загрузки{{ /api/v2/history/goods/task }}](ceny-i-skidki/get-api-v2-history-goods-task.md) |
| `GET` | `/api/v2/history/tasks` | Цены и скидки | [Состояние обработанной загрузки{{ /api/v2/history/tasks }}](ceny-i-skidki/get-api-v2-history-tasks.md) |
| `GET` | `/api/v2/list/goods/filter` | Цены и скидки | [Получить товары с ценами{{ /api/v2/list/goods/filter }}](ceny-i-skidki/get-api-v2-list-goods-filter.md) |
| `GET` | `/api/v2/list/goods/size/nm` | Цены и скидки | [Получить размеры товара с ценами{{ /api/v2/list/goods/size/nm }}](ceny-i-skidki/get-api-v2-list-goods-size-nm.md) |
| `GET` | `/api/v2/quarantine/goods` | Цены и скидки | [Получить товары в карантине{{ /api/v2/quarantine/goods }}](ceny-i-skidki/get-api-v2-quarantine-goods.md) |
| `GET` | `/api/v3/dbw/warehouses/{warehouseId}/contacts` | Склады продавца | [Список контактов{{ /api/v3/dbw/warehouses/{warehouseId}/contacts }}](sklady-prodavca/get-api-v3-dbw-warehouses-warehouseid-contacts.md) |
| `GET` | `/api/v3/offices` | Склады продавца | [Получить список складов WB{{ /api/v3/offices }}](sklady-prodavca/get-api-v3-offices.md) |
| `GET` | `/api/v3/warehouses` | Склады продавца | [Получить список складов продавца{{ /api/v3/warehouses }}](sklady-prodavca/get-api-v3-warehouses.md) |
| `GET` | `/content/v2/cards/limits` | listingItems | [Лимиты карточек товаров{{ /content/v2/cards/limits }}](listingitems/get-content-v2-cards-limits.md) |
| `GET` | `/content/v2/directory/colors` | categoriesSubcategoriesAndCharacteristics | [Цвет{{ /content/v2/directory/colors }}](categoriessubcategoriesandcharacteristics/get-content-v2-directory-colors.md) |
| `GET` | `/content/v2/directory/countries` | categoriesSubcategoriesAndCharacteristics | [Страна производства{{ /content/v2/directory/countries }}](categoriessubcategoriesandcharacteristics/get-content-v2-directory-countries.md) |
| `GET` | `/content/v2/directory/kinds` | categoriesSubcategoriesAndCharacteristics | [Пол{{ /content/v2/directory/kinds }}](categoriessubcategoriesandcharacteristics/get-content-v2-directory-kinds.md) |
| `GET` | `/content/v2/directory/seasons` | categoriesSubcategoriesAndCharacteristics | [Сезон{{ /content/v2/directory/seasons }}](categoriessubcategoriesandcharacteristics/get-content-v2-directory-seasons.md) |
| `GET` | `/content/v2/directory/tnved` | categoriesSubcategoriesAndCharacteristics | [ТНВЭД-код{{ /content/v2/directory/tnved }}](categoriessubcategoriesandcharacteristics/get-content-v2-directory-tnved.md) |
| `GET` | `/content/v2/directory/vat` | categoriesSubcategoriesAndCharacteristics | [Ставка НДС{{ /content/v2/directory/vat }}](categoriessubcategoriesandcharacteristics/get-content-v2-directory-vat.md) |
| `GET` | `/content/v2/object/all` | categoriesSubcategoriesAndCharacteristics | [Список предметов{{ /content/v2/object/all }}](categoriessubcategoriesandcharacteristics/get-content-v2-object-all.md) |
| `GET` | `/content/v2/object/charcs/{subjectId}` | categoriesSubcategoriesAndCharacteristics | [Характеристики предмета{{ /content/v2/object/charcs/{subjectId} }}](categoriessubcategoriesandcharacteristics/get-content-v2-object-charcs-subjectid.md) |
| `GET` | `/content/v2/object/parent/all` | categoriesSubcategoriesAndCharacteristics | [Родительские категории товаров{{ /content/v2/object/parent/all }}](categoriessubcategoriesandcharacteristics/get-content-v2-object-parent-all.md) |
| `GET` | `/content/v2/tags` | labels | [Список ярлыков{{ /content/v2/tags }}](labels/get-content-v2-tags.md) |
| `PATCH` | `/content/v2/tag/{id}` | labels | [Изменение ярлыка{{ /content/v2/tag/{id} }}](labels/patch-content-v2-tag-id.md) |
| `POST` | `/api/content/v1/recommendations/list` | recommendations | [Список рекомендаций в карточках товаров{{ /api/content/v1/recommendations/list }}](recommendations/post-api-content-v1-recommendations-list.md) |
| `POST` | `/api/content/v1/recommendations/set` | recommendations | [Установить рекомендации для товаров{{ /api/content/v1/recommendations/set }}](recommendations/post-api-content-v1-recommendations-set.md) |
| `POST` | `/api/discounts-prices/v1/upload/task/b2b/wholesale` | Цены и скидки | [Установить оптовые скидки для B2B-продаж{{ /api/discounts-prices/v1/upload/task/b2b/wholesale }}](ceny-i-skidki/post-api-discounts-prices-v1-upload-task-b2b-wholesale.md) |
| `POST` | `/api/v2/list/goods/filter` | Цены и скидки | [Получить товары с ценами по артикулам{{ /api/v2/list/goods/filter }}](ceny-i-skidki/post-api-v2-list-goods-filter.md) |
| `POST` | `/api/v2/upload/task/club-discount` | Цены и скидки | [Установить скидки WB Клуба{{ /api/v2/upload/task/club-discount }}](ceny-i-skidki/post-api-v2-upload-task-club-discount.md) |
| `POST` | `/api/v2/upload/task/size` | Цены и скидки | [Установить цены для размеров{{ /api/v2/upload/task/size }}](ceny-i-skidki/post-api-v2-upload-task-size.md) |
| `POST` | `/api/v2/upload/task` | Цены и скидки | [Установить цены и скидки{{ /api/v2/upload/task }}](ceny-i-skidki/post-api-v2-upload-task.md) |
| `POST` | `/api/v3/stocks/{warehouseId}` | Остатки на складах продавца | [Получить остатки товаров{{ /api/v3/stocks/{warehouseId} }}](ostatki-na-skladah-prodavca/post-api-v3-stocks-warehouseid.md) |
| `POST` | `/api/v3/warehouses` | Склады продавца | [Создать склад продавца{{ /api/v3/warehouses }}](sklady-prodavca/post-api-v3-warehouses.md) |
| `POST` | `/content/v2/barcodes` | listingItems | [Генерация баркодов{{ /content/v2/barcodes }}](listingitems/post-content-v2-barcodes.md) |
| `POST` | `/content/v2/cards/delete/trash` | listings | [Перенос карточек товаров в корзину{{ /content/v2/cards/delete/trash }}](listings/post-content-v2-cards-delete-trash.md) |
| `POST` | `/content/v2/cards/error/list` | listings | [Список несозданных карточек товаров с ошибками{{ /content/v2/cards/error/list }}](listings/post-content-v2-cards-error-list.md) |
| `POST` | `/content/v2/cards/moveNm` | listings | [Объединение и разъединение карточек товаров{{ /content/v2/cards/moveNm }}](listings/post-content-v2-cards-movenm.md) |
| `POST` | `/content/v2/cards/recover` | listings | [Восстановление карточек товаров из корзины{{ /content/v2/cards/recover }}](listings/post-content-v2-cards-recover.md) |
| `POST` | `/content/v2/cards/update` | listings | [Редактирование карточек товаров{{ /content/v2/cards/update }}](listings/post-content-v2-cards-update.md) |
| `POST` | `/content/v2/cards/upload/add` | listingItems | [Создание карточек товаров с присоединением{{ /content/v2/cards/upload/add }}](listingitems/post-content-v2-cards-upload-add.md) |
| `POST` | `/content/v2/cards/upload` | listingItems | [Создание карточек товаров{{ /content/v2/cards/upload }}](listingitems/post-content-v2-cards-upload.md) |
| `POST` | `/content/v2/get/cards/list` | listings | [Список карточек товаров{{ /content/v2/get/cards/list }}](listings/post-content-v2-get-cards-list.md) |
| `POST` | `/content/v2/get/cards/trash` | listings | [Список карточек товаров в корзине{{ /content/v2/get/cards/trash }}](listings/post-content-v2-get-cards-trash.md) |
| `POST` | `/content/v2/tag/nomenclature/link` | labels | [Управление ярлыками в карточке товара{{ /content/v2/tag/nomenclature/link }}](labels/post-content-v2-tag-nomenclature-link.md) |
| `POST` | `/content/v2/tag` | labels | [Создание ярлыка{{ /content/v2/tag }}](labels/post-content-v2-tag.md) |
| `POST` | `/content/v3/media/file` | mediaFiles | [Загрузить медиафайл{{ /content/v3/media/file }}](mediafiles/post-content-v3-media-file.md) |
| `POST` | `/content/v3/media/save` | mediaFiles | [Загрузить медиафайлы по ссылкам{{ /content/v3/media/save }}](mediafiles/post-content-v3-media-save.md) |
| `PUT` | `/api/v3/dbw/warehouses/{warehouseId}/contacts` | Склады продавца | [Обновить список контактов{{ /api/v3/dbw/warehouses/{warehouseId}/contacts }}](sklady-prodavca/put-api-v3-dbw-warehouses-warehouseid-contacts.md) |
| `PUT` | `/api/v3/stocks/{warehouseId}` | Остатки на складах продавца | [Обновить остатки товаров{{ /api/v3/stocks/{warehouseId} }}](ostatki-na-skladah-prodavca/put-api-v3-stocks-warehouseid.md) |
| `PUT` | `/api/v3/warehouses/{warehouseId}` | Склады продавца | [Обновить склад продавца{{ /api/v3/warehouses/{warehouseId} }}](sklady-prodavca/put-api-v3-warehouses-warehouseid.md) |
