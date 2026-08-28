---
title: Создать черновик для доставки в drop-off пункт
api: ozon-seller
method: POST
path: /v1/fbp/draft/drop-off/create
operation_id: FbpDraftDropOffCreate
tags:
  - DraftDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c334eb34b3432f69
---

# Создать черновик для доставки в drop-off пункт

`POST /v1/fbp/draft/drop-off/create`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `bundle_id` — string **обязательный**. Идентификатор провалидированного списка товаров.
- `delivery_details` — object **обязательный**. Детали доставки.
  - `drop_off_date` — string **обязательный**. Дата доставки.
  - `drop_off_point_id` — integer<int64> **обязательный**. Идентификатор drop-off пункта.
  - `drop_off_province_uuid` — string **обязательный**. Уникальный идентификатор провинции.
- `package_units_count` — integer<int32> **обязательный**. Количество грузомест.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада продавца.

## Ответы

**200** — Черновик создан

- `draft_id` — integer<int64>. Идентификатор черновика.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.
- `supply_id` — string. Идентификатор заявки на поставку.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
