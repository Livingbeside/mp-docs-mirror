---
title: Получить возможные значения дочерней характеристики
api: ozon-seller
method: POST
path: /v1/description-category/dependent-attributes/values
operation_id: DescriptionCategoryDependentAttributesValues
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d9185203f9dd09b9
---

# Получить возможные значения дочерней характеристики

`POST /v1/description-category/dependent-attributes/values`

Возвращает возможные значения дочерней характеристики для значений родительской.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2296-Novye-metody-zavisimykh-atributov/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `child_attribute_id` — integer<int64> **обязательный**. Идентификатор дочерней характеристики.
- `cursor` — string. Указатель для выборки следующих данных.
- `description_category_id` — integer<int64>. Идентификатор категории из метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
- `limit` — integer<int64>. Количество значений в ответе. По умолчанию: `100`.
- `parent_attribute_id` — integer<int64> **обязательный**. Идентификатор родительской характеристики.
- `type_id` — integer<int64>. Идентификатор типа товара из метода [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).

## Ответы

**200** — Возможные значения дочерней характеристики

- `cursor` — string. Указатель для выборки следующих данных.
- `result` — array[object]. Информация о зависимых характеристиках.
  - `children` — array[object]. Информация о дочерних характеристиках.
    - `child_value` — string. Значение дочерней характеристики.
    - `child_value_id` — integer<int64>. Идентификатор значения дочерней характеристики.
  - `parent_value` — string. Значение родительской характеристики.
  - `parent_value_id` — integer<int64>. Идентификатор значения родительской характеристики.

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
