---
title: Получить информацию о черновике заявки на поставку
api: ozon-seller
method: POST
path: /v2/draft/create/info
operation_id: DraftCreateInfo
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 766f46431380d909
---

# Получить информацию о черновике заявки на поставку

`POST /v2/draft/create/info`

Вы можете создавать черновики заявки на поставку 2 раза в минуту и 50 раз в час.

Если превысите лимит, вернётся ошибка 429.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `draft_id` — integer<int64> **обязательный**. Идентификатор черновика из методов [/v1/draft/crossdock/create](#operation/DraftCrossdockCreate), [/v1/draft/direct/create](#operation/DraftDirectCreate) или [/v1/draft/multi-cluster/create](#operation/DraftMultiClusterCreate).

## Ответы

**200** — Информация о черновике

- `clusters` — array[object]. Кластеры.
  - `cluster_name` — string. Название кластера.
  - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
  - `supply_type` — string (CROSSDOCK, DIRECT, MULTI_CLUSTER). Тип поставки: - `CROSSDOCK` — кросс-докинг; - `DIRECT` — прямая; - `MULTI_CLUSTER` — для нескольких кластеров.
  - `warehouses` — array[object]. Склады размещения.
    - `availability_status` — object. Информация о доступности склада.
      - `invalid_reason` — string (UNSPECIFIED, NO_REASON, PARTIAL_MATRIX_AVAILABLE, NOT_AVAILABLE_MATRIX, NOT_AVAILABLE_RANK, NOT_AVAILABLE_ROUTE, NOT_AVAILABLE_TIMESLOT_FOR_DROP_OFF_POINT, NOT_AVAILABLE_TIMESLOT_FOR_STORAGE_WAREHOUSE, NOT_AVAILABLE_TIMESLOT_FOR_BOTH_WAREHOUSES, NOT_AVAILABLE_TIMESLOT_NO_REASON). Причина недоступности склада: - `UNSPECIFIED` — не определена; - `NO_REASON` — нет причины; - `PARTIAL_MATRIX_AVAILABLE` — склад не может принять часть товаров; - `NOT_AVAILABLE_MATRIX` — склад не может принять все товары; - `NOT_AVAILABLE_RANK` — склад недоступен из-за рейтинга; - `NOT_AVAILABLE_ROUTE` — нет доступного маршрута; - `NOT_AVAILABLE_TIMESLOT_FOR_DROP_OFF_POINT` — нет таймслотов на точке отгрузки; - `NOT_AVAILABLE_TIMESLOT_FOR_STORAGE_WAREHOUSE` — нет таймслотов на складе поставки; - `NOT_AVAILABLE_TIMESLOT_FOR_BOTH_WAREHOUSES` — нет таймслотов на складах отгрузки и поставки; - `NOT_AVAILABLE_TIMESLOT_NO_REASON` — нет таймслотов. По умолчанию: `UNSPECIFIED`.
      - `state` — string (UNSPECIFIED, FULL_AVAILABLE, PARTIAL_AVAILABLE, NOT_AVAILABLE). Статус доступности: - `UNSPECIFIED` — не определён, - `FULL_AVAILABLE` — доступен, - `PARTIAL_AVAILABLE` — частично доступен, - `NOT_AVAILABLE` — недоступен. По умолчанию: `UNSPECIFIED`.
    - `bundle_id` — string. Идентификатор товарного состава.
    - `restricted_bundle_id` — string. Комплект товаров, которые не попадают в поставку. Используйте значение параметра в методе [/v1/supply-order/bundle](#operation/SupplyOrderBundle), чтобы получить подробную информацию.
    - `storage_warehouse` — object. Склад хранения для поставок с типом `DIRECT`.
      - `address` — string. Адрес склада хранения.
      - `name` — string. Название склада хранения.
      - `warehouse_id` — integer<int64>. Идентификатор склада хранения.
    - `supply_tags` — array[string (UNSPECIFIED, TRACEABLE, ETTN_REQUIRED, EVSD_REQUIRED, MARKING_REQUIRED, MARKING_POSSIBLE, JEWELRY, FREEZE_STOCK_FOR_MARKING_AFTER_ACCEPTANCE, UTD_REQUIRED, UNDEFINED)]. Метки товаров в заявке на поставку: - `UNSPECIFIED` — не определена; - `TRACEABLE` — товар с признаком прослеживаемости; - `ETTN_REQUIRED` — товар, для которого необходима электронная ТТН; - `EVSD_REQUIRED` — товар с сертификацией «Меркурий»; - `MARKING_REQUIRED` — товар с обязательной маркировкой «Честный ЗНАК»; - `MARKING_POSSIBLE` — товар с возможной маркировкой «Честный ЗНАК»; - `JEWELRY` — товар с признаком ювелирного изделия; - `FREEZE_STOCK_FOR_MARKING_AFTER_ACCEPTANCE` — заморозка стока для поставок, в которых есть маркируемые товары и не был передан УПД; - `UTD_REQUIRED` — товар с обязательным УПД; - `UNDEFINED` — неизвестная.
    - `total_rank` — integer<int32>. Ранг склада в кластере. Только для поставок с типом `DIRECT`.
    - `total_score` — number<double>. Рейтинг склада.
- `errors` — array[object]. Ошибки.
  - `error_message` — string (UNSPECIFIED, EMPTY_ITEMS_LIST, ITEMS_COUNT_MORE_THAN_MAX, UNKNOWN_CLUSTER_IDS, ITEMS_VALIDATION, DROP_OFF_POINT_DOES_NOT_EXIST, DROP_OFF_POINT_HAS_NO_TIMESLOTS, TOTAL_VOLUME_IN_LITRES_INVALID, SKU_DISTRIBUTION_REQUIRED_BUT_NOT_POSSIBLE, CROSS_DOCK_IN_DELIVERY_POINT_DISABLED_FOR_SELLER, DUPLICATE_SKUS_IN_REQUEST, CAN_NOT_CREATE_DRAFT…). Возможные ошибки: - `UNSPECIFIED` — ошибка не определена; - `EMPTY_ITEMS_LIST` — передан пустой список `items`; - `ITEMS_COUNT_MORE_THAN_MAX` — превышено количество `sku`; - `UNKNOWN_CLUSTER_IDS` — кластер с таким `id` не существует; - `ITEMS_VALIDATION` — ошибки валидации товарного состава; - `DROP_OFF_POINT_DOES_NOT_EXIST` — точка отгрузки с таким `id` не существует; - `DROP_OFF_POINT_HAS_NO_TIMESLOTS` — нет доступных таймслотов на точке отгрузки; - `TOTAL_VOLUME_IN_LITRES_INVALID` — объём поставляемых товаров слишком большой для этой точки; - `SKU_DISTRIBUTION_REQUIRED_BUT_NOT_POSSIBLE` — требуется распределение SKU, но оно невозможно; - `CROSS_DOCK_IN_DELIVERY_POINT_DISABLED_FOR_SELLER` — поставка кросс-докингом через пункт выдачи заказов недоступна для продавца; - `DUPLICATE_SKUS_IN_REQUEST` — в запросе есть дубликаты SKU; - `CAN_NOT_CREATE_DRAFT` — не удалось создать черновик; - `DRAFT_TOTALS_INVALID_ERROR` — некорректные итоговые данные в черновике; - `CAN_NOT_START_CALCULATION` — не удалось начать расчёт; - `PICKUP_IS_NOT_AVAILABLE` — самовывоз недоступен; - `DROP_OFF_NOT_COMPATIBLE_WITH_PICKUP` — точка отгрузки несовместима с самовывозом; - `UNDEFINED` — неизвестная ошибка. По умолчанию: `UNSPECIFIED`.
  - `error_reasons` — array[string (UNSPECIFIED, ORDER_CREATION_NOT_AVAILABLE_FOR_SELLER, ALL_ITEMS_REJECTED, NOT_AVAILABLE_CLUSTERS, ALL_ITEMS_COUNT_INVALID, ALL_ITEMS_VOLUME_INVALID, ALL_BUNDLES_EMPTY, HAS_EMPTY_BUNDLE, DISABLED_FOR_SELLER, NO_ACTIVE_SELLER_WAREHOUSE, INVALID_SELLER_WAREHOUSE, MINIMUM_VOLUME_IN_LITRES_INVALID…)]. Причина ошибки: - `UNSPECIFIED` — не определена; - `ALL_ITEMS_COUNT_INVALID` — в товарном составе больше 5000 SKU; - `ALL_ITEMS_VOLUME_INVALID` — в товарном составе объём товаров больше 100 000 литров; - `ALL_BUNDLES_EMPTY` — товарные составы пустые; - `HAS_EMPTY_BUNDLE` — минимум 1 товарный состав в черновике пустой; - `DISABLED_FOR_SELLER` — отгрузка курьером отключена для продавца; - `NO_ACTIVE_SELLER_WAREHOUSE` — нет хотя бы 1 активного склада продавца; - `INVALID_SELLER_WAREHOUSE` — склад продавца недоступен; - `MINIMUM_VOLUME_IN_LITRES_INVALID` — товарный состав слишком маленький для точки отгрузки.
  - `items_validation` — array[object]. Ошибки валидации.
    - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
    - `rejected_items` — array[object]. Отклонённые товары.
      - `reasons` — array[string (UNSPECIFIED, OUT_OF_ASSORTMENT, INVALID, INCOMPATIBLE_WAREHOUSE, EMPTY_BARCODE, EMPTY_PS_ATTRIBUTE, MULTIPLICITY, NO_PRICE, INVALID_ITEM_COUNT_MAX, INVALID_ITEM_COUNT_ZERO, SKU_REJECTED_BY_ACCEPTANCE_RESTRICTIONS, SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED…)]. Причины отклонения: - `UNSPECIFIED` — не определена; - `OUT_OF_ASSORTMENT` — товар не входит в ассортимент; - `INVALID` — недействительный товар; - `INCOMPATIBLE_WAREHOUSE` — товар нельзя разместить на выбранном складе; - `EMPTY_BARCODE` — нет штрихкода; - `EMPTY_PS_ATTRIBUTE` — нет обязательного атрибута товара; - `MULTIPLICITY` — количество товара в поставке не кратно продаваемым партиям; - `NO_PRICE` — нет цены; - `INVALID_ITEM_COUNT_MAX` — количество товара больше максимального; - `INVALID_ITEM_COUNT_ZERO` — количество товара равно нулю; - `SKU_REJECTED_BY_ACCEPTANCE_RESTRICTIONS` — товар отклонён из-за ограничений на приёмку; - `SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED` — товар с меткой `is_ettn_required` не разрешён; - `SKU_WITHOUT_ETTN_REQUIRED_TAG_NOT_ALLOWED` — товар без метки `is_ettn_required` не разрешён; - `SKU_WITH_TRACEABLE_TAG_NOT_ALLOWED` — товар с тегом отслеживаемости не разрешён; - `SKU_IS_RESTRICTED` — товар ограничен к приёмке; - `EMPTY_CLUSTER` — нет кластера; - `SKU_WITH_UTD_REQUIRED_TAG_NOT_ALLOWED` — товар с обязательным тегом UTD не разрешён; - `CORRUPTED_ASSORTMENT` — не получилось добавить товар в заявку; - `STORAGE_BELARUS_SKU_HAS_NO_ANY_FEACN` — у товара для хранения в Беларуси нет кода ТН ВЭД; - `STORAGE_BELARUS_SKU_HAS_NO_SELLER_FEACN`— у товара для хранения в Беларуси нет кода ТН ВЭД продавца; - `TRACEABLE_SKU_HAS_NO_GTIN_BARCODE` — у товара нет штрихкода GTIN; - `TRACEABLE_SKU_HAS_NO_MEASUREMENT_UNIT_QUANTITY` — у товара нет указанного количества в единицах; - `SKU_HAS_INVALID_HS_CODE` — у товара некорректный HS-код; - `SKU_HAS_STORAGE_COUNTRY_RESTRICTIONS` — у товара есть ограничения по стране хранения; - `UNDEFINED` — неизвестная ошибка.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `macrolocal_cluster_ids` — array[string<int64>]. Идентификаторы кластеров размещения.
  - `message` — string. Сообщение об ошибке.
  - `skus` — array[string<int64>]. Список идентификаторов товаров — SKU.
- `status` — string (UNSPECIFIED, SUCCESS, IN_PROGRESS, FAILED). Статус создания черновика заявки на поставку: - `UNSPECIFIED` — не определён, - `SUCCESS` — создан, - `IN_PROGRESS` — создаётся, - `FAILED` — не удалось создать. По умолчанию: `UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
