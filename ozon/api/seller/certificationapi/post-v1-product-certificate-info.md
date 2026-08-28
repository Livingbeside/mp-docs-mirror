---
title: Информация о сертификате
api: ozon-seller
method: POST
path: /v1/product/certificate/info
operation_id: CertificateInfo
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7641e45c0d73c421
---

# Информация о сертификате

`POST /v1/product/certificate/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `certificate_number` — string **обязательный**. Идентификатор сертификата.

## Ответы

**200** — Информация о сертификате

- `result` — object. Информация о сертификате.
  - `accordance_type_code` — string. Тип соответствия требованиям.
  - `certificate_id` — integer<int32>. Идентификатор.
  - `certificate_name` — string. Название.
  - `certificate_number` — string. Номер.
  - `expire_date` — string<date-time>. Дата окончания действия.
  - `issue_date` — string<date-time>. Дата создания.
  - `products_count` — integer<int32>. Количество товаров, привязанных к сертификату.
  - `rejection_reason_code` — string. Причина отклонения сертификата.
  - `status_code` — string. Статус.
  - `type_code` — string. Тип.
  - `verification_comment` — string. Комментарий модератора.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
