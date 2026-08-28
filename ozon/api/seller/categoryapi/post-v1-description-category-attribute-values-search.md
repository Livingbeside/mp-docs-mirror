---
title: Поиск по справочным значениям характеристики
api: ozon-seller
method: POST
path: /v1/description-category/attribute/values/search
operation_id: DescriptionCategoryAPI_SearchAttributeValues
tags:
  - CategoryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 901e4e413352246c
---

# Поиск по справочным значениям характеристики

`POST /v1/description-category/attribute/values/search`

Возвращает справочные значения характеристики по заданному значению `value` в запросе. Узнать, есть ли вложенный справочник, можно через метод [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `attribute_id` — integer<int64> **обязательный**. Идентификатор характеристики. Можно получить с помощью метода [/v1/description-category/attribute](#operation/DescriptionCategoryAPI_GetAttributes).
- `description_category_id` — integer<int64> **обязательный**. Идентификатор категории. Можно получить с помощью метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
- `limit` — integer<int64> **обязательный**. Количество значений в ответе: - максимум — 100, - минимум — 1.
- `type_id` — integer<int64> **обязательный**. Идентификатор типа товара. Можно получить с помощью метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
- `value` — string **обязательный**. Значение, по которому система будет искать справочные значения. Минимум — 2 символа.

## Ответы

**200** — Справочные значения характеристики.

- `result` — array[object]. Значения характеристики.
  - `id` — integer<int64>. Идентификатор значения характеристики.
  - `info` — string. Дополнительная информация.
  - `picture` — string. Ссылка на изображение.
  - `value` — string. Значение характеристики товара.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
