---
title: Получение возможных решений по возврату
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/returns/decisions
operation_id: getReturnAvailableDecisions
tags:
  - returns
  - dbs
  - fbs
  - express
  - fby
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 0dd363418bcb126e
---

# Получение возможных решений по возврату

`POST /v1/businesses/{businessId}/returns/decisions`

{% include notitle [access](../../_auto/method_scopes/getReturnAvailableDecisions.md) %}

Возвращает список доступных решений по возврату.

{% include notitle [limit](../../_auto/method_limits/getReturnAvailableDecisions.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `campaignId` — integer<int64> **обязательный**. Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями.
- `returnId` — integer<int64> **обязательный**. Идентификатор невыкупа или возврата.

## Ответы

**200** — Возможные решения по возврату.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Возможные решения по возврату.
  - `availableDecisions` — array[object] **обязательный**. Список доступных решений.
    - `decisionType` — string (FAST_REFUND_MONEY, REFUND_MONEY, REFUND_MONEY_INCLUDING_SHIPMENT, REPAIR, REPLACE, SEND_TO_EXAMINATION, DECLINE_REFUND, PARTIAL_MONEY_REFUND, OTHER_DECISION, UNKNOWN) **обязательный**. Решение по возврату: * `FAST_REFUND_MONEY` — вернуть покупателю деньги без возврата товара. * `REFUND_MONEY` — вернуть покупателю деньги за товар. * `REFUND_MONEY_INCLUDING_SHIPMENT` — вернуть покупателю деньги за товар и обратную пересылку. * `REPAIR` — отремонтировать товар. * `REPLACE` — заменить товар. * `SEND_TO_EXAMINATION` — взять товар на экспертизу. * `DECLINE_REFUND` — отказать в возврате. * `PARTIAL_MONEY_REFUND` — частичный возврат денег. * `OTHER_DECISION` — другое решение. * `UNKNOWN` — не указано.
    - `decisionReasonTypes` — array[string (ISSUE_WITH_THE_PRODUCT_WAS_NOT_CONFIRMED, MECHANICAL_DAMAGE, WARRANTY_PERIOD_HAS_EXPIRED, CONFIGURATION_OR_PACKAGING_COMPROMISED, PRODUCT_APPEARANCE_COMPROMISED, WARRANTY_TERMS_VIOLATED, DEVICE_ACTIVATED)]. Возможные причины отказа (только для решения DECLINE_REFUND).
    - `partialCompensationBounds` — object. Пределы суммы частичной компенсации. Заполнено только при `decisionType` = `PARTIAL_MONEY_REFUND`; для остальных типов решений поле отсутствует.
      - `minAmount` — object **обязательный**. Цена товара.
        - `value` — number **обязательный**. Цена товара.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `maxAmount` — object **обязательный**. Цена товара.
        - `value` — number **обязательный**. Цена товара.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `maxPercent` — integer<int64> **обязательный**. Верхний предел доли суммы позиции, которую можно компенсировать (в процентах).

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
