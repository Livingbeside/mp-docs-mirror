---
title: Получить PDF с этикетками грузовых мест
api: ozon-seller
method: GET
path: /v1/cargoes-label/file/{file_guid}
operation_id: CargoesAPI_CargoesLabelFile
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fd4d97426f2f9dc8
---

# Получить PDF с этикетками грузовых мест

`GET /v1/cargoes-label/file/{file_guid}`

10 апреля 2026 года отключим метод. Переключитесь на /v1/cargoes-label/get .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Этикетки грузовых мест

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
