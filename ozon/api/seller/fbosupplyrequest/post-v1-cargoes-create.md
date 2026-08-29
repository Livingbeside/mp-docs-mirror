---
title: Установка грузомест
api: ozon-seller
method: POST
path: /v1/cargoes/create
operation_id: CargoesAPI_CargoesCreate
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a6ee7dc252f8c35b
---

# Установка грузомест

`POST /v1/cargoes/create`

Используйте метод, чтобы передать грузоместа и товарный состав в заявку на поставку.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cargoes` — array[object] **обязательный**. Информация о грузоместах. Вы можете передать не больше 40 палет или 30 коробок.
  - `key` — string **обязательный**. Уникальный ключ для идентификации грузоместа.
  - `value` — object **обязательный**. Информация о грузоместе.
    - `items` — array[object]. Информация о товарах в грузоместе.
      - `barcode` — string. Штрихкод товара. Получите методом [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList).
      - `expires_at` — string<date-time>. Годен до.
      - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
      - `quant` — integer<int32>. Размер кванта.
      - `quantity` — integer<int32>. Количество товара.
    - `type` — string (BOX, PALLET) **обязательный**. Тип грузоместа: - `BOX` — коробка. - `PALLET` — палета. По умолчанию: `BOX`.
- `delete_current_version` — boolean. `true`, если нужно удалить предыдущие грузоместа.
- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки. Можно получить с помощью метода [/v3/supply-order/get](#operation/SupplyOrderGet). Нужное значение — в параметре ответа `orders.supplies.supply_id`.

## Ответы

**200** — Грузоместа установлены

- `operation_id` — string. Идентификатор операции.
- `errors` — object. Ошибки.
  - `error_reasons` — array[string (INVALID_STATE, VALIDATION_FAILED, WAREHOUSE_LIMITS_EXCEED, SUPPLY_NOT_BELONG_CONTRACTOR, SUPPLY_NOT_BELONG_COMPANY, IS_FINALIZED, SKU_DISTRIBUTION_DISABLED, SUPPLY_IS_NOT_EMPTY, OPERATION_NOT_FOUND, OPERATION_FAILED)]. Причина ошибки: - `INVALID_STATE` — недопустимое состояние поставки. - `VALIDATION_FAILED` — ошибки валидации. - `WAREHOUSE_LIMITS_EXCEED` — превышены лимиты склада. - `SUPPLY_NOT_BELONG_CONTRACTOR` — поставка не относится к указанному контрагенту. - `SUPPLY_NOT_BELONG_COMPANY` — поставка не относится к указанной компании. - `IS_FINALIZED` — редактирование поставки недоступно. - `SKU_DISTRIBUTION_DISABLED` — распределение состава недоступно. - `SUPPLY_IS_NOT_EMPTY` — поставка содержит распределение состава. - `OPERATION_NOT_FOUND` — операция не найдена. - `OPERATION_FAILED` — ошибка при обработке операции.
  - `items_validation` — array[object]. Ошибки валидации.
    - `barcode` — string. Штрихкод товара. Получите методом [/v3/product/info/list](#operation/ProductAPI_GetProductInfoList).
    - `cargo_key` — string. Ключ грузоместа.
    - `quant` — integer<int32>. Размер кванта.
    - `type` — string (SUPPLY_ITEM_NOT_FOUND, DUPLICATED_SUPPLY_ITEM, BEFORE_DEADLINE, SAME_BARCODES, SAME_ARTICLES, NOT_UNIQUE_SKU_BY_PRODUCT, QUANTITY_NOT_DIVISIBLE_BY_QUANT, NOT_SINGLE_PALLET_SKU_IN_PALLET_CARGO, NOT_ONE_QUANT_PALLET_SKU, NOT_ECONOM_SKU, QUANTITY_LESS_ONE, SUPPLY_ITEM_WITH_QUANT_NOT_FOUND). Тип ошибки: - `SUPPLY_ITEM_NOT_FOUND` — товар не найден; - `DUPLICATED_SUPPLY_ITEM` — найден дубликат товара; - `BEFORE_DEADLINE` — некорректный срок годности; - `SAME_BARCODES` — у разных SKU одинаковые штрихкоды; - `SAME_ARTICLES` — у разных SKU одинаковые артикулы; - `NOT_UNIQUE_SKU_BY_PRODUCT` — одинаковый SKU в грузоместе используется для разных товаров; - `QUANTITY_NOT_DIVISIBLE_BY_QUANT` — количество SKU в грузоместе не кратно кванту; - `NOT_SINGLE_PALLET_SKU_IN_PALLET_CARGO` — в грузоместе отсутствует палетная SKU; - `NOT_ONE_QUANT_PALLET_SKU` — в квантовом палетном грузоместе должен быть только один квант; - `NOT_ECONOM_SKU` — в эконом-поставке указан не эконом-SKU; - `QUANTITY_LESS_ONE` — количество SKU в эконом-поставке меньше 1; - `SUPPLY_ITEM_WITH_QUANT_NOT_FOUND` — товар не найден по артикулу, штрихкоду и размеру кванта. По умолчанию: `SUPPLY_ITEM_NOT_FOUND`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
