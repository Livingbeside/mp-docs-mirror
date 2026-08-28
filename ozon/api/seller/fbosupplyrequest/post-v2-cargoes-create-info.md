---
title: Получить информацию по установке грузомест
api: ozon-seller
method: POST
path: /v2/cargoes/create/info
operation_id: CargoesCreateInfoV2
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7db539c7ee9dc040
---

# Получить информацию по установке грузомест

`POST /v2/cargoes/create/info`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1721-Novyi-metod-dlia-peredachi-offer-id-pri-ustanovke-GM) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции.

## Ответы

**200** — Результат запроса

- `errors` — object. Ошибки.
  - `error_reasons` — array[string (ERROR_REASON_UNSPECIFIED, INVALID_STATE, VALIDATION_FAILED, WAREHOUSE_LIMITS_EXCEED, SUPPLY_NOT_BELONG_CONTRACTOR, SUPPLY_NOT_BELONG_COMPANY, IS_FINALIZED, SKU_DISTRIBUTION_DISABLED, SUPPLY_IS_NOT_EMPTY, OPERATION_NOT_FOUND, OPERATION_FAILED)]. Причина ошибки: - `INVALID_STATE` — недопустимое состояние поставки; - `VALIDATION_FAILED` — ошибки валидации; - `WAREHOUSE_LIMITS_EXCEED` — превышены лимиты склада; - `SUPPLY_NOT_BELONG_CONTRACTOR` — поставка не относится к указанному контрагенту; - `SUPPLY_NOT_BELONG_COMPANY` — поставка не относится к указанной компании; - `IS_FINALIZED` — редактирование поставки недоступно; - `SKU_DISTRIBUTION_DISABLED` — распределение состава недоступно; - `SUPPLY_IS_NOT_EMPTY` — поставка содержит распределение состава; - `OPERATION_NOT_FOUND` — операция не найдена; - `OPERATION_FAILED` — ошибка при обработке операции.
  - `items_validation` — array[object]. Ошибки валидации.
    - `cargo_key` — string. Ключ грузоместа.
    - `item` — string. Штрихкод или артикул товара.
    - `quant` — integer<int32>. Размер кванта.
    - `type` — string (SUPPLY_ITEM_NOT_FOUND, DUPLICATED_SUPPLY_ITEM, BEFORE_DEADLINE, SAME_BARCODES, SAME_ARTICLES, NOT_UNIQUE_SKU_BY_PRODUCT, QUANTITY_NOT_DIVISIBLE_BY_QUANT, NOT_SINGLE_PALLET_SKU_IN_PALLET_CARGO, NOT_ONE_QUANT_PALLET_SKU, NOT_ECONOM_SKU, QUANTITY_LESS_ONE, SUPPLY_ITEM_WITH_QUANT_NOT_FOUND). Тип ошибки: - `SUPPLY_ITEM_NOT_FOUND` — товар не найден; - `DUPLICATED_SUPPLY_ITEM` — найден дубликат товара; - `BEFORE_DEADLINE` — некорректный срок годности; - `SAME_BARCODES` — у разных SKU одинаковые штрихкоды; - `SAME_ARTICLES` — у разных SKU одинаковые артикулы; - `NOT_UNIQUE_SKU_BY_PRODUCT` — одинаковый SKU в грузоместе используется для разных товаров; - `QUANTITY_NOT_DIVISIBLE_BY_QUANT` — количество SKU в грузоместе не кратно кванту; - `NOT_SINGLE_PALLET_SKU_IN_PALLET_CARGO` — в грузоместе отсутствует палетная SKU; - `NOT_ONE_QUANT_PALLET_SKU` — в квантовом палетном грузоместе должен быть только один квант; - `NOT_ECONOM_SKU` — в эконом-поставке указан не эконом-SKU; - `QUANTITY_LESS_ONE` — количество SKU в эконом-поставке меньше 1; - `SUPPLY_ITEM_WITH_QUANT_NOT_FOUND` — товар не найден по артикулу, штрихкоду и размеру кванта. По умолчанию: `SUPPLY_ITEM_NOT_FOUND`.
- `result` — object. Результат запроса.
  - `cargoes` — array[object]. Информация о грузоместах.
    - `key` — string. Ключ грузоместа.
    - `value` — object. Информация о грузоместе.
      - `cargo_id` — integer<int64>. Идентификатор грузоместа.
- `status` — string (STATUS_UNSPECIFIED, SUCCESS, IN_PROGRESS, FAILED). Статус формирования грузоместа: - `SUCCESS` — успешно; - `IN_PROGRESS` — формируются; - `FAILED` — при формировании грузомест произошла ошибка. По умолчанию: `STATUS_UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
