---
title: Редактирование товарного состава
api: ozon-seller
method: POST
path: /v1/supply-order/content/update
operation_id: SupplyOrderAPI_SupplyOrderContentUpdate
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4c6efd13b1355c8b
---

# Редактирование товарного состава

`POST /v1/supply-order/content/update`

Метод для редактирования товарного состава в заявке на поставку. Чтобы проверить статус редактирования, используйте метод [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus).

## Запрос

**Тело запроса** (`application/json`):

- `items` — array[object] **обязательный**. Новый товарный состав заявки на поставку. Максимум 5000 товаров.
  - `quant` — integer<int32> **обязательный**. Размер кванта.
  - `quantity` — integer<int32> **обязательный**. Количество товара.
  - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
- `order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.
- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки.

## Ответы

**200** — Товарный состав обновлён

- `errors` — array[string (INVALID_DRAFT_BUNDLE_ID, SOME_SERVICE_ERROR, HAS_UTD, ORDER_SKU_LIMIT, SAME_SKU, SUPPLY_LOCKED, INBOUND_NO_CAPACITY, INBOUND_LOCK, SUPPLY_CONTENT_NOT_VALID, SUPPLY_BELONG_TO_ANOTHER_CONTRACTOR, SUPPLY_BELONG_TO_ANOTHER_COMPANY, INCORRECT_SUPPLY_STATE…)]. Ошибки при редактировании товарного состава: - `INVALID_DRAFT_BUNDLE_ID`, `SOME_SERVICE_ERROR`, `ORDER_IS_NOT_FOUND`, `SUPPLY_IS_NOT_FOUND`, `SUPPLY_DOES_NOT_BELONGS_TO_ORDER` — ошибка при редактировании поставки. - `HAS_UTD`, `UTD_IS_UPLOADED` — документы в системе ЭДО не удалены. Аннулируйте документы в системе ЭДО. Когда отредактируете состав, сформируйте и подпишите новые документы. - `ORDER_SKU_LIMIT` — количество товаров в поставке должно быть меньше или равно 5000. - `SAME_SKU` — товарный состав поставки остался прежним. - `SUPPLY_LOCKED` — обновление товарного состава в процессе, попробуйте позже. - `INBOUND_NO_CAPACITY` — на складе недостаточно места для поставки. - `INBOUND_LOCK`, `ORDER_LOCKED`, `STORAGE_WAREHOUSE_IS_NOT_WMS` — нельзя редактировать товарный состав. - `SUPPLY_CONTENT_NOT_VALID` — в составе поставки есть товары, которые склад не может принять. - `SUPPLY_BELONG_TO_ANOTHER_CONTRACTOR`, `COMPANY_DOES_NOT_BELONGS_TO_CONTRACTOR`, `ORDER_DOES_NOT_BELONG_TO_CONTRACTOR` — заявка на поставку не принадлежит вашему юридическому лицу. - `SUPPLY_BELONG_TO_ANOTHER_COMPANY`, `ORDER_DOES_NOT_BELONGS_TO_COMPANY` — заявка на поставку не принадлежит вашему кабинету. - `INCORRECT_SUPPLY_STATE` — нельзя изменить поставку в этом статусе. - `INCORRECT_SUPPLY_SOURCE` — нельзя изменить поставку с этим источником данных. - `INCORRECT_STORAGE_WAREHOUSE` — нельзя изменить поставку с этим складом хранения. - `NO_SUPPLY_PRODUCT_BUNDLE_ID` — отсутствует идентификатор товарного состава поставки. - `INVALID_VOLUME` — некорректный объём поставки. - `SUPPLY_IS_VIRTUAL` — нельзя редактировать виртуальную поставку. - `DEADLINE` — нельзя изменить поставку за час до таймслота. - `INACTIVE_CONTRACT` — нельзя редактировать состав поставки с истекшим договором. - `QUANTITY_OUT_OF_RANGE_BOTTOM` — количество экземпляров каждого товара должно быть больше 0. - `QUANTITY_OUT_OF_RANGE_UPPER` — количество экземпляров каждого товара должно быть меньше или равно 1 000 000. - `EMPTY_CONTENT` — не сможем принять пустую поставку, добавьте товары. - `CONTRACT_IS_NOT_FOUND`, `CONTRACT_IS_NOT_VALID_FOR_HANDLING_ORDERS` — в этом личном кабинете нельзя изменить поставку. - `MINIMUM_VOLUME_IN_LITRES_INVALID` — объём товаров в поставке ниже минимального.
- `operation_id` — string. Идентификатор операции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
