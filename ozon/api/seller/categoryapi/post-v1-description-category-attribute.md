---
title: Список характеристик категории
api: ozon-seller
method: POST
path: /v1/description-category/attribute
operation_id: DescriptionCategoryAPI_GetAttributes
tags:
  - CategoryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a6c9d07fcddce072
---

# Список характеристик категории

`POST /v1/description-category/attribute`

Получение характеристик для указанных категории и типа товара.

Если у `dictionary_id` значение `0`, у атрибута нет вложенных справочников.
Если значение другое, то справочники есть. Запросите их методом [/v1/description-category/attribute/values](#operation/DescriptionCategoryAPI_GetAttributeValues).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `description_category_id` — integer<int64> **обязательный**. Идентификатор категории. Можно получить с помощью метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
- `language` — string (DEFAULT, RU, EN, TR, ZH_HANS). Язык в ответе: - `EN` — английский, - `RU` — русский, - `TR` — турецкий, - `ZH_HANS` — китайский. По умолчанию используется русский язык. По умолчанию: `DEFAULT`.
- `type_id` — integer<int64> **обязательный**. Идентификатор типа товара. Можно получить с помощью метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).

## Ответы

**200** — Характеристики категории

- `result` — array[object]. Результат запроса.
  - `category_dependent` — boolean. Признак, что значения словарного атрибута зависят от категории: - `true` — у атрибута разные значения для каждой категории. - `false` — у атрибута одинаковые значения для всех категорий.
  - `description` — string. Описание характеристики.
  - `dictionary_id` — integer<int64>. Идентификатор справочника.
  - `group_id` — integer<int64>. Идентификатор группы характеристик.
  - `group_name` — string. Название группы характеристик.
  - `id` — integer<int64>. Идентификатор характеристики.
  - `is_aspect` — boolean. Признак аспектного атрибута. Аспектный атрибут — характеристика, по которой отличаются товары одной модели. Например, у одежды и обуви одной модели могут быть разные расцветки и размеры. То есть цвет и размер — это аспектные атрибуты. Значения поля: - `true` — атрибут аспектный и его нельзя изменить после поставки товара на склад или продажи со своего склада. - `false` — атрибут не аспектный, можно изменить в любое время.
  - `is_collection` — boolean. - `true`, если характеристика — набор значений. - `false`, если характеристика — одно значение.
  - `is_required` — boolean. Признак обязательной характеристики: - `true` — обязательная характеристика, - `false` — характеристику можно не указывать.
  - `name` — string. Название.
  - `type` — string. Тип характеристики.
  - `attribute_complex_id` — integer<int64>. Идентификатор комплексного атрибута.
  - `max_value_count` — integer<int64>. Максимальное количество значений для атрибута.
  - `complex_is_collection` — boolean. Признак, что комплексная характеристика — набор значений: - `true`, если комплексная характеристика — набор значений, - `false`, если комплексная характеристика — одно значение.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
