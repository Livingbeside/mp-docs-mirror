---
title: Список товаров, находящихся в карантине по цене в кабинете
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/price-quarantine
operation_id: getBusinessQuarantineOffers
tags:
  - price-quarantine
  - dbs
  - fby
  - fbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: c0b889f42953e9b9
---

# Список товаров, находящихся в карантине по цене в кабинете

`POST /v2/businesses/{businessId}/price-quarantine`

{% include notitle [access](../../_auto/method_scopes/getBusinessQuarantineOffers.md) %} Возвращает список товаров, которые находятся в карантине по цене, установленной для всех магазинов кабинета. Проверьте цену каждого из товаров, который попал в карантин. Если ошибки нет и цена правильная, подтвердите ее с помощью запроса [POST v2/businesses/{businessId}/price-quarantine/confirm](../../reference/price-quarantine/confirmBusinessPrices.md). Если цена в самом деле ошибочная, установите верную с помощью запроса [POST v2/businesses/{businessId}/offer-prices/updates](../../reference/prices/updateBusinessPrices.md). {% note info "Что такое карантин?" %} Товар попадает в карантин, если его цена меняется слишком резко или слишком сильно отличается от рыночной. [Подробнее](https://yandex.ru/support/marketplace/assortment/operations/prices.html#quarantine) {% endnote %} В запросе можно использовать фильтры. Результаты возвращаются постранично. {% include notitle [limit](../../_auto/method_limits/getBusinessQuarantineOffers.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `offerIds` — array[string]. Идентификаторы товаров, информация о которых нужна. ⚠️ Не используйте это поле одновременно с фильтрами по статусам карточек, категориям, брендам или тегам. Если вы хотите воспользоваться фильтрами, оставьте поле пустым.
- `cardStatuses` — array[string (HAS_CARD_CAN_NOT_UPDATE, HAS_CARD_CAN_UPDATE, HAS_CARD_CAN_UPDATE_ERRORS, HAS_CARD_CAN_UPDATE_PROCESSING, NO_CARD_NEED_CONTENT, NO_CARD_MARKET_WILL_CREATE, NO_CARD_ERRORS, NO_CARD_PROCESSING, NO_CARD_ADD_TO_CAMPAIGN)]. Фильтр по статусам карточек. [Что такое карточка товара](https://yandex.ru/support/marketplace/assortment/content/index.html)
- `categoryIds` — array[integer<int32>]. Фильтр по категориям на Маркете.
- `vendorNames` — array[string]. Фильтр по брендам.
- `tags` — array[string]. Фильтр по тегам.

## Ответы

**200** — Список товаров в карантине.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список товаров в карантине.
  - `paging` — object. Идентификатор следующей страницы.
    - `nextPageToken` — string. Идентификатор следующей страницы результатов.
  - `offers` — array[object] **обязательный**. Страница списка товаров в карантине.
    - `offerId` — string. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `currentPrice` — object. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} Вместо него используйте `verdicts.params`. {% endnote %} Новая цена.
      - `value` — number **обязательный**. Цена товара.
      - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
    - `lastValidPrice` — object. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} Вместо него используйте `verdicts.params`. {% endnote %} Последняя цена до попадания в карантин.
      - `value` — number **обязательный**. Цена товара.
      - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
    - `verdicts` — array[object]. Причины попадания товара в карантин.
      - `type` — string (PRICE_CHANGE, LOW_PRICE, LOW_PRICE_PROMO). Тип карантина.
      - `params` — array[object] **обязательный**. Цена, из-за которой товар попал в карантин, и значения для сравнения. Конкретный набор параметров зависит от типа карантина.
        - `name` — string (CURRENT_PRICE, LAST_VALID_PRICE, MIN_PRICE, CURRENCY) **обязательный**. Название параметра.
        - `value` — string **обязательный**. Значение параметра.

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
