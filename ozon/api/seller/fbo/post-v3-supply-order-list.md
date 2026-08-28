---
title: Список заявок на поставку на склад Ozon
api: ozon-seller
method: POST
path: /v3/supply-order/list
operation_id: SupplyOrderList
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: dfd833fc52c0a575
---

# Список заявок на поставку на склад Ozon

`POST /v3/supply-order/list`

Учитываются заявки с поставкой на конкретный склад и через [виртуальный распределительный центр (вРЦ)](https://seller-edu.ozon.ru/fbo/scheme-of-work/about#чем-отличаются-процессы-при-заявках-через-врц-и-напрямую-на-склад).

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object **обязательный**. Фильтр.
  - `dropoff_warehouse_ids` — array[string<int64>]. Идентификаторы пунктов отгрузки.
  - `order_number_search` — string. Номер заявки на поставку.
  - `states` — array[string (DATA_FILLING, READY_TO_SUPPLY, ACCEPTED_AT_SUPPLY_WAREHOUSE, IN_TRANSIT, ACCEPTANCE_AT_STORAGE_WAREHOUSE, REPORTS_CONFIRMATION_AWAITING, REPORT_REJECTED, COMPLETED, REJECTED_AT_SUPPLY_WAREHOUSE, CANCELLED, OVERDUE)] **обязательный**. Статус поставки: - `DATA_FILLING` — заполнение данных; - `READY_TO_SUPPLY` — готова к отгрузке; - `ACCEPTED_AT_SUPPLY_WAREHOUSE` — принята на точке отгрузки; - `IN_TRANSIT` — в пути; - `ACCEPTANCE_AT_STORAGE_WAREHOUSE` — приёмка на складе; - `REPORTS_CONFIRMATION_AWAITING` — согласование актов; - `REPORT_REJECTED` — спор; - `COMPLETED` — завершена; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отказано в приёмке; - `CANCELLED` — отменена; - `OVERDUE` — просрочена.
  - `timeslot_from_range` — object. Фильтр по таймслоту.
    - `from` — string<date-time>. Дата начала.
    - `timeslot_filter_type` — string (BY_LOCAL_TIME, BY_UTC_TIME). Тип даты таймслота: - `BY_LOCAL_TIME` — по локальному времени пункта отгрузки; - `BY_UTC_TIME` — по времени в UTC.
    - `to` — string<date-time>. Дата окончания.
- `last_id` — string. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса.
- `limit` — integer<int32> **обязательный**. Количество значений на странице.
- `sort_by` — string (ORDER_CREATION, ORDER_STATE_UPDATED_AT, TIMESLOT_FROM_UTC, TIMESLOT_FROM_LOCAL) **обязательный**. Параметр, по которому заявки на поставку будут отсортированы: - `ORDER_CREATION` — по дате создания заявки; - `ORDER_STATE_UPDATED_AT` — по обновлению статуса заявки; - `TIMESLOT_FROM_UTC` — по таймслоту в UTC; - `TIMESLOT_FROM_LOCAL` — по таймслоту в локальном времени.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию.

## Ответы

**200** — Список заявок на поставку

- `last_id` — string. Идентификатор последнего значения на странице. Чтобы получить следующие значения, укажите полученное значение в следующем запросе в параметре `last_id`.
- `order_ids` — array[string<int64>]. Идентификаторы заявок на поставку.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
