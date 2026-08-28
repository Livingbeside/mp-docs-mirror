---
title: Получить статус отмены заявки на поставку
api: ozon-seller
method: POST
path: /v1/supply-order/cancel/status
operation_id: SupplyOrderAPI_SupplyOrderCancelStatus
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9bb227b749757313
---

# Получить статус отмены заявки на поставку

`POST /v1/supply-order/cancel/status`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string **обязательный**. Идентификатор операции на отмену заявки на поставку.

## Ответы

**200** — Статус отмены заявки на поставку

- `error_reasons` — array[string (INVALID_ORDER_STATE, ORDER_IS_VIRTUAL, ORDER_DOES_NOT_BELONG_TO_CONTRACTOR, ORDER_DOES_NOT_BELONG_TO_COMPANY, OTHER_ASYNCHRONOUS_OPERATION_IN_PROGRESS)]. Причина, по которой не удалось отменить заявку на поставку: - `INVALID_ORDER_STATE` — неверный статус заявки на поставку. - `ORDER_IS_VIRTUAL` — заявка виртуальная. - `ORDER_DOES_NOT_BELONG_TO_CONTRACTOR` — заявка на поставку не принадлежит вашему юридическому лицу. - `ORDER_DOES_NOT_BELONG_TO_COMPANY` — заявка на поставку не принадлежит продавцу. - `OTHER_ASYNCHRONOUS_OPERATION_IN_PROGRESS` — заявка на поставку в процессе отмены.
- `result` — object. Информация об отмене заявки на поставку.
  - `is_order_cancelled` — boolean. `true`, если заявка на поставку отменена.
  - `supplies` — array[object]. Список отменённых поставок.
    - `error_reasons` — array[string (INVALID_SUPPLY_STATE, SUPPLY_DOES_NOT_BELONG_TO_CONTRACTOR, SUPPLY_DOES_NOT_BELONG_TO_COMPANY, SUPPLY_DOES_NOT_BELONG_TO_ORDER, SUPPLY_BELONGS_TO_VIRTUAL_ORDER, OTHER_ASYNCHRONOUS_OPERATION_IN_PROGRESS)]. Причина, по которой не удалось отменить поставки: - `INVALID_SUPPLY_STATE` — неверный статус поставки. - `SUPPLY_DOES_NOT_BELONG_TO_CONTRACTOR` — поставка не принадлежит юридическому лицу. - `SUPPLY_DOES_NOT_BELONG_TO_COMPANY` — поставка не принадлежит продавцу. - `SUPPLY_DOES_NOT_BELONG_TO_ORDER` — поставка не принадлежит заявке на поставку. - `SUPPLY_BELONGS_TO_VIRTUAL_ORDER` — поставка принадлежит виртуальной заявке на поставку. - `OTHER_ASYNCHRONOUS_OPERATION_IN_PROGRESS` — поставка в процессе отмены.
    - `is_supply_cancelled` — boolean. `true`, если поставка отменена.
    - `supply_id` — integer<int64>. Идентификатор поставки.
- `status` — string (SUCCESS, IN_PROGRESS, ERROR). Статус отмены заявки на поставку. Возможные значения: - `SUCCESS` — заявка отменена. - `IN_PROGRESS` — заявки в процессе отмены. - `ERROR` — ошибка.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
