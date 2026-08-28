---
title: Отвязать товар от сертификата
api: ozon-seller
method: POST
path: /v1/product/certificate/unbind
operation_id: CertificateUnbind
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6249aa07880499cd
---

# Отвязать товар от сертификата

`POST /v1/product/certificate/unbind`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Товар отвязан от сертификата

- `result` — array[object]. Результат работы метода.
  - `error` — string. Сообщение об ошибке при отвязывании товара.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `updated` — boolean. Был ли отвязан товар от сертификата: - `true` — отвязан, - `false` — не отвязан.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
