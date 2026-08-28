---
title: Отчёт по остаткам и товарам
api: ozon-seller
method: POST
path: /v2/analytics/stock_on_warehouses
operation_id: AnalyticsAPI_AnalyticsGetStockOnWarehousesV2
tags:
  - AnalyticsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 07ce1ef2908b4d47
---

# Отчёт по остаткам и товарам

`POST /v2/analytics/stock_on_warehouses`

В будущем метод будет отключён. Переключитесь на /v1/analytics/stocks . Метод для получения отчёта по остаткам и товарам в перемещении по складам Ozon. Отличается от отчёта в разделе Аналитика → Отчёты → Отчёт по остаткам и товарам в пути на склады Ozon в личном кабинете.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<int64> **обязательный**. Количество ответов на странице. По умолчанию — 100.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.
- `warehouse_type` — string (ALL, EXPRESS_DARK_STORE, NOT_EXPRESS_DARK_STORE). Фильтр по типу склада: - `EXPRESS_DARK_STORE` — склады Ozon с доставкой Fresh. - `NOT_EXPRESS_DARK_STORE` — склады Ozon без доставки Fresh. - `ALL` — все склады Ozon. По умолчанию: `ALL`.

## Ответы

**200** — Отчёт по остаткам и товарам

- `result` — object. Результат запроса.
  - `rows` — array[object]. Информация о товарах и остатках.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `item_code` — string. Идентификатор товара в системе продавца — артикул.
    - `item_name` — string. Название товара в системе Ozon.
    - `free_to_sell_amount` — integer<int64>. Количество товара, доступное к продаже на Ozon.
    - `promised_amount` — integer<int64>. Количество товара, указанное в подтверждённых будущих поставках.
    - `reserved_amount` — integer<int64>. Количество товара, зарезервированное для покупки, возврата и перевозки между складами.
    - `warehouse_name` — string. Название склада, где находится товар.

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
