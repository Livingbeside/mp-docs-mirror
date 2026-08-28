---
title: Удалить сертификат
api: ozon-seller
method: POST
path: /v1/product/certificate/delete
operation_id: CertificateDelete
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 587e0d5198ca6c55
---

# Удалить сертификат

`POST /v1/product/certificate/delete`

## Запрос

**Тело запроса** (`application/json`):

- `certificate_id` — integer<int32> **обязательный**. Идентификатор сертификата.

## Ответы

**200** — Результат удаления сертификата

- `result` — object. Результат удаления сертификата.
  - `error_message` — string. Описание ошибок при удалении сертификата.
  - `is_delete` — boolean. Удалён ли сертификат: - `true` — удалён, - `false` — не удалён.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
