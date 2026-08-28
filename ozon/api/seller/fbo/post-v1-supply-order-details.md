---
title: Получить подробную информацию о заявке на поставку
api: ozon-seller
method: POST
path: /v1/supply-order/details
operation_id: SupplyOrderAPI_SupplyOrderDetails
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 78c8f5ff4891758d
---

# Получить подробную информацию о заявке на поставку

`POST /v1/supply-order/details`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Подробная информация о заявке

- `created_date` — string<date-time>. Дата создания заявки на поставку.
- `data_filling_deadline_utc` — string<date-time>. Время в секундах, оставшееся на заполнение данных по поставке. Только для заявок с вРЦ.
- `dropoff_warehouse_id` — integer<int64>. Идентификатор пункта отгрузки.
- `order_id` — integer<int64>. Идентификатор заявки на поставку.
- `order_number` — string. Номер заявки на поставку.
- `order_tags` — object. Метки заявки на поставку.
  - `is_econom` — boolean. `true`, если в заявке на поставку есть товары «Суперэконом».
  - `is_super_fbo` — boolean. `true`, если продавец подключён к Super-поставкам.
  - `is_virtual` — boolean. `true`, если заявка на поставку виртуальная.
  - `original_supply_id` — integer<int64>. Идентификатор исходной поставки.
  - `product_super_fbo` — boolean. `true`, если в заявке на поставку есть Super-товары.
- `state` — string (UNSPECIFIED, DATA_FILLING, READY_TO_SUPPLY, ACCEPTED_AT_SUPPLY_WAREHOUSE, IN_TRANSIT, ACCEPTANCE_AT_STORAGE_WAREHOUSE, REPORTS_CONFIRMATION_AWAITING, REPORT_REJECTED, COMPLETED, REJECTED_AT_SUPPLY_WAREHOUSE, CANCELLED, OVERDUE). Статус заявки на поставку: - `UNSPECIFIED` — не определён; - `DATA_FILLING` — заполнение данных; - `READY_TO_SUPPLY` — готова к отгрузке; - `ACCEPTED_AT_SUPPLY_WAREHOUSE` — принята на точке отгрузки; - `IN_TRANSIT` — в пути; - `ACCEPTANCE_AT_STORAGE_WAREHOUSE` — приёмка на складе; - `REPORTS_CONFIRMATION_AWAITING` — согласование актов; - `REPORT_REJECTED` — спор; - `COMPLETED` — завершена; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отказано в приемке; - `CANCELLED` — отменена; - `OVERDUE` — просрочена. По умолчанию: `UNSPECIFIED`.
- `state_updated_date` — string<date-time>. Дата обновления статуса заявки на поставку.
- `supplies` — array[object]. Информация о поставках.
  - `cancellation_allowability` — object. Возможность отмены.
    - `can_not_set_reasons` — array[string (UNSPECIFIED, INVALID_SUPPLY_STATE, SUPPLY_IS_VIRTUAL, SUPPLY_HAS_ACTIVE_UTD, SUPPLY_DOES_NOT_BELONG_TO_COMPANY, PICKUP_SUPPLY_IS_LOCKED_DOWN, UNDEFINED)]. Причина, почему нельзя отменить поставку: - `UNSPECIFIED` — не определена; - `INVALID_SUPPLY_STATE` — некорректный статус поставки; - `SUPPLY_IS_VIRTUAL` — поставка виртуальная; - `SUPPLY_HAS_ACTIVE_UTD` — у поставки есть активный УПД; - `SUPPLY_DOES_NOT_BELONG_TO_COMPANY` — поставка не принадлежит продавцу; - `PICKUP_SUPPLY_IS_LOCKED_DOWN` — заблокировано редактирование поставки; - `UNDEFINED` — неизвестная.
    - `can_set` — boolean. `true`, если поставку можно отменить.
  - `content` — object. Товарный состав поставки.
    - `bundle_id` — string. Идентификатор товарного состава.
    - `can_not_set_reasons` — array[string (UNSPECIFIED, INCORRECT_SUPPLY_STATE, DEADLINE, UTD_IS_UPLOADED, STORAGE_WAREHOUSE_IS_NOT_WMS, CONTRACT_IS_NOT_VALID_FOR_HANDLING_ORDERS, SUPPLY_IS_VIRTUAL, SUPPLY_DOES_NOT_BELONG_TO_COMPANY, UNDEFINED)]. Причина, почему нельзя изменить товарный состав поставки: - `UNSPECIFIED` — не определена; - `INCORRECT_SUPPLY_STATE` — некорректный статус поставки; - `DEADLINE` — поставка просрочена; - `UTD_IS_UPLOADED` — УПД загружен; - `STORAGE_WAREHOUSE_IS_NOT_WMS` — некорректный склад хранения; - `CONTRACT_IS_NOT_VALID_FOR_HANDLING_ORDERS` — недействительный договор для обработки заявок на поставку; - `SUPPLY_IS_VIRTUAL` — поставка виртуальная; - `SUPPLY_DOES_NOT_BELONG_TO_COMPANY` — поставка не принадлежит продавцу; - `UNDEFINED` — неизвестная.
    - `can_set` — boolean. `true`, если можно изменить товарный состав поставки.
  - `ettn_info` — object. Информация по электронной ТТН.
    - `contains_valid` — boolean. `true`, если электронная ТТН действительная.
    - `is_required` — boolean. `true`, если для поставки нужна электронная ТТН.
    - `is_uploaded` — boolean. `true`, если электронная ТТН загружена.
  - `is_crossdock` — boolean. `true`, если поставка кросс-докинг.
  - `overdue_reason` — string (UNSPECIFIED, ORDER_TIMESLOT_EXPIRED, ORDER_TIMESLOT_NOT_SELECTED, NOT_READY_FOR_PICKUP, PICKUP_FAILED, UNDEFINED). Причина просрочки поставки: - `UNSPECIFIED` — не определена; - `ORDER_TIMESLOT_EXPIRED` — поставка не доставлена в указанный таймслот; - `ORDER_TIMESLOT_NOT_SELECTED` — таймслот не указан вовремя; - `NOT_READY_FOR_PICKUP` — пикап-поставка не приведена в статус `ReadyToSupply` вовремя; - `PICKUP_FAILED` — курьер не смог забрать поставку; - `UNDEFINED` — неизвестная. По умолчанию: `UNSPECIFIED`.
  - `storage_warehouse` — object. Склад хранения для поставок с типом `DIRECT`.
    - `address` — string. Адрес склада хранения.
    - `arrival_date` — string<date-time>. Дата прибытия на склад хранения.
    - `name` — string. Название склада хранения.
    - `warehouse_id` — integer<int64>. Идентификатор склада хранения.
  - `macrolocal_cluster_id` — integer<int64>. Идентификатор кластера размещения.
  - `supply_id` — integer<int64>. Идентификатор поставки.
  - `supply_state` — string (UNSPECIFIED, DATA_FILLING, READY_TO_SUPPLY, ACCEPTED_AT_SUPPLY_WAREHOUSE, REJECTED_AT_SUPPLY_WAREHOUSE, IN_TRANSIT, ACCEPTED_AT_STORAGE_WAREHOUSE, REPORTS_CONFIRMATION_AWAITING, REPORT_REJECTED, COMPLETED, CANCELLED, OVERDUE). Статус поставки: - `UNSPECIFIED` — не указан; - `DATA_FILLING` — заполнение данных; - `READY_TO_SUPPLY` — готова к отгрузке; - `ACCEPTED_AT_SUPPLY_WAREHOUSE` — принята на точке отгрузки; - `REJECTED_AT_SUPPLY_WAREHOUSE` — отказано в приёмке; - `IN_TRANSIT` — в пути; - `ACCEPTED_AT_STORAGE_WAREHOUSE` — принята на складе хранения; - `REPORTS_CONFIRMATION_AWAITING` — согласование актов; - `REPORT_REJECTED` — спор; - `COMPLETED` — завершена; - `CANCELLED` — отменена; - `OVERDUE` — просрочена. По умолчанию: `UNSPECIFIED`.
  - `supply_tags` — object. Метки поставки.
    - `is_ettn_required` — boolean. `true`, если для поставки нужна электронная ТТН.
    - `is_evsd_required` — boolean. `true`, если в поставке есть товары с сертификацией в системе «Меркурий».
    - `is_jewelry` — boolean. `true`, если в поставке есть ювелирные товары.
    - `is_marking_possible` — boolean. `true`, если в поставке есть товары, для которых возможна маркировка.
    - `is_marking_required` — boolean. `true`, если в поставке есть товары, для которых маркировка обязательна.
    - `is_utd` — boolean. `true`, если для поставки нужно передать УПД.
- `timeslot` — object. Информация о таймслоте.
  - `can_not_set_reasons` — array[string (UNSPECIFIED, INVALID_ORDER_STATE, ORDER_IS_VIRTUAL, SET_TIMESLOT_DEADLINE_EXCEED, ORDER_DOES_NOT_BELONG_TO_COMPANY, UNDEFINED)]. Причина, почему нельзя выбрать интервал поставки: - `UNSPECIFIED` — не определена; - `INVALID_ORDER_STATE` — нельзя установить таймслот в заявке с текущим статусом; - `ORDER_IS_VIRTUAL` — заявка на поставку виртуальная; - `SET_TIMESLOT_DEADLINE_EXCEED` — время установки таймслота истекло; - `ORDER_DOES_NOT_BELONG_TO_COMPANY` — заявка на поставку не принадлежит продавцу; - `UNDEFINED` — неизвестная.
  - `can_set` — boolean. `true`, если можно изменить интервал поставки.
  - `value` — object. Информация об интервале доставки.
    - `timeslot` — object. Интервал поставки по местному времени.
      - `from` — string<date-time>. Дата и время начала интервала.
      - `to` — string<date-time>. Дата и время окончания интервала.
    - `timezone_info` — object. Часовой пояс.
      - `iana_name` — string. Название часового пояса.
      - `offset` — string. Смещение часового пояса от UTC-0 в секундах.
- `vehicle` — object. Информация о водителе и машине.
  - `can_not_set_reasons` — array[string (UNSPECIFIED, INVALID_ORDER_STATE, VEHICLE_NOT_REQUIRED, ORDER_DOES_NOT_BELONG_TO_COMPANY, UNDEFINED)]. Причина, почему нельзя указать или изменить информацию о водителе или машине: - `UNSPECIFIED` — не определена; - `INVALID_ORDER_STATE` — нельзя установить информацию о машине в текущем статусе заявки; - `VEHICLE_NOT_REQUIRED` — не обязательно указывать машину; - `ORDER_DOES_NOT_BELONG_TO_COMPANY` — заявка на поставку не принадлежит продавцу; - `UNDEFINED` — неизвестная.
  - `can_set` — boolean. `true`, если можно изменить информацию о водителе или машине.
  - `value` — object. Информация о водителе и машине. Только для pick-up отгрузок.
    - `driver_is_deleted` — boolean. `true`, если информация о водителе удалена.
    - `driver_name` — string. Имя водителя.
    - `driver_phone` — string. Телефон водителя.
    - `vehicle_is_deleted` — boolean. `true`, если информация о машине удалена.
    - `vehicle_model` — string. Модель машины.
    - `vehicle_number` — string. Номер машины.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
