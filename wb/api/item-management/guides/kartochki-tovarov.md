---
title: Карточки товаров
api: wb-item-management
tag: listings
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: d52f973c599cf4d1
---

# Карточки товаров

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о карточках товаров можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-165?categoryId=3a795fe1-d5cb-4120-be1a-387eed6494e5)

После [создания карточек товаров](./work-with-products#tag/listingItems) вы можете:
 1. Получать [списки с подробной информацией](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post) об уже созданных карточках. Если вы не увидели карточку товара в списке после её создания, [произошла ошибка](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1error~1list/post).
 2. [Объединять и разъединять созданные карточки](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1moveNm/post).
 3. [Редактировать данные карточки товара](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post).
 4. Работать с корзиной: можно [переносить карточки товаров](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1delete~1trash/post) в корзину и [восстанавливать их](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1recover/post).
 5. Получать [списки карточек товаров в корзине](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1trash/post).
