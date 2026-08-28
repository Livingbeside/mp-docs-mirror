---
title: Создать черновик заявки на прямую поставку
api: ozon-seller
method: POST
path: /v1/draft/direct/create
operation_id: DraftDirectCreate
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ee89675cf80ffabe
---

# Создать черновик заявки на прямую поставку

`POST /v1/draft/direct/create`

Черновик заявки на поставку не отображается в личном кабинете продавца и доступен 30 минут. Вы можете создавать черновики заявки на поставку: - 2 раза в минуту; - 50 раз в час; - 500 раз в день. Если превысите лимит, вернётся ошибка 429.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cluster_info` — object **обязательный**. Информация о кластере.
  - `items` — array[object] **обязательный**. Товарный состав заявки на поставку.
    - `quantity` — integer<int32> **обязательный**. Количество.
    - `sku` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.
  - `macrolocal_cluster_id` — integer<int64> **обязательный**. Идентификатор кластера размещения. Получите значение параметра методом [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList).
- `deletion_sku_mode` — string (FULL, PARTIAL) **обязательный**. Режим удаления SKU, которые не попали в поставку. Возможные значения: - `PARTIAL` — система удалит только те единицы SKU, которые не прошли проверку; - `FULL` — система удалит все единицы SKU, если хотя бы одна единица этого SKU не прошла проверку.

## Ответы

**200** — Черновик создан

- `draft_id` — integer<int64>. Идентификатор черновика. Используйте в методе [/v2/draft/create/info](#operation/DraftCreateInfo).
- `errors` — array[object]. Ошибки.
  - `error_message` — string (UNSPECIFIED, EMPTY_ITEMS_LIST, ITEMS_COUNT_MORE_THAN_MAX, UNKNOWN_CLUSTER_IDS, ITEMS_VALIDATION, DROP_OFF_POINT_DOES_NOT_EXIST, DROP_OFF_POINT_HAS_NO_TIMESLOTS, TOTAL_VOLUME_IN_LITRES_INVALID, SKU_DISTRIBUTION_REQUIRED_BUT_NOT_POSSIBLE, CROSS_DOCK_IN_DELIVERY_POINT_DISABLED_FOR_SELLER, DUPLICATE_SKUS_IN_REQUEST, CAN_NOT_CREATE_DRAFT…). Возможные ошибки: - `UNSPECIFIED` — ошибка не определена; - `EMPTY_ITEMS_LIST` — передан пустой список `items`; - `ITEMS_COUNT_MORE_THAN_MAX` — превышено количество `sku`; - `UNKNOWN_CLUSTER_IDS` — кластер с таким `id` не существует; - `ITEMS_VALIDATION` — ошибки валидации товарного состава; - `DROP_OFF_POINT_DOES_NOT_EXIST` — точка отгрузки с таким `id` не существует; - `DROP_OFF_POINT_HAS_NO_TIMESLOTS` — нет доступных таймслотов на точке отгрузки; - `TOTAL_VOLUME_IN_LITRES_INVALID` — объём поставляемых товаров слишком большой для этой точки; - `SKU_DISTRIBUTION_REQUIRED_BUT_NOT_POSSIBLE` — требуется распределение SKU, но оно невозможно; - `CROSS_DOCK_IN_DELIVERY_POINT_DISABLED_FOR_SELLER` — поставка кросс-докингом через пункт выдачи заказов недоступна для продавца; - `DUPLICATE_SKUS_IN_REQUEST` — в запросе есть дубликаты SKU; - `CAN_NOT_CREATE_DRAFT` — не удалось создать черновик; - `DRAFT_TOTALS_INVALID_ERROR` — некорректные итоговые данные в черновике; - `CAN_NOT_START_CALCULATION` — не удалось начать расчёт; - `PICKUP_IS_NOT_AVAILABLE` — самовывоз недоступен; - `DROP_OFF_NOT_COMPATIBLE_WITH_PICKUP` — точка отгрузки несовместима с самовывозом; - `UNDEFINED` — неизвестная ошибка. По умолчанию: `UNSPECIFIED`.
  - `error_reasons` — array[string (UNSPECIFIED, ORDER_CREATION_NOT_AVAILABLE_FOR_SELLER, ALL_ITEMS_REJECTED, NOT_AVAILABLE_CLUSTERS, ALL_ITEMS_COUNT_INVALID, ALL_ITEMS_VOLUME_INVALID, ALL_BUNDLES_EMPTY, HAS_EMPTY_BUNDLE, DISABLED_FOR_SELLER, NO_ACTIVE_SELLER_WAREHOUSE, INVALID_SELLER_WAREHOUSE, UNDEFINED)]. Причина ошибки: - `UNSPECIFIED` — не определена; - `ALL_ITEMS_COUNT_INVALID` — в товарном составе больше 5000 SKU; - `ALL_ITEMS_VOLUME_INVALID` — в товарном составе объём товаров больше 100 000 литров; - `ALL_BUNDLES_EMPTY` — товарные составы пустые; - `HAS_EMPTY_BUNDLE` — минимум 1 товарный состав в черновике пустой; - `DISABLED_FOR_SELLER` — отгрузка курьером отключена для продавца; - `NO_ACTIVE_SELLER_WAREHOUSE` — нет активного склада продавца; - `INVALID_SELLER_WAREHOUSE` — склад продавца недоступен.
  - `items_validation` — array[object]. Ошибки валидации.
    - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
    - `rejected_items` — array[object]. Отклонённые товары.
      - `reasons` — array[string (UNSPECIFIED, OUT_OF_ASSORTMENT, INVALID, INCOMPATIBLE_WAREHOUSE, EMPTY_BARCODE, EMPTY_PS_ATTRIBUTE, MULTIPLICITY, NO_PRICE, INVALID_ITEM_COUNT_MAX, INVALID_ITEM_COUNT_ZERO, SKU_REJECTED_BY_ACCEPTANCE_RESTRICTIONS, SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED…)]. Причины отклонения: - `UNSPECIFIED` — не определена; - `OUT_OF_ASSORTMENT` — товар не входит в ассортимент; - `INVALID` — недействительный товар; - `INCOMPATIBLE_WAREHOUSE` — товар нельзя разместить на выбранном складе; - `EMPTY_BARCODE` — нет штрихкода; - `EMPTY_PS_ATTRIBUTE` — нет обязательного атрибута товара; - `MULTIPLICITY` — количество товара в поставке не кратно продаваемым партиям; - `NO_PRICE` — нет цены; - `INVALID_ITEM_COUNT_MAX` — количество товара больше максимального; - `INVALID_ITEM_COUNT_ZERO` — количество товара равно нулю; - `SKU_REJECTED_BY_ACCEPTANCE_RESTRICTIONS` — товар отклонён из-за ограничений на приёмку; - `SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED` — товар с меткой `is_ettn_required` не разрешён; - `SKU_WITHOUT_ETTN_REQUIRED_TAG_NOT_ALLOWED` — товар без метки `is_ettn_required` не разрешён; - `SKU_WITH_TRACEABLE_TAG_NOT_ALLOWED` — товар с тегом отслеживаемости не разрешён; - `SKU_IS_RESTRICTED` — товар ограничен к приёмке; - `EMPTY_CLUSTER` — нет кластера; - `SKU_WITH_UTD_REQUIRED_TAG_NOT_ALLOWED` — товар с обязательным тегом UTD не разрешён; - `CORRUPTED_ASSORTMENT` — не получилось добавить товар в заявку; - `STORAGE_BELARUS_SKU_HAS_NO_ANY_FEACN` — у товара для хранения в Беларуси нет кода ТН ВЭД; - `STORAGE_BELARUS_SKU_HAS_NO_SELLER_FEACN`— у товара для хранения в Беларуси нет кода ТН ВЭД продавца; - `TRACEABLE_SKU_HAS_NO_GTIN_BARCODE` — у товара нет штрихкода GTIN; - `TRACEABLE_SKU_HAS_NO_MEASUREMENT_UNIT_QUANTITY` — у товара нет указанного количества в единицах; - `SKU_HAS_INVALID_HS_CODE` — у товара некорректный HS-код; - `SKU_HAS_STORAGE_COUNTRY_RESTRICTIONS` — у товара есть ограничения по стране хранения; - `UNDEFINED` — неизвестная ошибка.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `macrolocal_cluster_ids` — array[string<int64>]. Список идентификаторов кластера размещения.
  - `message` — string. Сообщение об ошибке.
  - `skus` — array[string<int64>]. Список идентификаторов товаров — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
