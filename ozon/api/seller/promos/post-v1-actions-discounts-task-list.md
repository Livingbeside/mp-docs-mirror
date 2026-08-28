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
content_sha: a9710f10722e77a3
---

# Список заявок на скидку

`POST /v1/actions/discounts-task/list`

Метод устаревает и будет отключён в будущем. Переключитесь на /v2/actions/discounts-task/list . Метод для получения списка товаров, которые покупатели хотят купить со скидкой.

## Запрос

**Тело запроса** (`application/json`):

- `status` — string (NEW, SEEN, APPROVED, PARTLY_APPROVED, DECLINED, AUTO_DECLINED, DECLINED_BY_USER, COUPON, PURCHASED) **обязательный**. Статус заявки на скидку: - `NEW` — новая, - `SEEN` — просмотренная, - `APPROVED` — одобренная, - `PARTLY_APPROVED` — одобренная частично, - `DECLINED` — отклонённая, - `AUTO_DECLINED` — отклонена автоматически, - `DECLINED_BY_USER` — отклонена покупателем, - `COUPON` — скидка по купону, - `PURCHASED` — купленная. По умолчанию: `UNKNOWN`.
- `page` — integer<uint64> **обязательный**. Страница, с которой нужно выгрузить список заявок на скидку.
- `limit` — integer<uint64> **обязательный**. Максимальное количество заявок на странице.

## Ответы

**200** — Список заявок

- `result` — array[object]. Список заявок.
  - `id` — integer<uint64>. Идентификатор заявки.
  - `created_at` — string<date-time>. Дата создания заявки.
  - `end_at` — string<date-time>. Время окончания действия заявки.
  - `edited_till` — string<date-time>. Время для изменения решения.
  - `status` — string. Статус заявки.
  - `customer_name` — string. Имя покупателя.
  - `sku` — integer<uint64>. Идентификатор товара в системе Ozon — SKU.
  - `user_comment` — string. Комментарий покупателя к заявке.
  - `seller_comment` — string. Комментарий продавца к заявке.
  - `requested_price` — number<double>. Цена по заявке.
  - `approved_price` — number<double>. Одобренная цена.
  - `original_price` — number<double>. Цена товара до всех скидок.
  - `discount` — number<double>. Скидка в рублях.
  - `discount_percent` — number<double>. Скидка в процентах.
  - `base_price` — number<double>. Базовая цена, по которой товар продаётся на Ozon, если не участвует в акции.
  - `min_auto_price` — number<double>. Минимальное значение цены после автоприменения скидок и акций.
  - `prev_task_id` — integer<uint64>. Идентификатор предыдущей заявки от покупателя по этому товару.
  - `is_damaged` — boolean. Является ли товар уценённым. `true`, если уценённый.
  - `moderated_at` — string<date-time>. Дата модерации: просмотра, одобрения или отклонения заявки.
  - `approved_discount` — number<double>. Скидка в рублях, которую одобрил продавец. Передайте значение `0`, если продавец не одобрял заявку.
  - `approved_discount_percent` — number<double>. Скидка в процентах, которую одобрил продавец. Передайте значение `0`, если продавец не одобрял заявку.
  - `is_purchased` — boolean. Покупал ли пользователь товар. `true`, если покупал.
  - `is_auto_moderated` — boolean. Была ли заявка промодерирована автоматически. `true`, если модерация была автоматической.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `email` — string. Электронный адрес сотрудника продавца, который обработал заявку.
  - `last_name` — string. Фамилия сотрудника продавца, который обработал заявку.
  - `first_name` — string. Имя сотрудника продавца, который обработал заявку.
  - `patronymic` — string. Отчество сотрудника продавца, который обработал заявку.
  - `approved_quantity_min` — integer<uint64>. Минимальное одобренное количество товаров.
  - `approved_quantity_max` — integer<uint64>. Максимальное одобренное количество товаров.
  - `requested_quantity_min` — integer<uint64>. Запрошенное минимальное количество товаров.
  - `requested_quantity_max` — integer<uint64>. Запрошенное максимальное количество товаров.
  - `requested_price_with_fee` — number<double>. Цена по заявке c региональной наценкой.
  - `approved_price_with_fee` — number<double>. Одобренная цена с региональной наценкой.
  - `approved_price_fee_percent` — number<double>. Региональная наценка в процентах.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
