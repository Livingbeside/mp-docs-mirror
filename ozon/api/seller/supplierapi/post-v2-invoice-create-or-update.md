---
title: Создать или изменить счёт-фактуру
api: ozon-seller
method: POST
path: /v2/invoice/create-or-update
operation_id: InvoiceAPI_InvoiceCreateOrUpdateV2
tags:
  - SupplierAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 68000c28c3c18e15
---

# Создать или изменить счёт-фактуру

`POST /v2/invoice/create-or-update`

Создание или изменение таможенного счёта-фактуры для возврата НДС продавцам из Турции. Вы можете создать счёт-фактуру только для отправлений в статусах `awaiting_approve` или `awaiting_packaging`.

## Запрос

**Тело запроса** (`application/json`):

- `date` — string<date-time> **обязательный**. Дата счёта-фактуры.
- `hs_codes` — array[object]. HS-коды товаров.
  - `code` — string. HS-код товара.
  - `sku` — string. Идентификатор товара в системе Ozon — SKU.
- `number` — string. Номер счёта-фактуры. Номер может содержать буквы и цифры, максимальная длина — 50 символов.
- `posting_number` — string **обязательный**. Номер отправления.
- `price` — number<double>. Стоимость, указанная в счёте-фактуре. Разделитель дробной части — точка, до двух знаков после точки.
- `price_currency` — string. Валюта счёта-фактуры: - `USD` — доллар, - `EUR` — евро, - `TRY` — турецкая лира, - `CNY` — юань, - `RUB` — рубль, - `GBP` — фунт стерлингов. Значение по умолчанию — `USD`.
- `url` — string **обязательный**. Ссылка на счёт-фактуру. Чтобы создать ссылку, используйте метод [v1/invoice/file/upload](#operation/invoice_upload).

## Ответы

**200** — Счёт-фактура создана или изменена

- `result` — boolean. Результат работы метода.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
