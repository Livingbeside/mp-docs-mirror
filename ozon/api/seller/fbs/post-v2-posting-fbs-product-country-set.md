---
title: Добавить информацию о стране-изготовителе товара
api: ozon-seller
method: POST
path: /v2/posting/fbs/product/country/set
operation_id: PostingAPI_SetCountryProductFbsPostingV2
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6c099769e0e9fb8b
---

# Добавить информацию о стране-изготовителе товара

`POST /v2/posting/fbs/product/country/set`

Метод для добавления на продукт атрибута «Страна-изготовитель», если он не был указан.

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.
- `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — `product_id`.
- `country_iso_code` — string **обязательный**. Двухбуквенный код добавляемой страны по стандарту ISO_3166-1. Список доступных стран-изготовителей и их ISO коды можно получить с помощью метода [/v2/posting/fbs/product/country/list](#operation/PostingAPI_ListCountryProductFbsPostingV2).

## Ответы

**200** — Страна-изготовитель добавлена

- `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
- `is_gtd_needed` — boolean. Признак того, что необходимо передать номер грузовой таможенной декларации (ГТД) для продукта и отправления.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
