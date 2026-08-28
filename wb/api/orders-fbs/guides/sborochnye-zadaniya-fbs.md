---
title: Сборочные задания FBS
api: wb-orders-fbs
tag: Сборочные задания FBS
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: 29e4524b466a01ce
---

# Сборочные задания FBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать больше о сборочных заданиях можно в [справочном центре](https://seller.wildberries.ru/instructions/subcategory/6d85301c-719b-4145-9275-2ac8b793f345?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345)

Когда покупатель заказывает товар, у продавца появляется **сборочное задание**. Сборочное задание всегда содержит 1 единицу товара. Если покупатель закажет 10 единиц одного товара одной корзиной, у продавца появятся 10 сборочных заданий. Их можно сгруппировать по одинаковому `orderUid`.

Для работы со сборочными заданиями FBS:
1. [Получите новые сборочные задания](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1new/get).
2. [Создайте поставку и добавьте в неё сборочные задания](./orders-fbs#tag/Postavki-FBS).
3. [Получите стикеры](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1stickers/post) сборочных заданий, распечатайте их и промаркируйте сборочные задания.
4. Если нужно, добавьте к сборочным заданиям [код маркировки Честного знака](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1sgtin/put), [УИН](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1uin/put), [IMEI](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1imei/put), [GTIN](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1gtin/put), [срок годности товара](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1expiration/put) или [номер ДТ](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1marketplace~1v3~1orders~1%7BorderId%7D~1meta~1customs-declaration/put).
5. Если поставка доставляется в пункт выдачи заказов (ПВЗ), переходите к пункту 3 [инструкции](./orders-fbs#tag/Postavki-FBS). Если на склад WB, к пункту 6.
6. [Уточните](./orders-fbs#tag/Propuska-FBS/paths/~1api~1v3~1passes~1offices/get), требуется ли пропуск на склад, на который поедет поставка. Если нужен, [создайте](./orders-fbs#tag/Propuska-FBS/paths/~1api~1v3~1passes/post) пропуск.
