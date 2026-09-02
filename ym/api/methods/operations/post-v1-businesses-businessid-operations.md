---
title: Получение статусов операций
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/operations
operation_id: getOperations
tags:
  - operations
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 82a63a632c9a2882
---

# Получение статусов операций

`POST /v1/businesses/{businessId}/operations`

{% include notitle [access](../../_auto/method_scopes/getOperations.md) %}

Возвращает статусы запущенных операций по их идентификаторам.

{% include notitle [limit](../../_auto/method_limits/getOperations.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `operationType` — string (ORDER_RECIPIENT_UPDATE, ORDER_DELIVERY_INTERVAL_UPDATE, ORDER_STORAGE_LIMIT_DATE_UPDATE, ORDER_STATUS_UPDATE, RETURN_CANCELLATION) **обязательный**. Тип операции: * `ORDER_RECIPIENT_UPDATE` — изменение данных получателя. * `ORDER_DELIVERY_INTERVAL_UPDATE` — изменение интервала дат доставки. * `ORDER_STORAGE_LIMIT_DATE_UPDATE` — продление срока хранения заказа. * `ORDER_STATUS_UPDATE` — обновление статуса заказа для его отмены. * `RETURN_CANCELLATION` — отмена возврата.
- `operationIds` — array[string] **обязательный**. Список идентификаторов операций.

## Ответы

**200** — Информация об операциях.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация об операциях.
  - `operations` — array[object] **обязательный**. Список операций.
    - `id` — string **обязательный**. Идентификатор операции.
    - `type` — string (ORDER_RECIPIENT_UPDATE, ORDER_DELIVERY_INTERVAL_UPDATE, ORDER_STORAGE_LIMIT_DATE_UPDATE, ORDER_STATUS_UPDATE, RETURN_CANCELLATION) **обязательный**. Тип операции: * `ORDER_RECIPIENT_UPDATE` — изменение данных получателя. * `ORDER_DELIVERY_INTERVAL_UPDATE` — изменение интервала дат доставки. * `ORDER_STORAGE_LIMIT_DATE_UPDATE` — продление срока хранения заказа. * `ORDER_STATUS_UPDATE` — обновление статуса заказа для его отмены. * `RETURN_CANCELLATION` — отмена возврата.
    - `status` — string (IN_PROGRESS, DONE, FAILED) **обязательный**. Статус выполнения операции: * `IN_PROGRESS` — выполняется. * `DONE` — успешно завершена. * `FAILED` — завершена с ошибкой.

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
