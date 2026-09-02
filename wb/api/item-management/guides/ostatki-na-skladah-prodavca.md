---
title: Остатки на складах продавца
api: wb-item-management
tag: Остатки на складах продавца
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: 943a4aacd47d53c9
---

# Остатки на складах продавца

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше об остатках на складах продавца можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-123?categoryId=2a88d2ed-45c4-4205-a540-7d0e87f0193d)

Если вы работаете по модели продаж со [склада продавца](./work-with-products#tag/Sklady-prodavca), через эти методы вы можете:
 1. [Обновлять остатки товаров](./work-with-products#tag/Ostatki-na-skladah-prodavca/paths/~1api~1v3~1stocks~1%7BwarehouseId%7D/put).
 2. [Удалять остатки](./work-with-products#tag/Ostatki-na-skladah-prodavca/paths/~1api~1v3~1stocks~1%7BwarehouseId%7D/delete). После удаления остатки можно будет загрузить повторно.
 3. Проверять [количество остатков](./work-with-products#tag/Ostatki-na-skladah-prodavca/paths/~1api~1v3~1stocks~1%7BwarehouseId%7D/post).
