---
title: Информация о возвратной отгрузке
api: ozon-seller
method: POST
path: /v1/return/giveout/info
operation_id: ReturnAPI_GiveoutInfo
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: eb7a60377c524364
---

# Информация о возвратной отгрузке

`POST /v1/return/giveout/info`

Метод для получения информации о возвратной отгрузке. 
В параметр `giveout_id` передаётся значение, полученное в методе [/v1/return/giveout/list](#operation/ReturnAPI_GiveoutList).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `giveout_id` — integer<int64> **обязательный**. Идентификатор отгрузки.

## Ответы

**200** — Информация о возвратной отгрузке

- `articles` — array[object]. Артикулы товаров.
  - `approved` — boolean. `true`, если отгрузка подтверждена.
  - `barcodes` — array[object]. Штрихкоды товара.
    - `type` — string. Тип штрихкода: - `BT_DATA_MATRIX` — контрольный идентификационный знак (КИЗ); - `BT_SCAN_IT` — штрихкод ScanIt с этикетки; - `BT_LOZON_ID`, `BT_BARCODE` — штрихкод с этикетки.
    - `value` — string. Значение штрихкода.
  - `delivery_schema` — string. Cхема доставки: - `GIVEOUT_DELIVERY_SCHEMA_UNSPECIFIED` — не определёна, напишите в поддержку. - `GIVEOUT_DELIVERY_SCHEMA_FBO` — FBO. - `GIVEOUT_DELIVERY_SCHEMA_FBS` — FBS.
  - `name` — string. Название товара.
  - `seller_id` — integer<int64>. Идентификатор продавца.
  - `type` — string (UNSPECIFIED, EXEMPLAR, POSTING, TRANSIT_BOX). Тип возврата: - `UNSPECIFIED` — не указан; - `EXEMPLAR` — экземпляр товара; - `POSTING` — отправление; - `TRANSIT_BOX` — транзитная коробка. По умолчанию: `UNSPECIFIED`.
- `giveout_id` — integer<int64>. Идентификатор отгрузки.
- `giveout_status` — string. Статусы возвратной отгрузки: - `GIVEOUT_STATUS_UNSPECIFIED` — не определён, напишите в поддержку. - `GIVEOUT_STATUS_CREATED` — создана. - `GIVEOUT_STATUS_APPROVED` — одобрена. - `GIVEOUT_STATUS_COMPLETED` — завершена. - `GIVEOUT_STATUS_CANCELLED` — отменена.
- `warehouse_address` — string. Адрес склада.
- `warehouse_name` — string. Название склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
