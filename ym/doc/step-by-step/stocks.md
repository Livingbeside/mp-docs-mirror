---
title: Передача остатков
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/stocks.md"
fetched_at: "2026-09-24T02:13:17Z"
content_sha: 2f378cd8fd86ca9c
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/stocks.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/stocks.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/stocks.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/stocks.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Передача остатков через API

Чтобы Маркет получал актуальную информацию об остатках, используйте один из методов:

* Если в кабинете нет групп складов — [POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md)
* Если в кабинете есть группы складов — [PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)

[Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks).

## Что должно быть готово, прежде чем вы приступите {#before-you-start}

Прежде чем настраивать обработку заказов через API, вам нужно добавить товары на Маркет и настроить обновление ассортимента. Это необязательно делать через API — выберите любой удобный для вас способ. Все нужные инструкции есть в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/assortment/index.html).

## Как устроена передача остатков {#details}

Маркету важно знать, сколько товаров осталось на складе магазина — иначе может получиться, что покупатель оформит заказ, а товара не окажется. Исключение — модели FBY и LaaS, потому что товары хранятся на складе Маркета и он сам может их пересчитать.

Чтобы передавать остатки правильно, обязательно прочтите [статью в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/assortment/operations/stocks.html). Все общие правила передачи остатков распространяются и на API тоже.

{% note info "Можно ли использовать одновременно API и другие способы передачи остатков?" %}

Да, вы можете передавать остатки по этой инструкции с помощью API и в кабинете через YML или через Excel-файлы.

{% endnote %}

## Разработка интеграции {#getting-it-done}

### Если в кабинете нет групп складов {#no-warehouse-groups}

1. Получите идентификаторы складов — [POST v3/businesses/{businessId}/warehouses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/warehouses/getPartnerWarehouses.md).
2. Передайте остатки — [POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md). В запросе укажите ваш SKU, идентификатор склада и значение остатков.
3. При необходимости проверьте актуальные остатки — [POST v3/businesses/{businessId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/getStocksOnPartnerWarehouses.md).

### Если в кабинете есть группы складов {#with-warehouse-groups}

С помощью запроса [PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md) можно передавать остатки в любой момент.

Каждая запись включает:

* Ваш SKU товара, для которого нужно обновить остатки.
* Дату и время — момент, по состоянию на который новое значение актуально.
* Само значение остатков.

### Как проверить работоспособность интеграции {#check}

1. Скройте товары с помощью [POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md).
2. Выполните запрос на передачу остатков — [POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md) или [PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md).
3. Возобновите показ скрытых товаров — [POST v2/campaigns/{campaignId}/hidden-offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md).

### Какое число передавать {#count}

Остаток товара — это число единиц, **доступных для заказа на Маркете**.

Когда покупатель делает заказ, число доступных товаров уменьшается, — поэтому и остатки тоже. Например, если было 20 и кто-то заказал 2 единицы, остаток составит 18.

{% note info "Учитываются продажи и на Маркете, и вне Маркета" %}

Неважно, где куплен товар: на Маркете или, например, прямо в офлайн-магазине. В любом случае сразу уменьшайте остаток товара.

{% endnote %}

Например:

#|
||**Событие**|**Изменение остатков**||
||На склад привезли 10 единиц нового товара|0 → 10||
||Покупатель заказал 2 единицы на Маркете|10 → 8||
||Поставщик привез еще 10 штук|8 → 18||
||Посетитель [офлайн-магазина](*warehouse) купил 3 штуки|18 → 15||
|#


## Как передавать остатки для группы складов {#warehouse-group}

Передавайте остатки только для **одного любого склада**. Информация для остальных складов в этой группе обновится автоматически.

[*warehouse]: Подразумевается, что офлайн-магазин продает с **того же склада**, что и магазин на Маркете.
