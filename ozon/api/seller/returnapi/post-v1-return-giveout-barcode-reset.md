---
title: Сгенерировать новый штрихкод
api: ozon-seller
method: POST
path: /v1/return/giveout/barcode-reset
operation_id: ReturnAPI_GiveoutBarcodeReset
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3ded99d21884e7a4
---

# Сгенерировать новый штрихкод

`POST /v1/return/giveout/barcode-reset`

Используйте метод, если ваш штрихкод попал в посторонние руки.

Метод возвращает PNG-файл с новым штрихкодом. После использования метода вы не сможете получить возвратную отгрузку по старым штрихкодам.
Чтобы получить новый штрихкод в PDF-формате, запросите его методом [/v1/return/giveout/get-pdf](#operation/ReturnAPI_GiveoutGetPDF).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Новый штрихкод

- `content_type` — string. Тип файла.
- `file_content` — string. Изображение со штрихкодом в бинарном виде.
- `file_name` — string. Название файла.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
