---
title: Штрихкод для получения возвратной отгрузки в формате PDF
api: ozon-seller
method: POST
path: /v1/return/giveout/get-pdf
operation_id: ReturnAPI_GiveoutGetPDF
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4d8aed396b5a32da
---

# Штрихкод для получения возвратной отгрузки в формате PDF

`POST /v1/return/giveout/get-pdf`

Возвращает PDF-файл со штрихкодом. Метод работает только для схемы FBS.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Штрихкод для возвратной отгрузки

- `content_type` — string. Тип файла.
- `file_content` — string. PDF-файл со штрихкодом в кодировке Base64.
- `file_name` — string. Название файла.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
