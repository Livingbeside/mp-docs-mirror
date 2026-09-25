---
title: Получение заказов продавца
api: uzum-seller
method: GET
path: /v2/fbs/orders
operation_id: getFbsOrdersV2
tags:
  - Работа с заказами FBS/DBS
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 3f374ef83b2b3a77
---

# Получение заказов продавца

`GET /v2/fbs/orders`

Возвращает заказы продавца по статусу.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopIds` | query | array[integer<int64>] | да | Массив идентификаторов магазинов, для которых нужно получить заказы. |
| `status` | query | string (CREATED, PACKING, PENDING_DELIVERY, DELIVERING, DELIVERED, ACCEPTED_AT_DP, DELIVERED_TO_CUSTOMER_DELIVERY_POINT, COMPLETED, CANCELED, PENDING_CANCELLATION, RETURNED) | нет | Статус заказов, которые нужно получить. |
| `scheme` | query | string (FBS, DBS) | нет | Тип заказа. Если ничего не передать, вернутся и FBS и DBS |
| `dateFrom` | query | integer<int64> | нет | Дата, с которой необходимо показывать заказы |
| `dateTo` | query | integer<int64> | нет | Дата, по которую необходимо показывать заказы |
| `page` | query | integer<int32> | нет | Номер страницы для получения данных (начинается с 0) |
| `size` | query | integer<int32> | нет | Количество возвратов на странице (максимум 50). |

## Ответы

**200** — Success

- `payload` — object. Информация о заказах продавца.
  - `orders` — array[object]. Список заказов.
    - `id` — integer<int64>. Уникальный идентификатор заказа.
    - `status` — string (CREATED, PACKING, DELIVERED, DELIVERED_TO_CUSTOMER_DELIVERY_POINT, COMPLETED, CANCELED, PENDING_CANCELLATION, RETURNED). Статус заказа.
    - `dateCreated` — string<date-time>. Дата создания заказа.
    - `acceptUntil` — string<date-time>. Дата, до которой заказ может быть принят.
    - `deliverUntil` — string<date-time>. Дата, до которой заказ должен быть доставлен.
    - `deliveringDate` — string<date-time>. Дата перехода заказа в статус DELIVERING
    - `deliveryDate` — string<date-time>. Дата фактической доставки заказа.
    - `acceptedDate` — string<date-time>. Дата принятия заказа продавцом.
    - `deliveredToDeliveryPointDate` — string<date-time>. Дата доставки заказа в пункт доставки.
    - `completedDate` — string<date-time>. Дата завершения заказа.
    - `dateCancelled` — string<date-time>. Дата отмены заказа.
    - `returnDate` — string<date-time>. Дата возврата заказа.
    - `cancelReason` — string. Причина отмены заказа.
    - `identifierRequired` — boolean. Требуется ли идентификатор для обработки заказа.
    - `price` — integer<int64>. Стоимость заказа.
    - `shopId` — integer<int64>. Идентификатор магазина, связанного с заказом.
    - `stock` — object. Информация о складе, связанном с заказом.
      - `id` — integer<int64>. Уникальный идентификатор склада
      - `externalId` — string. Внешний идентификатор склада
      - `title` — string. Название склада
      - `address` — string. Адрес склада
      - `timeFrom` — string. Время начала работы склада
      - `timeTo` — string. Время окончания работы склада
      - `poolSource` — string. Источник складских запасов
      - `dimensionalGroups` — array[object]. Список размерных групп, поддерживаемых складом
        - `group` — string (SMALL, MEDIUM, LARGE, UNKNOWN). Группа размеров: малый, средний, большой или неизвестный
        - `title` — string. Название размерной группы
    - `orderItems` — array[object]. Список товаров в заказе.
      - `id` — integer<int64>. Идентификатор элемента заказа
      - `status` — string (TO_WITHDRAW, PROCESSING, CANCELED, PARTIALLY_CANCELLED). Статус элемента заказа
      - `date` — integer<int64>. Время в формате Unix Epoch в миллисекундах (пример: 1727427283895)
      - `orderId` — integer<int64>. Идентификатор заказа
      - `skuTitle` — string. Название SKU
      - `sellerSkuCode` — string. Идентификатор SKU селлера. Отсутствует, если селлер не задал код для этого SKU
      - `productId` — integer<int64>. Идентификатор продукта
      - `productImage` — object. Изображение продукта
        - `photo` — object
        - `photoKey` — string. Уникальный ключ изображения
        - `color` — string. Цвет изображения, может быть null
        - `hasVerticalPhoto` — boolean. Имеет ли изображение вертикальную ориентацию
      - `shopId` — integer<int64>. Идентификатор магазина
      - `dateIssued` — integer<int64>. Время в формате Unix Epoch в миллисекундах (пример: 1727427283895)
      - `sellerPrice` — integer<int64>. Цена продавца
      - `amount` — integer. Количество
      - `amountReturns` — integer. Количество возвратов
      - `commission` — integer<int64>. Комиссия
      - `sellerProfit` — integer<int64>. Прибыль продавца
      - `purchasePrice` — integer<int64>. Цена закупки
      - `logisticDeliveryFee` — integer<int64>. Стоимость логистики
      - `cancelled` — integer<int64>. Количество отмен
      - `withdrawnProfit` — integer<int64>. Прибыль после вычета
      - `returnCause` — string. Причина возврата
      - `comment` — string. Комментарий
      - `skuCharValue` — string. Значение характеристики SKU
      - `skuCharTitle` — string. Название характеристики SKU
      - `productTitle` — string. Название продукта
    - `place` — string. Информация о месте обработки заказа.
    - `invoiceNumber` — integer<int64>. Номер накладной
    - `timeSlot` — object. Модель временного интервала
      - `timeFrom` — string<date-time>. Время начала временного интервала
      - `timeTo` — string<date-time>. Время окончания временного интервала
    - `dropOffPoint` — object. Пункт приема
      - `uuid` — string<uuid>. Идентификатор пункта приема
      - `address` — string. Адрес пункта приема
      - `type` — string (UNKNOWN, STOCK, ISSUE_POINT, UZ_POST, UCELL, NOT_UZUM, PHOTO_STUDIO, CROSS_DOCK, DROP_OFF_POINT, SORT_CENTER). Тип пункта доставки
    - `scheme` — string (FBS, DBS, FBO). Тип заказа
    - `deliveryInfo` — object. Данные о доставке заказа
      - `deliveryAddress` — string **обязательный**. Адрес покупателя
      - `customerFullname` — string **обязательный**. ФИО покупателя
      - `customerPhone` — string **обязательный**. Номер телефона покупателя
      - `deliveryComment` — string. Комментарий покупателя
  - `totalAmount` — integer<int64>. Общее количество заказов.
- `errors` — array[object]. Список ошибок, возникших при обработке запроса.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Метка времени ответа.
- `trace` — string. Трассировочная информация для отладки.
- `error` — string. Описание ошибки, если она произошла.

**400** — seller-order-12 - dateTo is before dateFrom

- `payload` — object. Информация о заказах продавца.
  - `orders` — array[object]. Список заказов.
    - `id` — integer<int64>. Уникальный идентификатор заказа.
    - `status` — string (CREATED, PACKING, DELIVERED, DELIVERED_TO_CUSTOMER_DELIVERY_POINT, COMPLETED, CANCELED, PENDING_CANCELLATION, RETURNED). Статус заказа.
    - `dateCreated` — string<date-time>. Дата создания заказа.
    - `acceptUntil` — string<date-time>. Дата, до которой заказ может быть принят.
    - `deliverUntil` — string<date-time>. Дата, до которой заказ должен быть доставлен.
    - `deliveringDate` — string<date-time>. Дата перехода заказа в статус DELIVERING
    - `deliveryDate` — string<date-time>. Дата фактической доставки заказа.
    - `acceptedDate` — string<date-time>. Дата принятия заказа продавцом.
    - `deliveredToDeliveryPointDate` — string<date-time>. Дата доставки заказа в пункт доставки.
    - `completedDate` — string<date-time>. Дата завершения заказа.
    - `dateCancelled` — string<date-time>. Дата отмены заказа.
    - `returnDate` — string<date-time>. Дата возврата заказа.
    - `cancelReason` — string. Причина отмены заказа.
    - `identifierRequired` — boolean. Требуется ли идентификатор для обработки заказа.
    - `price` — integer<int64>. Стоимость заказа.
    - `shopId` — integer<int64>. Идентификатор магазина, связанного с заказом.
    - `stock` — object. Информация о складе, связанном с заказом.
      - `id` — integer<int64>. Уникальный идентификатор склада
      - `externalId` — string. Внешний идентификатор склада
      - `title` — string. Название склада
      - `address` — string. Адрес склада
      - `timeFrom` — string. Время начала работы склада
      - `timeTo` — string. Время окончания работы склада
      - `poolSource` — string. Источник складских запасов
      - `dimensionalGroups` — array[object]. Список размерных групп, поддерживаемых складом
        - `group` — string (SMALL, MEDIUM, LARGE, UNKNOWN). Группа размеров: малый, средний, большой или неизвестный
        - `title` — string. Название размерной группы
    - `orderItems` — array[object]. Список товаров в заказе.
      - `id` — integer<int64>. Идентификатор элемента заказа
      - `status` — string (TO_WITHDRAW, PROCESSING, CANCELED, PARTIALLY_CANCELLED). Статус элемента заказа
      - `date` — integer<int64>. Время в формате Unix Epoch в миллисекундах (пример: 1727427283895)
      - `orderId` — integer<int64>. Идентификатор заказа
      - `skuTitle` — string. Название SKU
      - `sellerSkuCode` — string. Идентификатор SKU селлера. Отсутствует, если селлер не задал код для этого SKU
      - `productId` — integer<int64>. Идентификатор продукта
      - `productImage` — object. Изображение продукта
        - `photo` — object
        - `photoKey` — string. Уникальный ключ изображения
        - `color` — string. Цвет изображения, может быть null
        - `hasVerticalPhoto` — boolean. Имеет ли изображение вертикальную ориентацию
      - `shopId` — integer<int64>. Идентификатор магазина
      - `dateIssued` — integer<int64>. Время в формате Unix Epoch в миллисекундах (пример: 1727427283895)
      - `sellerPrice` — integer<int64>. Цена продавца
      - `amount` — integer. Количество
      - `amountReturns` — integer. Количество возвратов
      - `commission` — integer<int64>. Комиссия
      - `sellerProfit` — integer<int64>. Прибыль продавца
      - `purchasePrice` — integer<int64>. Цена закупки
      - `logisticDeliveryFee` — integer<int64>. Стоимость логистики
      - `cancelled` — integer<int64>. Количество отмен
      - `withdrawnProfit` — integer<int64>. Прибыль после вычета
      - `returnCause` — string. Причина возврата
      - `comment` — string. Комментарий
      - `skuCharValue` — string. Значение характеристики SKU
      - `skuCharTitle` — string. Название характеристики SKU
      - `productTitle` — string. Название продукта
    - `place` — string. Информация о месте обработки заказа.
    - `invoiceNumber` — integer<int64>. Номер накладной
    - `timeSlot` — object. Модель временного интервала
      - `timeFrom` — string<date-time>. Время начала временного интервала
      - `timeTo` — string<date-time>. Время окончания временного интервала
    - `dropOffPoint` — object. Пункт приема
      - `uuid` — string<uuid>. Идентификатор пункта приема
      - `address` — string. Адрес пункта приема
      - `type` — string (UNKNOWN, STOCK, ISSUE_POINT, UZ_POST, UCELL, NOT_UZUM, PHOTO_STUDIO, CROSS_DOCK, DROP_OFF_POINT, SORT_CENTER). Тип пункта доставки
    - `scheme` — string (FBS, DBS, FBO). Тип заказа
    - `deliveryInfo` — object. Данные о доставке заказа
      - `deliveryAddress` — string **обязательный**. Адрес покупателя
      - `customerFullname` — string **обязательный**. ФИО покупателя
      - `customerPhone` — string **обязательный**. Номер телефона покупателя
      - `deliveryComment` — string. Комментарий покупателя
  - `totalAmount` — integer<int64>. Общее количество заказов.
- `errors` — array[object]. Список ошибок, возникших при обработке запроса.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Метка времени ответа.
- `trace` — string. Трассировочная информация для отладки.
- `error` — string. Описание ошибки, если она произошла.
