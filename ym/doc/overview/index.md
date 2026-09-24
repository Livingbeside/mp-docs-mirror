---
title: Обзор методов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/overview/index.md"
fetched_at: "2026-09-24T02:13:27Z"
content_sha: 4cf5d6b2c36a72a7
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/overview/index.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/overview/index.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/overview/index.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/overview/index.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Обзор методов

## Методы на уровне кабинета {#businesses}

Часть методов из [списка](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md) — например, управляющие каталогом товаров — работают на уровне **кабинета** вне зависимости от того, какие модели подключены и используются. [Что такое кабинет](https://yandex.ru/support/marketplace/account/introduction.html)

В параметрах пути передается идентификатор кабинета — `businessId`. Пример: `POST v2/businesses/{businessId}/settings`

[Как получить идентификатор кабинета](#get-id)

## Методы на уровне магазина {#campaigns}

Есть методы, которые работают с отдельными **магазинами** внутри кабинета. [Что такое магазин на Маркете](https://yandex.ru/support/marketplace/account/add-shop.html)

Для их вызова необходим идентификатор кампании `campaignId`. Пример: `GET v2/campaigns/{campaignId}/orders/{orderId}`

[Как получить идентификатор кампании](#get-id)

Часть таких методов перечислена в [общем списке](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md), некоторые работают только для определенных моделей размещения:

* [FBY](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fby.md)
* [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md)
* [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md)
* [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md)
* [LaaS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/laas.md)

[Сравнение методов по моделям](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md)

## Методы для получения отчетов {#reports}

Ресурс `reports` позволяет запрашивать и получать отчеты о вашей работе на Маркете. Пример: `POST v2/reports/shows-sales/generate`

В зависимости от типа отчета может потребоваться как `businessId`, так и `campaignId`. [Как получить](#get-id)

Например, чтобы запустить генерацию отчета по оборачиваемости — [POST v2/reports/goods-turnover/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsTurnoverReport.md), необходим идентификатор кампании — `campaignId`.

[Запросы к reports](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md#otchety)

## Справочные методы {#common}

В запросах, которые предоставляют общую информацию, не относящуюся к конкретному бизнесу, не требуются идентификаторы `businessId` или`campaignId`.

| **Общие ресурсы**  | **Информация, которую они возвращают**   |
| ------------------ | ---------------------------------------- |
| `auth`             | данные о Api-Key-токене                  |
| `categories`       | категории Маркета                        |
| `models`           | модели товаров                           |
| `regions`          | как регион представлен в геобазе Маркета |
| `tariffs`          | тарифы Маркета                           |
| `warehouses`       | склады Маркета                           |


## Как получить идентификаторы кабинета и кампании {#get-id}

Чтобы получить идентификаторы `businessId` и `campaignId`, выполните запрос [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md). Он возвращает все идентификаторы, к которым открывает доступ заданный токен авторизации.

Идентификатор кампании можно также найти в кабинете продавца на Маркете — нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:

* блок **Идентификатор кампании**;
* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
