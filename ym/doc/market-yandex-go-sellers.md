---
title: Продавцам Market Yandex Go
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md"
fetched_at: "2026-09-16T02:26:48Z"
content_sha: 560f7dcd3eb85565
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/market-yandex-go-sellers.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/market-yandex-go-sellers.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Как работать с API Маркета продавцам Market Yandex Go

В документации мы описываем взаимодействие продавцов Маркета с API Яндекс Маркета для продавцов. На этой странице собрали особенности работы для продавцов из Узбекистана, которые размещают товары на Market Yandex Go.

[Справка Market Yandex Go для продавцов](https://yandex.uz/support/market-yandex-go/partner/ru/)

## Вызов методов {#method-call}

В запросах вместо `.ru` используйте `.net`. Формат:

  ```no-highlight translate=no
  <http_method> https://api.partner.market.yandex.net/<version>/<resource>.<format>?<query_parameters>
  ```

[Подробнее о вызове методов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md)

## Методы {#methods}

Если метод недоступен для продавцов Market Yandex Go, это указано в описании.

Пример: [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md)

## Название и описание товара {#name-and-description}

Когда вы добавляете товары в каталог с помощью метода [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md), указывайте значения параметров `name` и `description` на русском языке. Чтобы на витрине они отображались и на другом языке, выполните запрос еще раз, где укажите:

* язык в параметре `language`;
* значения параметров `name` и `description` на указанном языке.

Повторно передавать остальные характеристики товара не нужно.

## Товарный код {#commodity-code}

Передавайте товарные коды и их тип `IKPU_CODE` в параметрах `code` и `type` — метод [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md).

## Цены на товары {#price}

Методы для передачи цен на товары:

* [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) — добавление товаров и передача цен;
* [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md) — передача цен для всех магазинов;
* [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) — передача цен в конкретном магазине.


Указывайте цены в национальной валюте в параметре `value` и саму валюту в `currencyId`. При получении информации, например о заказах, цены возвращаются в той валюте, которая установлена при добавлении товара.

Передавать НДС не нужно (параметр `vat`).

## Коды маркировки {#cis}

В методе [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) передавайте коды маркировки товаров в системе [«ASL BELGISI»](https://aslbelgisi.uz) в параметре `cis`.

## Ярлыки {#labels}

Для продавцов Market Yandex Go приходят другие ярлыки:

{% cut "Ярлык `A9_HORIZONTALLY`" %}

![Изображение горизонтального ярлыка формата A9 для продавцов Market Yandex Go](_images/labels/label-A9-horizontally-uz.png)

{% endcut %}


{% cut "Ярлык `A9`" %}

![Изображение вертикального ярлыка формата A9 для продавцов Market Yandex Go](_images/labels/label-A9-uz.png)

{% endcut %}


{% cut "Ярлык `A7`" %}

![Изображение ярлыка формата A7 для продавцов Market Yandex Go](_images/labels/label-A7-uz.png)

{% endcut %}

[Методы для работы с ярлыками](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md#yarlyki-fbs-i-dbs)
