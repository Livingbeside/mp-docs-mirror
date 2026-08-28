---
title: Загруженность складов Ozon
api: ozon-seller
method: GET
path: /v1/supplier/available_warehouses
operation_id: SupplierAPI_SupplierAvailableWarehouses
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 17bd57f45f8ae5fa
---

# Загруженность складов Ozon

`GET /v1/supplier/available_warehouses`

Метод возвращает список активных складов Ozon с информацией об их средней загруженности на ближайшее время.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Информация о загруженности складов

- `result` — ?. Результат работы метода.
  - `schedule` — object. Загруженность.
    - `capacity` — ?. Данные о количестве поставляемых на склад товаров.
      - `end` — string<date-time>. Конец периода по местному времени.
      - `start` — string<date-time>. Начало периода по местному времени.
      - `value` — integer<int32>. Среднее количество товаров, которые склад может принять в день за период.
    - `date` — string<date-time>. Ближайшая доступная дата для записи на поставку по местному времени.
  - `warehouse` — object. Склад.
    - `id` — string. Идентификатор склада.
    - `name` — string. Название склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
