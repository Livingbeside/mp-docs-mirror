---
title: Подтвердить заявку на отмену rFBS
api: ozon-seller
method: POST
path: /v2/conditional-cancellation/approve
operation_id: CancellationAPI_ConditionalCancellationApproveV2
tags:
  - CancellationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2073db27ca932d18
---

# Подтвердить заявку на отмену rFBS

`POST /v2/conditional-cancellation/approve`

Метод позволяет согласовать заявку на отмену в статусе `ON_APPROVAL`. Заказ будет отменён, а деньги вернутся покупателю.

## Запрос

**Тело запроса** (`application/json`):

- `cancellation_id` — integer<int64> **обязательный**. Идентификатор заявки на отмену.
- `comment` — string. Комментарий.

## Ответы

**200** — Заявка подтверждена

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
