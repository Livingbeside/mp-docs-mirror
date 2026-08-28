---
title: Получить статус генерации акта приёмки
api: ozon-seller
method: POST
path: /v1/fbp/act-from/get
operation_id: FbpAPI_FbpCheckActState
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9c82b01dab6d1745
---

# Получить статус генерации акта приёмки

`POST /v1/fbp/act-from/get`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `file_uuid` — string **обязательный**. Идентификатор акта приёмки.

## Ответы

**200** — Статус генерации акта приёмки

- `cdn_url` — string. Ссылка на акт приёмки.
- `error` — string (ERROR_REASON_UNSPECIFIED, INVALID_COMPANY, FILE_NOT_FOUND, GENERATE_TIMEOUT_REACHED, GENERATION_ERROR). Ошибка генерации: - `ERROR_REASON_UNSPECIFIED` — не определена; - `INVALID_COMPANY` — неверная компания; - `FILE_NOT_FOUND` — файл не найден; - `GENERATE_TIMEOUT_REACHED` — превышено время генерации; - `GENERATION_ERROR` — ошибка во время генерации. По умолчанию: `ERROR_REASON_UNSPECIFIED`.
- `status` — string (STATUS_UNSPECIFIED, NOT_EXIST, PROCESSING, EXIST, ERROR). Статус генерации: - `STATUS_UNSPECIFIED` — не определён; - `NOT_EXIST` — не существует; - `PROCESSING` — в процессе; - `EXIST` — завершена; - `ERROR` — ошибка. По умолчанию: `STATUS_UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
