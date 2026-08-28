---
title: Статус ввода данных о водителе и автомобиле
api: ozon-seller
method: POST
path: /v1/supply-order/pass/status
operation_id: SupplyOrderAPI_SupplyOrderPassStatus
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 36366c4e0fe9870a
---

# Статус ввода данных о водителе и автомобиле

`POST /v1/supply-order/pass/status`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции.

## Ответы

**200** — Статус

- `errors` — array[string (SET_VEHICLE_ERROR_UNSPECIFIED, SET_VEHICLE_ERROR_INVALID_ORDER_STATE, SET_VEHICLE_ERROR_VEHICLE_NOT_REQUIRED, SET_VEHICLE_ERROR_ORDER_NOT_BELONG_CONTRACTOR, SET_VEHICLE_ERROR_ORDER_NOT_BELONG_COMPANY)]. Причина ошибки: - `UNSPECIFIED` — статус не указан; - `INVALID_ORDER_STATE` — неверный статус заявки; - `VEHICLE_NOT_REQUIRED` — указывать данные автомобиля необязательно; - `ORDER_NOT_BELONG_CONTRACTOR` — заявка создана другим юридическом лицом, работать с ней не получится; - `ORDER_NOT_BELONG_COMPANY` — заявка не принадлежит вашему кабинету, работать с ней не получится.
- `result` — string (Unknown, Success, InProgress, Failed). Статус ввода данных о водителе и автомобиле: - `Unknown` — статус неизвестен; - `Success` — данные указаны; - `InProgress` — данные обрабатываются; - `Failed` — не удалось обработать данные. По умолчанию: `Unknown`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
