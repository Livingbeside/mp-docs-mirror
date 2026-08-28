---
title: Получить обязательные параметры для создания сертификата качества
api: ozon-seller
method: POST
path: /v2/product/certification/params
operation_id: ProductCertificateParams
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 63534bc2077f8516
---

# Получить обязательные параметры для создания сертификата качества

`POST /v2/product/certification/params`

Используйте информацию о параметрах в запросе метода [/v2/product/certificate/create](#operation/ProductCertificateCreate).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2278-Novye-beta-metody-dlia-dobavleniia-sertifikatov-kachestva/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `params` — object. Параметры для создания сертификата.
  - `accordance_type` — string (UNKNOWN, EAEU, NATIONAL, TECHNICAL_REGULATIONS_RF, TECHNICAL_REGULATIONS_CU, GOST, CHEMICAL_PRODUCTS, SAFETY_DATA_SHEET, REJECTION_LETTER). Тип соответствия требованиям из метода [/v2/product/certificate/accordance-types/list](#operation/CertificateAccordanceTypes): - `UNKNOWN` — неизвестный; - `EAEU` — стандарт сертификации ЕАЭС; - `NATIONAL` — национальный стандарт сертификации; - `TECHNICAL_REGULATIONS_RF` — технический регламент Российской Федерации; - `TECHNICAL_REGULATIONS_CU` — технический регламент Таможенного союза; - `GOST` — ГОСТ; - `CHEMICAL_PRODUCTS` — паспорт безопасности химической продукции; - `SAFETY_DATA_SHEET` — паспорт безопасности; - `REJECTION_LETTER` — отказное письмо.
  - `certificate_country` — string. Код страны, где выдали сертификат.
  - `certificate_type` — string (UNKNOWN, CERTIFICATE_OF_CONFORMITY, DECLARATION, CERTIFICATE_OF_REGISTRATION, REGISTRATION_CERTIFICATE, REFUSED_LETTER, VETERINARY_COVER_DOCUMENT, SAFETY_DATA_SHEET). Тип сертификата: - `UNKNOWN` — неизвестный; - `CERTIFICATE_OF_CONFORMITY` — сертификат соответствия; - `DECLARATION` — декларация о соответствии; - `CERTIFICATE_OF_REGISTRATION` — свидетельство о государственной регистрации; - `REGISTRATION_CERTIFICATE` — регистрационное удостоверение; - `REFUSED_LETTER` — отказное письмо; - `VETERINARY_COVER_DOCUMENT` — ветеринарный сопроводительный документ; - `SAFETY_DATA_SHEET` — паспорт безопасности.
  - `expired_date` — object. Информация о дате истечения сертификата.
    - `date` — object. Дата истечения сертификата. Не передавайте параметр, если `infinite = true`.
      - `day` — integer<int32>. День.
      - `month` — integer<int32>. Месяц.
      - `year` — integer<int32>. Год.
    - `infinite` — boolean. `true`, если сертификат бессрочный. Не передавайте параметр, если указали `date`.
  - `files` — array[object]. Файлы сертификата.
    - `file_content` — string **обязательный**. Файл в кодировке Base64.
    - `name` — string **обязательный**. Название файла.
  - `issue_date` — string<date-time>. Дата выдачи сертификата.
  - `link_to_registry` — string. Ссылка на государственный реестр.
  - `name` — string. Название сертификата.
  - `number` — string. Номер сертификата.
  - `product_type` — string (UNKNOWN, PRODUCTS_SUBJECT_TO_REGISTRATION, PESTICIDE, AGROCHEMICAL, FEED_ADDITIVE, MEDICAL_PRODUCT, MEDICINE, VETERINARY_DRUG, PHARMACEUTICAL_SUBSTANCE). Тип товаров: - `UNKNOWN` — неизвестный; - `PRODUCTS_SUBJECT_TO_REGISTRATION` — продукт, подлежащий государственной регистрации; - `PESTICIDE` — пестицид; - `AGROCHEMICAL` — агрохимикат; - `FEED_ADDITIVE` — кормовая добавка; - `MEDICAL_PRODUCT` — медицинский продукт; - `MEDICINE` — лекарственный препарат; - `VETERINARY_DRUG` — ветеринарный препарат; - `PHARMACEUTICAL_SUBSTANCE` — фармацевтический ингредиент.
  - `skus` — array[string<int64>]. Список идентификаторов товара в системе Ozon — SKU.

## Ответы

**200** — Обязательные параметры для создания сертификата

- `params` — array[object]. Параметры для создания сертификата.
  - `name` — string. Название параметра сертификата: - `NAME` — название; - `CERTIFICATE_TYPE` — тип; - `NUMBER` — номер; - `FILES` — файл с сертификатом в кодировке Base64; - `CERTIFICATE_COUNTRY` — страна выдачи; - `ACCORDANCE_TYPE` — тип соответствия требованиям; - `SKUS` — список идентификаторов товара в системе Ozon, SKU; - `ISSUE_DATE` — дата выпуска; - `EXPIRED_DATE` — дата истечения; - `LINK_TO_REGISTRY` — ссылка на государственный реестр; - `PRODUCT_TYPE` — тип товаров; - `INFINITE` — бессрочность.
  - `required` — boolean. `true`, если параметр обязательный.

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
