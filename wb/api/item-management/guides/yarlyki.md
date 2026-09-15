---
title: Ярлыки
api: wb-item-management
tag: labels
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: c8c038187abefa5d
---

# Ярлыки

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о ярлыках можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-166?categoryId=3a795fe1-d5cb-4120-be1a-387eed6494e5)

Ярлыки позволяют быстро фильтровать и искать карточки товаров в личном кабинете. В разделе вам доступны методы:
 1. [Получения списка ярлыков продавца](./item-management#tag/labels/operation/getV2Tags). Эти ярлыки можно использовать в карточках товаров.
 2. [Добавления новых ярлыков](./item-management#tag/labels/operation/postV2Tag).
 3. [Изменения существующих ярлыков](./item-management#tag/labels/operation/patchV2TagId).
 4. [Удаления ярлыков](./item-management#tag/labels/operation/deleteV2TagId).
 5. [Управления ярлыками в карточке товара](./item-management#tag/labels/operation/postV2TagNomenclatureLink): добавления или удаления ярлыка.
