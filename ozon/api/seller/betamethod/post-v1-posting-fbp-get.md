---
title: Получить информацию об отправлении по идентификатору
api: ozon-seller
method: POST
path: /v1/posting/fbp/get
operation_id: GetFbpPosting
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: aec73e57fddf87b9
---

# Получить информацию об отправлении по идентификатору

`POST /v1/posting/fbp/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2237-Novyi-metod-polucheniia-FBP-postingov-po-identifikatoru-otpravleniia/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Идентификатор отправления.

## Ответы

**200** — Информация об отправлении

- `posting` — object. Информация об отправлении.
  - `analytics_data` — object. Данные аналитики.
    - `city` — string. Город доставки.
    - `delivery_date_begin` — string<date-time>. Дата и время начала доставки.
    - `delivery_date_end` — string<date-time>. Дата и время конца доставки.
    - `delivery_type` — string. Способ доставки.
    - `region` — string. Регион доставки.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `cancellation` — object. Информация об отмене.
    - `cancel_reason` — string. Причина отмены.
    - `cancel_reason_id` — integer<int64>. Идентификатор причины отмены отправления.
    - `cancellation_initiator` — string. Инициатор отмены.
    - `cancellation_type` — string. Тип отмены.
  - `financial_data` — object. Финансовые данные.
    - `cluster_from` — string. Код региона, откуда отправляется заказ.
    - `cluster_to` — string. Код региона, куда доставляется заказ.
    - `delivery_amount` — number<double>. Стоимость доставки.
    - `products` — array[object]. Список товаров в заказе.
      - `actions` — array[object]. Список акций.
        - `action_id` — integer<int64>. Идентификатор акции.
        - `action_type` — string. Тип акции.
        - `date_from` — string<date-time>. Дата начала акции.
        - `date_to` — string<date-time>. Дата окончания акции.
        - `description` — string. Название акции.
        - `discount_percent` — number<double>. Скидка в процентах.
        - `discount_value` — number<double>. Сумма скидки.
      - `commissions_price` — object. Комиссия за товар.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `customer_price` — object. Цена товара на сайте.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `old_price` — number<double>. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
      - `posting_commission` — object. Коммисия за отправление.
        - `amount` — number<double>. Сумма.
        - `payout` — number<double>. Выплата.
        - `percent` — number<double>. Процент комиссии.
      - `quantity` — integer<int64>. Количество товара в отправлении.
      - `return_commission` — object. Комиссия за возврат товара.
        - `amount` — number<double>. Сумма.
        - `payout` — number<double>. Выплата.
        - `percent` — number<double>. Процент комиссии.
      - `seller_price` — object. Цена для продавца с учётом скидок Ozon.
        - `amount` — string. Сумма.
        - `currency` — string. Валюта.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `total_discount_percent` — number<double>. Процент скидки.
      - `total_discount_value` — number<double>. Сумма скидки.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `order_date` — string<date-time>. Дата создания заказа.
  - `order_id` — integer<int64>. Идентификатор заказа, к которому относится отправление.
  - `order_number` — string. Номер заказа, к которому относится отправление.
  - `posting_number` — string. Идентификатор отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `has_imei` — boolean. `true`, если есть IMEI.
    - `marketplace_seller_price` — object. Цена товара с учётом акций, кроме акций за счёт Ozon.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `quantity` — integer<int32>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `weight_max` — number<double>. Максимальный вес экземпляра.
  - `status` — integer<int64>. Статус отправления.
  - `substatus` — string. Подстатус отправления.
  - `tpl_provider_id` — integer<int64>. Идентификатор провайдера доставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
