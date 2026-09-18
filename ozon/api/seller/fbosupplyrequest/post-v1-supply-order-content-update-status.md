---
title: Информация о статусе редактирования товарного состава
api: ozon-seller
method: POST
path: /v1/supply-order/content/update/status
operation_id: SupplyOrderAPI_SupplyOrderContentUpdateStatus
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ac4647e93d0d0ae5
---

# Информация о статусе редактирования товарного состава

`POST /v1/supply-order/content/update/status`

Метод для получения статуса редактирования товарного состава.

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции.

## Ответы

**200** — Статус редактирования

- `error_details` — object. Информация об ошибках при попытке редактирования товарного состава.
  - `backup_supply_id` — integer<int64>. Идентификатор резервной поставки в кластер, которая была создана ранее.
  - `code` — array[string (SHIPMENT_PLANNING_DISCIPLINE_CLUSTER_LIMIT_EXCEEDED, SHIPMENT_PLANNING_DISCIPLINE_CLUSTER_BACKUP_SUPPLY_ALREADY_USED)]. Код ошибки: - `SHIPMENT_PLANNING_DISCIPLINE_CLUSTER_LIMIT_EXCEEDED` — превышен лимит на изменение товаров в поставке; - `SHIPMENT_PLANNING_DISCIPLINE_CLUSTER_BACKUP_SUPPLY_ALREADY_USED` — превышен лимит на обновление товарного состава поставок.
  - `items_quantity_limit` — integer<int64>. Доступный лимит на изменение товаров в поставке.
- `errors` — array[string (INVALID_DRAFT_BUNDLE_ID, SOME_SERVICE_ERROR, HAS_UTD, ORDER_SKU_LIMIT, SAME_SKU, SUPPLY_LOCKED, INBOUND_NO_CAPACITY, INBOUND_LOCK, SUPPLY_CONTENT_NOT_VALID, SUPPLY_BELONG_TO_ANOTHER_CONTRACTOR, SUPPLY_BELONG_TO_ANOTHER_COMPANY, INCORRECT_SUPPLY_STATE…)]. Список ошибок при редактировании товарного состава: - `INVALID_DRAFT_BUNDLE_ID`, `SOME_SERVICE_ERROR` — ошибка при редактировании поставки. - `HAS_UTD` — документы в системе ЭДО не удалены. Аннулируйте документы в системе ЭДО. Когда отредактируете состав, сформируйте и подпишите новые документы. - `ORDER_SKU_LIMIT` — количество товаров в поставке должно быть меньше или равно 5000. - `SAME_SKU` — товарный состав поставки остался прежним. - `SUPPLY_LOCKED` — обновление товарного состава в процессе, попробуйте позже. - `INBOUND_NO_CAPACITY` — на складе недостаточно места для поставки. - `INBOUND_LOCK`, `ORDER_LOCKED` — нельзя редактировать товарный состав. - `SUPPLY_CONTENT_NOT_VALID` — в составе поставки есть товары, которые склад не может принять. Провалидируйте товарный состав методом [/v1/supply-order/content/update/validation](#operation/SupplyOrderContentUpdateValidation). - `SUPPLY_BELONG_TO_ANOTHER_CONTRACTOR` — заявка на поставку не принадлежит вашему юридическому лицу. - `SUPPLY_BELONG_TO_ANOTHER_COMPANY` — заявка на поставку не принадлежит вашему кабинету. - `INCORRECT_SUPPLY_STATE` — нельзя изменить поставку в этом статусе. - `INCORRECT_SUPPLY_SOURCE` — нельзя изменить поставку с этим источником данных. - `INCORRECT_STORAGE_WAREHOUSE` — нельзя изменить поставку с этим складом хранения. - `NO_SUPPLY_PRODUCT_BUNDLE_ID` — отсутствует идентификатор товарного состава поставки. - `INVALID_VOLUME` — некорректный объём поставки. - `SUPPLY_IS_VIRTUAL` — нельзя редактировать виртуальную поставку. - `DEADLINE` — нельзя изменить поставку за час до таймслота. - `INACTIVE_CONTRACT` — нельзя редактировать состав поставки с истекшим договором. - `QUANTITY_OUT_OF_RANGE_BOTTOM` — количество экземпляров каждого товара должно быть больше 0. - `QUANTITY_OUT_OF_RANGE_UPPER` — количество экземпляров каждого товара должно быть меньше или равно 1 000 000. - `EMPTY_CONTENT` — не сможем принять пустую поставку, добавьте товары. - `MINIMUM_VOLUME_IN_LITRES_INVALID` — объём товаров в поставке ниже минимального.
- `new_bundle_id` — string. Идентификатор нового товарного состава поставки.
- `status` — string (SUCCESS, IN_PROGRESS, ERROR). Статус редактирования товарного состава поставки. Возможные статусы: - `SUCCESS` — товарный состав изменён, - `IN_PROGRESS` — товарный состав в процессе изменения, - `ERROR` — возникла ошибка при изменении товарного состава.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
