---
title: Отчет по остаткам на складах
api: yandex-market
method: POST
path: /v2/reports/stocks-on-warehouses/generate
operation_id: generateStocksOnWarehousesReport
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
content_sha: a3312e54de2b5b54
---

# Отчет по остаткам на складах

`POST /v2/reports/stocks-on-warehouses/generate`

{% include notitle [access](../../_auto/method_scopes/generateStocksOnWarehousesReport.md) %} Запускает генерацию отчета по остаткам на складах. [Что это за отчет](https://yandex.ru/support/marketplace/ru/storage/logistics#remains-history) {% note warning "Когда использовать этот метод" %} Метод актуален: * для моделей FBY и LaaS; * для моделей FBS, DBS и Экспресс, если в кабинете есть группы складов. Если в кабинете нет групп складов и вы работаете с моделями FBS, DBS или Экспресс, используйте метод [POST v3/businesses/{businessId}/reports/stocks/generate](../../reference/reports/generateStocksReport.md). [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks). {% endnote %} **Какая информация вернется:** * Для моделей FBY и LaaS, если указать `campaignId`, — об остатках на складах Маркета. * Для остальных моделей, если указать `campaignId`, — об остатках на соответствующем складе магазина. * Для остальных моделей, если указать `businessId`, — об остатках на всех складах магазинов в кабинете, кроме FBY и LaaS. Используйте фильтр `campaignIds`, чтобы указать определенные магазины. ⚠️ Не передавайте одновременно `campaignId` и `businessId`. Узнать статус генерации и получить ссылку на готовый отчет можно с помощью запроса [GET v2/reports/info/{reportId}](../../reference/reports/getReportInfo.md). {% list tabs %} - Склад Маркета {% include notitle [reports](../../_auto/reports/stocks/stocks_on_warehouses.md) %} - Склад магазина {% include notitle [reports](../../_auto/reports/offers/mass/mass_shared_stocks_business_csv_config.md) %} - Все склады магазинов в кабинете, кроме FBY и LaaS {% include notitle [reports](../../_auto/reports/offers/stocks_business_config.md) %} {% endlist %} {% include notitle [limit](../../_auto/method_limits/generateStocksOnWarehousesReport.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `format` | query | string (FILE, CSV, JSON) | нет | Формат отчета или документа. |

## Запрос

**Тело запроса** (`application/json`):

- `campaignId` — integer<int64>. {% note warning "Для моделей DBS, FBS и Экспресс параметр скоро станет недоступен" %} Для получения информации об остатках на складе магазина передайте `businessId` и идентификатор нужного магазина в `campaignIds`. {% endnote %}
- `businessId` — integer<int64>. **Только для моделей DBS, FBS и Экспресс** Идентификатор кабинета, по магазинам которого нужно сформировать отчет (кроме моделей FBY и LaaS).
- `warehouseIds` — array[integer<int64>]. Фильтр по идентификаторам складов (только модели FBY и LaaS). Чтобы узнать идентификатор, воспользуйтесь запросом [GET v2/warehouses](../../reference/warehouses/getFulfillmentWarehouses.md).
- `reportDate` — string<date>. Фильтр по дате (для моделей FBY и LaaS). В отчет попадут данные за **предшествующий** дате день. Формат даты: `ГГГГ-ММ-ДД`.
- `categoryIds` — array[integer<int32>]. Фильтр по категориям на Маркете (кроме моделей FBY и LaaS).
- `hasStocks` — boolean. Фильтр по наличию остатков (кроме моделей FBY и LaaS).
- `campaignIds` — array[integer<int64>]. Фильтр по магазинам для отчета по кабинету (кроме моделей FBY и LaaS). Передавайте вместе с `businessId`.

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
