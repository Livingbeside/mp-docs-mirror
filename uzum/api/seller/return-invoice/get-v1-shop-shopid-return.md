---
title: Получение накладных возврата
api: uzum-seller
method: GET
path: /v1/shop/{shopId}/return
operation_id: getShopReturnsByShopId
tags:
  - Return Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 2b81cb8ec742feaa
---

# Получение накладных возврата

`GET /v1/shop/{shopId}/return`

Этот метод позволяет получить список накладных возврата.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopId` | path | integer<int64> | да | ID магазина, для которого необходимо получить список накладных возврата. |
| `page` | query | integer<int32> | нет | Номер страницы для постраничного просмотра накладных поставки. |
| `size` | query | integer<int32> | нет | Количество записей на странице (постраничный просмотр). |

## Ответы

**200** — OK

- `id` — integer<int64>. Идентификатор возврата.
- `dateCreated` — string<date-time>. Дата создания возврата.
- `status` — string. Статус возврата, например, 'COMPLETED' или 'PENDING'.
- `stock` — object. Информация о складе, на который возвращается товар.
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
- `timeSlotReservation` — object. Зарезервированный временной интервал для возврата.
  - `id` — integer<int64>. Идентификатор резервации.
  - `timeSlots` — array[object]. Reserved time slots
    - `timeFrom` — string<date-time>. Модель временного слота.
    - `timeTo` — string<date-time>. Конец временного слота.
  - `status` — string (RESERVED, CANCELED). Статус резервации, например, 'RESERVED' или 'CANCELED'.
  - `timeFrom` — string<date-time>. Начало зарезервированного временного интервала.
  - `timeTo` — string<date-time>. Окончание зарезервированного временного интервала.
- `paidStorage` — object. Информация об оплачиваемом хранении для возвращенного товара.
  - `startDate` — string<date-time> **обязательный**. Дата начала платного хранения
  - `endDate` — string<date-time>. Фактическая дата окончания платного хранения
  - `status` — string (PENDING, ACTIVE, COMPLETED, EXPIRED) **обязательный**. Статус платного хранения, например, 'PENDING', 'ACTIVE', 'COMPLETED', или 'EXPIRED'.
- `executionDate` — string<date-time>. Дата исполнения возврата в зависимости от его статуса (COMPLETED, CANCELED и т.д.).
- `assembledDate` — string<date-time>. Дата сборки возврата.
- `completedDate` — string<date-time>. Дата завершения возврата, если он выполнен.
- `canceledDate` — string<date-time>. Дата отмены возврата, если он был отменен.
- `externalNumber` — string **обязательный**. Электронный номер товаросопроводительного документа.
- `type` — string (DEFECTED, RETURN, FBS) **обязательный**. Тип возврата: 'DEFECTED' для дефектного товара, 'RETURN' для обычного возврата, 'FBS' для доставки продавцом.
