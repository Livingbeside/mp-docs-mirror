---
title: Отчет по стоимости услуг
api: yandex-market
method: POST
path: /v2/reports/united-marketplace-services/generate
operation_id: generateUnitedMarketplaceServicesReport
tags:
  - reports
  - fby
  - dbs
  - fbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 5c4160fff16912d1
---

# Отчет по стоимости услуг

`POST /v2/reports/united-marketplace-services/generate`

{% include notitle [access](../../_auto/method_scopes/generateUnitedMarketplaceServicesReport.md) %} Запускает генерацию отчета по стоимости услуг за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/accounting/transactions#reports) Тип отчета зависит от того, какие поля заполнены в запросе: |**Тип отчета** |**Какие поля нужны** | |-----------------------------|---------------------------------| |По дате начисления услуги |`dateFrom` и `dateTo` | |По дате формирования акта |`year` и `month` | Заказать отчеты обоих типов одним запросом нельзя. Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](../../reference/reports/getReportInfo.md). {% include notitle [reports](../../_auto/reports/united/services/generator/united_marketplace_services.md) %} {% include notitle [limit](../../_auto/method_limits/generateUnitedMarketplaceServicesReport.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `format` | query | string (FILE, CSV, JSON) | нет | Формат отчета или документа. |
| `language` | query | string (RU, EN) | нет | Язык отчета или документа. |

## Запрос

**Тело запроса** (`application/json`):

- `businessId` — integer<int64> **обязательный**. Идентификатор кабинета. {% if audience == "partner" %}Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %}
- `dateTimeFrom` — string<date-time>. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} Вместо него используйте `dateFrom`. {% endnote %} Начало периода, включительно.
- `dateTimeTo` — string<date-time>. {% note warning "Параметр устарел и будет отключен 12.10.2026." %} Вместо него используйте `dateTo`. {% endnote %} Конец периода, включительно. Максимальный период — 3 месяца.
- `dateFrom` — string<date>. Начало периода, включительно. Формат даты: `ГГГГ-ММ-ДД`.
- `dateTo` — string<date>. Конец периода, включительно. Максимальный период — 3 месяца. Формат даты: `ГГГГ-ММ-ДД`.
- `yearFrom` — integer<int32>. Начальный год формирования акта.
- `monthFrom` — integer<int32>. Начальный номер месяца формирования акта.
- `yearTo` — integer<int32>. Конечный год формирования акта.
- `monthTo` — integer<int32>. Конечный номер месяца формирования акта.
- `placementPrograms` — array[string (FBS, FBY, DBS, LAAS)]. Список моделей, которые нужны в отчете.
- `inns` — array[string]. Список ИНН, которые нужны в отчете.
- `campaignIds` — array[integer<int64>]. Список идентификаторов кампании тех магазинов, которые нужны в отчете.

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

**404** — Запрашиваемый ресурс не найден. [Подробнее об ошибке](../../concepts/error-codes.md#404)

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
