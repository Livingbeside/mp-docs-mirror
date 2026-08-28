---
title: Отменить отправку некоторых товаров в отправлении
api: ozon-seller
method: POST
path: /v2/posting/fbs/product/cancel
operation_id: PostingAPI_CancelFbsPostingProduct
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ce868fb889079857
---

# Отменить отправку некоторых товаров в отправлении

`POST /v2/posting/fbs/product/cancel`

Используйте метод, если вы не можете отправить часть продуктов из отправления. Чтобы получить идентификаторы причин отмены `cancel_reason_id` при работе по схемам FBS или rFBS, используйте метод [/v2/posting/fbs/cancel-reason/list](#operation/PostingAPI_GetPostingFbsCancelReasonList). Условно-доставленные отправления отменить нельзя.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cancel_reason_id` — integer<int64> **обязательный**. Идентификатор причины отмены отправления товара.
- `cancel_reason_message` — string **обязательный**. Обязательное поле. Дополнительная информация по отмене.
- `items` — array[object] **обязательный**. Информация о товарах.
  - `quantity` — integer<int32> **обязательный**. Количество товара в отправлении.
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
- `posting_number` — string **обязательный**. Идентификатор отправления.

## Ответы

**200** — Отправка отменена

- `result` — string. Номер отправления.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
