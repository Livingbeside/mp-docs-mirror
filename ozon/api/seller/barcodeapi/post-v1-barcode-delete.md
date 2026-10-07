---
title: Отвязать штрихкод от товара
api: ozon-seller
method: POST
path: /v1/barcode/delete
operation_id: BarcodeDelete
tags:
  - BarcodeAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ad7820e54e6dcb3e
---

# Отвязать штрихкод от товара

`POST /v1/barcode/delete`

Не получится отвязать штрихкод, если на складе есть остатки товара с таким штрихкодом или после продажи остатков прошло меньше 6 месяцев.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `barcodes` — array[object] **обязательный**. Список пар штрихкодов и товаров, которые нужно отвязать.
  - `barcode` — string **обязательный**. Значение штрихкода.
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Штрихкод отвязан от товара

- `errors` — array[object]. Список ошибок. Если список пустой, все штрихкоды отвязаны успешно.
  - `barcode` — string. Штрихкод, который не удалось отвязать.
  - `code` — string. Код ошибки.
  - `error` — string. Описание ошибки.
  - `sku` — integer<int64>. Идентификатор товара, от которого не удалось отвязать штрихкод.

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
