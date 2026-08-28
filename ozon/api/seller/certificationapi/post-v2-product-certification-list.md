---
title: Список сертифицируемых категорий
api: ozon-seller
method: POST
path: /v2/product/certification/list
operation_id: ProductAPI_ProductCertificationList
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e812e02ad043a286
---

# Список сертифицируемых категорий

`POST /v2/product/certification/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `page` — integer<int64> **обязательный**. Номер страницы.
- `page_size` — integer<int64> **обязательный**. Количество элементов на странице.

## Ответы

**200** — Список сертифицируемых категорий

- `certification` — array[object]. Информация о сертифицируемых категориях.
  - `category_id` — integer<int64>. Идентификатор сертифицируемой категории.
  - `category_name` — string. Название сертифицируемой категории.
  - `is_required` — boolean. Признак обязательной характеристики.
  - `type_id` — integer<int64>. Идентификатор типа сертифицируемой категории.
  - `type_name` — string. Название типа сертифицируемой категории.
- `total` — integer<int64>. Всего категорий.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
