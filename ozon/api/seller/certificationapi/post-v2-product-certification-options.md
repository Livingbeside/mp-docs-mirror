---
title: Получить параметры для создания сертификата качества
api: ozon-seller
method: POST
path: /v2/product/certification/options
operation_id: ProductCertificateOptions
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5da32b59a507c280
---

# Получить параметры для создания сертификата качества

`POST /v2/product/certification/options`

Используйте информацию о параметрах в запросе метода [/v2/product/certification/params](#operation/ProductCertificateParams).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Параметры для создания сертификата

- `option` — array[object]. Параметры для создания сертификата.
  - `name` — string. Название параметра сертификата: - `NAME` — название; - `CERTIFICATE_TYPE` — тип; - `NUMBER` — номер; - `FILES` — файл с сертификатом в кодировке Base64; - `CERTIFICATE_COUNTRY` — страна выдачи; - `ACCORDANCE_TYPE` — стандарт сертификации; - `SKUS` — список идентификаторов товара в системе Ozon, SKU; - `ISSUE_DATE` — дата выпуска; - `EXPIRED_DATE` — дата истечения; - `LINK_TO_REGISTRY` — ссылка на государственный реестр; - `PRODUCT_TYPE` — тип товаров; - `INFINITE` — бессрочность.
  - `required` — boolean. `true`, если параметр обязательный.
  - `variants` — array[object]. Список возможных значений.
    - `name` — string. Название значения параметра.
    - `value` — string. Значение параметра.

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
