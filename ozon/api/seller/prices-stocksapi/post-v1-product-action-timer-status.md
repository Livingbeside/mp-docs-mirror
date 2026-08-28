---
title: Получить статус установленного таймера
api: ozon-seller
method: POST
path: /v1/product/action/timer/status
operation_id: ProductAPI_ActionTimerStatus
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 23d72079153f8de2
---

# Получить статус установленного таймера

`POST /v1/product/action/timer/status`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `product_ids` — ?. Список идентификаторов товаров в системе Ozon — `product_id`.

## Ответы

**200** — Статусы

- `statuses` — ?
  - `expired_at` — string<date-time>. Время окончания таймера. Если параметр пустой, активного таймера нет.
  - `min_price_for_auto_actions_enabled` — boolean. `true`, если Ozon учитывает минимальную цену при добавлении в акции.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
