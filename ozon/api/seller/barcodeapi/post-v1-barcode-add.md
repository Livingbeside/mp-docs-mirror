---
title: Привязать штрихкод к товару
api: ozon-seller
method: POST
path: /v1/barcode/add
operation_id: add-barcode
tags:
  - BarcodeAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 520de64bb613f7f3
---

# Привязать штрихкод к товару

`POST /v1/barcode/add`

Если у товара есть штрихкод, который не указан в системе Ozon, привяжите его с помощью этого метода.
Чтобы сгенерировать штрихкод, используйте метод [/v1/barcode/generate]( #operation/generate-barcode).

[Подробнее о требованиях к штрихкодам в Базе знаний продавца](https://seller-edu.ozon.ru/libra/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/rabota-so-shtrihkodami#какие-требования-у-штрихкодов)

На одном товаре может быть до 100 штрихкодов. 
С одного аккаунта продавца можно использовать метод не больше 20 раз в минуту.

## Запрос

**Тело запроса** (`application/json`):

- `barcodes` — array[object] **обязательный**. Список штрихкодов и товаров.
  - `barcode` — string **обязательный**. Значение штрихкода. Не больше 100 символов.
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Штрихкод привязан

- `errors` — array[object]. Список ошибок.
  - `barcode` — string. Штрихкод, который не удалось привязать.
  - `code` — string. Код ошибки.
  - `error` — string. Описание ошибки.
  - `sku` — integer<int64>. Идентификатор товара, к которому не удалось привязать штрихкод.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
