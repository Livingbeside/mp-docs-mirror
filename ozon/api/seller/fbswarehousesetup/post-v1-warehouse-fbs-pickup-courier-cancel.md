---
title: Отменить вызов курьера на забор отгрузки pick-up
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/pickup/courier/cancel
operation_id: WarehouseFbsPickUpCourierCancel
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 18fd6a89806ed138
---

# Отменить вызов курьера на забор отгрузки pick-up

`POST /v1/warehouse/fbs/pickup/courier/cancel`

Метод позволяет отменить запланированный приезд курьера. [Подробнее об отгрузках курьеру на FBS в Базе знаний](https://seller-edu.ozon.ru/fbs/ozon-logistika/otgruzka-kyruery)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Вызов отменён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
