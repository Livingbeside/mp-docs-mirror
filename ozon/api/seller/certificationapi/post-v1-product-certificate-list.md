---
title: Список сертификатов
api: ozon-seller
method: POST
path: /v1/product/certificate/list
operation_id: CertificateList
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 7ac5e7ee79034ab5
---

# Список сертификатов

`POST /v1/product/certificate/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `offer_id` — string. Идентификатор товара в системе продавца — артикул, привязанный к сертификату. Передайте параметр, если нужны сертификаты, к которым привязаны определённые товары.
- `status` — string. Статус сертификата. Передайте параметр, если нужны сертификаты с определённым статусом.
- `type` — string. Тип сертификата. Передайте параметр, если нужны сертификаты с определённым типом.
- `page` — integer<int32> **обязательный**. Страница, с которой следует выводить список. Минимальное значение — 1.
- `page_size` — integer<int32> **обязательный**. Количество объектов на странице. Значение — от 1 до 1000.

## Ответы

**200** — Список сертификатов

- `result` — object. Список сертификатов.
  - `certificates` — array[object]. Информация о сертификате.
    - `certificate_id` — integer<int32>. Идентификатор.
    - `certificate_number` — string. Номер.
    - `certificate_name` — string. Название.
    - `type_code` — string. Тип.
    - `status_code` — string. Статус.
    - `accordance_type_code` — string. Тип соответствия требованиям.
    - `rejection_reason_code` — string. Причина отклонения сертификата.
    - `verification_comment` — string. Комментарий модератора.
    - `issue_date` — string<date-time>. Дата создания.
    - `expire_date` — string<date-time>. Дата окончания действия.
    - `products_count` — integer<int32>. Количество товаров, привязанных к сертификату.
  - `page_count` — integer<int32>. Количество страниц.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
