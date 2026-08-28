---
title: Создать заказ
api: ozon-seller
method: POST
path: /v2/order/create
operation_id: OrderAPI_OrderCreate
tags:
  - OrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9b69c77e7b918ebd
---

# Создать заказ

`POST /v2/order/create`

Создаёт заказ для покупателя и получателя в системе Ozon. Передайте вариант доставки из ответа метода [/v2/delivery/checkout](#operation/DeliveryCheckout). В ответе могут быть не все отправления. Получите список всех отправлений по номеру заказа `order_number` методом: - [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList) — для схемы FBO; - [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) — для схемы FBS. Значение параметра `delivery_schema` должно совпадать с тем, что вы передали в [/v2/delivery/checkout](#operation/DeliveryCheckout).

## Запрос

**Тело запроса** (`application/json`):

- `buyer` — object **обязательный**. Информация о покупателе.
  - `first_name` — string **обязательный**. Имя.
  - `last_name` — string **обязательный**. Фамилия.
  - `middle_name` — string. Отчество.
  - `phone` — string **обязательный**. Номер телефона.
- `delivery` — object **обязательный**. Информация о доставке.
- `delivery_schema` — string (MIX, FBO, FBS) **обязательный**. Схема доставки: - `MIX` — на выбор Ozon; - `FBO` — FBO; - `FBS` — FBS. По умолчанию: `MIX`.
- `recipient` — object **обязательный**. Информация о получателе.
  - `recipient_first_name` — string **обязательный**. Имя.
  - `recipient_last_name` — string **обязательный**. Фамилия.
  - `recipient_middle_name` — string. Отчество.
  - `recipient_phone` — string **обязательный**. Номер телефона.
- `splits` — array[object] **обязательный**. Информация об отправлениях в заказе.
  - `delivery_method` — object **обязательный**. Метод доставки.
    - `delivery_method_id` — integer<int64> **обязательный**. Идентификатор способа доставки.
    - `delivery_type` — string (COURIER, PVZ, POSTAMAT) **обязательный**. Тип доставки: - `COURIER` — курьером; - `PVZ` — в пункт выдачи заказов; - `POSTAMAT` — в постамат.
    - `logistic_date_range` — object **обязательный**. Интервал времени, в течение которого заказ может быть доставлен до точки выдачи.
      - `from` — string<date-time> **обязательный**. Время начала интервала.
      - `to` — string<date-time> **обязательный**. Время конца интервала.
    - `price` — object. Цена доставки. Чтобы отобразить покупателю бесплатную доставку, не передавайте объект.
      - `currency_code` — string. Код валюты.
      - `nanos` — integer<int32>. Часть стоимости в копейках.
      - `units` — integer<int64>. Часть стоимости в рублях.
    - `timeslot_id` — integer<int64> **обязательный**. Идентификатор таймслота.
  - `items` — array[object] **обязательный**. Товары в отправлении.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — object **обязательный**. Цена товара.
      - `currency_code` — string **обязательный**. Код валюты.
      - `nanos` — integer<int32>. Часть стоимости в копейках.
      - `units` — integer<int64> **обязательный**. Часть стоимости в рублях.
    - `quantity` — integer<int64> **обязательный**. Количество товара.
    - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
  - `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Заказ создан

- `order_number` — string. Номер заказа.
- `postings` — array[string]. Отправления.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
