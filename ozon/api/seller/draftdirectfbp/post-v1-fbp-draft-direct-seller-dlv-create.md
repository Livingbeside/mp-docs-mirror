---
title: Создать черновик с доставкой силами продавца
api: ozon-seller
method: POST
path: /v1/fbp/draft/direct/seller-dlv/create
operation_id: FbpDraftDirectSellerDlvCreate
tags:
  - DraftDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ff5567f2461770ac
---

# Создать черновик с доставкой силами продавца

`POST /v1/fbp/draft/direct/seller-dlv/create`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `bundle_id` — string **обязательный**. Идентификатор провалидированного списка товаров.
- `delivery_details` — object **обязательный**. Детали доставки.
  - `driver_name` — string **обязательный**. ФИО водителя.
  - `timeslot_start` — string<date-time> **обязательный**. Начало таймслота.
  - `vehicle_number` — string **обязательный**. Номер автомобиля.
  - `vehicle_type` — string **обязательный**. Тип автомобиля.
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
