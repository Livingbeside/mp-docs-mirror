---
title: Справочник значений характеристики
api: ozon-seller
method: POST
path: /v1/description-category/attribute/values
operation_id: DescriptionCategoryAPI_GetAttributeValues
tags:
  - CategoryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d26d3c27ead24f3f
---

# Справочник значений характеристики

`POST /v1/description-category/attribute/values`

Возвращает справочник значений характеристики. Узнать, есть ли вложенный справочник, можно через метод [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `attribute_id` — integer<int64> **обязательный**. Идентификатор характеристики. Можно получить с помощью метода [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes).
- `description_category_id` — integer<int64> **обязательный**. Идентификатор категории. Можно получить с помощью метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
- `language` — string (DEFAULT, RU, EN, TR, ZH_HANS). Язык в ответе: - `EN` — английский, - `RU` — русский, - `TR` — турецкий, - `ZH_HANS` — китайский. По умолчанию используется русский язык. По умолчанию: `DEFAULT`.
- `last_value_id` — integer<int64>. Идентификатор справочника, с которого нужно начать ответ. Если `last_value_id` — 10, то в ответе будут справочники, начиная с одиннадцатого.
- `limit` — integer<int64> **обязательный**. Количество значений в ответе: - максимум — 2000, - минимум — 1.
- `type_id` — integer<int64> **обязательный**. Идентификатор типа товара. Можно получить с помощью метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).

## Ответы

**200** — Справочник характеристик

- `has_next` — boolean. Признак, что в ответе вернулась только часть значений характеристики: - `true` — сделайте повторный запрос с новым параметром `last_value_id` для получения остальных значений; - `false` — ответ содержит все значения характеристики.
- `result` — array[object]. Значения характеристики.
  - `id` — integer<int64>. Идентификатор значения характеристики.
  - `info` — string. Дополнительное описание.
  - `picture` — string. Ссылка на изображение.
  - `value` — string. Значение характеристики товара.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
