---
title: Проверить необходимость установки возвратной мили на склад
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/return-mile/check
operation_id: WarehouseFbsReturnMileCheck
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6eef997c9b8f6354
---

# Проверить необходимость установки возвратной мили на склад

`POST /v1/warehouse/fbs/return-mile/check`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `country_code` — string **обязательный**. Код страны в формате ISO 2.
- `first_mile_type` — string (PICK_UP, DROP_OFF) **обязательный**. Тип первой мили: - `PICK_UP` — отгрузка заказов курьеру; - `DROP_OFF` — отгрузка заказов в пункт приёма.
- `is_kgt` — boolean **обязательный**. Признак крупногабаритного товара.
- `warehouse_id` — integer<int64>. Идентификатор склада.

## Ответы

**200** — Успешно

- `should_set_return_mile` — boolean. Признак, что необходимо установить возвратную милю.
- `unavailability_reasons` — array[string]. Причины, по которым нельзя установить возвратную милю.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
