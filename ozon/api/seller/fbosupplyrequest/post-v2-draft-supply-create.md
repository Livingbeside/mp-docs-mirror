---
title: Создать заявку на поставку по черновику
api: ozon-seller
method: POST
path: /v2/draft/supply/create
operation_id: DraftSupplyCreate
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d79c2edaa745e554
---

# Создать заявку на поставку по черновику

`POST /v2/draft/supply/create`

Вы можете создавать заявку на поставку по черновику:
- 2 раза в минуту;
- 50 раз в час;
- 500 раз в день.

Если превысите лимит, вернётся ошибка 429.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `draft_id` — integer<int64> **обязательный**. Идентификатор черновика из метода [/v2/draft/create/info](#operation/DraftCreateInfo).
- `selected_cluster_warehouses` — array[object] **обязательный**. Информация о кластере и складах в нём. Можно передать один кластер для кросс-докинговой и прямой поставки или список всех кластеров для поставки в несколько кластеров.
  - `macrolocal_cluster_id` — integer<int64> **обязательный**. Идентификатор кластера размещения.
  - `storage_warehouse_id` — integer<int64> **обязательный**. Идентификатор склада размещения. Получите значение параметра методом [/v2/draft/create/info](#operation/DraftCreateInfo). Только для поставок с типом `DIRECT`.
- `timeslot` — object. Таймслот поставки.
  - `from_in_timezone` — string. Начало таймслота.
  - `to_in_timezone` — string. Конец таймслота.
- `supply_type` — string (CROSSDOCK, DIRECT, MULTI_CLUSTER) **обязательный**. Тип поставки: - `CROSSDOCK` — кросс-докинг; - `DIRECT` — прямая; - `MULTI_CLUSTER` — для нескольких кластеров.

## Ответы

**200** — Заявка создана

- `draft_id` — integer<int64>. Идентификатор черновика.
- `error_reasons` — array[string (UNSPECIFIED, SOME_SERVICE_ERROR, ORDER_SKU_LIMIT, INVALID_QUANTITY_OR_QUANT, ORDER_ALREADY_CREATED, ORDER_CREATION_IN_PROGRESS, DRAFT_DOES_NOT_EXIST, CONTRACTOR_CAN_NOT_CREATE_ORDER, INACTIVE_CONTRACT, DRAFT_INCORRECT_STATE, INVALID_VOLUME, INVALID_ROUTE…)]. Причина ошибки: - `UNSPECIFIED` — не определена; - `SOME_SERVICE_ERROR` — ошибка при редактировании поставки; - `ORDER_SKU_LIMIT` — количество товаров в поставке больше 5000; - `INVALID_QUANTITY_OR_QUANT` — некорректное количество товара или грузомест; - `ORDER_ALREADY_CREATED` — заказ уже создан; - `ORDER_CREATION_IN_PROGRESS` — создание заказа в процессе; - `DRAFT_DOES_NOT_EXIST` — черновик не существует; - `CONTRACTOR_CAN_NOT_CREATE_ORDER` — контрагент не может создать заказ; - `INACTIVE_CONTRACT` — нельзя редактировать состав поставки с неактивным договором; - `DRAFT_INCORRECT_STATE` — некорректный статус черновика; - `INVALID_VOLUME` — некорректный объём поставки; - `INVALID_ROUTE` — некорректный маршрут; - `INVALID_STORAGE_WAREHOUSE` — некорректный склад хранения; - `INVALID_STORAGE_REGION` — некорректный регион хранения; - `INVALID_SPLITTING` — некорректное разделение; - `INVALID_SUPPLY_CONTENT` — некорректное содержимое поставки; - `TIMESLOT_NOT_AVAILABLE` — нет доступных таймслотов; - `SKU_DISTRIBUTION_REQUIRED_BUT_NOT_POSSIBLE` — требуется распределение SKU, но оно невозможно; - `XDOCK_IN_DELIVERY_POINT_DISABLED_FOR_SELLER` — поставка кросс-докингом через пункт выдачи заказов недоступна для продавца; - `DRAFT_IS_LOCKED` — черновик заблокирован; - `INVALID_PACKAGE_UNITS_COUNTS` — некорректное количество грузомест; - `SELLER_CONVERSATION_DOES_NOT_EXIST` — точка отгрузки с таким `id` не существует; - `USER_CAN_NOT_CREATE_SELLER_CONVERSATION` — пользователь не может создать диалог с продавцом; - `SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED_FOR_DROP_OFF_POINT` — товар с меткой `is_ettn_required` не разрешён для точки отгрузки; - `INVALID_SELLER_WAREHOUSE` — склад продавца недоступен; - `PICKUP_ORDER_LIMIT_EXCEEDED` — превышен лимит заказов на самовывоз; - `MINIMUM_VOLUME_IN_LITRES_INVALID` — некорректный минимальный объём в литрах; - `INVALID_CLUSTERS_COUNT` — переданы не все кластеры из расчёта; - `CAN_NOT_CREATE_ORDER` — не удалось создать заказ; - `UNDEFINED` — неизвестная ошибка.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
