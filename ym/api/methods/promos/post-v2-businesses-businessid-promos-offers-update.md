---
title: Добавление товаров в акцию или изменение их цен
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/promos/offers/update
operation_id: updatePromoOffers
tags:
  - promos
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 741367b41839e8ca
---

# Добавление товаров в акцию или изменение их цен

`POST /v2/businesses/{businessId}/promos/offers/update`

{% include notitle [access](../../_auto/method_scopes/updatePromoOffers.md) %} Добавляет товары в акцию или изменяет цены на товары, которые участвуют в акции. Изменения начинают действовать в течение 4–6 часов. Узнать, применились ли они, можно с помощью параметра `processing` в ответе метода [POST v2/businesses/{businessId}/promos](../../reference/promos/getPromos.md). {% include notitle [limit](../../_auto/method_limits/updatePromoOffers.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `promoId` — string **обязательный**. Идентификатор акции.
- `offers` — array[object] **обязательный**. Товары, которые необходимо добавить в акцию или цены которых нужно изменить.
  - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  - `params` — object. Параметры товара, который участвует в акции.
    - `discountParams` — object. Параметры товара в акции с типом `DIRECT_DISCOUNT` или `BLUE_FLASH`. Обязательный параметр для акций с этими типами.
      - `price` — integer<int64>. Зачеркнутая цена — та, по которой товар продавался до акции. Указывается в рублях. Число должно быть целым.
      - `promoPrice` — integer<int64>. Цена по акции — та, по которой вы хотите продавать товар. Указывается в рублях. Число должно быть целым.

## Ответы

**200** — Результат добавления товаров в акцию или обновления их цен.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Ошибки и предупреждения, которые появились при добавлении товаров в акцию.
  - `rejectedOffers` — array[object]. Изменения, которые были отклонены. Возвращается, только если есть отклоненные изменения.
    - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `reason` — string (OFFER_DOES_NOT_EXIST, OFFER_DUPLICATION, OFFER_NOT_ELIGIBLE_FOR_PROMO, OFFER_PROMOS_MAX_BYTE_SIZE_EXCEEDED, DEADLINE_FOR_FOCUS_PROMOS_EXCEEDED, EMPTY_OLD_PRICE, EMPTY_PROMO_PRICE, MAX_PROMO_PRICE_EXCEEDED, PROMO_PRICE_BIGGER_THAN_MAX, PROMO_PRICE_SMALLER_THAN_MIN, PRICE_TOO_BIG, OLD_PRICE_TOO_BIG) **обязательный**. Причина отклонения изменения: * `OFFER_DOES_NOT_EXIST` — в кабинете нет товара с таким SKU. * `OFFER_DUPLICATION` — один и тот же товар передан несколько раз. * `OFFER_NOT_ELIGIBLE_FOR_PROMO` — товар не подходит под условия акции. * `OFFER_PROMOS_MAX_BYTE_SIZE_EXCEEDED` — товар не добавлен в акцию по техническим причинам. * `DEADLINE_FOR_FOCUS_PROMOS_EXCEEDED` — истек срок добавления товаров в акцию. * `EMPTY_OLD_PRICE` — не указана зачеркнутая цена. * `EMPTY_PROMO_PRICE` — не указана цена по акции. * `MAX_PROMO_PRICE_EXCEEDED` — цена по акции превышает максимально возможную цену для участия в акции. * `PROMO_PRICE_BIGGER_THAN_MAX` — цена по акции больше 95% от зачеркнутой цены. * `PROMO_PRICE_SMALLER_THAN_MIN` — цена по акции меньше 1% от зачеркнутой цены. * `PRICE_TOO_BIG` — слишком большая цена по акции. * `OLD_PRICE_TOO_BIG` — слишком большая зачеркнутая цена.
  - `warningOffers` — array[object]. Изменения, по которым есть предупреждения. Они информируют о возможных проблемах. Информация о товарах обновится. Возвращается, только если есть предупреждения.
    - `offerId` — string **обязательный**. Ваш SKU — идентификатор товара в вашей системе. Правила использования SKU: * У каждого товара SKU должен быть свой. * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге. SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku). {% note warning %} Пробельные символы в начале и конце значения автоматически удаляются. Например, `" SKU123 "` и `"SKU123"` будут обработаны как одинаковые значения. {% endnote %} [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
    - `warnings` — array[object] **обязательный**. Предупреждения, которые появились при добавлении товара в акцию или изменении его цен.
      - `code` — string (DEEP_DISCOUNT_OFFER, CATALOG_PRICE_IS_LOWER_THAN_PROMO, SHOP_PRICES_ARE_LOWER_THAN_PROMO, SHOP_OFFER_NOT_ELIGIBLE_FOR_PROMO) **обязательный**. Предупреждение, которое появилось при добавлении товара: * `DEEP_DISCOUNT_OFFER` — большая разница с ценой в каталоге. Проверьте, нет ли ошибки. * `CATALOG_PRICE_IS_LOWER_THAN_PROMO` — цена, которая действует во всех магазинах, ниже цены по акции. У товара не будет отображаться цена по акции. * `SHOP_PRICES_ARE_LOWER_THAN_PROMO` — цена в отдельном магазине ниже цены по акции. У товара в акции будет отображаться цена в магазине. Для остальных магазинов будет действовать цена по акции. * `SHOP_OFFER_NOT_ELIGIBLE_FOR_PROMO` — товар в отдельном магазине не подходит под условия акции.
      - `campaignIds` — array[integer<int64>]. Идентификаторы кампаний тех магазинов, для которых получены предупреждения. Не возвращается, если предупреждения действуют для всех магазинов в кабинете.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибках при работе с акциями](../../concepts/error-codes#promos)

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
