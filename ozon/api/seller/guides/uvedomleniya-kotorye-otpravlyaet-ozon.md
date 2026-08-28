---
title: Уведомления, которые отправляет Ozon
api: ozon-seller
tag: push_types
group: Пуш-уведомления
kind: guide
source: "https://docs.ozon.ru/api/seller/"
content_sha: f3f0ce467cc7b561
---

# Уведомления, которые отправляет Ozon

Уведомление о новом заказе может приходить с задержкой.
Чтобы иметь актуальную информацию, периодически получайте список необработанных отправлений через метод [POST /v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList).

Для каждого из типов уведомлений Ozon отправляет REST-запросы на адрес вашего сервиса. Ваш сервис [должен отвечать](#tag/service_response) по стандартам REST API.

| Тип | Назначение |
|---------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| [TYPE_PING](#section/Zapros-dlya-proverki-soedineniya) | Проверка статуса готовности сервиса при первичном подключении и периодически после подключения |
| [TYPE_NEW_POSTING](#section/Novoe-otpravlenie) | Новое отправление |
| [TYPE_POSTING_CANCELLED](#section/Otmena-otpravleniya) | Отмена отправления |
| [TYPE_STATE_CHANGED](#section/Izmenenie-statusa-otpravleniya) | Изменение статуса отправления |
| [TYPE_CUTOFF_DATE_CHANGED](#section/Izmenenie-daty-otgruzki-otpravleniya) | Изменение даты отгрузки отправления |
| [TYPE_DELIVERY_DATE_CHANGED](#section/Izmenenie-daty-dostavki-otpravleniya) | Изменение даты доставки отправления |
| [TYPE_CREATE_OR_UPDATE_ITEM](#section/Sozdanie-ili-obnovlenie-tovara) | Создание и обновление товара или ошибка в процессе |
| [TYPE_CREATE_ITEM](#section/Sozdanie-tovara) | Создание товара или ошибка при его создании |
| [TYPE_UPDATE_ITEM](#section/Obnovlenie-tovara) | Обновление товара или ошибка при обновлении |
| [TYPE_STOCKS_CHANGED](#section/Izmenenie-ostatkov-na-skladah-prodavca) | Изменение остатков на складах продавца |
| [TYPE_NEW_MESSAGE](#section/Novoe-soobshenie-v-chate) | Новое сообщение в чате |
| [TYPE_UPDATE_MESSAGE](#section/Soobshenie-v-chate-izmeneno) | Изменение сообщения в чате |
| [TYPE_MESSAGE_READ](#section/Vashe-soobshenie-prochitano) | Ваше сообщение прочитано покупателем или поддержкой |
| [TYPE_CHAT_CLOSED](#section/Chat-zakryt) | Чат закрыт |
| [TYPE_DESCRIPTION_CATEGORY_TREE_CHANGED](#section/Izmenenie-dereva-kategorij) | Изменение дерева категорий |
| [TYPE_FBO_POSTING_NEW](#section/Novoe-otpravlenie-FBO) | Новое отправление FBO |
| [TYPE_FBO_POSTING_CANCELLED](#section/Otmena-otpravleniya-FBO) | Отмена отправления FBO |
| [TYPE_FBO_POSTING_STATE_CHANGED](#section/Izmenenie-statusa-otpravleniya-FBO) | Изменение статуса отправления FBO |
| [TYPE_FBO_POSTING_DELIVERY_DATE_CHANGED](#section/Izmenenie-daty-dostavki-otpravleniya-FBO) | Изменение даты доставки отправления FBO |
| [TYPE_FBO_STOCKS_CHANGED](#section/Izmenenie-ostatkov-na-skladah-Ozon) | Изменение остатков на складах Ozon |
| [TYPE_ORDER_NEW](#section/Novyj-zakaz) | Новый заказ |
| [TYPE_ORDER_CANCELLED](#section/Otmena-zakaza) | Отмена заказа |
| [TYPE_ORDER_STATE_CHANGED](#section/Izmenenie-statusa-zakaza) | Изменение статуса заказа |

## Новое отправление

 При поздней оплате заказа поле in_process_at может быть пустым. Вы можете проверить дату отгрузки через метод [POST /v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) в поле result.in_process_at.

Уведомления приходят только для FBS и rFBS отправлений:

```
{
 "message_type": "TYPE_NEW_POSTING",
 "posting_number": "24319409-0021-1",
 "products": [
 {
 "sku": 147451939,
 "offer_id": "Товар2",
 "quantity": 1
 }
 ],
 "in_process_at": "2021-01-26T06:56:36.294Z",
 "warehouse_id": 12850503335000,
 "shipment_date": "2021-01-26T06:56:36.294Z",
 "tpl_integration_type": "3pl_tracking",
 "is_express": false,
 "tracking_number": "ZZV-23",
 "delivery_date_begin": "2025-01-26T06:56:36.294Z",
 "delivery_date_end": "2025-01-26T06:56:36.294Z",
 "seller_id": 1
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|----------|
| `message_type` | string | — | Тип уведомления — `TYPE_NEW_POSTING`. |
| `posting_number` | string | — | Номер отправления. |
| `products` | array | — | Информация о товарах. |
| `sku` | integer | int64 | Идентификатор товара в системе Ozon — SKU. |
| `offer_id` | string | — | Идентификатор товара в системе продавца — артикул. |
| `quantity` | integer | int64 | Количество товара. |
| `in_process_at` | string | date-time | Дата и время начала обработки отправления в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада. |
| `shipment_date` | string | date-time | Дата и время, до которой необходимо собрать отправление. |
| `tpl_integration_type` | string | — | Тип интеграции со службой доставки:<br>`ozon` — доставка службой Ozon;
`3pl_tracking` — доставка интегрированной службой;
`non_integrated` — доставка сторонней службой;
`aggregator` — доставка через партнёрскую доставку Ozon;
`hybryd` — схема доставки Почты России.
 |
| `is_express` | boolean | — | Признак доставки express. |
| `tracking_number` | string | — | Трек-номер отправления. |
| `delivery_date_begin` | string | date-time | Дата и время начала доставки. |
| `delivery_date_end` | string | date-time | Дата и время конца доставки. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Отмена отправления

Уведомления приходят только для FBS и rFBS отправлений:

```
{
 "message_type": "TYPE_POSTING_CANCELLED",
 "posting_number": "24219509-0020-1",
 "products": [
 {
 "sku": 147451959,
 "quantity": 1
 }
 ],
 "old_state": "posting_transferred_to_courier_service",
 "new_state": "posting_canceled",
 "changed_state_date": "2021-01-26T06:56:36.294Z",
 "reason": {
 "id": 0,
 "message": "string"
 },
 "warehouse_id": 0,
 "seller_id": 15
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|--------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_POSTING_CANCELLED`. |
| `posting_number` | string | — | Номер отправления. |
| `products` | array | — | Информация о товарах. |
| `sku` | integer | int64 | Идентификатор товара в системе Ozon — SKU. |
| `quantity` | integer | int64 | Количество товара. |
| `old_state` | string | — | Предыдущий статус отправления. |
| `new_state` | string | — | Новый статус отправления: `posting_canceled` — отменено. |
| `changed_state_date` | string | date-time | Дата и время изменения статуса отправления в формате UTC. |
| `reason` | object | — | Информация о причине отмены. | 
| `id` | integer | int64 | Идентификатор причины отмены. |
| `message` | string | — | Причина отмены. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

### Статусы отправлений

- `posting_acceptance_in_progress` — идёт приёмка,
- `posting_created` — создано,
- `posting_transferring_to_delivery` — передаётся в доставку,
- `posting_in_carriage` — в перевозке,
- `posting_not_in_carriage` — не добавлен в перевозку,
- `posting_in_client_arbitration` — клиентский арбитраж доставки,
- `posting_on_way_to_city` — на пути в город,
- `posting_transferred_to_courier_service` — передаётся курьеру,
- `posting_in_courier_service` — курьер в пути,
- `posting_on_way_to_pickup_point` — на пути в пункт выдачи,
- `posting_in_pickup_point` — в пункте выдачи,
- `posting_conditionally_delivered` — условно доставлено,
- `posting_driver_pick_up` — у водителя,
- `posting_not_in_sort_center` — не принят на сортировочном центре.

## Изменение статуса отправления

Соответствие статусных моделей Seller API и статусов пуш-модели.

| Seller API | | Push-модель | |
|-------------------------|-------------------------------------|------------------------------------------|-------------------------------------|
| **Статус** | **Описание** | **Статус** | **Описание** |
| `acceptance_in_progress`| Идёт приёмка. | `posting_acceptance_in_progress` | Идёт приёмка. |
| `awaiting_approve` | Ожидает подтверждения. | `posting_created` | Создана. |
| `awaiting_packaging` | Ожидает упаковки. | `posting_created` | Создана. |
| `awaiting_registration` | Ожидает регистрации. | `posting_awaiting_registration` | Ожидает регистрации. |
| `awaiting_deliver` | Ожидает отгрузки. | `posting_transferring_to_delivery` | Передаётся в доставку. |
| | | `posting_in_carriage` | В перевозке. |
| | | `posting_not_in_carriage` | Не добавлен в перевозку. |
| `arbitration` | Арбитраж. | `posting_in_arbitration` | Арбитраж. |
| `client_arbitration` | Клиентский арбитраж доставки. | `posting_in_client_arbitration` | Клиентский арбитраж. |
| `delivering` | Доставляется. | `posting_on_way_to_city` | На пути в ваш город. |
| | | `posting_transferred_to_courier_service` | Передаётся курьеру. |
| | | `posting_in_courier_service` | Курьер в пути. |
| | | `posting_on_way_to_pickup_point` | На пути в пункт выдачи. |
| | | `posting_in_pickup_point` | В пункте выдачи. |
| | | `posting_conditionally_delivered` | Условно доставлено. |
| `driver_pickup` | У водителя. | `posting_driver_pick_up` | У водителя. |
| `delivered` | Доставлено. | `posting_delivered` | Доставлено. |
| | | `posting_received` | Получено. |
| `cancelled` | Отменено. | `posting_canceled` | Отменено. |
| `not_accepted` | Не принято на сортировочном центре. | `posting_not_in_sort_center` | Не принято на сортировочном центре. |

Уведомления приходят только для FBS и rFBS отправлений.

```
{
 "message_type": "TYPE_STATE_CHANGED",
 "posting_number": "24219509-0020-2",
 "new_state": "posting_delivered",
 "changed_state_date": "2021-02-02T15:07:46.765Z",
 "warehouse_id": 0,
 "seller_id": 15
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|--------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_STATE_CHANGED`. |
| `posting_number` | string | — | Номер отправления. |
| `new_state` | string | — | Новый статус отправления. |
| `changed_state_date` | string | date-time | Дата и время изменения статуса отправления в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

### Статусы отправлений

- `posting_acceptance_in_progress` — идёт приёмка,
- `posting_transferring_to_delivery` — передаётся в доставку,
- `posting_in_carriage` — в перевозке,
- `posting_not_in_carriage` — не добавлен в перевозку,
- `posting_in_arbitration` — арбитраж,
- `posting_in_client_arbitration` — клиентский арбитраж доставки,
- `posting_on_way_to_city` — на пути в город,
- `posting_transferred_to_courier_service` — передаётся курьеру,
- `posting_in_courier_service` — курьер в пути,
- `posting_on_way_to_pickup_point` — на пути в пункт выдачи,
- `posting_in_pickup_point` — в пункте выдачи,
- `posting_conditionally_delivered` — условно доставлено,
- `posting_driver_pick_up` — у водителя,
- `posting_delivered` — доставлено,
- `posting_not_in_sort_center` — не принят на сортировочном центре.

## Изменение даты отгрузки отправления

 Уведомление работает в тестовом режиме. Рекомендуем проверять дату отгрузки через метод [POST /v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3) в поле result.shipment_date.

Поле new_cutoff_date может приходить пустым из-за удаления интервала доставки. Дождитесь назначения новой даты — после этого придёт новое уведомление.

 Иногда уведомления этого типа могут приходить после сборки заказа —&nbsp;игнорируйте их.

Уведомления приходят только для FBS и rFBS отправлений:

```
{
 "message_type": "TYPE_CUTOFF_DATE_CHANGED",
 "posting_number": "24219509-0020-2",
 "new_cutoff_date": "2021-11-24T07:00:00Z",
 "old_cutoff_date": "2021-11-21T10:00:00Z",
 "warehouse_id": 0,
 "seller_id": 15
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_CUTOFF_DATE_CHANGED`. |
| `posting_number` | string | — | Номер отправления. |
| `new_cutoff_date` | string | date-time | Новые дата и время отгрузки в формате UTC. |
| `old_cutoff_date` | string | date-time | Предыдущие дата и время отгрузки в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Изменение даты доставки отправления

Уведомление, которое отправляет Ozon:

Уведомление будет приходить, если товары в отправлении продаются по схемам rFBS и FBS.

Поля new_delivery_date_begin и new_delivery_date_end могут приходить пустыми из-за удаления интервала доставки. Дождитесь назначения новой даты — после этого придёт новое уведомление.

```
{
 "message_type": "TYPE_DELIVERY_DATE_CHANGED",
 "posting_number": "24219509-0020-2",
 "new_delivery_date_begin": "2021-11-24T07:00:00Z",
 "new_delivery_date_end": "2021-11-24T16:00:00Z",
 "old_delivery_date_begin": "2021-11-21T10:00:00Z",
 "old_delivery_date_end": "2021-11-21T19:00:00Z",
 "warehouse_id": 0,
 "seller_id": 15
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|--------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_DELIVERY_DATE_CHANGED`. |
| `posting_number` | string | — | Номер отправления. |
| `new_delivery_date_begin` | string | date-time | Новые дата и время начала доставки в формате UTC. |
| `new_delivery_date_end` | string | date-time | Новые дата и время окончания доставки в формате UTC. |
| `old_delivery_date_begin` | string | date-time | Предыдущие дата и время начала доставки в формате UTC. |
| `old_delivery_date_end` | string | date-time | Предыдущие дата и время окончания доставки в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Создание или обновление товара

Уведомление, которое отправляет Ozon:

```
{
 "message_type": "TYPE_CREATE_OR_UPDATE_ITEM",
 "seller_id": 0,
 "offer_id": "string",
 "product_id": 0,
 "is_error": false,
 "changed_at": "2022-09-01T14:15:22Z"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|-------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `seller_id` | integer | int64 | Идентификатор продавца. |
| `message_type` | string | — | Тип уведомления — `TYPE_CREATE_OR_UPDATE_ITEM`. |
| `offer_id` | string | — | Идентификатор товара в системе продавца — артикул. |
| `product_id` | integer | int64 | Идентификатор товара в системе Ozon — `product_id`. |
| `is_error` | boolean | — | Признак, что при создании или обновлении товара возникли ошибки:<br>• `true` — были ошибки, товар не создан или не обновлён;<br>• `false` — товар создан или обновлён без ошибок. |
| `changed_at` | string | date-time | Дата и время изменения. |

## Создание товара

Отправка пуш-уведомлений TYPE_CREATE_ITEM будет приостановлена 15 июля 2023 года.

Настройте свой сервис для получения уведомлений [TYPE_CREATE_OR_UPDATE_ITEM](#section/Sozdanie-ili-obnovlenie-tovara).

Уведомление, которое отправляет Ozon:

```
{
 "message_type": "TYPE_CREATE_ITEM",
 "seller_id": 0,
 "offer_id": "string",
 "product_id": 0,
 "is_error": false,
 "changed_at": "2021-09-01T14:15:22Z"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|-------------|-----------|---------------------------------------------------------------------------------------------------------------------------------------|
| `seller_id` | integer | int64 | Идентификатор продавца. |
| `message_type` | string | — | Тип уведомления — `TYPE_CREATE_ITEM`. |
| `offer_id` | string | — | Идентификатор товара в системе продавца — артикул. |
| `product_id` | integer | int64 | Идентификатор товара в системе Ozon — `product_id`. |
| `is_error` | boolean | — | Признак, что при создании товара возникли ошибки:<br>• `true` — были ошибки, товар не создан;<br>• `false` — товар создан без ошибок. |
| `changed_at` | string | date-time | Дата и время изменения. |

## Обновление товара

Отправка пуш-уведомлений TYPE_UPDATE_ITEM будет приостановлена 15 июля 2023 года.

Настройте свой сервис для получения уведомлений [TYPE_CREATE_OR_UPDATE_ITEM](#section/Sozdanie-ili-obnovlenie-tovara).

Уведомление, которое отправляет Ozon:

```
{
 "message_type": "TYPE_UPDATE_ITEM",
 "seller_id": 0,
 "offer_id": "string",
 "product_id": 0,
 "is_error": false, 
 "changed_at": "2021-09-01T14:15:22Z"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|-------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `seller_id` | integer | int64 | Идентификатор продавца. |
| `message_type` | string | — | Тип уведомления — `TYPE_UPDATE_ITEM`. |
| `offer_id` | string | — | Идентификатор товара в системе продавца — артикул. |
| `product_id` | integer | int64 | Идентификатор товара в системе Ozon — `product_id`. |
| `is_error` | boolean | — | Признак, что при обновлении товара возникли ошибки:<br>• `true` — были ошибки, товар не создан;<br>• `false` — товар создан без ошибок. |
| `changed_at` | string | date-time | Дата и время изменения. |

## Изменение остатков на складах продавца

Уведомление, которое отправляет Ozon:

```
{
 "message_type": "string",
 "seller_id": 0,
 "items": [
 {
 "product_id": 0,
 "sku": 0,
 "updated_at": "2021-09-01T14:15:22Z",
 "stocks": [
 {
 "warehouse_id": 0,
 "present": 0,
 "reserved": 0
 }
 ]
 }
 ]
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------|
| `seller_id` | integer | int64 | Идентификатор продавца. |
| `message_type` | string | — | Тип уведомления — `TYPE_STOCKS_CHANGED`. |
| `items` | array | — | Массив с данными товаров. |
| `updated_at` | string | date-time | Дата и время изменения. |
| `sku` | integer | int64 | SKU товара при работе по схемам FBS или rFBS. |
| `product_id` | integer | int64 | Идентификатор товара в системе Ozon — `product_id`. |
| `stocks` | array | — | Массив с данными по остаткам товара. |
| `warehouse_id` | integer | int64 | Идентификатор склада. |
| `present` | integer | int64 | Общее количество товара на складе. |
| `reserved` | integer | int64 | Количество зарезервированных товаров на складе. |

## Новое сообщение в чате

```
{ 
 "message_type": "TYPE_NEW_MESSAGE",
 "chat_id": "b646d975-0c9c-4872-9f41-8b1e57181063",
 "chat_type": "Buyer_Seller",
 "message_id": "3000000000817031942",
 "created_at": "2022-07-18T20:58:04.528Z",
 "user": {
 "id": "115568",
 "type": "Сustomer"
 },
 "data": [
 "Текст сообщения"
 ], 
 "seller_id": "7"
}
```

| Параметр
 | Тип | Формат | Описание |
|------------------------------------------|-----------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_NEW_MESSAGE`. |
| `chat_id` | string | — | Идентификатор чата. |
| `chat_type` | string | — | Тип чата:<br>• `Seller_Support` — чат с поддержкой.<br>• `Buyer_Seller` — чат с покупателем.<br>• `Seller_Notification` — уведомления Ozon.<br>• `Seller_API_Updates` — обновления Seller API.<br>• `Seller_API_Notifications` — уведомления Seller API.<br>• `Seller_Notification_Logistics` — уведомления Ozon Доставка.<br>• `Buyer_Seller_Select` — чат с покупателем Селект.<br>• `Seller_Personal_Manager_Unity_Crm` — чат с персональным менеджером Ozon.<br>• `Seller_Business_Development_Group` — чат с группой бизнес-развития Ozon. |
| `message_id` | string | — | Идентификатор сообщения. |
| `created_at` | string | date-time | Дата создания сообщения. |
| `user` | object | — | Информация об отправителе сообщения. |
| `id` | string | — | Идентификатор отправителя. |
| `type` | string | — | Тип отправителя:<br>• `Customer` — покупатель.<br>• `Support` — поддержка.<br>• `NotificationUser` — Ozon. |
| `data` | array of string | — | Массив с содержимым сообщения в формате Markdown. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Сообщение в чате изменено

```
{ 
 "message_type": "TYPE_UPDATE_MESSAGE",
 "chat_id": "b646d975-0c9c-4872-9f41-8b1e57181063",
 "chat_type": "Buyer_Seller",
 "message_id": "3000000000817031942",
 "created_at": "2022-07-18T20:58:04.528Z",
 "updated_at": "2022-07-18T20:59:04.528Z",
 "user": {
 "id": "115568",
 "type": "Сustomer"
 },
 "data": [
 "Текст сообщения"
 ], 
 "seller_id": "7"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|-----------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_UPDATE_MESSAGE`. |
| `chat_id` | string | — | Идентификатор чата. |
| `chat_type` | string | — | Тип чата:<br>• `Seller_Support` — чат с поддержкой.<br>• `Buyer_Seller` — чат с покупателем.<br>• `Seller_Notification` — уведомления Ozon.<br>• `Seller_API_Updates` — обновления Seller API.<br>• `Seller_API_Notifications` — уведомления Seller API.<br>• `Seller_Notification_Logistics` — уведомления Ozon Доставка.<br>• `Buyer_Seller_Select` — чат с покупателем Селект.<br>• `Seller_Personal_Manager_Unity_Crm` — чат с персональным менеджером Ozon.<br>• `Seller_Business_Development_Group` — чат с группой бизнес-развития Ozon. |
| `message_id` | string | — | Идентификатор сообщения. |
| `created_at` | string | date-time | Дата создания сообщения. |
| `updated_at` | string | date-time | Дата изменения сообщения. |
| `user` | object | — | Информация об отправителе сообщения. |
| `id` | string | — | Идентификатор отправителя. |
| `type` | string | — | Тип отправителя:<br>• `Customer` — покупатель.<br>• `Support` — поддержка.<br>• `NotificationUser` — Ozon. |
| `data` | array of string | — | Массив с содержимым сообщения в формате Markdown. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Ваше сообщение прочитано

```
{ 
 "message_type": "TYPE_MESSAGE_READ",
 "chat_id": "b646d975-0c9c-4872-9f41-8b1e57181063",
 "chat_type": "Buyer_Seller",
 "message_id": "3000000000817031942",
 "created_at": "2022-07-18T20:58:04.528Z", 
 "user": {
 "id": "115568",
 "type": "Сustomer"
 },
 "last_read_message_id": "3000000000817031942",
 "seller_id": "7"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_MESSAGE_READ`. |
| `chat_id` | string | — | Идентификатор чата. |
| `chat_type` | string | — | Тип чата:<br>• `Seller_Support` — чат с поддержкой.<br>• `Buyer_Seller` — чат с покупателем.<br>• `Seller_Notification` — уведомления Ozon.<br>• `Seller_API_Updates` — обновления Seller API.<br>• `Seller_API_Notifications` — уведомления Seller API.<br>• `Seller_Notification_Logistics` — уведомления Ozon Доставка.<br>• `Buyer_Seller_Select` — чат с покупателем Селект.<br>• `Seller_Personal_Manager_Unity_Crm` — чат с персональным менеджером Ozon.<br>• `Seller_Business_Development_Group` — чат с группой бизнес-развития Ozon. |
| `message_id` | string | — | Идентификатор сообщения. |
| `created_at` | string | date-time | Дата создания сообщения. |
| `user` | object | — | Информация о пользователе, прочитавшем сообщение. |
| `id` | string | — | Идентификатор пользователя. |
| `type` | string | — | Тип пользователя:<br>• `Customer` — покупатель.<br>• `Support` — поддержка.<br>• `NotificationUser` — Ozon. |
| `last_read_message_id` | string | — | Идентификатор последнего прочитанного сообщения. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Чат закрыт

```
{ 
 "message_type": "TYPE_CHAT_CLOSED",
 "chat_id": "b646d975-0c9c-4872-9f41-8b1e57181063",
 "chat_type": "Buyer_Seller",
 "user": {
 "id": "115568",
 "type": "Сustomer"
 },
 "seller_id": "7"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_CHAT_CLOSED`. |
| `chat_id` | string | — | Идентификатор чата. |
| `chat_type` | string | — | Тип чата:<br>• `Seller_Support` — чат с поддержкой.<br>• `Buyer_Seller` — чат с покупателем.<br>• `Seller_Notification` — уведомления Ozon.<br>• `Seller_API_Updates` — обновления Seller API.<br>• `Seller_API_Notifications` — уведомления Seller API.<br>• `Seller_Notification_Logistics` — уведомления Ozon Доставка.<br>• `Buyer_Seller_Select` — чат с покупателем Селект.<br>• `Seller_Personal_Manager_Unity_Crm` — чат с персональным менеджером Ozon.<br>• `Seller_Business_Development_Group` — чат с группой бизнес-развития Ozon. |
| `user` | object | — | Информация о пользователе, закрывшем чат. |
| `id` | string | — | Идентификатор пользователя. |
| `type` | string | — | Тип пользователя:<br>• `Customer` — покупатель.<br>• `Support` — поддержка.<br>• `NotificationUser` — Ozon. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Изменение дерева категорий

```
{
 "message_type": "TYPE_DESCRIPTION_CATEGORY_TREE_CHANGED",
 "changed_at": "2026-04-07T10:27:55.955Z"
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|--------|-----------|-------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_DESCRIPTION_CATEGORY_TREE_CHANGED`. |
| `changed_at` | string | date-time | Дата и время изменения. |

## Новое отправление FBO

```
{
 "message_type": "TYPE_FBO_POSTING_NEW",
 "posting_number": "24219509-0020-1",
 "order_number": "24219509-0020", 
 "uuid": "bf354adc-e404-480c-a037-cf865464f1d9", 
 "products": [
 {
 "sku": 147451959,
 "quantity": 1
 }
 ],
 "creation_date": "2026-04-07T10:27:55.955Z",
 "warehouse_id": 18044249781000,
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|--------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_FBO_POSTING_NEW`. |
| `posting_number` | string | — | Номер отправления. |
| `order_number` | string | — | Номер заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `products` | array | — | Информация о товарах. |
| `sku` | integer | int64 | Идентификатор товара в системе Ozon — SKU. |
| `quantity` | integer | int64 | Количество товара. |
| `creation_date` | string | date-time | Дата и время создания отправления в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Отмена отправления FBO

```
{
 "message_type": "TYPE_FBO_POSTING_CANCELLED",
 "posting_number": ""0574652831-0001-1",
 "order_number": "0574652831-0001",
 "uuid": "bf354adc-e404-480c-a037-cf865464f1d9",
 "products": [
 {
 "sku": 147451959,
 "quantity": 1
 }
 ],
 "old_state": "posting_transferred_to_courier_service",
 "new_state": "posting_canceled",
 "cancel_date": "2026-04-07T10:27:55.955Z",
 "reason": {
 "id": 537,
 "message": "Не вручен"
 },
 "warehouse_id": 18044249781000,
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_FBO_POSTING_CANCELLED`. |
| `posting_number` | string | — | Номер отправления. |
| `order_number` | string | — | Номер заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `products` | array | — | Информация о товарах. |
| `sku` | integer | int64 | Идентификатор товара в системе Ozon — SKU. |
| `quantity` | integer | int64 | Количество товара. |
| `old_state` | string | — | Предыдущий статус отправления. |
| `new_state` | string | — | Новый статус отправления: `posting_canceled` — отменено. |
| `cancel_date` | string | date-time | Дата и время отмены отправления в формате UTC. |
| `reason` | object | — | Информация о причине отмены. | 
| `id` | integer | int64 | Идентификатор причины отмены. |
| `message` | string | — | Причина отмены. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

### Статусы отправлений

- `posting_created` — создано;
- `posting_packing` — на упаковке;
- `posting_delivered` — доставлено;
- `posting_transferring_to_delivery` — передаётся в доставку;
- `posting_on_way_to_city` — на пути в город;
- `posting_transferred_to_courier_service` — передаётся курьеру;
- `posting_returned_to_warehouse` — возвращено на склад;
- `posting_in_courier_service` — курьер в пути;
- `posting_on_way_to_pickup_point` — на пути в пункт выдачи;
- `posting_received` — получено;
- `posting_in_pickup_point` — в пункте выдачи.

## Изменение статуса отправления FBO

Соответствие статусных моделей Seller API и статусов пуш-модели.

| Seller API | | Push-модель | |
|----------------------|------------------------|------------------------------------------|-------------------------|
| **Статус** | **Описание** | **Статус** | **Описание** |
| `awaiting_approve` | Ожидает подтверждения. | `posting_created` | Создана. |
| `awaiting_packaging` | Ожидает упаковки. | `posting_created` | Создана. |
| | | `posting_packing` | На упаковке. |
| `awaiting_deliver` | Ожидает отгрузки. | `posting_transferring_to_delivery` | Передаётся в доставку. |
| `delivering` | Доставляется. | `posting_on_way_to_city` | На пути в ваш город. |
| | | `posting_transferred_to_courier_service` | Передаётся курьеру. |
| | | `posting_returned_to_warehouse` | Возвращено на склад. |
| | | `posting_in_courier_service` | Курьер в пути. |
| | | `posting_on_way_to_pickup_point` | На пути в пункт выдачи. |
| | | `posting_in_pickup_point` | В пункте выдачи. |
| `delivered` | Доставлено. | `posting_delivered` | Доставлено. |
| | | `posting_received` | Получено. |
| `cancelled` | Отменено. | `posting_canceled` | Отменено. |

```
{
 "message_type": "TYPE_FBO_POSTING_STATE_CHANGED",
 "posting_number": "68498622-0815-1",
 "order_number": "68498622-0815", 
 "uuid": "bf354adc-e404-480c-a037-cf865464f1d9", 
 "new_state": "posting_transferring_to_delivery",
 "changed_state_date": "2026-04-07T10:27:55.955Z",
 "warehouse_id": 18044249781000,
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_FBO_POSTING_STATE_CHANGED`. |
| `posting_number` | string | — | Номер отправления. |
| `order_number` | string | — | Номер заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `new_state` | string | — | Новый статус отправления. |
| `changed_state_date` | string | date-time | Дата и время изменения статуса отправления в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

### Статусы отправлений

- `posting_created` — создано;
- `posting_packing` — на упаковке;
- `posting_delivered` — доставлено;
- `posting_transferring_to_delivery` — передаётся в доставку;
- `posting_on_way_to_city` — на пути в город;
- `posting_transferred_to_courier_service` — передаётся курьеру;
- `posting_returned_to_warehouse` — возвращено на склад;
- `posting_in_courier_service` — курьер в пути;
- `posting_on_way_to_pickup_point` — на пути в пункт выдачи;
- `posting_received` — получено;
- `posting_in_pickup_point` — в пункте выдачи.

## Изменение даты доставки отправления FBO

```
{
 "message_type": "TYPE_FBO_POSTING_DELIVERY_DATE_CHANGED",
 "posting_number": "24219509-0020-1",
 "order_number": "24219509-0020", 
 "uuid": "bf354adc-e404-480c-a037-cf865464f1d9", 
 "old_delivery_date_begin": "2026-04-07T10:27:55.955Z",
 "old_delivery_date_end": "2026-04-07T10:27:55.955Z", 
 "new_delivery_date_begin": "2026-04-07T10:27:55.955Z", 
 "new_delivery_date_end": "2026-04-07T10:27:55.955Z", 
 "warehouse_id": 18044249781000,
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_FBO_POSTING_DELIVERY_DATE_CHANGED`. |
| `posting_number` | string | — | Номер отправления. |
| `order_number` | string | — | Номер заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `old_delivery_date_begin` | string | date-time | Предыдущие дата и время начала доставки в формате UTC. |
| `old_delivery_date_end` | string | date-time | Предыдущие дата и время окончания доставки в формате UTC. |
| `new_delivery_date_begin` | string | date-time | Новые дата и время начала доставки в формате UTC. |
| `new_delivery_date_end` | string | date-time | Новые дата и время окончания доставки в формате UTC. |
| `warehouse_id` | integer | int64 | Идентификатор склада, на котором хранятся товары для этого отправления. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Изменение остатков на складах Ozon

```
{
 "message_type": "TYPE_FBO_STOCKS_CHANGED",
 "sku": 325119272,
 "stocks": {
 "new_present": 321,
 "new_reserved": 12,
 "old_present": 321,
 "old_reserved": 12, 
 },
 "updated_at": "2026-04-07T10:27:55.955Z",
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|------------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_FBO_STOCKS_CHANGED`. |
| `sku` | integer | int64 | Идентификатор товара в системе Ozon — SKU. |
| `stocks` | array | — | Массив с данными по остаткам товара. |
| `new_reserved` | integer | int64 | Количество зарезервированных товаров на складе. |
| `new_present` | integer | int64 | Общее количество товара на складе. |
| `old_reserved` | integer | int64 | Предыдущее количество зарезервированных товаров на складе. |
| `old_present` | integer | int64 | Предыдущее общее количество товара на складе. |
| `updated_at` | string | date-time | Дата и время изменения. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Новый заказ

```
{
 "message_type": "TYPE_ORDER_NEW",
 "order_number": "24219509-0020-1",
 "order_id":35452597966,
 "uuid": "bf354adc-e404-480c-a037-cf865464f1d9", 
 "created_at": "2026-04-07T10:27:55.955Z",
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|---------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_ORDER_NEW`. |
| `order_number` | string | — | Номер заказа. |
| `order_id` | integer | int64 | Идентификатор заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `creation_date` | string | date-time | Дата и время создания заказа в формате UTC. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Отмена заказа

```
{
 "message_type": "TYPE_ORDER_CANCELLED",
 "order_number": "24219509-0020-1",
 "order_id":35452597966,
 "uuid": "bf354adc-e404-480c-a037-cf865464f1d9", 
 "cancelled_at": "2026-04-07T10:27:55.955Z",
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|-------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_ORDER_CANCELLED`. |
| `order_number` | string | — | Номер заказа. |
| `order_id` | integer | int64 | Идентификатор заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `cancelled_at` | string | date-time | Дата и время отмены заказа в формате UTC. |
| `seller_id` | integer | int64 | Идентификатор продавца. |

## Изменение статуса заказа

```
{
 "message_type": "TYPE_ORDER_STATE_CHANGED",
 "order_number": "24219509-0020-1",
 "order_id":35452597966,
 "uuid": "7d65308d-79f2-41d1-8d3e-f2eff46cc3d0", 
 "old_state": "order_in_delivery",
 "new_state": "order_done"
 "updated_at": "2026-04-07T10:27:55.955Z",
 "seller_id": 7376
}
```

| Параметр
 | Тип | Формат | Описание |
|-----------------------------------------|---------|-----------|------------------------------------------------------|
| `message_type` | string | — | Тип уведомления — `TYPE_ORDER_STATE_CHANGED`. |
| `order_number` | string | — | Номер заказа. |
| `order_id` | integer | int64 | Идентификатор заказа. |
| `uuid` | string | — | Уникальный идентификатор события. |
| `old_state` | string | — | Предыдущий статус заказа. |
| `new_state` | string | — | Новый статус заказа. |
| `updated_at` | string | date-time | Дата и время изменения статуса заказа в формате UTC. |
| `seller_id` | integer | int64 | Идентификатор продавца. |
