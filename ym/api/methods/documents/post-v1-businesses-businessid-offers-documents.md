---
title: Получение документов
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/offers/documents
operation_id: getDocuments
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
content_sha: bd69a20eb9bd3b37
---

# Получение документов

`POST /v1/businesses/{businessId}/offers/documents`

{% include notitle [access](../../_auto/method_scopes/getDocuments.md) %}

Возвращает страницу документов на товары с учетом переданных фильтров.

{% include notitle [limit](../../_auto/method_limits/getDocuments.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | — |

## Запрос

**Тело запроса** (`application/json`):

- `documentIds` — array[integer<int64>]. Идентификаторы документов.
- `documentNumbers` — array[string]. Номера документов.
- `documentTypes` — array[string (CONFORMITY_DECLARATION, CONFORMITY_CERTIFICATE, STATE_REGISTRATION_CERTIFICATE, MEDICINAL_PRODUCT_CERTIFICATE, BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE, MEDICAL_DEVICE_CERTIFICATE, AGROCHEMICAL_PESTICIDE_CERTIFICATE)]. Типы документов.
- `documentStatuses` — array[string (ACTIVE, NOT_FOUND, VALIDATING, WAITING_FIXES, EXPIRED, REVOKED)]. Статусы документов.

## Ответы

**200** — Страница документов.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Страница документов.
  - `documents` — array[object] **обязательный**. Документы на странице.
    - `number` — string **обязательный**. Номер, указанный в сертификате, декларации или другом документе.
    - `type` — string (CONFORMITY_DECLARATION, CONFORMITY_CERTIFICATE, STATE_REGISTRATION_CERTIFICATE, MEDICINAL_PRODUCT_CERTIFICATE, BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE, MEDICAL_DEVICE_CERTIFICATE, AGROCHEMICAL_PESTICIDE_CERTIFICATE) **обязательный**. Тип документа: * `CONFORMITY_DECLARATION` — Декларация о соответствии. * `CONFORMITY_CERTIFICATE` — Сертификат соответствия. * `STATE_REGISTRATION_CERTIFICATE` — Государственная регистрация продукции (санэпид требования). * `MEDICINAL_PRODUCT_CERTIFICATE` — Обязательные документы для аптеки. * `BIOLOGICALLY_ACTIVE_ADDITIVE_CERTIFICATE` — Свидетельство о государственной регистрации БАД. * `MEDICAL_DEVICE_CERTIFICATE` — Регистрационное удостоверение медицинского изделия. * `AGROCHEMICAL_PESTICIDE_CERTIFICATE` — Государственная регистрация пестицида и агрохимиката.
    - `activeFromDate` — string<date>. Дата начала действия документа.
    - `activeToDate` — string<date>. Дата окончания действия документа.
    - `id` — integer<int64> **обязательный**. Идентификатор документа.
    - `status` — string (ACTIVE, NOT_FOUND, VALIDATING, WAITING_FIXES, EXPIRED, REVOKED) **обязательный**. Статус документа: * `ACTIVE` — действует. * `NOT_FOUND` — не найден в реестре. * `VALIDATING` — проверяется. * `WAITING_FIXES` — ожидает исправлений. * `EXPIRED` — срок действия истек. * `REVOKED` — отозван.
  - `paging` — object **обязательный**. Идентификатор следующей страницы.
    - `nextPageToken` — string. Идентификатор следующей страницы результатов.

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
