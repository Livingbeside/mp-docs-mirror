---
title: Узнать информацию об уценке и основном товаре по SKU уценённого товара
api: ozon-seller
method: POST
path: /v1/product/info/discounted
operation_id: ProductAPI_GetProductInfoDiscounted
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fa167e2ff3a0ebae
---

# Узнать информацию об уценке и основном товаре по SKU уценённого товара

`POST /v1/product/info/discounted`

Метод для получения информации о состоянии и дефектах уценённого товара по его SKU. Работает только с уценёнными товарами по схеме FBO. Также метод возвращает SKU основного товара.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `discounted_skus` — ? **обязательный**. Список SKU уценённых товаров.

## Ответы

**200** — Информация об уценке и основном товаре

- `items` — ?. Информация об уценке и основном товаре.
  - `comment_reason_damaged` — string. Комментарий к причине повреждения.
  - `condition` — string. Состояние товара — новый или Б/У.
  - `condition_estimation` — string. Состояние товара по шкале от 1 до 7: - 1 — удовлетворительное, - 2 — хорошее, - 3 — очень хорошее, - 4 — отличное, - 5–7 — как новый.
  - `defects` — string. Дефекты товара.
  - `discounted_sku` — integer<int64>. SKU уценённого товара.
  - `mechanical_damage` — string. Описание механического повреждения.
  - `package_damage` — string. Описание повреждения упаковки.
  - `packaging_violation` — string. Признак нарушения целостности упаковки.
  - `reason_damaged` — string. Причина повреждения.
  - `repair` — string. Признак, что товар отремонтирован.
  - `shortage` — string. Признак, что товар некомплектный.
  - `sku` — integer<int64>. SKU основного товара.
  - `warranty_type` — string. Наличие у товара действующей гарантии.

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
