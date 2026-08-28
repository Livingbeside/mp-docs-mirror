---
title: Отчёт о выкупленных товарах
api: ozon-seller
method: POST
path: /v1/finance/products/buyout
operation_id: GetFinanceProductsBuyout
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d71715aa52141619
---

# Отчёт о выкупленных товарах

`POST /v1/finance/products/buyout`

Возвращает отчёт о товарах, которые выкупил Ozon. Соответствует разделу **Финансы → Документы → УПД по сделкам с юр. лицами → УПД по выкупленным товарам** в личном кабинете. [Подробнее о выкупе товаров в Базе знаний](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/prodaji-tovarov-v-eaes-i-drugie-strany?search=выкупленные+товары)

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string **обязательный**. Дата, с которой будут данные в отчёте.
- `date_to` — string **обязательный**. Дата, по которую будут данные в отчёте. Максимальный период — 31 день.

## Ответы

**200** — Отчёт по выкупленным товарам

- `products` — array[object]. Список выкупленных товаров
  - `amount` — number<float>. Сумма к начислению.
  - `buyout_price` — number<float>. Цена выкупа товара с НДС.
  - `deduction_by_category_percent` — number<float>. Скидка по категории в процентах.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `posting_number` — string. Номер отправления.
  - `quantity` — integer<int32>. Количество товара.
  - `seller_price_per_instance` — number<float>. Цена продавца с учётом скидки.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `vat_percent` — integer<int32>. Ставка НДС для товара в процентах.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
