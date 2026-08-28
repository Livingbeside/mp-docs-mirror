---
title: Получить информацию об отправлении по штрихкоду
api: ozon-seller
method: POST
path: /v2/posting/fbs/get-by-barcode
operation_id: PostingAPI_GetFbsPostingByBarcode
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3760b519f9258f8e
---

# Получить информацию об отправлении по штрихкоду

`POST /v2/posting/fbs/get-by-barcode`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `barcode` — string **обязательный**. Штрихкод отправления. Можно получить с помощью методов: [/v3/posting/fbs/get](#operation/PostingAPI_GetFbsPostingV3), [/v3/posting/fbs/list](#operation/PostingAPI_GetFbsPostingListV3) и [/v3/posting/fbs/unfulfilled/list](#operation/PostingAPI_GetFbsPostingUnfulfilledList) в массиве `barcodes`.

## Ответы

**200** — Информация об отправлении

- `result` — object. Результаты запроса.
  - `barcodes` — object. Штрихкоды отправления.
    - `lower_barcode` — string. Нижний штрихкод на маркировке отправления.
    - `upper_barcode` — string. Верхний штрихкод на маркировке отправления.
  - `cancel_reason_id` — integer<int64>. Идентификатор причины отмены отправления.
  - `created_at` — string<date-time>. Дата и время создания отправления.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `order_id` — integer<int64>. Идентификатор заказа, к которому относится отправление.
  - `order_number` — string. Номер заказа, к которому относится отправление.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — string. Цена товара.
    - `quantity` — integer<int64>. Количество товара в отправлении.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `shipment_date` — string<date-time>. Дата и время, до которой необходимо собрать отправление. Если отправление не собрать к этой дате — оно автоматически отменится.
  - `status` — string. Статус отправления.

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
