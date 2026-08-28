---
title: Добавить сертификаты для товаров
api: ozon-seller
method: POST
path: /v1/product/certificate/create
operation_id: ProductAPI_ProductCertificateCreate
tags:
  - CertificationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: 80af6c2dbdf44066
---

# Добавить сертификаты для товаров

`POST /v1/product/certificate/create`

> ⚠️ Метод помечен как **deprecated**.

31 августа 2026 года отключим метод. Переключитесь на методы [/v2/product/certification/options](#operation/ProductCertificateOptions), [/v2/product/certification/params](#operation/ProductCertificateParams) и [/v2/product/certificate/create](#operation/ProductCertificateCreate).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`multipart/form-data`):

- `accordance_type_code` — string (technical_regulations_rf, technical_regulations_cu, gost). Тип соответствия требованиям. Чтобы получить доступные типы, используйте метод [GET /v1/product/certificate/accordance-types](#operation/ProductAPI_ProductCertificateAccordanceTypes). Параметр обязательный, если `type_code = declaration`, `certificate_of_conformity` или `safety_data_sheet`.
- `expire_date` — string<date-time>. Дата окончания действия сертификата. Может быть пустым для бессрочных сертификатов. Формат: `2021-04-30T11:31:26Z`.
- `files` — array[file] **обязательный**. Массив сертификатов для товара. Допустимые расширения jpg, jpeg, png, pdf.
- `issue_date` — string<date-time> **обязательный**. Дата начала действия сертификата. По умолчанию: `2021-04-30T11:31:26Z`.
- `name` — string **обязательный**. Название сертификата. Максимум 100 символов.
- `number` — string **обязательный**. Номер сертификата. Максимум 100 символов.
- `type_code` — string (certificate_of_conformity, declaration, certificate_of_registration, registration_certificate, refused_letter, veterinary_cover_document, safety_data_sheet) **обязательный**. Тип сертификата. Чтобы получить доступные типы, используйте метод [GET /v1/product/certificate/types](#operation/ProductAPI_ProductCertificateTypes).

## Ответы

**200** — Идентификатор загруженного сертификата

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
