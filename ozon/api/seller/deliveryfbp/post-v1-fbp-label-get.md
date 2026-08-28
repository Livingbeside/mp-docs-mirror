---
title: Получить статус задания на генерацию этикеток
api: ozon-seller
method: POST
path: /v1/fbp/label/get
operation_id: FbpAPI_FbpGetLabel
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bda3bc4dce810d8c
---

# Получить статус задания на генерацию этикеток

`POST /v1/fbp/label/get`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `code` — string **обязательный**. Идентификатор задания на генерацию этикеток.
- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Задание создано

- `label_url` — string. Ссылка на этикетки для поставки.
- `state` — string (UNSPECIFIED, IN_PROGRESS, FINISHED, FAILED). Статус задания на генерацию этикеток: - `UNSPECIFIED` — не определён; - `IN_PROGRESS` — в процессе генерации; - `FINISHED` — генерация завершилась успешно; - `FAILED` — генерация завершилась с ошибкой. По умолчанию: `UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
