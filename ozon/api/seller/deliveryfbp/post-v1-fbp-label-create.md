---
title: Cоздать задание на генерацию этикеток
api: ozon-seller
method: POST
path: /v1/fbp/label/create
operation_id: FbpAPI_FbpCreateLabel
tags:
  - DeliveryFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9dbfc874676a5dd8
---

# Cоздать задание на генерацию этикеток

`POST /v1/fbp/label/create`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — string **обязательный**. Идентификатор поставки.

## Ответы

**200** — Задание создано

- `code` — string. Идентификатор задания на генерацию этикеток.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
