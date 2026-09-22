---
title: Управление акциями
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/promos.md"
fetched_at: "2026-09-22T02:26:26Z"
content_sha: 7752deebd7765ef5
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/promos.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/promos.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/promos.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/promos.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Управление акциями

API Маркета позволяет получать информацию об акциях Маркета и принимать в них участие.

## Добавить товары в акцию {#add-goods}

{% note tip "Вы уже знаете идентификаторы списка акций и товаров" %}

Пропустите шаги их получения.

{% endnote %}

<!-- source: ru/_includes/mermaid/promo-add-goods.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    rect rgb(251, 243, 232)
        note right of Merchant: Получение списка акций
        Merchant ->>+ Market: Идентификатор кабинета<br>POST v2/businesses/{businessId}/promos
        Market -->> Merchant: OK: текущие и будущие акции Маркета.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Получение списка товаров, которые могут участвовать в акции
        Merchant ->>+ Market: Идентификатор акции<br>POST v2/businesses/{businessId}/promos/offers
        Market -->> Merchant: OK: товары, которые могут участвовать в акции.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Добавление товаров в акцию
        Merchant ->>+ Market: Идентификатор акции и товары, которые нужно добавить<br>POST v2/businesses/{businessId}/promos/offers/update
        Market ->> Market: Добавляет<br>товары в акцию.
        Market -->>- Merchant: OK: результат добавления товаров в акцию.
    end

```
<!-- endsource: ru/_includes/mermaid/promo-add-goods.md -->

1. Получите список акций Маркета с помощью запроса [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md).
2. Передайте идентификатор акции в запросе [POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md), чтобы узнать, какие товары могут участвовать в акции.
3. Выполните запрос [POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md), где передайте идентификатор акции и товары, которые необходимо добавить.

## Изменить цену товаров, которые уже добавлены в акцию {#change-price}

{% note tip "Вы уже знаете идентификаторы списка акций и товаров" %}

Пропустите шаги их получения.

{% endnote %}

<!-- source: ru/_includes/mermaid/promo-change-price.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    rect rgb(251, 243, 232)
        note right of Merchant: Получение списка акций
        Merchant ->>+ Market: Идентификатор кабинета<br>POST v2/businesses/{businessId}/promos
        Market -->> Merchant: OK: текущие и будущие акции Маркета.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Получение списка товаров, которые добавлены в акцию
        Merchant ->>+ Market: Идентификатор акции<br>и параметр statusType со значением MANUALLY_ADDED<br>POST v2/businesses/{businessId}/promos/offers
        Market -->> Merchant: OK: товары, которые добавлены в акцию.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Изменение цен на товары в акции
        Merchant ->>+ Market: SKU товаров и их новые цены<br>POST v2/businesses/{businessId}/promos/offers/update
        Market ->> Market: Изменяет цены<br>на товары в акции.
        Market -->>- Merchant: OK: результат обновления цен.
    end

```
<!-- endsource: ru/_includes/mermaid/promo-change-price.md -->

1. Получите список акций Маркета с помощью запроса [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md).
2. Передайте идентификатор акции и параметр `statusType` со значением `MANUALLY_ADDED` в запросе [POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md), чтобы узнать, какие товары добавлены в акцию.
3. Передайте SKU товаров и их новые цены — запрос [POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md).

## Удалить товары из акции {#delete-goods}

{% note tip "Вы уже знаете идентификаторы списка акций и товаров" %}

Пропустите шаги их получения.

{% endnote %}

<!-- source: ru/_includes/mermaid/promo-delete-goods.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    rect rgb(251, 243, 232)
        note right of Merchant: Получение списка акций
        Merchant ->>+ Market: Идентификатор кабинета<br>POST v2/businesses/{businessId}/promos
        Market -->> Merchant: OK: текущие и будущие акции Маркета.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Получение списка товаров, которые добавлены в акцию
        Merchant ->>+ Market: Идентификатор акции<br>и параметр statusType со значением MANUALLY_ADDED<br>POST v2/businesses/{businessId}/promos/offers
        Market -->> Merchant: OK: товары, которые добавлены в акцию.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Удаление товаров из акции
        Merchant ->>+ Market: Параметр deleteAllOffers со значением true<br>или SKU товаров в параметре offerIds<br>POST v2/businesses/{businessId}/promos/offers/delete
        Market ->> Market: Удаляет<br>товары из акции.
        Market -->>- Merchant: OK: результат удаления товаров.
    end

```
<!-- endsource: ru/_includes/mermaid/promo-delete-goods.md -->

1. Получите список акций Маркета с помощью запроса [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md).
2. Передайте идентификатор акции и параметр `statusType` со значением `MANUALLY_ADDED` в запросе [POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md), чтобы узнать, какие товары добавлены в акцию.
3. Выполните запрос [POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md), чтобы удалить из акции:

    * все товары — параметр `deleteAllOffers` со значением `true`;
    * некоторые товары — параметр `offerIds`.

## Посмотреть результаты участия в акции {#promo-results}

Вы можете скачать отчет со всеми заказами, в которых есть проданные по акции товары. О том, как получать отчеты, читайте в [пошаговой инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/reports.md).
