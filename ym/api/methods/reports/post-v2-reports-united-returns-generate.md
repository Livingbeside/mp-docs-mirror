---
title: Отчет по невыкупам и возвратам
api: yandex-market
method: POST
path: /v2/reports/united-returns/generate
operation_id: generateUnitedReturnsReport
tags:
  - reports
  - fby
  - fbs
  - dbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 62efdbb69c20aa19
---

# Отчет по невыкупам и возвратам

`POST /v2/reports/united-returns/generate`

{% include notitle [access](../../_auto/method_scopes/generateUnitedReturnsReport.md) %}

Запускает генерацию сводного отчета по невыкупам и возвратам за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/orders/returns/logistic#rejected-orders)

Отчет содержит информацию о невыкупах и возвратах за указанный период, а также о тех, которые готовы к выдаче.

Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](../../reference/reports/getReportInfo.md).

{% include notitle [reports](../../_auto/reports/united/returns/generator/united_returns.md) %}

{% include notitle [tariff-period](../../_includes/common/report-data-period-unchanged.md) %}

{% include notitle [limit](../../_auto/method_limits/generateUnitedReturnsReport.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `format` | query | string (FILE, CSV, JSON) | нет | Формат отчета или документа. |

## Запрос

**Тело запроса** (`application/json`):

- `businessId` — integer<int64> **обязательный**. Идентификатор кабинета. {% if audience == "partner" %}Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %}
- `dateFrom` — string<date> **обязательный**. Начало периода, включительно. Формат даты: `ГГГГ-ММ-ДД`.
- `dateTo` — string<date> **обязательный**. Конец периода, включительно. Формат даты: `ГГГГ-ММ-ДД`.
- `campaignIds` — array[integer<int64>]. Список идентификаторов кампании тех магазинов, которые нужны в отчете.
- `returnType` — string (UNREDEEMED, RETURN). Тип фильтрации: * `UNREDEEMED` — невыкупы. * `RETURN` — возвраты. Если не указывать, в ответе будут и невыкупы, и возвраты.
- `returnStatusTypes` — array[string (CREATED, RECEIVED, IN_TRANSIT, READY_FOR_PICKUP, PICKED, LOST, EXPIRED, CANCELLED, FULFILMENT_RECEIVED, PREPARED_FOR_UTILIZATION, NOT_IN_DEMAND, UTILIZED…)]. Статусы передачи возвратов, которые нужны в отчете. Если их не указать, вернется информация по всем возвратам.

## Ответы

**200** — В ответ приходит идентификатор, который позволяет узнавать статус генерации и скачать готовый отчет.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  - `reportId` — string **обязательный**. Идентификатор, который понадобится для отслеживания статуса генерации и получения готового отчета или документа.
  - `estimatedGenerationTime` — integer<int64> **обязательный**. Ожидаемая продолжительность генерации в миллисекундах.

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
