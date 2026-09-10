---
title: Создание документов
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/offers/documents/create
operation_id: createDocuments
tags:
  - documents
  - dbs
  - fby
  - fbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: c305c593d3a5401a
---

# Создание документов

`POST /v1/businesses/{businessId}/offers/documents/create`

{% include notitle [access](../../_auto/method_scopes/createDocuments.md) %}

Создает для указанного бизнеса документы на товары. За один запрос можно создать не более 100 документов.

Для привязки документа к товару передайте его номер в поле `certificates` метода
[POST v2/businesses/{businessId}/offer-mappings/update](../../reference/business-offer-mappings/updateOfferMappings.md).

Если документ с таким номером уже существует, результат для документа содержит ошибку
`DOCUMENT_ALREADY_EXISTS`. Существующий документ при этом не возвращается. Ошибка одного документа
не мешает обработке остальных.

{% include notitle [limit](../../_auto/method_limits/createDocuments.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `documents` — array[object] **обязательный**. Документы для создания. Номера документов не должны повторяться в одном запросе. Если номера повторяются, запрос не обрабатывается.
  - `number` — string **обязательный**. Номер, указанный в сертификате, декларации или другом документе.
  - `type` — string (CONFORMITY_DECLARATION, CONFORMITY_CERTIFICATE, STATE_REGISTRATION_CERTIFICATE, MEDICINAL_PRODUCT_CERTIFICATE, BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE, MEDICAL_DEVICE_CERTIFICATE, AGROCHEMICAL_PESTICIDE_CERTIFICATE) **обязательный**. Тип документа: * `CONFORMITY_DECLARATION` — Декларация о соответствии. * `CONFORMITY_CERTIFICATE` — Сертификат соответствия. * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация продукции (санэпид требования). * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки. * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о государственной регистрации БАД. * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение медицинского изделия. * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация пестицида и агрохимиката.
  - `activeFromDate` — string<date>. Дата начала действия документа.
  - `activeToDate` — string<date>. Дата окончания действия документа.

## Ответы

**200** — Документы, созданные этим запросом, и ошибки создания. Если хотя бы один документ не удалось создать, поле `status` принимает значение `ERROR`. Остальные документы при этом обрабатываются.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Созданные документы и ошибки обработки.
  - `documents` — array[object]. Документы, созданные этим запросом.
    - `number` — string **обязательный**. Номер, указанный в сертификате, декларации или другом документе.
    - `type` — string (CONFORMITY_DECLARATION, CONFORMITY_CERTIFICATE, STATE_REGISTRATION_CERTIFICATE, MEDICINAL_PRODUCT_CERTIFICATE, BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE, MEDICAL_DEVICE_CERTIFICATE, AGROCHEMICAL_PESTICIDE_CERTIFICATE) **обязательный**. Тип документа: * `CONFORMITY_DECLARATION` — Декларация о соответствии. * `CONFORMITY_CERTIFICATE` — Сертификат соответствия. * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация продукции (санэпид требования). * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки. * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о государственной регистрации БАД. * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение медицинского изделия. * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация пестицида и агрохимиката.
    - `activeFromDate` — string<date>. Дата начала действия документа.
    - `activeToDate` — string<date>. Дата окончания действия документа.
    - `id` — integer<int64> **обязательный**. Идентификатор документа.
    - `status` — string (ACTIVE, NOT_FOUND, VALIDATING, WAITING_FIXES, EXPIRED, REVOKED) **обязательный**. Статус документа: * `ACTIVE` — действует. * `NOT_FOUND` — не найден в реестре. * `VALIDATING` — проверяется. * `WAITING_FIXES` — ожидает исправлений. * `EXPIRED` — срок действия истек. * `REVOKED` — отозван.
  - `errors` — array[object]. Ошибки документов, которые не удалось создать.
    - `number` — string **обязательный**. Номер, указанный в сертификате, декларации или другом документе.
    - `code` — string (DOCUMENT_VALIDATION_FAILED, DOCUMENT_ALREADY_EXISTS, DOCUMENT_NOT_FOUND, DOCUMENT_UPDATE_NOT_ALLOWED, DOCUMENT_CONCURRENT_MODIFICATION) **обязательный**. Код ошибки документа: * `DOCUMENT_VALIDATION_FAILED` — документ не прошел проверку. * `DOCUMENT_ALREADY_EXISTS` — документ уже существует. * `DOCUMENT_NOT_FOUND` — документ не найден. * `DOCUMENT_UPDATE_NOT_ALLOWED` — изменение документа запрещено. * `DOCUMENT_CONCURRENT_MODIFICATION` — документ был изменен параллельно.
    - `message` — string. Описание ошибки для человека. Для обработки ошибки используйте поле `code`.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибке](../../concepts/error-codes.md#400)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**401** — В запросе не указаны данные для авторизации. [Подробнее об ошибке](../../concepts/error-codes.md#401)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**403** — Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](../../concepts/error-codes.md#403)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
