---
title: Получить зависимые характеристики
api: ozon-seller
method: POST
path: /v1/description-category/dependent-attributes
operation_id: DescriptionCategoryDependentAttributes
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3fa875e53e7f8a9d
---

# Получить зависимые характеристики

`POST /v1/description-category/dependent-attributes`

Возвращает пары идентификаторов родительской и дочерней характеристик. Получите возможные значения дочерней характеристики для значений родительской методом [/v1/description-category/dependent-attributes/values](#operation/DescriptionCategoryDependentAttributesValues).

Характеристика с `parent_attribute_id = 8229` — это идентификатор типа товара `type_id`. Не указывайте её в параметре `items.attributes.id` в запросах к методам [/v3/product/import](#operation/ProductAPI_ImportProductsV3) и [/v1/product/attributes/update](#operation/ProductAPI_ProductUpdateAttributes).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2296-Novye-metody-zavisimykh-atributov/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `description_category_id` — integer<int64> **обязательный**. Идентификатор категории из метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
- `type_id` — integer<int64>. Идентификатор типа товара из метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).

## Ответы

**200** — Зависимые характеристики

- `result` — array[object]. Информация о зависимых характеристиках.
  - `child_attribute_id` — integer<int64>. Идентификатор дочерней характеристики.
  - `parent_attribute_id` — integer<int64>. Идентификатор родительской характеристики.

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
