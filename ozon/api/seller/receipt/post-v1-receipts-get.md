---
title: Получить чек в формате PDF
api: ozon-seller
method: POST
path: /v1/receipts/get
operation_id: GetReceipt
tags:
  - Receipt
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 05b7fda283bc5eb9
---

# Получить чек в формате PDF

`POST /v1/receipts/get`

Метод доступен продавцам, которые заключили договор с ТОО «ОЗОН Маркетплейс Казахстан».

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `receipt_id` — string **обязательный**. Идентификатор чека. Получите значение параметра методом [/v1/receipts/seller/list](#operation/ReceiptsSellerList).

## Ответы

**200** — Чек

- `content` — string<byte>. PDF-файл с чеком в бинарном виде.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
