---
title: Получение накладных поставки по ID магазина
api: uzum-seller
method: GET
path: /v1/shop/{shopId}/invoice
operation_id: getShopInvoicesByShopId
tags:
  - FBO Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 95ea9ca5528d682e
---

# Получение накладных поставки по ID магазина

`GET /v1/shop/{shopId}/invoice`

Этот метод позволяет получить список накладных поставки для указанного магазина.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopId` | path | integer<int64> | да | ID магазина, для которого необходимо получить список накладных поставки. |
| `size` | query | integer<int32> | нет | Количество записей на странице (постраничный просмотр). |
| `page` | query | integer<int32> | нет | Номер страницы для постраничного просмотра накладных поставки. |

## Ответы

**200** — OK

- `id` — integer<int64>. Уникальный идентификатор накладной.
- `invoiceNumber` — integer<int64>. Номер накладной, используемый для идентификации.
- `deliveryCertificate` — string. Сертификат поставки, подтверждающий доставку.
- `dateCreated` — string. Дата создания накладной.
- `status` — string. Статус накладной (устарело, используйте invoiceStatus).
- `invoiceStatus` — object. Статус накладной с более детальной информацией.
  - `text` — string. Текстовое описание статуса накладной, например, 'В обработке'.
  - `color` — string. Цвет, соответствующий текущему статусу накладной, для визуального отображения.
  - `value` — string. Ключевое значение статуса, например, 'ACCEPTED' или 'PENDING'.
- `fullPrice` — integer<int64>. Полная стоимость всех товаров в накладной.
- `timeSlotReservation` — object. Зарезервированный временной интервал для доставки или получения товаров по накладной.
  - `id` — integer<int64>. Идентификатор резервации.
  - `timeSlots` — array[object]. Reserved time slots
    - `timeFrom` — string<date-time>. Модель временного слота.
    - `timeTo` — string<date-time>. Конец временного слота.
  - `status` — string (RESERVED, CANCELED). Статус резервации, например, 'RESERVED' или 'CANCELED'.
  - `timeFrom` — string<date-time>. Начало зарезервированного временного интервала.
  - `timeTo` — string<date-time>. Окончание зарезервированного временного интервала.
- `totalAccepted` — integer<int32>. Общее количество товаров, принятых по накладной.
- `totalToStock` — integer<int32>. Общее количество товаров, которые должны быть добавлены на склад по накладной.
- `remainingAmountOfUpdates` — integer<int32>. Оставшееся количество возможных обновлений по накладной.
- `dateAccepted` — string<date-time>. Дата, когда накладная была принята.
- `expressAcceptanceDate` — string<date-time>. Дата ускоренного принятия накладной, если применимо.
- `stock` — object. Информация о складе, связанном с накладной.
  - `id` — integer<int64>. Уникальный идентификатор склада.
  - `externalId` — string. Внешний идентификатор склада, используемый в других системах.
  - `title` — string. Название склада.
  - `address` — string. Адрес, по которому находится склад.
  - `timeFrom` — string. Время начала работы склада.
  - `timeTo` — string. Время окончания работы склада.
  - `poolSource` — string. Источник складского пула, если применимо.
  - `dimensionalGroups` — array[object]. Список габаритных групп, которые склад поддерживает для хранения товаров.
    - `group` — string (SMALL, MEDIUM, LARGE, UNKNOWN). Категория размера товара, например, малая, средняя или большая.
    - `title` — string. Название категории размера.
- `externalNumber` — string. Внешний номер накладной, используемый для идентификации вне системы.
