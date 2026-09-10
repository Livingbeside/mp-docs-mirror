---
title: Обновление документов
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/offers/documents/update
operation_id: updateDocuments
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
content_sha: 010146e76534f4d2
---

# Обновление документов

`POST /v1/businesses/{businessId}/offers/documents/update`

{% include notitle [access](../../_auto/method_scopes/updateDocuments.md) %}

Полностью обновляет номер, тип и даты документов на товары. За один запрос можно обновить не более 100 документов.

Для каждого документа передайте его идентификатор и актуальные значения номера, типа и дат.
Если дата не указана, ранее сохраненная дата будет удалена.
Ошибка одного документа не мешает обработке остальных.

{% include notitle [limit](../../_auto/method_limits/updateDocuments.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `documents` — array[object] **обязательный**. Документы для обновления. Идентификаторы документов не должны повторяться в одном запросе. Если идентификаторы повторяются, запрос не обрабатывается.
  - `number` — string **обязательный**. Номер, указанный в сертификате, декларации или другом документе.
  - `type` — string (CONFORMITY_DECLARATION, CONFORMITY_CERTIFICATE, STATE_REGISTRATION_CERTIFICATE, MEDICINAL_PRODUCT_CERTIFICATE, BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE, MEDICAL_DEVICE_CERTIFICATE, AGROCHEMICAL_PESTICIDE_CERTIFICATE) **обязательный**. Тип документа: * `CONFORMITY_DECLARATION` — Декларация о соответствии. * `CONFORMITY_CERTIFICATE` — Сертификат соответствия. * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация продукции (санэпид требования). * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки. * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о государственной регистрации БАД. * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение медицинского изделия. * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация пестицида и агрохимиката.
  - `activeFromDate` — string<date>. Дата начала действия документа.
  - `activeToDate` — string<date>. Дата окончания действия документа.
  - `id` — integer<int64> **обязательный**. Идентификатор документа.

## Ответы

**200** — Если все документы обновлены, поле `status` принимает значение `OK`, а поле `result` не возвращается. Если хотя бы один документ не удалось обновить, поле `status` принимает значение `ERROR`, а поле `result` содержит только ошибки. Остальные документы при этом обрабатываются.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Ошибки документов, которые не удалось обновить.
  - `errors` — array[object] **обязательный**. Ошибки обработки документов.
    - `id` — integer<int64> **обязательный**. Идентификатор документа.
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
