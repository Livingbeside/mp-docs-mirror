---
title: Перенести склад в архив
api: ozon-seller
method: POST
path: /v1/warehouse/archive
operation_id: ArchiveWarehouseFBS
tags:
  - WarehouseAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 19fbb85bc4b1c5b4
---

# Перенести склад в архив

`POST /v1/warehouse/archive`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `reason` — string **обязательный**. Причина переноса склада в архив.
- `return_point_id` — integer<int64>. Идентификатор пункта возврата. Получите значение параметра методом [/v1/warehouse/fbs/update/return-point/list](#operation/WarehouseFBSUpdateReturnPointList).
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Склад перенесён в архив

- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/warehouse/operation/status](#operation/GetWarehouseFBSOperationStatus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
