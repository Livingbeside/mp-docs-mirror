---
title: Рекомендации Маркета, касающиеся цен
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/offers/recommendations
operation_id: getOfferRecommendations
tags:
  - offers
  - dbs
  - fby
  - fbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: dd646befdd1f0ee2
---

# Рекомендации Маркета, касающиеся цен

`POST /v2/businesses/{businessId}/offers/recommendations`

{% include notitle [access](../../_auto/method_scopes/getOfferRecommendations.md) %} Метод возвращает рекомендации нескольких типов. 1. Порог для привлекательной цены. 2. Оценка привлекательности цен на витрине. Рекомендации показывают, какие цены нужно установить, чтобы привлечь покупателя. В запросе можно использовать фильтры. Результаты возвращаются постранично. {% include notitle [limit](../../_auto/method_limits/getOfferRecommendations.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `offerIds` — array[string]. Идентификаторы товаров, информация о которых нужна. ⚠️ Не используйте это поле одновременно с остальными фильтрами. Если вы хотите воспользоваться фильтрами, оставьте поле пустым.
- `competitivenessFilter` — string (OPTIMAL, AVERAGE, LOW). Фильтр, выводящий товары, с привлекательными, умеренными и непривлекательными ценами.

## Ответы

**200** — Список товаров с рекомендациями.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Список товаров с рекомендациями.
  - `paging` — object. Идентификатор следующей страницы.
    - `nextPageToken` — string. Идентификатор следующей страницы результатов.
  - `offerRecommendations` — array[object] **обязательный**. Страница списка товаров.
    - `offer` — object. Информация о состоянии цен.
      - `offerId` — string. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
      - `price` — object. Цена товара в каталоге.
        - `value` — number **обязательный**. Цена товара.
        - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
      - `competitiveness` — string (OPTIMAL, AVERAGE, LOW). Привлекательность цены на товар.
      - `shows` — integer<int64>. Количество показов карточки товара за последние 7 дней.
    - `recommendation` — object. Рекомендации.
      - `offerId` — string. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
      - `competitivenessThresholds` — object. Максимальные значения цены, при которых она является привлекательной или умеренной.
        - `optimalPrice` — object. Максимальная привлекательная цена.
          - `value` — number **обязательный**. Цена товара.
          - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.
        - `averagePrice` — object. Максимальная умеренная цена.
          - `value` — number **обязательный**. Цена товара.
          - `currencyId` — string (RUR, USD, EUR, UAH, AUD, GBP, BYR, BYN, DKK, ISK, KZT, CAD…) **обязательный**. Валюта.

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
