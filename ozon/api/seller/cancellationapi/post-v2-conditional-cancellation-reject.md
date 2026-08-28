---
title: Отклонить заявку на отмену rFBS
api: ozon-seller
method: POST
path: /v2/conditional-cancellation/reject
operation_id: CancellationAPI_ConditionalCancellationRejectV2
tags:
  - CancellationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5e0e4de4ab44eccd
---

# Отклонить заявку на отмену rFBS

`POST /v2/conditional-cancellation/reject`

Метод позволяет отклонить заявку на отмену в статусе `ON_APPROVAL`. В параметре `comment` опишите причину. Заказ останется в том же статусе, и его нужно будет доставить покупателю.

## Запрос

**Тело запроса** (`application/json`):

- `cancellation_id` — integer<int64> **обязательный**. Идентификатор заявки на отмену.
- `comment` — string. Комментарий.

## Ответы

**200** — Заявка отклонена

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
