---
title: Список заявок на скидку
api: ozon-seller
method: POST
path: /v1/actions/discounts-task/list
operation_id: promos_task_list
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 83cf1cc5516a4f94
---

# Список заявок на скидку

`POST /v1/actions/discounts-task/list`

Метод устаревает и будет отключён в будущем. Переключитесь на [/v2/actions/discounts-task/list](#operation/GetDiscountTaskListV2).
 

 Метод для получения списка товаров, которые покупатели хотят купить со скидкой.

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<uint64> **обязательный**. Максимальное количество заявок на странице.
- `page` — integer<uint64> **обязательный**. Страница, с которой нужно выгрузить список заявок на скидку.
- `status` — string (NEW, SEEN, APPROVED, PARTLY_APPROVED, DECLINED, AUTO_DECLINED, DECLINED_BY_USER, COUPON, PURCHASED) **обязательный**. Статус заявки на скидку: - `NEW` — новая, - `SEEN` — просмотренная, - `APPROVED` — одобренная, - `PARTLY_APPROVED` — одобренная частично, - `DECLINED` — отклонённая, - `AUTO_DECLINED` — отклонена автоматически, - `DECLINED_BY_USER` — отклонена покупателем, - `COUPON` — скидка по купону, - `PURCHASED` — купленная. По умолчанию: `UNKNOWN`.

## Ответы

**200** — Список заявок

- `result` — array[object]. Список заявок.
  - `approved_discount` — number<double>. Скидка в рублях, которую одобрил продавец. Передайте значение `0`, если продавец не одобрял заявку.
  - `approved_discount_percent` — number<double>. Скидка в процентах, которую одобрил продавец. Передайте значение `0`, если продавец не одобрял заявку.
  - `approved_price` — number<double>. Одобренная цена.
  - `approved_price_fee_percent` — number<double>. Региональная наценка в процентах.
  - `approved_price_with_fee` — number<double>. Одобренная цена с региональной наценкой.
  - `approved_quantity_max` — integer<uint64>. Максимальное одобренное количество товаров.
  - `approved_quantity_min` — integer<uint64>. Минимальное одобренное количество товаров.
  - `base_price` — number<double>. Базовая цена, по которой товар продаётся на Ozon, если не участвует в акции.
  - `created_at` — string<date-time>. Дата создания заявки.
  - `customer_name` — string. Имя покупателя.
  - `discount` — number<double>. Скидка в рублях.
  - `discount_percent` — number<double>. Скидка в процентах.
  - `edited_till` — string<date-time>. Время для изменения решения.
  - `email` — string. Электронный адрес сотрудника продавца, который обработал заявку.
  - `end_at` — string<date-time>. Время окончания действия заявки.
  - `first_name` — string. Имя сотрудника продавца, который обработал заявку.
  - `id` — integer<uint64>. Идентификатор заявки.
  - `is_auto_moderated` — boolean. Была ли заявка промодерирована автоматически. `true`, если модерация была автоматической.
  - `is_damaged` — boolean. Является ли товар уценённым. `true`, если уценённый.
  - `is_purchased` — boolean. Покупал ли пользователь товар. `true`, если покупал.
  - `last_name` — string. Фамилия сотрудника продавца, который обработал заявку.
  - `min_auto_price` — number<double>. Минимальное значение цены после автоприменения скидок и акций.
  - `moderated_at` — string<date-time>. Дата модерации: просмотра, одобрения или отклонения заявки.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `original_price` — number<double>. Цена товара до всех скидок.
  - `patronymic` — string. Отчество сотрудника продавца, который обработал заявку.
  - `prev_task_id` — integer<uint64>. Идентификатор предыдущей заявки от покупателя по этому товару.
  - `requested_price` — number<double>. Цена по заявке.
  - `requested_price_with_fee` — number<double>. Цена по заявке c региональной наценкой.
  - `requested_quantity_max` — integer<uint64>. Запрошенное максимальное количество товаров.
  - `requested_quantity_min` — integer<uint64>. Запрошенное минимальное количество товаров.
  - `seller_comment` — string. Комментарий продавца к заявке.
  - `sku` — integer<uint64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string. Статус заявки.
  - `user_comment` — string. Комментарий покупателя к заявке.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
