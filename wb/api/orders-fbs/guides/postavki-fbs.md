---
title: Поставки FBS
api: wb-orders-fbs
tag: Поставки FBS
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
content_sha: 9509865e3aae0e24
---

# Поставки FBS

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Маркетплейс

 Узнать больше о поставках FBS можно в [справочном центре](https://seller.wildberries.ru/instructions/material/A-11?goBackOption=prevRoute&categoryId=6d85301c-719b-4145-9275-2ac8b793f345)

Для работы с поставками:

 
 Пункты 3-5 обязательны к выполнению при доставке поставки на пункт выдачи заказов (ПВЗ).
 

 1. [Создайте новую поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies/post). В ответ вернется ID созданной поставки в формате `WB-GI-1234567`.
 1. [Установите параметры отгрузки поставки](./orders-fbs#tag/Postavki-FBS/operation/patchV3FbsSuppliesShippingMethod). Для этого получите [список пунктов отгрузки поставок](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsShippingPoints). Доступно только для продавцов из РФ.

 Для доставки транспортной компанией обязательно укажите ID ЭТрН — электронной транспортной накладной.
 1. В текущую новую поставку [добавьте сборочные задания](./orders-fbs#tag/Postavki-FBS/paths/~1api~1marketplace~1v3~1supplies~1%7BsupplyId%7D~1orders/patch), которые вы повезёте на склад или ПВЗ. После того, как сборочные задания будут добавлены к поставке, они будут переведены в статус `confirm` — на сборке.
 1. [Добавьте грузоместа в поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1trbx/post).
 1. [Проверьте список грузомест](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1trbx/get).
 1. [Получите стикеры грузомест](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1trbx~1stickers/post). Распечатайте и наклейте стикеры на грузоместа.
 1. После того как поставка будет укомплектована нужными сборочными заданиями, необходимо [передать её в доставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1deliver/patch). Если поставка не была передана в доставку, то при сканировании её QR-кода или приёмке первого товара на ПВЗ поставка автоматически закроется. При передаче сборочных заданий в доставку они будут автоматически собраны и переведены в статус `complete` — в доставке.
 1. Для поставок из стран ЕАЭС добавьте данные [СПОТ](https://www.nalog.gov.ru/rn77/related_activities/spot). Получите [список стран ОКСМ](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsDictionariesCountriesOksm) для [добавления данных СПОТ в поставку](./orders-fbs#tag/Postavki-FBS/operation/putV3FbsSuppliesSupplyIdSpot). Вы можете получать [данные СПОТ для списка поставок](./orders-fbs#tag/Postavki-FBS/operation/postV3FbsSuppliesSpotList) и [QR-коды СПОТ](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsSuppliesSupplyIdStickersSpot). Сейчас методы доступны только для продавцов из Кыргызстана. В дальнейшем методы будут доступны продавцам из любой страны ЕАЭС кроме РФ, следите за обновлениями.
 1. Если поставка была отсканирована в пункте приёмки, но при этом в ней всё ещё есть неотсканированные товары, спустя определённое время необходимо доставить их повторно. Проверьте все [сборочные задания, требующие повторной отгрузки на данный момент](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1supplies~1orders~1reshipment/get). Данные сборочные задания можно перевести в [другую активную поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1marketplace~1v3~1supplies~1%7BsupplyId%7D~1orders/patch). Сборочное задание также будет переведено в статус `confirm` — на сборке.

Также вы можете:
 - [удалить грузоместа из поставки](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1trbx/delete), но только пока поставка находится на сборке
 - получить [ID всех сборочных заданий, добавленных к поставке](./orders-fbs#tag/Postavki-FBS/paths/~1api~1marketplace~1v3~1supplies~1%7BsupplyId%7D~1order-ids/get)
 - получить информацию [обо всех поставках продавца](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies/get) или [о конкретной поставке](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/get)
 - [удалить поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/delete) при условии, что она активна и за ней не закреплены сборочные задания
 - [перемещать сборочные задания между активными поставками](./orders-fbs#tag/Postavki-FBS/paths/~1api~1marketplace~1v3~1supplies~1%7BsupplyId%7D~1orders/patch). Нельзя перемещать сборочное задание из уже закрытой поставки, только если оно не требует повторной отгрузки
 - получить [QR-код поставки](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D~1barcode/get) в форматах SVG, ZPL или PNG. Доступно только после передачи поставки в доставку
