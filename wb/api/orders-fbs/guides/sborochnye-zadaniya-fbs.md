---
title: Сборочные задания FBS
api: wb-orders-fbs
tag: fbsAssemblyOrders
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: da5ecd16e9342a79
---

# Сборочные задания FBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать больше о сборочных заданиях можно в [справочном центре](https://seller.wildberries.ru/instructions/subcategory/6d85301c-719b-4145-9275-2ac8b793f345?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345)

Когда покупатель заказывает товар, у продавца появляется **сборочное задание**. Сборочное задание всегда содержит 1 единицу товара. Если покупатель закажет 10 единиц одного товара одной корзиной, у продавца появятся 10 сборочных заданий. Их можно сгруппировать по одинаковому `orderUid`.

Для работы со сборочными заданиями FBS:
1. [Получите новые сборочные задания](./orders-fbs#tag/fbsAssemblyOrders/operation/getV3OrdersNew).
2. [Создайте поставку и добавьте в неё сборочные задания](./orders-fbs#tag/fbsSupplies).
3. [Получите стикеры](./orders-fbs#tag/fbsAssemblyOrders/operation/postV3OrdersStickers) сборочных заданий, распечатайте их и промаркируйте сборочные задания.
4. Если нужно, добавьте к сборочным заданиям [код маркировки Честного знака](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaSgtin), [УИН](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaUin), [IMEI](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaImei), [GTIN](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaGtin), [срок годности товара](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaExpiration) или [номер ДТ](./orders-fbs#tag/fbsLabelIdentifiers/operation/putV3OrdersOrderIdMetaCustomsDeclaration).
5. Если поставка доставляется в пункт выдачи заказов (ПВЗ), переходите к пункту 3 [инструкции](./orders-fbs#tag/fbsSupplies). Если на склад WB, к пункту 6.
6. [Уточните](./orders-fbs#tag/fbsPasses/operation/getV3PassesOffices), требуется ли пропуск на склад, на который поедет поставка. Если нужен, [создайте](./orders-fbs#tag/fbsPasses/operation/postV3Passes) пропуск.
