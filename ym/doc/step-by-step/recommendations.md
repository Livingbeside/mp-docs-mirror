---
title: Рекомендации по карточкам
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/recommendations.md"
fetched_at: "2026-09-04T01:57:47Z"
content_sha: 4d015ce8babcbb33
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/recommendations.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/recommendations.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/recommendations.md
  - href: ru/step-by-step/recommendations.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Рекомендации Маркета по карточкам

Иногда в ответ на [POST v2/businesses/{businessId}/offer-cards](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getOfferCardsContentStatus.md) вы будете получать **рекомендации** по заполнению карточек в поле `recommendations`.

Посмотрите тип полученной рекомендации в поле `recommendations` → `type`. Найдите этот тип в документации и посмотрите, какие поля товара относятся к рекомендации такого типа:

{% list tabs %}

- Основные параметры товара

  1. Посмотрите в документации, в чем заключается смысл рекомендации и какой параметр нужно изменить или заполнить.
  2. Отредактируйте параметр с помощью запроса [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md).

- Категорийные характеристики товара

  1. Посмотрите в документации, в чем заключается смысл рекомендации.
  2. Сделайте запрос [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  3. Из ответа отберите характеристики, у которых в массиве `recommendationTypes` есть нужный тип. Например, если вы получили рекомендацию типа `MAIN`, вам нужны характеристики, имеющие пометку `MAIN` в `recommendationTypes`.
  4. Передайте значения характеристик с помощью запроса [POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md).

{% endlist %}

{% note tip "Также прочитайте инструкции" %}

* [Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)
* [Изменение категорийных характеристик](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/content-change.md)
* [Управление товарами в архиве](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-archive.md)

{% endnote %}
