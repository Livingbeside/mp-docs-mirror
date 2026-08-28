---
title: Получить информацию о скидке от количества
api: ozon-seller
method: POST
path: /v1/product/stairway-discount/by-quantity/get
operation_id: ProductAPI_GetProductStairwayDiscountByQuantity
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 78e4c5b4844e430b
---

# Получить информацию о скидке от количества

`POST /v1/product/stairway-discount/by-quantity/get`

Возвращает информацию о скидке на товар в зависимости от его количества в заказе.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1719-Novye-metody-dlia-raboty-so-skidkoi-ot-kolichestva/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>] **обязательный**. Список идентификаторов товара в системе Ozon — SKU.

## Ответы

**200** — Информация получена

- `stairways` — array[object]. Информация о скидке от количества по конкретному товару.
  - `enabled` — boolean. `true`, если скидка от количества включена.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `stairway` — object. Информация об уровне скидки от количества.
    - `steps` — array[object]. Информация об уровнях скидки.
      - `discount` — integer<int64>. Размер скидки в процентах.
      - `quantity` — integer<int64>. Количество товара в заказе для применения скидки.
      - `step` — integer<int64>. Уровень скидки.
  - `status` — string (IN_PROCESS, ERROR, SUCCESS). Статус изменения скидки от количества. Возможные значения: - `ERROR` — ошибка при изменении скидки. Вызовите метод [/v1/product/stairway-discount/by-quantity/set](#operation/ProductAPI_SetProductStairwayDiscountByQuantity) ещё раз. - `IN_PROCESS` — изменение в процессе. - `SUCCESS` — изменение скидки применено к товару.

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
