---
title: Включение/выключение модели работы склада
api: yandex-market
method: POST
path: /v3/businesses/{businessId}/warehouse/models/status
operation_id: updateWarehouseModelStatus
tags:
  - warehouses
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: a55b7b344f6d5c0e
---

# Включение/выключение модели работы склада

`POST /v3/businesses/{businessId}/warehouse/models/status`

{% include notitle [access](../../_auto/method_scopes/updateWarehouseModelStatus.md) %} Отключает или включает модель работы (FBS, DBS или Экспресс) для указанного склада. После отключения модели товары, которые работают по ней на данном складе, скрываются через 15 минут. После включения они возвращаются на витрину через 15 минут, а если модель была выключена 30 дней или дольше — через 4 часа. {% include notitle [limit](../../_auto/method_limits/updateWarehouseModelStatus.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `partnerWarehouseId` — integer<int64> **обязательный**. Идентификатор склада. Чтобы узнать идентификатор склада, воспользуйтесь запросом [POST v3/businesses/{businessId}/warehouses](../../reference/warehouses/getPartnerWarehouses.md).
- `model` — string (FBS, DBS, EXPRESS) **обязательный**. Модель работы склада.
- `enabled` — boolean **обязательный**. Статус модели работы склада: * `true` — включена. * `false` — отключена.

## Ответы

**200** — Новый статус модели работы склада.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о статусе модели склада.
  - `status` — string (DISABLED_MANUALLY, OTHER) **обязательный**. Статус модели склада: * `DISABLED_MANUALLY` – отключен вами. * `OTHER` – другой статус. Например, модель склада включена или отключена Маркетом.

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
