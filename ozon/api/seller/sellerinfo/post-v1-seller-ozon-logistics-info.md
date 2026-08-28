---
title: Информация о подключении Ozon Доставки
api: ozon-seller
method: POST
path: /v1/seller/ozon-logistics/info
operation_id: SellerAPI_SellerOzonLogisticsInfo
tags:
  - SellerInfo
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1678cce23f2503df
---

# Информация о подключении Ozon Доставки

`POST /v1/seller/ozon-logistics/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Информация о подключении Ozon Доставки

- `available_schemas` — array[string (UNKNOWN, FBO, FBS)]. Тип доступной схемы: - `UNKNOWN` — не определён, - `FBO`, - `FBS`. По умолчанию: `UNKNOWN`.
- `ozon_logistics_enabled` — boolean. `true`, если Ozon Доставка подключена.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
