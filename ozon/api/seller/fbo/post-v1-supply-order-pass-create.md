---
title: Указать данные о водителе и автомобиле
api: ozon-seller
method: POST
path: /v1/supply-order/pass/create
operation_id: SupplyOrderAPI_SupplyOrderPassCreate
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bd92d4d5ed255d6c
---

# Указать данные о водителе и автомобиле

`POST /v1/supply-order/pass/create`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку.
- `vehicle` — object **обязательный**. Информация о водителе и автомобиле.
  - `driver_name` — string **обязательный**. Имя водителя.
  - `driver_phone` — string **обязательный**. Телефон водителя.
  - `vehicle_model` — string **обязательный**. Модель автомобиля.
  - `vehicle_number` — string **обязательный**. Номер автомобиля.

## Ответы

**200** — Данные указаны

- `error_reasons` — array[string (SET_VEHICLE_ERROR_UNSPECIFIED, SET_VEHICLE_ERROR_INVALID_ORDER_STATE, SET_VEHICLE_ERROR_VEHICLE_NOT_REQUIRED, SET_VEHICLE_ERROR_ORDER_NOT_BELONG_CONTRACTOR, SET_VEHICLE_ERROR_ORDER_NOT_BELONG_COMPANY)]. Причина ошибки: - `UNSPECIFIED` — статус заявки не указан; - `INVALID_ORDER_STATE` — неверный статус заявки; - `VEHICLE_NOT_REQUIRED` — указывать данные автомобиля необязательно; - `ORDER_NOT_BELONG_CONTRACTOR` — заявка создана другим юридическом лицом, работать с ней не получится; - `ORDER_NOT_BELONG_COMPANY` — заявка не принадлежит вашему кабинету, работать с ней не получится.
- `operation_id` — string. Идентификатор операции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
