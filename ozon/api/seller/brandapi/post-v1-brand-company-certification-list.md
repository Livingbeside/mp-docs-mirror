---
title: Список сертифицируемых брендов
api: ozon-seller
method: POST
path: /v1/brand/company-certification/list
operation_id: BrandAPI_BrandCompanyCertificationList
tags:
  - BrandAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1ec69427a50fc262
---

# Список сертифицируемых брендов

`POST /v1/brand/company-certification/list`

Метод для получения списка брендов, для которых требуется предоставить сертификат. Ответ содержит список брендов,
товары которых есть в вашем личном кабинете.

Список брендов может изменяться, если Ozon получит требование от бренда предоставлять сертификат.

[Подробнее о работе с брендами в Базе знаний продавца](https://seller-edu.ozon.ru/libra/work-with-goods/trebovaniya-k-kartochkam-tovarov/characteristics/brendy)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `page` — integer<int32> **обязательный**. Номер страницы, возвращаемой в запросе.
- `page_size` — integer<int32> **обязательный**. Количество элементов на странице.

## Ответы

**200** — Список брендов

- `result` — object. Результат запроса.
  - `brand_certification` — array[object]. Информация о сертифицируемых брендах.
    - `brand_name` — string. Название бренда.
    - `has_certificate` — boolean. Признак, что требуется сертификат: - `true` — сертификат не нужен; - `false` — требуется сертификат.
  - `total` — integer<int64>. Общее количество брендов.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
