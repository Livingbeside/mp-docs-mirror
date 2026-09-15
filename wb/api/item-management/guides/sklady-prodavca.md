---
title: Склады продавца
api: wb-item-management
tag: sellerWarehouses
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: 2973bd8c71bd2518
---

# Склады продавца

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о складах продавца можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-6?categoryId=2a88d2ed-45c4-4205-a540-7d0e87f0193d)

На складах продавца доступно управление [остатками товаров](./item-management#tag/sellerWarehousesInventory).

Чтобы работать со складами продавца, вы можете:
 1. Получать [список складов WB](./item-management#tag/sellerWarehouses/operation/getV3Offices), чтобы связывать склады WB и склады продавца при [создании](./item-management#tag/sellerWarehouses/operation/postV3Warehouses) и [редактировании](./item-management#tag/sellerWarehouses/operation/putV3WarehousesWarehouseId) склада.
 2. Получать [список складов продавца](./item-management#tag/sellerWarehouses/operation/getV3Warehouses).
 3. [Получать](./item-management#tag/sellerWarehouses/operation/getV3DbwWarehousesWarehouseIdContacts) и [обновлять](./item-management#tag/sellerWarehouses/operation/putV3DbwWarehousesWarehouseIdContacts) список контактов складов модели DBW.
 4. [Создавать](./item-management#tag/sellerWarehouses/operation/postV3Warehouses) склады модели FBS.
 5. [Обновлять](./item-management#tag/sellerWarehouses/operation/putV3WarehousesWarehouseId) склады продавца.
 6. [Удалять](./item-management#tag/sellerWarehouses/operation/deleteV3WarehousesWarehouseId) склады продавца.
