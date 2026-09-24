---
title: Архив товаров
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-archive.md"
fetched_at: "2026-09-24T02:13:17Z"
content_sha: 52a01ce6ce47a2a5
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/assortment-archive.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-archive.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/assortment-archive.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-archive.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Управление товарами в архиве

Вы можете помещать товары в архив, чтобы они скрылись с витрин во всех магазинах.

{% note warning "В архив нельзя отправить товар, который хранится на складе Маркета" %}

Вначале такой товар нужно распродать или вывезти.

{% endnote %}

1. Для архивации товаров используйте запрос [POST v2/businesses/{businessId}/offer-mappings/archive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/addOffersToArchive.md). Если товары не удалось архивировать, они вернутся в ответе запроса.

1. Для просмотра товаров в архиве используйте фильтр `archived` в запросе [POST v2/businesses/{businessId}/offer-mappings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/getOfferMappings.md).

1. Чтобы восстановить товар из архива, используйте запрос [POST v2/businesses/{businessId}/offer-mappings/unarchive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffersFromArchive.md).

{% note tip "Также прочитайте инструкции" %}

* [Добавление и редактирование товаров](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-add-goods.md)
* [Изменение категорийных характеристик](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/content-change.md)
* [Рекомендации Маркета по карточкам](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/recommendations.md)

{% endnote %}
