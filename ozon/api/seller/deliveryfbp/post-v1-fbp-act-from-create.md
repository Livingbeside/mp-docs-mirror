---
title: Сгенерировать акт приёмки
api: ozon-seller
method: POST
path: /v1/fbp/act-from/create
operation_id: FbpAPI_FbpCreateAct
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3d433949142a55a5
---

# Сгенерировать акт приёмки

`POST /v1/fbp/act-from/create`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Успешно

- `errors` — array[string (CREATE_ACT_ERROR_REASON_UNSPECIFIED, INVALID_ORDER_TYPE)]. Причина ошибки: - `CREATE_ACT_ERROR_REASON_UNSPECIFIED` — не определена; - `INVALID_ORDER_TYPE` — нельзя создать акт для указанного идентификатора поставки. По умолчанию: `CREATE_ACT_ERROR_REASON_UNSPECIFIED`.
- `file_uuid` — string. Идентификатор акта приёмки.
- `is_success` — boolean. `true`, если в запросе нет ошибок.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
