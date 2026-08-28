---
title: Создание карточек товаров
api: wb-work-with-products
tag: listingItems
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
content_sha: 71c43d82871896fe
---

# Создание карточек товаров

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о создании карточек товаров можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-164?categoryId=bcbf9386-1316-4ad4-ab10-34ddb2857b54)

После получения [категорий, предметов и характеристик товаров](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics) вы можете создать карточку товара. Для этого:
 1. Проверьте [лимиты для создания карточек товаров](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1limits/get).
 2. Вы можете [сгенерировать баркоды](./work-with-products#tag/listingItems/paths/~1content~1v2~1barcodes/post) для карточек товаров. Но если вы создадите карточку товара без баркода, он будет сгенерирован автоматически. Либо вы можете использовать свой баркод.

Можно создавать карточки товаров:
 1. [Объединёнными или отдельными](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post).
 2. [Присоединёнными](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload~1add/post) к уже существующим карточкам товаров.

Присоединять, [объединять и разъединять](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1moveNm/post) карточки товаров можно через `imtID` — ID WB для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров.
