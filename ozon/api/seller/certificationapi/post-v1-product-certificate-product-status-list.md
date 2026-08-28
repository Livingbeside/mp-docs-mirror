---
title: Список возможных статусов товаров
api: ozon-seller
method: POST
path: /v1/product/certificate/product_status/list
operation_id: ProductStatusList
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5192958fa378b5d2
---

# Список возможных статусов товаров

`POST /v1/product/certificate/product_status/list`

Метод для получения списка возможных статусов товаров при их привязке к сертификату.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список статусов товаров

- `result` — array[object]. Список статусов товаров.
  - `code` — string. Код статуса товара при привязке к сертификату.
  - `name` — string. Описание статуса.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
