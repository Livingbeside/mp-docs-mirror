---
title: Получение состава накладной возврата
api: uzum-seller
method: GET
path: /v1/shop/{shopId}/return/{returnId}
operation_id: getShopReturnByShopIdAndReturnId
tags:
  - Return Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: d7f5f1ff6abe7627
---

# Получение состава накладной возврата

`GET /v1/shop/{shopId}/return/{returnId}`

Этот метод позволяет получить список товаров входящих в накладные возврата

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `returnId` | path | integer<int64> | да | ID накладной возврата, для которой необходимо получить содержимое |
| `shopId` | path | integer<int64> | да | ID магазина, для которого необходимо получить список накладных возврата. |

## Ответы

**200** — OK

- `payload` — object. Содержит основные сведения о возврате продавца
  - `id` — integer<int64>. Уникальный идентификатор возврата
  - `dateCreated` — string<date-time>. Дата создания возврата
  - `status` — string. Текущий статус возврата
  - `stock` — object. Сведения о складе, на который возвращается товар
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
  - `timeSlotReservation` — object. Зарезервированный временной интервал для возврата
    - `id` — integer<int64>. Идентификатор резервации временного интервала
    - `timeSlots` — array[object]. Зарезервированные временные интервалы
      - `timeFrom` — string<date-time>. Время начала временного интервала
      - `timeTo` — string<date-time>. Время окончания временного интервала
    - `status` — string (RESERVED, CANCELED). Статус резервации, например, RESERVED или CANCELED
    - `timeFrom` — string<date-time>. Начало зарезервированного временного интервала
    - `timeTo` — string<date-time>. Окончание зарезервированного временного интервала
  - `paidStorage` — object. Информация о платном хранении для возврата
    - `startDate` — string<date-time> **обязательный**. Дата начала платного хранения
    - `endDate` — string<date-time>. Фактическая дата окончания платного хранения
    - `status` — string (PENDING, ACTIVE, COMPLETED, EXPIRED) **обязательный**. Текущий статус платного хранения, например, PENDING, ACTIVE, COMPLETED, EXPIRED
  - `executionDate` — string<date-time>. Дата исполнения возврата в зависимости от его статуса (например, завершено или отменено)
  - `assembledDate` — string<date-time>. Дата сборки возвращенного товара
  - `completedDate` — string<date-time>. Дата завершения возврата
  - `canceledDate` — string<date-time>. Дата отмены возврата
  - `externalNumber` — string **обязательный**. Электронный номер накладной на возврат
  - `type` — string (DEFECTED, RETURN, FBS) **обязательный**. Тип возврата: 'FBS' - Fulfilled by Seller, 'DEFECTED' - Дефектный товар, 'RETURN' - Стандартный возврат
  - `returnItems` — array[object]. Список предметов, возвращенных по этому возврату
    - `id` — integer<int64>. Уникальный идентификатор элемента возврата
    - `skuId` — integer<int64>. Идентификатор SKU
    - `amount` — integer<int32>. Количество возвращаемых единиц
    - `packedAmount` — integer<int32>. Количество упакованных единиц для возврата
    - `skuTitle` — string. Название SKU
    - `productTitle` — string. Название продукта
    - `purchasePrice` — integer<int64>. Цена закупки единицы продукта
  - `totalAmount` — integer<int32> **обязательный**. Общее количество возвращенных товаров
  - `totalPackedAmount` — integer<int32> **обязательный**. Общее количество упакованных товаров для возврата
  - `countAllowedChange` — integer<int32> **обязательный**. Допустимое количество изменений временного интервала
  - `maxCountAllowedChange` — integer<int32> **обязательный**. Максимальное количество разрешенных изменений временного интервала
- `errors` — array[object]. Список ошибок, возникших при выполнении запроса
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Метка времени, когда был сгенерирован ответ
- `trace` — string. Информация для отладки
- `error` — string. Сообщение об ошибке, если оно присутствует
