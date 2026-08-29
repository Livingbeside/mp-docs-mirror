---
title: Отчет по платежам
api: yandex-market
method: POST
path: /v2/reports/united-netting/generate
operation_id: generateUnitedNettingReport
tags:
  - reports
  - fby
  - dbs
  - fbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: e2b2cc537c321467
---

# Отчет по платежам

`POST /v2/reports/united-netting/generate`

{% include notitle [access](../../_auto/method_scopes/generateUnitedNettingReport.md) %}

Запускает генерацию отчета по платежам за заданный период. [Что это за отчет](https://yandex.ru/support/marketplace/ru/accounting/transactions#all-pay)

Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](../../reference/reports/getReportInfo.md).

Тип отчета зависит от того, какие поля заполнены в запросе:

#|
|| **Тип отчета** | **Какие поля нужны** | **Комментарий** ||
|| О платежах за период | `dateFrom` и `dateTo` |
 В отчет попадают все платежи, которые были выплачены и начислены в выбранный период.

 Пример: если перевод выполнен 31 августа и зачислен 1 сентября, он попадет в отчет за оба месяца.
||
|| О платежном поручении | `bankOrderId` и `bankOrderDateTime` |—||
|| [О баллах Маркета](*баллы_маркета) | `monthOfYear` |—||
|#

Заказать отчеты нескольких типов одним запросом нельзя.

{% include notitle [reports](../../_auto/reports/united/netting/generator/united_netting.md) %}

{% include notitle [limit](../../_auto/method_limits/generateUnitedNettingReport.md) %}

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
- `bankOrderId` — integer<int64>. Номер платежного поручения.
- `bankOrderDateTime` — string<date-time>. Дата платежного поручения.
- `monthOfYear` — object. Месяц, за который нужен отчет о баллах Маркета.
  - `year` — integer<int32> **обязательный**. Год.
  - `month` — integer<int32> **обязательный**. Номер месяца.
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
