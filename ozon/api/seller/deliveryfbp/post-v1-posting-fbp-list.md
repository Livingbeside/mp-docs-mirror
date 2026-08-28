---
title: Получить список отправлений
api: ozon-seller
method: POST
path: /v1/posting/fbp/list
operation_id: PostingFbpList
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d9a824a676d2553e
---

# Получить список отправлений

`POST /v1/posting/fbp/list`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/2054-Novyi-beta-metod-dlia-raboty-s-FBP-postingami-v-Seller-API/ ) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтр для поиска отправлений.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `posting_numbers` — array[string]. Номера отправлений.
  - `since` — string<date-time>. Начало периода.
  - `statuses` — array[string]. Статус отправления.
  - `to` — string<date-time>. Конец периода.
- `limit` — integer<int64>. Количество значений в ответе.
- `sort_by` — string. Параметр, по которому сортируются отправления: - `last_change_status_date` — по дате последнего изменения статуса; - `in_process_at` — по дате начала обработки.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию.

## Ответы

**200** — Список отправлений

- `cursor` — string. Указатель для выборки следующих данных.
- `postings` — array[object]. Список отправлений.
  - `financial_data` — object. Финансовые данные.
    - `cluster_from` — string. Код региона, откуда отправляется заказ.
    - `cluster_to` — string. Код региона, куда доставляется заказ.
    - `delivery_amount` — number<double>. Стоимость доставки.
    - `products` — array[object]. Список товаров в заказе.
      - `actions` — array[object]. Список акций.
        - `action_id` — string. Идентификатор акции.
        - `date_from` — string<date-time>. Дата начала акции.
        - `date_to` — string<date-time>. Дата окончания акции.
        - `description` — string. Название акции.
        - `discount_percent` — number<double>. Скидка в процентах.
        - `discount_value` — number<double>. Сумма скидки.
        - `is_from_seller` — boolean. `true`, если акцию создал продавец.
      - `commissions_currency_code` — string. Код валюты комиссии.
      - `old_price` — number<double>. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
      - `posting_commission` — object. Комиссия за отправление.
        - `amount` — number<double>. Сумма.
        - `payout` — number<double>. Выплата.
        - `percent` — number<double>. Процент комиссии.
      - `price` — number<double>. Цена товара с учётом акций, кроме акций за счёт Ozon.
      - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `quantity` — integer<int64>. Количество товара.
      - `return_commission` — object. Комиссия за возврат товара.
        - `amount` — number<double>. Сумма.
        - `payout` — number<double>. Выплата.
        - `percent` — number<double>. Процент комиссии.
      - `total_discount_percent` — number<double>. Процент скидки.
      - `total_discount_value` — number<double>. Сумма скидки.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `order_date` — string<date-time>. Дата создания заказа.
  - `order_id` — integer<int64>. Идентификатор заказа, к которому относится отправление.
  - `order_number` — string. Номер заказа, к которому относится отправление.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `customer_price` — object. Цена товара на сайте.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `name` — string. Название товара в заказе.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — object. Цена товара.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `quantity` — integer<int32>. Количество товара в отправлении.
    - `seller_price` — object. Цена для продавца с учётом скидок Ozon.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `provider_id` — integer<int64>. Идентификатор службы доставки.
  - `status` — string. Статус отправления.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
