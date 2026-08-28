---
title: Значение штрихкода для возвратных отгрузок
api: ozon-seller
method: POST
path: /v1/return/giveout/barcode
operation_id: ReturnAPI_GiveoutGetBarcode
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9e19b624577bf0a9
---

# Значение штрихкода для возвратных отгрузок

`POST /v1/return/giveout/barcode`

Используйте этот метод, чтобы получить штрихкод из ответа методов [/v1/return/giveout/get-png](#operation/ReturnAPI_GiveoutGetPNG) и [/v1/return/giveout/get-pdf](#operation/ReturnAPI_GiveoutGetPDF) в текстовом виде.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Значение штрихкода

- `barcode` — string. Значение штрихкода в текстовом виде.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
