---
title: Получить список доступных таймслотов
api: ozon-seller
method: POST
path: /v2/draft/timeslot/info
operation_id: DraftTimeslotInfo
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 15e6ec88f942a7b5
---

# Получить список доступных таймслотов

`POST /v2/draft/timeslot/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string **обязательный**. Дата начала периода доступных таймслотов.
- `date_to` — string **обязательный**. Дата окончания периода доступных таймслотов. Максимальный период — 28 дней с текущей даты.
- `draft_id` — integer<int64> **обязательный**. Идентификатор черновика из метода [/v2/draft/create/info](#operation/DraftCreateInfo).
- `supply_type` — string (CROSSDOCK, DIRECT, MULTI_CLUSTER) **обязательный**. Тип поставки: - `CROSSDOCK` — кросс-докинг; - `DIRECT` — прямая; - `MULTI_CLUSTER` — для нескольких кластеров.
- `selected_cluster_warehouses` — array[object] **обязательный**. Информация о кластере и складах в нём. Можно передать один кластер для кросс-докинговой и прямой поставки или список всех кластеров для поставки в несколько кластеров.
  - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
  - `storage_warehouse_id` — integer<int64>. Идентификатор склада хранения. Только для поставок с типом `DIRECT`.

## Ответы

**200** — Список таймслотов

- `error_reason` — string (UNSPECIFIED, INVALID_CLUSTERS_COUNT, REQUESTED_PERIOD_MORE_THAN_MAX, UNDEFINED). Причина ошибки: - `UNSPECIFIED` — не определена; - `INVALID_CLUSTERS_COUNT` — переданы не все кластеры из расчёта; - `REQUESTED_PERIOD_MORE_THAN_MAX` — превышен период; - `INVALID_REQUESTED_CLUSTER_IDS` — переданы кластеры, которых нет в расчёте. - `UNDEFINED` — неизвестная ошибка. По умолчанию: `UNSPECIFIED`.
- `result` — object. Информация о таймслотах.
  - `drop_off_warehouse_timeslots` — object. Таймслоты складов.
    - `current_time_in_timezone` — string. Текущее время в часовом поясе склада.
    - `days` — array[object]. Таймслоты по датам.
      - `date_in_timezone` — string. Дата таймслотов.
      - `timeslots` — array[object]. Таймслоты.
        - `from_in_timezone` — string. Начало таймслота.
        - `to_in_timezone` — string. Конец таймслота.
    - `warehouse_timezone` — string. Часовой пояс склада.
  - `requested_date_from` — string. Дата начала периода.
  - `requested_date_to` — string. Дата окончания периода.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
