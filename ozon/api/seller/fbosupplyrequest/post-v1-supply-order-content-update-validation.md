---
title: Проверить новый товарный состав
api: ozon-seller
method: POST
path: /v1/supply-order/content/update/validation
operation_id: SupplyOrderContentUpdateValidation
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 99f7418ea3d4c497
---

# Проверить новый товарный состав

`POST /v1/supply-order/content/update/validation`

Используйте этот метод, если в [/v1/supply-order/content/update/status](#operation/SupplyOrderAPI_SupplyOrderContentUpdateStatus) вы получили ошибку `SUPPLY_CONTENT_NOT_VALID`.

## Запрос

**Тело запроса** (`application/json`):

- `new_bundle_id` — string **обязательный**. Идентификатор нового товарного состава поставки.
- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки.

## Ответы

**200** — Успешно

- `editing_errors` — array[string (UNSPECIFIED, UNKNOWN, INCORRECT_SUPPLY_STATE, DEADLINE, UTD_IS_UPLOADED, STORAGE_WAREHOUSE_IS_NOT_WMS, CONTRACT_IS_NOT_VALID_FOR_HANDLING_ORDERS, SUPPLY_IS_VIRTUAL, SUPPLY_DOES_NOT_BELONG_TO_COMPANY, ASSORTMENT_REJECTION_REASON_CORRUPTED_ASSORTMENT, ASSORTMENT_REJECTION_REASON_STORAGE_BELARUS_SKU_HAS_NO_ANY_FEACN, ASSORTMENT_REJECTION_REASON_STORAGE_BELARUS_SKU_HAS_NO_SELLER_FEACN…)]. Ошибки: - `UNSPECIFIED` — не определено. - `UNKNOWN` — неизвестный тип. - `INCORRECT_SUPPLY_STATE` — нельзя изменить поставку в этом статусе. - `DEADLINE` — нельзя изменить поставку за час до таймслота. - `UTD_IS_UPLOADED` — документы в системе ЭДО не удалены. Аннулируйте документы в системе ЭДО. Когда отредактируете состав, сформируйте и подпишите новые документы. - `STORAGE_WAREHOUSE_IS_NOT_WMS` — нельзя редактировать товарный состав. - `CONTRACT_IS_NOT_VALID_FOR_HANDLING_ORDERS` — в этом личном кабинете нельзя изменить поставку. - `SUPPLY_IS_VIRTUAL` — нельзя редактировать виртуальную поставку. - `SUPPLY_DOES_NOT_BELONG_TO_COMPANY` — заявка на поставку не принадлежит вашему кабинету. - `ASSORTMENT_REJECTION_REASON_CORRUPTED_ASSORTMENT` — не получилось добавить товар в заявку. Попробуйте ещё раз. - `ASSORTMENT_REJECTION_REASON_STORAGE_BELARUS_SKU_HAS_NO_ANY_FEACN`, `ASSORTMENT_REJECTION_REASON_STORAGE_BELARUS_SKU_HAS_NO_SELLER_FEACN` — у товара нет кода ТН ВЭД ЕАЭС. - `ASSORTMENT_REJECTION_REASON_TRACEABLE_SKU_HAS_NO_GTIN_BARCODE` — у товара нет штрихкода GTIN. - `ASSORTMENT_REJECTION_REASON_TRACEABLE_SKU_HAS_NO_MEASUREMENT_UNIT_QUANTITY` — не указано количество товара в унифицированных единицах измерения. По умолчанию: `UNSPECIFIED`.
- `validated_assortment` — object. Информация о товарном составе.
  - `approved_items` — array[object]. Принятые товары.
    - `barcode` — string. Штрихкод товара.
    - `item_link` — string. Ссылка на товар.
    - `name` — string. Название товара.
    - `offer_id` — string. Артикул товара.
    - `origin_quantity` — integer<int32>. Исходное количество товара.
    - `origin_total_volume_in_litres` — number<double>. Исходное количество товара в литрах.
    - `quant` — integer<int32>. Количество товаров в одной упаковке.
    - `quantity` — integer<int32>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `sku_quantity_limit` — integer<int32>. Ограничение на количество товаров в одной упаковке.
    - `total_volume_in_litres` — number<double>. Объём всех товаров в литрах.
  - `rejected_items` — array[object]. Не принятые товары.
    - `barcode` — string. Штрихкод товара.
    - `name` — string. Название товара.
    - `offer_id` — string. Артикул товара.
    - `origin_quantity` — integer<int32>. Исходное количество товара.
    - `origin_total_volume_in_litres` — number<double>. Исходное количество товара в литрах.
    - `quantity` — integer<int32>. Количество товара.
    - `rejection_reason` — array[string (UNSPECIFIED, UNKNOWN, OUT_OF_ASSORTMENT, INVALID, INCOMPATIBLE_WAREHOUSE, EMPTY_BARCODE, EMPTY_PS_ATTRIBUTE, MULTIPLICITY, NO_PRICE, INVALID_ITEM_COUNT_MAX, INVALID_ITEM_COUNT_ZERO, INCOMPATIBLE_SHIPMENT_TYPE…)]. Причина отклонения товара: - `UNSPECIFIED` — не определена; - `UNKNOWN` — неизвестный тип; - `OUT_OF_ASSORTMENT` — товара нет в ассортименте поставки; - `INVALID` — некорректные данные по товару; - `INCOMPATIBLE_WAREHOUSE` — товар нельзя поставить на выбранный склад; - `EMPTY_BARCODE` — штрихкод не указан; - `EMPTY_PS_ATTRIBUTE` — не заполнен обязательный атрибут; - `MULTIPLICITY` — количество товара не кратно упаковке; - `NO_PRICE` — цена не указана; - `INVALID_ITEM_COUNT_MAX` — превышено максимальное количество; - `INVALID_ITEM_COUNT_ZERO` — количество должно быть больше 0; - `INCOMPATIBLE_SHIPMENT_TYPE` — товар недоступен для выбранного типа отгрузки; - `ECONOM_QUANT_IS_NOT_FROZEN` — квант для тарифа «Эконом» не заморожен; - `QUANTITY_NOT_MULTIPLE_BY_QUANT` — количество товара не кратно кванту; - `INVALID_QUANT_VALUE` — некорректное значение кванта; - `JEWELRY_FORBIDDEN_FOR_ECONOM` — ювелирные изделия недоступны для тарифа «Эконом»; - `NON_UNIQUE_ECONOM_ITEM_IN_REQUEST` — в запросе есть дубликаты SKU для тарифа «Эконом»; - `NON_UNIQUE_ECONOM_ITEM_IN_DESTINATION_BUNDLE` — в грузоместе есть дубликаты SKU для тарифа «Эконом»; - `SKU_REJECTED_BY_ACCEPTANCE_RESTRICTIONS` — товар не принимается по ограничениям приёмки; - `SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED` — товар с тегом электронной ТТН недоступен; - `SKU_WITHOUT_ETTN_REQUIRED_TAG_NOT_ALLOWED` — товар без тега электронной ТТН; - `SKU_WITH_TRACEABLE_TAG_NOT_ALLOWED` — товары с тегом прослеживаемости недоступны; - `EMPTY_CLUSTER` — не указан кластер; - `SKU_IS_RESTRICTED` — товар запрещён к поставке; - `SKU_WITH_UTD_REQUIRED_TAG_NOT_ALLOWED` — товары с тегом УПД недоступны.
    - `restrictions` — object. Ограничения.
      - `reasons_restrictions` — array[string (UNKNOWN, SKU_HAS_NO_SALES, SKU_HAS_QUANTITY_LIMIT)]. Причины ограничения: - `UNKNOWN` — неизвестный тип; - `SKU_HAS_NO_SALES` — товар не продавался; - `SKU_HAS_QUANTITY_LIMIT` — лимит по количеству товара.
      - `sku_has_no_sales_in_days` — integer<int32>. Количество дней, которое товар не продавался.
      - `sku_quantity_limit` — integer<int32>. Лимит по количеству товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `total_volume_in_litres` — number<double>. Объём всех товаров в литрах.
  - `total_approved_item_count` — integer<int32>. Количество принятого товара.
  - `total_approved_quantity` — integer<int32>. Количество единиц принятого товара.
  - `total_approved_volume_in_litres` — number<double>. Количество принятого товара в литрах.
  - `total_rejected_item_count` — integer<int32>. Количество не принятого товара.
  - `total_restricted_item_count` — integer<int32>. Количество товара с ограничениями.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
