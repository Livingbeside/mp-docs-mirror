---
title: Получить список складов с ограниченными для доставки товарами
api: ozon-seller
method: POST
path: /v1/warehouse/warehouses-with-invalid-products
operation_id: WarehouseWithInvalidProducts
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 649c7e373dce2139
---

# Получить список складов с ограниченными для доставки товарами

`POST /v1/warehouse/warehouses-with-invalid-products`

Возвращает идентификаторы складов, на которых находятся товары с ограничениями. Такие товары недоступны для доставки со склада.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список складов

- `warehouse_ids` — array[string<int64>]. Список идентификаторов складов, у которых есть хотя бы 1 товар, который недоступен для доставки со склада. Чтобы получить список товаров с ограничениями, используйте метод [/v1/warehouse/invalid-products/get](#operation/WarehouseInvalidProductsGet).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
