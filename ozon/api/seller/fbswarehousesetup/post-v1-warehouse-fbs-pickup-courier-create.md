---
title: Создать вызов курьера на забор отгрузки pick-up
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/pickup/courier/create
operation_id: WarehouseFbsPickUpCourierCreate
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 46859a91b5f52373
---

# Создать вызов курьера на забор отгрузки pick-up

`POST /v1/warehouse/fbs/pickup/courier/create`

Метод позволяет запланировать приезд курьера для отгрузки ему отправлений. 

[Подробнее об отгрузках курьеру на FBS в Базе знаний](https://seller-edu.ozon.ru/fbs/ozon-logistika/otgruzka-kyruery)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада. Чтобы получить список складов для планирования выездов, используйте [/v1/warehouse/fbs/pickup/planning/list](#operation/WarehouseFbsPickUpPlanningList).

## Ответы

**200** — Вызов создан

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
