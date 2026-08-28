---
title: Получить список чеков продавца
api: ozon-seller
method: POST
path: /v1/receipts/seller/list
operation_id: ReceiptsSellerList
tags:
  - Receipt
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 36956d721b2bc7ad
---

# Получить список чеков продавца

`POST /v1/receipts/seller/list`

Метод доступен продавцам, которые заключили договор с ТОО «ОЗОН Маркетплейс Казахстан».

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `page` — integer<int64>. Количество страниц, которое нужно пропустить. По умолчанию: `0`.
- `page_size` — integer<int64>. Количество элементов на странице. По умолчанию: `100`.
- `posting_numbers` — array[string]. Фильтр по номерам отправлений.

## Ответы

**200** — Список чеков продавца

- `has_next` — boolean. Признак, что в ответе вернулись не все записи: - `true` — сделайте повторный запрос с новым параметром `page`, чтобы получить остальные значения; - `false` — ответ содержит все записи с чеками.
- `receipts` — array[object]. Информация о чеках.
  - `created_at` — string<date-time>. Дата создания чека.
  - `operation_type` — string (UNSPECIFIED, COMMODITY). Тип операции: - `UNSPECIFIED` — не определён; - `COMMODITY` — товарная операция. По умолчанию: `UNSPECIFIED`.
  - `order_id` — integer<int64>. Идентификатор заказа.
  - `parent_receipt_id` — string. Идентификатор родительского чека.
  - `posting_numbers` — array[string]. Номера отправлений.
  - `receipt_id` — string. Идентификатор чека.
  - `receipt_number` — string. Номер чека.
  - `type` — string (UNSPECIFIED, INCOMING, REFUND). Тип чека: - `UNSPECIFIED` — не определён; - `INCOMING` — чек реализации; - `REFUND` — чек возврата. По умолчанию: `UNSPECIFIED`.
  - `updated_at` — string<date-time>. Дата обновления.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
