---
title: Создать штрихкод для товара
api: ozon-seller
method: POST
path: /v1/barcode/generate
operation_id: generate-barcode
tags:
  - BarcodeAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 84ed1c2499e95e42
---

# Создать штрихкод для товара

`POST /v1/barcode/generate`

Если у товара нет штрихкода, вы можете создать его с помощью этого метода. Если штрихкод уже есть, но он не указан в системе Ozon, вы можете привязать его через метод [/v1/barcode/add](#operation/add-barcode). За один запрос вы можете создать штрихкоды не больше чем для 100 товаров. С одного аккаунта продавца можно использовать метод не больше 20 раз в минуту.

## Запрос

**Тело запроса** (`application/json`):

- `product_ids` — array[string<int64>] **обязательный**. Идентификаторы товаров, для которых нужно создать штрихкод.

## Ответы

**200** — Штрихкод создан

- `errors` — array[object]. Ошибки при создании штрихкода.
  - `code` — string. Код ошибки.
  - `error` — string. Описание ошибки.
  - `barcode` — string. Штрихкод, при создании которого произошла ошибка.
  - `product_id` — integer<int64>. Идентификатор товара, для которого не удалось создать штрихкод.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
