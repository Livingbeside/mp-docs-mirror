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
content_sha: 62bec4283fda3b38
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
  - `country_iso_code` — string. ISO код страны.
  - `name` — string. Название страны на русском языке.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
