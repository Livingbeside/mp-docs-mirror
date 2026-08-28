---
title: Информация о заявке на поставку
api: ozon-seller
method: POST
path: /v3/supply-order/get
operation_id: SupplyOrderGet
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 271e79ab6346dc7c
---

# Информация о заявке на поставку

`POST /v3/supply-order/get`

Учитываются заявки с поставкой на конкретный склад и через [виртуальный распределительный центр (вРЦ)](https://seller-edu.ozon.ru/fbo/scheme-of-work/about#чем-отличаются-процессы-при-заявках-через-врц-и-напрямую-на-склад).

## Запрос

**Тело запроса** (`application/json`):

- `order_ids` — array[string<int64>] **обязательный**. Идентификаторы заявок на поставку.

## Ответы

**200** — Информация о заявке

- `orders` — array[object]. Список заявок на поставку.
  - `created_date` — string<date-time>. Дата создания заявки на поставку.
  - `data_filling_deadline_utc` — string<date-time>. Время в секундах, оставшееся на заполнение данных по поставке. Только для заявок с вРЦ.
  - `dropoff_warehouse` — object. Информация о пункте отгрузки.
    - `address` — string. Адрес пункта отгрузки.
    - `name` — string. Название пункта отгрузки.
    - `warehouse_id` — integer<int64>. Идентификатор пункта отгрузки.
  - `order_id` — integer<int64>. Идентификатор заявки на поставку.
  - `order_number` — string. Номер заявки на поставку.
  - `order_tags` — object. Метки заявки на поставку.
    - `is_econom` — boolean. `true`, если заявка на поставку относится к товарам «Суперэконом».
    - `is_pickup` — boolean. `true`, если доступна отгрузка курьером.
    - `is_quant` — boolean. Признак, что в поставке есть кванты.
    - `is_super_fbo` — boolean. `true`, если продавец подключён к Super-поставкам.
    - `is_virtual` — boolean. `true`, если заявка на поставку виртуальная.
    - `original_supply_id` — integer<int64>. Идентификатор исходной поставки.
    - `product_super_fbo` — boolean. `true`, если заявка на поставку относится к Super-товарам.
    - `seller_warehouse_id` — integer<int64>. Идентификатор склада продавца.
  - `state` — string (UNSPECIFIED, DATA_FILLING, READY_TO_SUPPLY, ACCEPTED_AT_SUPPLY_WAREHOUSE, IN_TRANSIT, ACCEPTANCE_AT_STORAGE_WAREHOUSE, REPORTS_CONFIRMATION_AWAITING, REPORT_REJECTED, COMPLETED, REJECTED_AT_SUPPLY_WAREHOUSE, CANCELLED, OVERDUE). Статус заявки на поставку: - `UNSPECIFIED` — не определён; - `DATA_FILLING` — заполнение данных; - `READY_TO_SUPPLY` — готова к отгрузке; - `ACCEPTED_AT_SUPPLY_WAREHOUSE` — принята на точке отгрузки; - `IN_TRANSIT` — в пути; - `ACCEPTANCE_AT_STORAGE_WAREHOUSE` — приёмка на складе; - `REPORTS_CONFIRMATION_AWAITING` — согласование актов; - `REPORT_REJECTED` — спор; - `COMPLETED` — завершена; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отказано в приёмке; - `CANCELLED` — отменена; - `OVERDUE` — просрочена. По умолчанию: `UNSPECIFIED`.
  - `state_updated_date` — string<date-time>. Дата обновления статуса заявки на поставку.
  - `supplies` — array[object]. Информация о поставках.
    - `bundle_id` — string. Идентификатор состава поставки.
    - `is_crossdock` — boolean. `true`, если поставка кросс-докинг.
    - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
    - `state` — string (UNSPECIFIED, DATA_FILLING, READY_TO_SUPPLY, ACCEPTED_AT_SUPPLY_WAREHOUSE, IN_TRANSIT, ACCEPTANCE_AT_STORAGE_WAREHOUSE, REPORTS_CONFIRMATION_AWAITING, REPORT_REJECTED, COMPLETED, REJECTED_AT_SUPPLY_WAREHOUSE, CANCELLED, OVERDUE). Статус поставки: - `UNSPECIFIED` — не определён; - `DATA_FILLING` — заполнение данных; - `READY_TO_SUPPLY` — готова к отгрузке; - `ACCEPTED_AT_SUPPLY_WAREHOUSE` — принята на точке отгрузки; - `IN_TRANSIT` — в пути; - `ACCEPTANCE_AT_STORAGE_WAREHOUSE` — приёмка на складе; - `REPORTS_CONFIRMATION_AWAITING` — согласование актов; - `REPORT_REJECTED` — спор; - `COMPLETED` — завершена; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отказано в приёмке; - `CANCELLED` — отменена; - `OVERDUE` — просрочена. По умолчанию: `UNSPECIFIED`.
    - `storage_warehouse` — object. Склад хранения для поставок с типом `DIRECT`.
      - `address` — string. Адрес склада хранения.
      - `arrival_date` — string<date-time>. Дата прибытия на склад хранения.
      - `name` — string. Название склада хранения.
      - `warehouse_id` — integer<int64>. Идентификатор склада хранения.
    - `supply_id` — integer<int64>. Идентификатор поставки.
    - `supply_tags` — object. Метки поставки.
      - `freeze_stock_for_marking` — boolean. `true`, если включена схема поставки товаров с заморозкой стока.
      - `is_ettn_required` — boolean. `true`, если для поставки нужна электронная ТТН.
      - `is_evsd_required` — boolean. `true`, если в поставке есть товары с сертификацией в системе «Меркурий».
      - `is_jewelry` — boolean. `true`, если в поставке есть ювелирные товары.
      - `is_marking_possible` — boolean. `true`, если в поставке есть товары, для которых возможна маркировка.
      - `is_marking_required` — boolean. `true`, если в поставке есть товары, для которых маркировка обязательна.
      - `is_utd` — boolean. `true`, если для поставки нужно передать УПД.
  - `timeslot` — object. Информация о таймслоте.
    - `timeslot` — object. Интервал поставки по местному времени.
      - `from` — string<date-time>. Дата начала.
      - `to` — string<date-time>. Дата окончания.
    - `timezone_info` — object. Часовой пояс.
      - `iana_name` — string. Название часового пояса.
      - `offset` — string. Смещение часового пояса от UTC-0 в секундах.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
