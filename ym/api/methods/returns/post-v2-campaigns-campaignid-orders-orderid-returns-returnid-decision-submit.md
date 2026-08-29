---
title: Передача решения по возврату
api: yandex-market
method: POST
path: /v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit
operation_id: submitReturnDecision
tags:
  - returns
  - dbs
  - fbs
  - express
  - fby
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 7ddf1817020eaa9e
---

# Передача решения по возврату

`POST /v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit`

{% include notitle [access](../../_auto/method_scopes/submitReturnDecision.md) %}

Позволяет передать список решений по возврату.

{% note info "Перед вызовом метода" %}

Получите список доступных решений — [POST v1/businesses/{businessId}/returns/decisions](../../reference/returns/getReturnAvailableDecisions.md).

{% endnote %}

{% include notitle [limit](../../_auto/method_limits/submitReturnDecision.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |
| `orderId` | path | integer<int64> | да | Идентификатор заказа. |
| `returnId` | path | integer<int64> | да | Идентификатор невыкупа или возврата. |

## Запрос

**Тело запроса** (`application/json`):

- `returnItemDecisions` — array[object] **обязательный**. Решения по товарам в возврате.
  - `returnItemId` — integer<int64> **обязательный**. Идентификатор товара в возврате.
  - `decisionType` — string (FAST_REFUND_MONEY, REFUND_MONEY, REFUND_MONEY_INCLUDING_SHIPMENT, REPAIR, REPLACE, SEND_TO_EXAMINATION, DECLINE_REFUND, PARTIAL_MONEY_REFUND, OTHER_DECISION) **обязательный**. Решение по товару в возврате.
  - `decisionReasonType` — string (ISSUE_WITH_THE_PRODUCT_WAS_NOT_CONFIRMED, MECHANICAL_DAMAGE, WARRANTY_PERIOD_HAS_EXPIRED, CONFIGURATION_OR_PACKAGING_COMPROMISED, PRODUCT_APPEARANCE_COMPROMISED, WARRANTY_TERMS_VIOLATED, DEVICE_ACTIVATED). Причина отказа.
  - `comment` — string. Комментарий к решению. Укажите: * для `REFUND_MONEY_INCLUDING_SHIPMENT`— стоимость обратной пересылки. * для `REPAIR` — когда вы устраните недостатки товара. * для `DECLINE_REFUND` — причину отказа. * для `OTHER_DECISION` — какое решение вы предлагаете.
  - `compensation` — object. Сумма добровольной компенсации по позиции возврата. Указывайте только при `decisionType` = `PARTIAL_MONEY_REFUND`.
    - `value` — number **обязательный**. Цена товара.
    - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.

## Ответы

**200** — Статус выполнения операции.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.

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
