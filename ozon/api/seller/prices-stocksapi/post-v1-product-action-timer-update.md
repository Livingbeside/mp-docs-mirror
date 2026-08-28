---
title: Обновление таймера актуальности минимальной цены
api: ozon-seller
method: POST
path: /v1/product/action/timer/update
operation_id: ProductAPI_ActionTimerUpdate
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 856b774749d6d29e
---

# Обновление таймера актуальности минимальной цены

`POST /v1/product/action/timer/update`

Минимальная цена действует 30 дней после установки. После этого настройка выключается. Вы можете продлить её: вызовите метод повторно и укажите `product_ids`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `product_ids` — array[string<int64>]. Список идентификаторов товаров в системе Ozon — `product_id`.

## Ответы

**200** — Обновлено

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
