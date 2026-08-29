---
title: Настройки кабинета
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/settings
operation_id: getBusinessSettings
tags:
  - businesses
  - dbs
  - fbs
  - fby
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: ef64ed1588dd6762
---

# Настройки кабинета

`POST /v2/businesses/{businessId}/settings`

{% include notitle [access](../../_auto/method_scopes/getBusinessSettings.md) %}

Возвращает информацию о настройках кабинета, идентификатор которого указан в запросе.

{% include notitle [limit](../../_auto/method_limits/getBusinessSettings.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Ответы

**200** — Настройки кабинета.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о кабинете и его настройках.
  - `info` — object. Базовая информация о кабинете.
    - `id` — integer<int64>. Идентификатор кабинета. {% if audience == "partner" %}Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %}
    - `name` — string. Название бизнеса.
  - `settings` — object. Настройки на уровне кабинета.
    - `onlyDefaultPrice` — boolean. Управление ценами на товары: * `false` — можно установить цену, которая действует: * во всех магазинах кабинета — [POST v2/businesses/{businessId}/offer-prices/updates](../../reference/prices/updateBusinessPrices.md); * в конкретном магазине — [POST v2/campaigns/{campaignId}/offer-prices/updates](../../reference/prices/updatePrices.md). * `true` — можно установить только цену, которая действует во всех магазинах кабинета, — [POST v2/businesses/{businessId}/offer-prices/updates](../../reference/prices/updateBusinessPrices.md).
    - `currency` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…). Валюта [в кабинете продавца на Маркете](https://partner.market.yandex.ru/).
  - `subscriptionLevel` — string (NONE, LIGHT, MEDIUM). Уровень подписки кабинета. Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription).
  - `traits` — array[string (MARKET_YANDEX_GO)]. Свойства кабинета.

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
