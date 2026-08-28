---
title: Список акций
api: ozon-seller
method: GET
path: /v1/actions
operation_id: Promos
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 589acd075e590aa2
---

# Список акций

`GET /v1/actions`

Метод для получения списка акций Ozon, в которых можно участвовать.

[Подробнее об акциях Ozon](https://seller-edu.ozon.ru/ceny-i-akcii/akcii-skidki-i-kupony/promo)

## Ответы

**200** — Список акций

- `result` — array[object]. Результаты запроса.
  - `action_type` — string. Тип акции.
  - `auto_add_dates` — array[string<date-time>]. Дата и время автодобавления товаров в акцию.
  - `banned_products_count` — number<double>. Количество заблокированных товаров.
  - `date_end` — string. Дата окончания акции.
  - `date_start` — string. Дата начала акции.
  - `description` — string. Описание акции.
  - `discount_type` — string. Тип скидки.
  - `discount_value` — number<double>. Размер скидки.
  - `freeze_date` — string. Дата приостановки акции. Если поле заполнено, продавец не может повышать цены, изменять список товаров и уменьшать количество единиц товаров в акции. Продавец может понижать цены и увеличивать количество единиц товара в акции.
  - `id` — number<double>. Идентификатор акции.
  - `is_participating` — boolean. Участвуете вы в этой акции или нет.
  - `is_voucher_action` — boolean. Признак, что для участия в акции покупателям нужен промокод.
  - `order_amount` — number<double>. Сумма заказа.
  - `participating_products_count` — number<double>. Количество товаров, которые участвуют в акции.
  - `potential_products_count` — number<double>. Количество товаров, доступных для акции.
  - `title` — string. Название акции.
  - `with_targeting` — boolean. Признак, что акция с целевой аудиторией.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
