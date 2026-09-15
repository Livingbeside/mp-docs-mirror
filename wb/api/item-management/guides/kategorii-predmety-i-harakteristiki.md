---
title: Категории, предметы и характеристики
api: wb-item-management
tag: categoriesSubcategoriesAndCharacteristics
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: 2274e5c561b78b76
---

# Категории, предметы и характеристики

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о категориях, предметах и характеристиках можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-254?categoryId=f878a9b1-850b-4538-899c-4e4f4a9ab15c)

Для [создания карточек товаров](./item-management#tag/listingItems) необходимо:
 1. Определить [родительскую категорию](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectParentAll), к которой будет относиться товар.
 2. Внутри категории выбрать [предмет](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectAll).
 3. Подобрать для каждого предмета [характеристики](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectCharcsSubjectId) товара. Характеристики [Цвет](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryColors), [Пол](item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryKinds), [Страна производства](item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryCountries), [Сезон](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectorySeasons), [Ставка НДС](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryVat) и [ТНВЭД-код](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryTnved) можно получить с помощью отдельных методов.
 4. Выбрать [бренд](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV1Brands) товара.
