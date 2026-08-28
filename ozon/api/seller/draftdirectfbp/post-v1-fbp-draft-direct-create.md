---
title: Создать черновик заявки на поставку без указания способа доставки
api: ozon-seller
method: POST
path: /v1/fbp/draft/direct/create
operation_id: FbpDraftDirectCreate
tags:
  - DraftDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 002c728d360b9a50
---

# Создать черновик заявки на поставку без указания способа доставки

`POST /v1/fbp/draft/direct/create`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `bundle_id` — string **обязательный**. Идентификатор провалидированного списка товаров. Чтобы получить, используйте метод [/v1/fbp/draft/direct/product/validate](#operation/FbpDraftDirectProductValidate).
- `delivery_details` — object **обязательный**. Детали доставки.
  - `timeslot_start` — string<date-time> **обязательный**. Начало таймслота доставки.
- `package_units_count` — integer<int32> **обязательный**. Количество единиц упаковки.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Черновик создан

- `draft_id` — integer<int64>. Идентификатор черновика.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.
- `supply_id` — string. Идентификатор поставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
