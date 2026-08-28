---
title: Получить информацию о счёте-фактуре
api: ozon-seller
method: POST
path: /v2/invoice/get
operation_id: invoice_getV2
tags:
  - SupplierAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 19fb59d9bd07173b
---

# Получить информацию о счёте-фактуре

`POST /v2/invoice/get`

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Информация о счёте-фактуре

- `result` — object. Информация о счёте-фактуре.
  - `date` — string<date-time>. Дата загрузки счёта-фактуры.
  - `file_url` — string. Ссылка на счёт-фактуру.
  - `hs_codes` — array[object]. HS-коды товаров.
    - `code` — string. HS-код товара.
    - `sku` — string. Идентификатор товара в системе Ozon — SKU.
  - `number` — string. Номер счёта-фактуры.
  - `price` — number<double>. Стоимость, указанная в счёте-фактуре. Разделитель дробной части — точка, до двух знаков после точки. Пример: `199.99`.
  - `price_currency` — string. Валюта счёта-фактуры: - `USD` — доллар, - `EUR` — евро, - `TRY` — турецкая лира, - `CNY` — юань, - `RUB` — рубль, - `GBP` — фунт стерлингов. Значение по умолчанию — `USD`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
