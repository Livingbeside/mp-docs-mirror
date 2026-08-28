---
title: Загрузка счёта-фактуры
api: ozon-seller
method: POST
path: /v1/invoice/file/upload
operation_id: invoice_upload
tags:
  - SupplierAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f1549876b64bf1ed
---

# Загрузка счёта-фактуры

`POST /v1/invoice/file/upload`

Доступные форматы: JPEG и PDF. Максимальный размер файла: 10 МБ.

## Запрос

**Тело запроса** (`application/json`):

- `base64_content` — string **обязательный**. Счёт-фактура в кодировке Base64.
- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Ссылка на счёт-фактуру

- `url` — string. Ссылка на счёт-фактуру.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
