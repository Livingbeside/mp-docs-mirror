---
title: Установка цен на товары для всех магазинов
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/offer-prices/updates
operation_id: updateBusinessPrices
tags:
  - prices
  - fby
  - fbs
  - dbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 52342e7a181cae75
---

# Установка цен на товары для всех магазинов

`POST /v2/businesses/{businessId}/offer-prices/updates`

{% include notitle [access](../../_auto/method_scopes/updateBusinessPrices.md) %}

Устанавливает цены, которые действуют во всех магазинах. Чтобы получить рекомендации Маркета, касающиеся цен, выполните запрос [POST v2/businesses/{businessId}/offers/recommendations](../../reference/offers/getOfferRecommendations.md).

При необходимости передавайте НДС с помощью параметра `vat` в запросе [POST v2/campaigns/{campaignId}/offers/update](../../reference/offers/updateCampaignOffers.md).

{% note info "Данные в каталоге обновляются не мгновенно" %}

Это занимает до нескольких минут.

{% endnote %}

{% include notitle [limit](../../_auto/method_limits/updateBusinessPrices.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `offers` — array[object] **обязательный**. Список товаров с ценами. В рамках одного запроса все значения `offerId` должны быть уникальными. Не допускается передача двух объектов с одинаковым `offerId`.
  - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  - `price` — object **обязательный**. Цены.
    - `value` — number **обязательный**. Цена товара.
    - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
    - `discountBase` — number. Зачеркнутая цена. Число должно быть целым. Вы можете указать цену со скидкой от 5 до 99%. Передавайте этот параметр при каждом обновлении цены, если предоставляете скидку на товар.
    - `minimumForBestseller` — number. Минимальная цена товара для попадания в акцию «Бестселлеры Маркета». Подробнее об этом способе участия читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/promos/market/bestsellers#minimum). При передаче цены ориентируйтесь на значение параметра `maxPromoPrice` (максимально возможная цена для участия в акции) в методе [POST v2/businesses/{businessId}/promos/offers](../../reference/promos/getPromoOffers.md). Товар не попадет в акцию с помощью этого способа, если: * Не передать этот параметр. Удалится значение, которое вы указали ранее. * В методе [POST v2/businesses/{businessId}/offer-prices](../../reference/prices/getDefaultPrices.md) для этого товара возвращается параметр `excludedFromBestsellers` со значением `true`. Но товар по-прежнему сможет попасть в акцию через [автоматическое участие](*auto) или [ручное добавление](*updatePromoOffers).

## Ответы

**200** — Маркет принял информацию о новых ценах.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибках при работе с ценами](../../concepts/error-codes#prices)

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

**423** — К ресурсу нельзя применить указанный метод. [Подробнее об ошибке](../../concepts/error-codes.md#423)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
