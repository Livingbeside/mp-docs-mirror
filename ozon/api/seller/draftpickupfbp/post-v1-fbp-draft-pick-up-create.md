---
title: Создать черновик заявки на pick-up поставку
api: ozon-seller
method: POST
path: /v1/fbp/draft/pick-up/create
operation_id: FbpAPI_FbpDraftPickupCreate
tags:
  - DraftPickupFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 85e3264d28643aad
---

# Создать черновик заявки на pick-up поставку

`POST /v1/fbp/draft/pick-up/create`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `bundle_id` — string **обязательный**. Идентификатор состава поставки.
- `delivery_details` — object **обязательный**. Детали доставки.
  - `address` — string **обязательный**. Адрес.
  - `comment` — string **обязательный**. Комментарий.
  - `date` — string<date-time> **обязательный**. Дата доставки.
  - `sender_name` — string **обязательный**. ФИО отправителя.
  - `sender_phone` — string **обязательный**. Номер телефона отправителя.
- `package_units_count` — integer<int32> **обязательный**. Количество грузомест.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Черновик создан

- `draft_id` — integer<int64>. Идентификатор черновика заявки на поставку.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.
- `supply_id` — string. Идентификатор поставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
