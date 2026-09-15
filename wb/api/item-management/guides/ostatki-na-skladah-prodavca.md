---
title: Остатки на складах продавца
api: wb-item-management
tag: sellerWarehousesInventory
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: dae7a5190aee427e
---

# Остатки на складах продавца

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше об остатках на складах продавца можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-123?categoryId=2a88d2ed-45c4-4205-a540-7d0e87f0193d)

Если вы работаете по модели продаж со [склада продавца](./item-management#tag/sellerWarehouses), через эти методы вы можете:
 1. [Обновлять остатки товаров](./item-management#tag/sellerWarehousesInventory/operation/putV3StocksWarehouseId).
 2. [Удалять остатки](./item-management#tag/sellerWarehousesInventory/operation/deleteV3StocksWarehouseId). После удаления остатки можно будет загрузить повторно.
 3. Проверять [количество остатков](./item-management#tag/sellerWarehousesInventory/operation/postV3StocksWarehouseId).
