---
title: Получить список складов для планирования отгрузок курьеру
api: ozon-seller
method: POST
path: /v1/warehouse/fbs/pickup/planning/list
operation_id: WarehouseFbsPickUpPlanningList
tags:
  - FBSWarehouseSetup
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e165f9176ab17815
---

# Получить список складов для планирования отгрузок курьеру

`POST /v1/warehouse/fbs/pickup/planning/list`

Чтобы создать отгрузку, используйте метод [/v1/warehouse/fbs/pickup/courier/create](#operation/WarehouseFbsPickUpCourierCreate). [Подробнее об отгрузках курьеру на FBS в Базе знаний](https://seller-edu.ozon.ru/fbs/ozon-logistika/otgruzka-kyruery)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список складов

- `result` — object. Список складов.
  - `warehouses` — array[object]. Информация о складах.
    - `can_modify_pickup_plan` — boolean. `true`, если можно изменить возможность планирования вызова курьера.
    - `has_postings_to_be_planned` — boolean. `true`, если есть отправления для отгрузки.
    - `is_pickup_planned` — boolean. `true`, если запланирована отгрузка курьером.
    - `last_pickup_plan_date_at` — string<date-time>. Дата и время окончания планирования выезда курьера.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `warehouse_name` — string. Название склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
