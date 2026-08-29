---
title: Обновить метод доставки «Партнёры Ozon»
api: ozon-seller
method: POST
path: /v1/warehouse/erfbs/aggregator/delivery-method/update
operation_id: WarehouseERFBSAggregatorDeliveryMethodUpdate
tags:
  - rFBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 380a4b8a74c75a86
---

# Обновить метод доставки «Партнёры Ozon»

`POST /v1/warehouse/erfbs/aggregator/delivery-method/update`

[Подробнее о схеме rFBS Express](https://seller-edu.ozon.ru/rfbs/scheme-of-work/rfbs-express#%D1%87%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-realfbs-express)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `courier_comment` — string. Комментарий для курьера.
- `is_courier_phone_same_as_warehouse` — boolean. `true`, если номер телефона курьера совпадает с номером телефона склада. Если `is_courier_phone_same_as_warehouse = true`, текущий номер телефона будет указан в `courier_phones`. По умолчанию: `True`.
- `courier_phones` — array[string]. Номера телефонов для связи с курьером.
- `cut_in` — integer (15, 30, 60, 120, 180, 240, 300, 360, 420, 480). Время сборки.
- `deliver_to_pvz` — boolean. `true`, если доставка Ozon Express в пункт выдачи Ozon.
- `delivery_costs` — object. Расходы на доставку, которые вы готовы оплатить.
  - `min_weight` — integer<int64>. Минимальный вес в килограммах.
  - `max_weight` — integer<int64>. Максимальный вес в килограммах.
  - `min_order_price` — integer<int64>. Минимальная стоимость заказа в копейках.
  - `max_order_price` — integer<int64>. Максимальная стоимость заказа в копейках.
  - `seller_payment` — integer<int64>. Цена в копейках.
- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки.
- `name` — string. Название метода доставки.
- `return_settings` — object. Настройки возвратов от покупателей.
  - `contact_days` — integer<int64>. Количество дней, за которое вы свяжетесь с покупателем. Параметр обязательный, если `return_method = COURIER`.
  - `post_office_zipcode` — string. Индекс отделения Почты России.
  - `return_method` — string (COURIER, TRANSPORT_COMPANY). Способ возврата: - `COURIER` — курьером; - `TRANSPORT_COMPANY` — транспортной компанией.
  - `transport_company_name` — string **обязательный**. Название транспортной компании. Параметр обязательный, если `return_method = TRANSPORT_COMPANY`.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Успешно

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
