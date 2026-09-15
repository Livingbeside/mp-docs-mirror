---
title: Создание карточек товаров
api: wb-item-management
tag: listingItems
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: 9b48f7a38335ac25
---

# Создание карточек товаров

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о создании карточек товаров можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-164?categoryId=bcbf9386-1316-4ad4-ab10-34ddb2857b54)

После получения [категорий, предметов и характеристик товаров](./item-management#tag/categoriesSubcategoriesAndCharacteristics) вы можете создать карточку товара. Для этого:
 1. Проверьте [лимиты для создания карточек товаров](./item-management#tag/listingItems/operation/getV2CardsLimits).
 2. Вы можете [сгенерировать баркоды](./item-management#tag/listingItems/operation/postV2Barcodes) для карточек товаров. Но если вы создадите карточку товара без баркода, он будет сгенерирован автоматически. Либо вы можете использовать свой баркод.

Можно создавать карточки товаров:
 1. [Объединёнными или отдельными](./item-management#tag/listingItems/operation/postV2CardsUpload).
 2. [Присоединёнными](./item-management#tag/listingItems/operation/postV2CardsUploadAdd) к уже существующим карточкам товаров.

Присоединять, [объединять и разъединять](./item-management#tag/listings/operation/postV2CardsMoveNm) карточки товаров можно через `imtID` — ID WB для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров.
