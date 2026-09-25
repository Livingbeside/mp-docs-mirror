---
title: Получение списка заказов.
api: uzum-seller
method: GET
path: /v1/finance/orders
operation_id: getFinanceOrders
tags:
  - Finance
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 9397260444b00fe1
---

# Получение списка заказов.

`GET /v1/finance/orders`

Этот метод позволяет получить список продаж.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `page` | query | integer<int32> | нет | Номер страницы для постраничного просмотра накладных поставки. |
| `size` | query | integer<int32> | нет | Количество записей на странице (постраничный просмотр). |
| `group` | query | boolean | нет | Группировать заказы или нет. В зависимости от состояния этого флага, будет возвращаться то или иное наполнения поля orderItems. > Если флаг true: вернется `ProductGroupedSellerItem` Если флаг false: вернется `SellerOrderItemDto` |
| `dateFrom` | query | integer<int64> | нет | Дата, с которой необходимо показывать заказы |
| `dateTo` | query | integer<int64> | нет | Дата, с которой необходимо показывать заказы |
| `statuses` | query | array[string (TO_WITHDRAW, PROCESSING, CANCELED, PARTIALLY_CANCELLED)] | нет | Статусы заказов (к выводу средств (TO_WITHDRAW), в обработке (PROCESSING), отменен (CANCELED), частично отменен( PARTIALLY_CANCELLED)) |
| `shopIds` | query | array[integer<int64>] | да | Список магазинов, для которых необходимо показывать заказы |

## Ответы

**200** — OK

- `orderItems` — array[object]. Список элементов заказа для финансовых расчетов
- `totalElements` — integer<int32>. Общее количество элементов

**400** — Bad request

- `payload` — object. Данные ответа, содержит информацию об объекте, возвращаемом сервисом.
- `errors` — array[object]. Список ошибок, если запрос не был успешно выполнен.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Время формирования ответа, формат даты и времени.
- `trace` — string. Трассировка для отладки ошибок.
- `error` — string. Сообщение об ошибке, если оно имеется.
