---
title: Получение списка накладных
api: uzum-seller
method: GET
path: /v1/invoice
operation_id: getSellerInvoice
tags:
  - FBO Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 1260477d98716af8
---

# Получение списка накладных

`GET /v1/invoice`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `size` | query | integer<int32> | нет | Количество накладных на странице (максимум 50). |
| `page` | query | integer<int32> | нет | Номер страницы для получения данных (начинается с 0). |

## Ответы

**200** — OK

- `id` — integer<int64>. Уникальный идентификатор накладной.
- `shopId` — integer<int64>. Идентификатор магазина, связанного с накладной.
- `shopTitle` — string. Название магазина, связанного с накладной.
- `invoiceNumber` — integer<int64>. Номер накладной.
- `deliveryCertificate` — string. Документ подтверждающий доставку.
- `dateCreated` — string. Дата создания накладной.
- `status` — string. Старый статус накладной (устаревший, используйте invoiceStatus).
- `invoiceStatus` — object. Текущий статус накладной.
  - `text` — string. Текстовое описание статуса накладной, например, 'В обработке'.
  - `color` — string. Цвет, соответствующий текущему статусу накладной, для визуального отображения.
  - `value` — string. Ключевое значение статуса, например, 'ACCEPTED' или 'PENDING'.
- `fullPrice` — integer<int64>. Полная стоимость накладной.
- `timeSlotReservation` — object. Информация о зарезервированном временном интервале для доставки/приемки.
  - `id` — integer<int64>. Идентификатор резервации временного интервала
  - `timeSlots` — array[object]. Зарезервированные временные интервалы
    - `timeFrom` — string<date-time>. Время начала временного интервала
    - `timeTo` — string<date-time>. Время окончания временного интервала
  - `status` — string (RESERVED, CANCELED). Статус резервации, например, RESERVED или CANCELED
  - `timeFrom` — string<date-time>. Начало зарезервированного временного интервала
  - `timeTo` — string<date-time>. Окончание зарезервированного временного интервала
- `totalAccepted` — integer<int32>. Общее количество товаров, принятых по накладной.
- `totalToStock` — integer<int32>. Общее количество товаров, которые должны быть добавлены на склад.
- `remainingAmountOfUpdates` — integer<int32>. Количество оставшихся возможных обновлений накладной.
- `dateAccepted` — string<date-time>. Дата, когда накладная была принята.
- `expressAcceptanceDate` — string<date-time>. Дата и время экспресс-приемки накладной.
- `stock` — object. Информация о складе, связанная с накладной.
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
- `externalNumber` — string. Внешний номер накладной (если применимо).
- `productForInvoiceDto` — array[object]. Список товаров, включенных в накладную.
  - `id` — integer<int64>. Уникальный идентификатор продукта для счета-фактуры
  - `skuTitle` — string. Название SKU продукта
  - `productTitle` — string. Название продукта
  - `quantityToStock` — integer<int32>. Количество единиц на складе
  - `quantityAccepted` — integer<int32>. Количество принятых единиц
  - `purchasePrice` — integer<int64>. Цена закупки единицы продукта
  - `skuForInvoiceDtoList` — array[object]. Список SKU, связанных с продуктом для счета-фактуры
    - `id` — integer<int64>. Уникальный идентификатор SKU для счета-фактуры
    - `skuTitle` — string. Название SKU
    - `quantityToStock` — integer<int32>. Количество SKU на складе
    - `quantityAccepted` — integer<int32>. Количество принятых SKU
    - `purchasePrice` — integer<int64>. Цена закупки SKU

**400** — Bad Request

- `payload` — object. Данные ответа, содержит информацию об объекте, возвращаемом сервисом.
- `errors` — array[object]. Список ошибок, если запрос не был успешно выполнен.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Время формирования ответа, формат даты и времени.
- `trace` — string. Трассировка для отладки ошибок.
- `error` — string. Сообщение об ошибке, если оно имеется.
