---
title: Склады продавца
api: wb-work-with-products
tag: Склады продавца
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
content_sha: 1d31faf7f16f051d
---

# Склады продавца

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о складах продавца можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-6?categoryId=2a88d2ed-45c4-4205-a540-7d0e87f0193d)

На складах продавца доступно управление [остатками товаров](./work-with-products#tag/Ostatki-na-skladah-prodavca).

Чтобы работать со складами продавца, вы можете:
 1. Получать [список складов WB](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1offices/get), чтобы связывать склады WB и склады продавца при [создании](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses/post) и [редактировании](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses~1%7BwarehouseId%7D/put) склада.
 2. Получать [список складов продавца](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses/get).
 3. [Получать](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1dbw~1warehouses~1%7BwarehouseId%7D~1contacts/get) и [обновлять](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1dbw~1warehouses~1%7BwarehouseId%7D~1contacts/put) список контактов складов модели DBW.
 4. [Создавать](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses/post) склады модели FBS.
 5. [Обновлять](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses~1%7BwarehouseId%7D/put) склады продавца.
 6. [Удалять](./work-with-products#tag/Sklady-prodavca/paths/~1api~1v3~1warehouses~1%7BwarehouseId%7D/delete) склады продавца.
