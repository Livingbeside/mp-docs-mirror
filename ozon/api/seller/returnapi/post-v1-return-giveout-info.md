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
content_sha: c44673330b2dd0ca
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
  - `delivery_schema` — string. Cхема доставки: - `GIVEOUT_DELIVERY_SCHEMA_UNSPECIFIED` — не определёна, напишите в поддержку. - `GIVEOUT_DELIVERY_SCHEMA_FBO` — FBO. - `GIVEOUT_DELIVERY_SCHEMA_FBS` — FBS.
  - `name` — string. Название товара.
  - `seller_id` — integer<int64>. Идентификатор продавца.
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
