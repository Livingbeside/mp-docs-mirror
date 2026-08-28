---
title: Удалить ссылку на счёт-фактуру
api: ozon-seller
method: POST
path: /v1/invoice/delete
operation_id: invoice_delete
tags:
  - SupplierAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f7b83ddfe37d24c5
---

# Удалить ссылку на счёт-фактуру

`POST /v1/invoice/delete`

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Ссылка удалена

- `result` — boolean. Результат работы метода.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
