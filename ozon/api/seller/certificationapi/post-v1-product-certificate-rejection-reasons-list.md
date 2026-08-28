---
title: Возможные причины отклонения сертификата
api: ozon-seller
method: POST
path: /v1/product/certificate/rejection_reasons/list
operation_id: RejectionReasonsList
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 858f89fa1854c511
---

# Возможные причины отклонения сертификата

`POST /v1/product/certificate/rejection_reasons/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Причины отклонения сертификата

- `result` — array[object]. Причины отклонения сертификата.
  - `code` — string. Код причины отклонения сертификата.
  - `name` — string. Описание причины отклонения сертификата.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
