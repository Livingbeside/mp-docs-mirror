---
title: Список доступных стран-изготовителей
api: ozon-seller
method: POST
path: /v2/posting/fbs/product/country/list
operation_id: PostingAPI_ListCountryProductFbsPostingV2
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: baae7cb4a56866d8
---

# Список доступных стран-изготовителей

`POST /v2/posting/fbs/product/country/list`

Метод для получения списка доступных стран-изготовителей и их ISO кодов.

## Запрос

**Тело запроса** (`application/json`):

- `name_search` — string. Фильтрация по строке.

## Ответы

**200** — Список доступных стран-изготовителей

- `result` — array[object]. Список стран-изготовителей и ISO коды.
  - `name` — string. Название страны на русском языке.
  - `country_iso_code` — string. ISO код страны.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
