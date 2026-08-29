---
title: Готовые ярлыки‑наклейки на все коробки в нескольких заказах
api: yandex-market
method: POST
path: /v2/reports/documents/labels/generate
operation_id: generateMassOrderLabelsReport
tags:
  - reports
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 045536f139d76e0c
---

# Готовые ярлыки‑наклейки на все коробки в нескольких заказах

`POST /v2/reports/documents/labels/generate`

{% include notitle [access](../../_auto/method_scopes/generateMassOrderLabelsReport.md) %}

Запускает генерацию PDF-файла с ярлыками для переданных заказов. Подробно о том, зачем они нужны и как выглядят, рассказано [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/orders/fbs/packaging/marking.html).

Чтобы на ярлыке отображался внешний идентификатор заказа, передайте его в методе [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](../../reference/orders/updateExternalOrderId.md).

Узнать статус генерации и получить ссылку на готовый файл можно с помощью запроса [GET v2/reports/info/{reportId}](../../reference/reports/getReportInfo.md).

{% include notitle [limit](../../_auto/method_limits/generateMassOrderLabelsReport.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `format` | query | string (A9_HORIZONTALLY, A9, A7, A4) | нет | Настройка размещения ярлыков на странице. Если параметра нет, возвращается PDF с ярлыками формата :no-translate[A7]. |

## Запрос

**Тело запроса** (`application/json`):

- `businessId` — integer<int64> **обязательный**. Идентификатор кабинета. {% if audience == "partner" %}Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %}
- `orderIds` — array[integer<int64>] **обязательный**. Список идентификаторов заказов.
- `sortingType` — string (SORT_BY_GIVEN_ORDER, SORT_BY_ORDER_CREATED_AT). Тип сортировки ярлыков в файле.

## Ответы

**200** — В ответ приходит идентификатор, который позволяет узнавать статус генерации и скачать готовый файл. Если при генерации не удалось найти часть заказов, в ответе на запрос получения готового файла вернется подстатус `RESOURCE_NOT_FOUND`.

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
