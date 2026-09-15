---
title: Карточки товаров
api: wb-item-management
tag: listings
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: f338668e5e0f761a
---

# Карточки товаров

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о карточках товаров можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-165?categoryId=3a795fe1-d5cb-4120-be1a-387eed6494e5)

После [создания карточек товаров](./item-management#tag/listingItems) вы можете:
 1. Получать [списки с подробной информацией](./item-management#tag/listings/operation/postV2GetCardsList) об уже созданных карточках. Если вы не увидели карточку товара в списке после её создания, [произошла ошибка](./item-management#tag/listings/operation/postV2CardsErrorList).
 2. [Объединять и разъединять созданные карточки](./item-management#tag/listings/operation/postV2CardsMoveNm).
 3. [Редактировать данные карточки товара](./item-management#tag/listings/operation/postV2CardsUpdate).
 4. Работать с корзиной: можно [переносить карточки товаров](./item-management#tag/listings/operation/postV2CardsDeleteTrash) в корзину и [восстанавливать их](./item-management#tag/listings/operation/postV2CardsRecover).
 5. Получать [списки карточек товаров в корзине](./item-management#tag/listings/operation/postV2GetCardsTrash).
