---
title: Получить статус генерации транспортной накладной
api: ozon-seller
method: POST
path: /v1/fbp/act-to/get
operation_id: FbpAPI_FbpCheckConsignmentNoteState
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9be39fde4129ff10
---

# Получить статус генерации транспортной накладной

`POST /v1/fbp/act-to/get`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `code` — string **обязательный**. Идентификатор транспортной накладной.
- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Статус генерации транспортной накладной

- `error_message` — string. Описание ошибки.
- `label_url` — string. Ссылка на этикетки для поставки.
- `state` — string (STATE_TYPE_UNSPECIFIED, IN_PROGRESS, FINISHED, FAILED). Статус генерации: - `STATE_TYPE_UNSPECIFIED` — не определён; - `IN_PROGRESS` — в процессе; - `FINISHED` — завершилась успешно; - `FAILED` — ошибка. По умолчанию: `STATE_TYPE_UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
