---
title: Управлять скидкой от количества
api: ozon-seller
method: POST
path: /v1/product/stairway-discount/by-quantity/set
operation_id: ProductAPI_SetProductStairwayDiscountByQuantity
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 29cd6e4abb9c9122
---

# Управлять скидкой от количества

`POST /v1/product/stairway-discount/by-quantity/set`

Устанавливает или удаляет скидку на товар в зависимости от его количества в заказе. Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1719-Novye-metody-dlia-raboty-so-skidkoi-ot-kolichestva/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `stairways` — array[object] **обязательный**. Информация о скидке от количества по товарам.
  - `enabled` — boolean **обязательный**. `true`, чтобы включить скидку.
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
  - `stairway` — object **обязательный**. Информация об уровне скидки от количества.
    - `steps` — array[object] **обязательный**. Информация об уровнях скидки. Количество уровней — от 1 до 4.
      - `discount` — integer<int64> **обязательный**. Размер скидки в процентах.
      - `quantity` — integer<int64> **обязательный**. Количество товаров в заказе для применения скидки.
      - `step` — integer<int64> **обязательный**. Уровень скидки.
- `suppress_warnings` — boolean. Передайте `true`, чтобы игнорировать предупреждения и установить скидку.

## Ответы

**200** — Настройки скидки изменены

- `accepted` — boolean. `true`, если запрос принят. Используйте метод [/v1/product/stairway-discount/by-quantity/get](#operation/ProductAPI_GetProductStairwayDiscountByQuantity), чтобы узнать результат изменения скидки.
- `errors` — array[object]. Описание ошибок.
  - `data` — array[object]. Описание ошибки или предупреждения.
    - `code` — string. Код.
    - `field` — string. Причина.
    - `message` — string. Текстовое описание.
    - `step` — integer<int64>. Уровень скидки.
    - `value` — string. Значение поля с ошибкой.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `warnings` — array[object]. Описание предупреждения.
  - `data` — array[object]. Описание ошибки или предупреждения.
    - `code` — string. Код.
    - `field` — string. Причина.
    - `message` — string. Текстовое описание.
    - `step` — integer<int64>. Уровень скидки.
    - `value` — string. Значение поля с ошибкой.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

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
