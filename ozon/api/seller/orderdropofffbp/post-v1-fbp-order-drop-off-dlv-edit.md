---
title: Отредактировать информацию о поставке на drop-off пункт
api: ozon-seller
method: POST
path: /v1/fbp/order/drop-off/dlv/edit
operation_id: FbpAPI_FbpOrderDropOffDlvEdit
tags:
  - OrderDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ee94e1d8c55550b7
---

# Отредактировать информацию о поставке на drop-off пункт

`POST /v1/fbp/order/drop-off/dlv/edit`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `drop_off_date` — string **обязательный**. Дата прибытия поставки на drop-off пункт.
- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Информация передана

- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
