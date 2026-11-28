---
title: Таблицы размеров
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/size-tables.md"
fetched_at: "2026-11-28T02:53:58Z"
content_sha: 9d8c4c4b9110a069
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.71.0
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/size-tables.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/size-tables.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/size-tables.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/size-tables.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22349463
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt?revision=r22349463

# Таблицы размеров

Таблица размеров показывает покупателю, какому размеру в других размерных сетках и каким обмерам соответствует размер товара. Ее можно указать товарам с размером, например одежде и обуви.

Таблица относится не к категории, а к размерной характеристике товара, например к размеру одежды или обуви. Поэтому одну таблицу можно указывать товарам всех категорий с той же размерной характеристикой.

Колонки таблицы — это размерные сетки (например, RU, EU, INT) и обмеры (например, обхват груди, длина стопы). Каждая строка описывает один размер: его значения во всех сетках и обмерах.

Можно использовать готовую таблицу Маркета или создать свою.

## Подобрать готовую таблицу {#suggest}

1. Подберите таблицы для категории товара с помощью [POST v2/businesses/{businessId}/size-tables/suggest](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/suggestContentSizeTables.md). Подбор можно уточнить брендом и полом.

      В ответ вы получите:

      * подходящие таблицы: таблицы Маркета (`STANDARD`) и таблицы, которые вы создали (`CUSTOM`);
      * идентификатор размерной характеристики категории в поле `result.sizeParameterId`. Он понадобится, чтобы создать свою таблицу.

2. Чтобы посмотреть содержимое таблиц, получите их по идентификаторам с помощью [POST v2/businesses/{businessId}/size-tables](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeTables.md).

## Создать свою таблицу {#create}

1. Передайте `sizeParameterId` в [POST v2/businesses/{businessId}/size-tables/charts](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeCharts.md). В ответе вернутся размерные сетки и обмеры, которые можно использовать в таблице. Для каждой из них есть:

      * идентификатор `sizeChartId` и название;
      * признак обязательности `required`. В таблице должна быть хотя бы одна обязательная сетка;
      * справочник значений `sizeValues`, если это стандартная размерная сетка Маркета.

2. Создайте таблицу с помощью [POST v2/businesses/{businessId}/size-tables/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/createContentSizeTables.md). В каждой строке передайте по одной ячейке на сетку или обмер. Остальные требования к таблице описаны в справке метода.

      Для каждой созданной таблицы в ответе вернется ее идентификатор `sizeTableId`.

3. Чтобы изменить таблицу, передайте ее полное содержимое в [POST v2/businesses/{businessId}/size-tables/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateContentSizeTables.md). Изменять можно только свои таблицы: у них в ответе [POST v2/businesses/{businessId}/size-tables](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeTables.md) указано `editable: true`.

## Указать таблицу и размер в карточке товара {#offer-card}

1. Получите характеристики категории товара с помощью [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md). У категорий с таблицами размеров в списке есть:

      * таблица размеров (`id: 73979829`);
      * размерная сетка, в которой указан размер товара (`id: 73979830`);
      * размерная характеристика категории. Ее идентификатор совпадает с `sizeParameterId`.

      Для каждой характеристики в ответе есть тип значения и допустимые значения.

2. Передайте характеристики с помощью [POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md):

      * в характеристике `73979829` укажите идентификатор таблицы в `value`;
      * в характеристике `73979830` укажите `sizeChartId` сетки, в которой задан размер товара, в `value`;
      * в размерной характеристике укажите размер товара в этой сетке. Для стандартной сетки Маркета передайте в `valueId` значение из ее справочника, `sizeValueId` из ответа [POST v2/businesses/{businessId}/size-tables/charts](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getContentSizeCharts.md). Для остальных сеток передайте размер текстом в `value`.

      Сетку и размер передавайте вместе. Размер должен быть в выбранной сетке таблицы.

## Какую таблицу Маркет применит к товару {#resolve}

Ваша таблица применяется к товару, только если она указана в характеристике `73979829`.

Если таблица в карточке не указана или указана таблица Маркета, Маркет выбирает таблицу сам среди своих таблиц для пола товара. Пол берется из характеристики товара, а если он не указан, используется пол по умолчанию для категории.

1. Если у товара указан бренд и для этого бренда есть таблица, выбирается брендовая таблица. Иначе выбирается стандартная.
2. Из подходящих таблиц выбирается та, в которой есть сетка из характеристики `73979830`. Если эта сетка есть в нескольких таблицах и одна из них указана в карточке, применяется указанная. Если сетки нет ни в одной таблице, применяется таблица Маркета по умолчанию.

Размер товара Маркет ищет в колонке этой сетки: в стандартной сетке по значению справочника, в остальных по тексту. Если сетки нет в таблице или размера нет в сетке, в карточке появится ошибка.

Если таблицу изменить, новое содержимое применится ко всем товарам, которым она указана. Передавать товары повторно не нужно.

{% note tip "Также прочитайте инструкции" %}

* [Изменение категорийных характеристик](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/content-change.md)
* [Передача значений характеристики](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/parameter-values.md)

{% endnote %}
