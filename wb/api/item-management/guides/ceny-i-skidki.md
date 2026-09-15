---
title: Цены и скидки
api: wb-item-management
tag: pricesAndDiscounts
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: 9df67d72457597df
---

# Цены и скидки

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Цены и скидки

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

 Узнать больше о ценах и скидках можно в [справочном центре](https://seller.wildberries.ru/instructions/ru/ru/subcategory/85fc88fa-a455-4df8-b530-bc67761edf84)

С помощью этих методов можно устанавливать [цены и скидки](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTask), в том числе [цены для размеров одного товара](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskSize), [скидки WB Клуба](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskClubDiscount) и [оптовые скидки для B2B-продаж](./item-management#tag/pricesAndDiscounts/operation/postV1UploadTaskB2bWholesale).

Когда вы обновляете цены или скидки, данные по каким-то товарам могут не обновиться. Например, если вы передали неправильную цену или скидку. Проверяйте статус загрузки с помощью метода [состояния обработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryTasks).

Статусы загрузки:
 - `3` — обработана. В товарах нет ошибок, цены и скидки обновились.
 - `4` — отменена.
 - `5` — обработана, но в товарах есть ошибки. Ошибки можно получить с помощью метода [детализации обработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask). Для товаров без ошибок цены и скидки обновились.
 - `6` — обработана, но во всех товарах есть ошибки. Ошибки можно получить с помощью метода [детализации обработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask).

Если вы задаёте скидки в [календаре акций](./promotion#tag/promoCalendar), загрузки попадают в обработку. Скидка применится в момент старта акции. У такой загрузки будет статус `1`, получить информацию о ней можно с помощью методов [состояния необработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2BufferTasks) и [детализации необработанной загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2BufferGoodsTask).

Вы можете создавать карточки товара в песочнице [Контента](./api-information#tag/authorization/Kategorii-tokenov), а потом редактировать цены карточек в песочнице Цен и скидок.

 У загрузки не может быть статуса 2.
