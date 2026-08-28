---
title: Разделить отправление с прослеживаемыми товарами
api: ozon-seller
method: POST
path: /v1/posting/fbs/traceable/split
operation_id: PostingFbsTraceableSplit
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 79adc29665421bbd
---

# Разделить отправление с прослеживаемыми товарами

`POST /v1/posting/fbs/traceable/split`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Заказ разделён

- `postings` — array[object]. Информация об отправлениях.
  - `posting_number` — string. Номер отправления.
  - `potential_blr_traceable` — boolean. Признак, что товар потенциально прослеживаемый: - `true` — отправление считается прослеживаемым на данный момент. При сборке статус может измениться. - `false` — отправление не прослеживаемое на данный момент или его статус неизвестный.
  - `products` — array[object]. Список товаров в отправлении.
    - `quantity` — integer<int32>. Количество.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
