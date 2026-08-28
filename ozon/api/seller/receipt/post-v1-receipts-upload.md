---
title: Загрузить чек
api: ozon-seller
method: POST
path: /v1/receipts/upload
operation_id: UploadReceipt
tags:
  - Receipt
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4418c50659bbf7f6
---

# Загрузить чек

`POST /v1/receipts/upload`

Метод доступен продавцам, которые заключили договор с ТОО «ОЗОН Маркетплейс Казахстан».

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`multipart/form-data`):

- `content` — string<byte> **обязательный**. Содержание файла в бинарном виде.
- `operation_type` — string **обязательный**. Тип операции. Получите значение параметра методом [/v1/receipts/seller/list](#operation/ReceiptsSellerList).
- `parent_receipt_id` — string. Идентификатор родительского чека. Передайте параметр с идентификатором чека, который нужно изменить.
- `posting_numbers` — array[string] **обязательный**. Номера отправлений.
- `receipt_number` — string **обязательный**. Номер чека.
- `type` — string (INCOMING, REFUND) **обязательный**. Тип чека: - `INCOMING` — чек реализации; - `REFUND` — чек возврата.

## Ответы

**200** — Чек загружен

- `receipt_id` — string. Идентификатор чека.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
