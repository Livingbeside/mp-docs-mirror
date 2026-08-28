---
title: Штрихкод для получения возвратной отгрузки в формате PNG
api: ozon-seller
method: POST
path: /v1/return/giveout/get-png
operation_id: ReturnAPI_GiveoutGetPNG
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: db104e94b9e5a504
---

# Штрихкод для получения возвратной отгрузки в формате PNG

`POST /v1/return/giveout/get-png`

Возвращает PNG-файл со штрихкодом.

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
- `file_content` — string. PNG-файл со штрихкодом в кодировке Base64.
- `file_name` — string. Название файла.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
