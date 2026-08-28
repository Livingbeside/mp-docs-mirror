---
title: Изменить черновик заявки на pick-up поставку
api: ozon-seller
method: POST
path: /v1/fbp/draft/pick-up/dlv/edit
operation_id: FbpAPI_FbpDraftPickupDlvEdit
tags:
  - DraftPickupFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 269a17dc25f38476
---

# Изменить черновик заявки на pick-up поставку

`POST /v1/fbp/draft/pick-up/dlv/edit`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `pickup_details` — object **обязательный**. Детали доставки.
  - `address` — string **обязательный**. Адрес.
  - `comment` — string **обязательный**. Комментарий.
  - `date` — string<date-time> **обязательный**. Дата доставки.
  - `sender_name` — string **обязательный**. ФИО отправителя.
  - `sender_phone` — string **обязательный**. Номер телефона отправителя.
- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Информация отредактирована

- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
