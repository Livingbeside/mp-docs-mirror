---
title: Отчет по охватному продвижению
api: yandex-market
method: POST
path: /v2/reports/banners-statistics/generate
operation_id: generateBannersStatisticsReport
tags:
  - reports
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: e578aaf502e197b7
---

# Отчет по охватному продвижению

`POST /v2/reports/banners-statistics/generate`

{% include notitle [access](../../_auto/method_scopes/generateBannersStatisticsReport.md) %} Запускает генерацию сводного отчета по охватному продвижению. {% if audience == "partner" %}Что это за отчет: [для баннеров](https://yandex.ru/support/marketplace/ru/marketing/advertising-tools/banner#statistics), [для пуш-уведомлений](https://yandex.ru/support/marketplace/ru/marketing/advertising-tools/push-notifications#statistics).{% endif %} Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](../../reference/reports/getReportInfo.md). {% include notitle [reports](../../_auto/reports/incuts/banners_statistics.md) %} {% if audience != "advertiser" %} {% include notitle [tariff-period](../../_includes/common/report-data-period-400-days.md) %} {% endif %} {% include notitle [limit](../../_auto/method_limits/generateBannersStatisticsReport.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `format` | query | string (FILE, CSV, JSON) | нет | Формат отчета или документа. |
| `sourceType` | query | string (SELLER, ADVERTISER) | нет | Признак типа кабинета, от имени которого вызывается метод: {% if audience == "partner" %} - `SELLER` — продавец. {% endif %} - `ADVERTISER` — рекламодатель. {% if audience == "advertiser" %} {% note info "Обязательно указывайте sourceType=ADVERTISER в каждом запросе." %} {% endnote %} {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `businessId` — integer<int64> **обязательный**. Идентификатор кабинета. {% if audience == "partner" %}Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %}
- `dateFrom` — string<date> **обязательный**. Начало периода, включительно. Формат даты: `ГГГГ-ММ-ДД`.
- `dateTo` — string<date> **обязательный**. Конец периода, включительно. Формат даты: `ГГГГ-ММ-ДД`.

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
