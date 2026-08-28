---
title: Возможные статусы сертификатов
api: ozon-seller
method: POST
path: /v1/product/certificate/status/list
operation_id: CertificateStatusList
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c40e772438d18a42
---

# Возможные статусы сертификатов

`POST /v1/product/certificate/status/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Возможные статусы сертификатов

- `result` — array[object]. Список возможных статусов сертификатов.
  - `code` — string. Код статуса сертификата.
  - `name` — string. Описание статуса.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
