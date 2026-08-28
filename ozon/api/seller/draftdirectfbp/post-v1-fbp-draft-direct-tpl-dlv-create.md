---
title: Создать черновик заявки на доставку сторонней транспортной компанией
api: ozon-seller
method: POST
path: /v1/fbp/draft/direct/tpl-dlv/create
operation_id: FbpAPI_FbpDraftDirectTplDlvCreate
tags:
  - DraftDirectFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7b74e62603ab22c2
---

# Создать черновик заявки на доставку сторонней транспортной компанией

`POST /v1/fbp/draft/direct/tpl-dlv/create`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `bundle_id` — string **обязательный**. Идентификатор комплекта.
- `delivery_details` — object **обязательный**. Детали доставки.
  - `timeslot_start` — string<date-time> **обязательный**. Время начала таймслота по местному времени.
  - `tracking_number` — string **обязательный**. Трек-номер отправления.
  - `transport_company_name` — string **обязательный**. Название транспортной компании.
- `package_units_count` — integer<int32> **обязательный**. Количество грузомест.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Статус генерации

- `draft_id` — integer<int64>. Идентификатор черновика.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.
- `supply_id` — string. Идентификатор поставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
