---
title: Информация о кластерах и их складах
api: ozon-seller
method: POST
path: /v1/cluster/list
operation_id: SupplyDraftAPI_DraftClusterList
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 00e3db678bd00aa5
---

# Информация о кластерах и их складах

`POST /v1/cluster/list`

## Запрос

**Тело запроса** (`application/json`):

- `cluster_ids` — array[string<int64>]. Идентификаторы кластеров.
- `cluster_type` — string (CLUSTER_TYPE_OZON, CLUSTER_TYPE_CIS) **обязательный**. Тип кластера: - `CLUSTER_TYPE_OZON` — кластер в России, - `CLUSTER_TYPE_CIS` — кластер в СНГ.

## Ответы

**200** — Информация о кластерах

- `clusters` — array[object]. Кластеры.
  - `id` — integer<int64>. Идентификатор кластера.
  - `logistic_clusters` — array[object]. Информация о складах кластера.
    - `warehouses` — array[object]. Склады.
      - `name` — string. Название склада.
      - `type` — string (FULL_FILLMENT, EXPRESS_DARK_STORE, SORTING_CENTER, ORDERS_RECEIVING_POINT, CROSS_DOCK, DISTRIBUTION_CENTER). Тип склада: - `FULL_FILLMENT` — фулфилмент, - `EXPRESS_DARK_STORE` — даркстор, - `SORTING_CENTER` — сортировочный центр, - `ORDERS_RECEIVING_POINT` — пункт приёма заказов, - `CROSS_DOCK` — кросс-докинг, - `DISTRIBUTION_CENTER` — распределительный центр.
      - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
  - `name` — string. Название кластера.
  - `type` — string (CLUSTER_TYPE_OZON, CLUSTER_TYPE_CIS). Тип кластера: - `CLUSTER_TYPE_OZON` — кластер в России, - `CLUSTER_TYPE_CIS` — кластер в СНГ.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
