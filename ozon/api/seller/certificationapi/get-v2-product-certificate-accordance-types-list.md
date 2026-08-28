---
title: Список типов соответствия требованиям (версия 2)
api: ozon-seller
method: GET
path: /v2/product/certificate/accordance-types/list
operation_id: CertificateAccordanceTypes
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1774fe435b5a2852
---

# Список типов соответствия требованиям (версия 2)

`GET /v2/product/certificate/accordance-types/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список типов соответствия требованиям

- `result` — object. Список типов соответствия требованиям.
  - `base` — array[object]. Основные типы соответствия требованиям.
    - `code` — string. Код типа соответствия требованиям.
    - `title` — string. Описание типа соответствия требованиям.
  - `hazard` — array[object]. Типов соответствия требованиям, относящиеся к опасным товарам.
    - `code` — string. Код типа соответствия требованиям.
    - `title` — string. Описание типа соответствия требованиям.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
