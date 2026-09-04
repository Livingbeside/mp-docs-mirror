---
title: Пагинация в запросах
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/pagination.md"
fetched_at: "2026-09-04T01:57:42Z"
content_sha: b68d62f8fdd41370
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/pagination.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/pagination.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/pagination.md
  - href: ru/concepts/pagination.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Пагинация в запросах к API Яндекс Маркета для продавцов

Некоторые запросы возвращают результат не целиком, а постранично. Чтобы получить результат полностью, выполните несколько последовательных запросов — в каждом новом запросе передавайте параметр со следующей страницей результатов.

{% note warning "Устаревший тип пагинации" %}

Некоторые методы поддерживают пагинацию с номером страницы (параметр `page`). Этот тип пагинации устарел — не используйте его. Если в методе доступны оба типа пагинации, используйте `pageToken`.

{% endnote %}

## Как получить все страницы результата {#page-token}

Примеры методов с пагинацией по `pageToken`:

* [POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md)
* [POST v2/campaigns/{campaignId}/offer-prices](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)
* [GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)
* [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

Чтобы получить результат полностью:

1. Выполните запрос, где:

   * Не передавайте `pageToken`.
   * При желании передайте `limit`. В спецификации каждого метода для параметра `limit` указаны значения `minimum`, `maximum` и `default`. Если не передать параметр, будет использовано значение по умолчанию.

   {% note warning "Автоматическое уменьшение `limit`" %}

   Некоторые методы автоматически уменьшают переданное значение `limit` до `maximum`, если оно превышает допустимый максимум — это указано в описании параметра `limit` таких методов.

   Примеры методов:
      * [GET v2/campaigns/{campaignId}/returns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturns.md)
      * [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

   {% endnote %}

   В ответе вернется параметр `paging`.

2. Если в `paging` вернулся параметр `nextPageToken`, значит, есть следующая страница результата. Повторите запрос, где передайте значение `nextPageToken` в параметре `pageToken`.

   {% note warning "Значение  параметра `nextPageToken`" %}

   Это не номер страницы, а строка, которую нужно передать в запросе.

   {% endnote %}

   Если параметра нет, то вернулась последняя страница. Больше запросов делать **не нужно**.

3. Продолжайте выполнять запросы, пока возвращается `nextPageToken`.
