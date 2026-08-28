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
content_sha: a6dada551f615b6c
---

# Список акций

`GET /v1/actions`

Метод для получения списка акций Ozon, в которых можно участвовать. [Подробнее об акциях Ozon](https://seller-edu.ozon.ru/ceny-i-akcii/akcii-skidki-i-kupony/promo)

## Ответы

**200** — Список акций

- `result` — array[object]. Результаты запроса.
  - `id` — number<double>. Идентификатор акции.
  - `title` — string. Название акции.
  - `action_type` — string. Тип акции.
  - `description` — string. Описание акции.
  - `date_start` — string. Дата начала акции.
  - `date_end` — string. Дата окончания акции.
  - `auto_add_dates` — array[string<date-time>]. Дата и время автодобавления товаров в акцию.
  - `freeze_date` — string. Дата приостановки акции. Если поле заполнено, продавец не может повышать цены, изменять список товаров и уменьшать количество единиц товаров в акции. Продавец может понижать цены и увеличивать количество единиц товара в акции.
  - `potential_products_count` — number<double>. Количество товаров, доступных для акции.
  - `participating_products_count` — number<double>. Количество товаров, которые участвуют в акции.
  - `is_participating` — boolean. Участвуете вы в этой акции или нет.
  - `is_voucher_action` — boolean. Признак, что для участия в акции покупателям нужен промокод.
  - `banned_products_count` — number<double>. Количество заблокированных товаров.
  - `with_targeting` — boolean. Признак, что акция с целевой аудиторией.
  - `order_amount` — number<double>. Сумма заказа.
  - `discount_type` — string. Тип скидки.
  - `discount_value` — number<double>. Размер скидки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
