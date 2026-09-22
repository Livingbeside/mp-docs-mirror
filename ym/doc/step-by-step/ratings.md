---
title: Индекс качества
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/ratings.md"
fetched_at: "2026-09-22T02:26:32Z"
content_sha: 13308d319c7adbd5
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/ratings.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/ratings.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/ratings.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/ratings.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Индекс качества

Через API можно узнать:

* значение индекса качества магазинов и его составляющие;
* информацию по заказам, которые повлияли на индекс качества.

Подробнее об индексе качества читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/quality/score/).

<!-- source: ru/_includes/mermaid/ratings.md -->
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
        note right of Merchant: Получение значения индекса качества
        Merchant ->>+ Market: Идентификаторы кампаний<br>POST v2/businesses/{businessId}/ratings/quality
        Market -->> Merchant: OK: значение индекса качества магазинов и его составляющие.
    end

    rect rgb(251, 243, 232)
        note right of Merchant: Получение заказов, которые повлияли на индекс качества
        Merchant ->>+ Market: Идентификатор кампании<br>POST v2/campaigns/{campaignId}/ratings/quality/details
        Market -->> Merchant: OK: список заказов, которые повлияли на индекс качества.
    end

```
<!-- endsource: ru/_includes/mermaid/ratings.md -->

1. Чтобы узнать значение индекса качества, передайте идентификаторы кампаний в запросе [POST v2/businesses/{businessId}/ratings/quality](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatings.md).
2. Получить информацию по заказам, которые повлияли на индекс качества магазина, можно с помощью запроса [POST v2/campaigns/{campaignId}/ratings/quality/details](https://yandex.ru/dev/market/partner-api/doc/ru/reference/ratings/getQualityRatingDetails.md).
