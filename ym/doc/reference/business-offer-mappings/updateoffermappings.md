---
title: Добавление товаров и изменение информации
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md"
fetched_at: "2026-09-26T02:06:48Z"
content_sha: e0307d8c53248e33
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/business-offer-mappings/updateOfferMappings.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/business-offer-mappings/updateOfferMappings.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/business-offer-mappings/updateOfferMappings.md -->
<div class="openapi">

# Добавление товаров в каталог и изменение информации о них

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/updateOfferMappings.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/business.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/updateOfferMappings.md -->
  
  Добавляет товары в каталог и передает:
  
  * их [листовые категории](*list-categories) на Маркете и категорийные характеристики;
  * основные характеристики;
  * цены на товары в кабинете.
  
  Также объединяет товары на карточке, редактирует и удаляет информацию об уже добавленных товарах, в том числе цены в кабинете и категории товаров.
  
  Список категорий Маркета можно получить с помощью запроса [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md), а характеристики товаров по категориям с помощью [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  {% cut "Добавить новый товар" %}
  
  Передайте его с новым идентификатором, который раньше никогда не использовался в каталоге.
  
  Обязательно укажите параметры: `offerId`, `name`, `marketCategoryId`, `pictures`, `vendor`, `description`.
  
  Старайтесь сразу передать как можно больше информации — она потребуется Маркету для подбора подходящей карточки или создания новой.
  
  Если известно, какой карточке на Маркете соответствует товар, можно сразу указать идентификатор этой карточки (SKU на Маркете) в поле `marketSKU`.
  
  **Для продавцов Market Yandex Go:**
  
  Когда вы добавляете товары в каталог, указывайте значения параметров `name` и `description` на русском языке. Чтобы на витрине они отображались и на другом языке, еще раз выполните запрос `POST v2/businesses/{businessId}/offer-mappings/update`, где укажите:
  
    * язык в параметре `language`;
    * значения параметров `name` и `description` на указанном языке.
  
    Повторно передавать остальные характеристики товара не нужно.
  
  {% endcut %}
  
  {% cut "Изменить информацию о товаре" %}
  
  Передайте новые данные, указав в `offerId` SKU товара в вашей системе.
  
  Поля, в которых ничего не меняется, можно не передавать.
  
  {% endcut %}
  
  {% cut "Удалить переданные ранее параметры товара" %}
  
  В `deleteParameters` укажите значения параметров, которые хотите удалить. Можно передать сразу несколько значений.
  
  Для параметров с типом `string` также можно передать пустое значение.
  
  {% endcut %}
  
  Параметр `offerId` (SKU товара в вашей системе) должен быть **уникальным** для всех товаров, которые вы передаете.
  
  {% note warning "Правила использования SKU" %}
  
  * У каждого товара SKU должен быть свой.
  
  * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.
  
  SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).
  
  {% endnote %}
  
  {% note info "Данные в каталоге обновляются не мгновенно" %}
  
  Это занимает до нескольких минут.
  
  {% endnote %}
  
  <!-- source: ru/_auto/method_limits/updateOfferMappings.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 5 000 товаров в минуту<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 10 000 товаров в минуту</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/updateOfferMappings.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/businesses/{businessId}/offer-mappings/update
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _businessId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор кабинета.
  
  
  Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
  
  ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)
  
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _language_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CatalogLanguageType](#entity-CatalogLanguageType)
  
  Язык, на котором принимаются и возвращаются значения в параметрах `name` и `description`.
  
  Значение по умолчанию: `RU`.
  
  
  Язык:
  
  * `RU` — русский.
  * `UZ` — узбекский.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `UZ`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### CatalogLanguageType {#entity-CatalogLanguageType}
  
  Язык:
  
  * `RU` — русский.
  * `UZ` — узбекский.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RU`, `UZ`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "offerMappings": [
      {
        "offer": {
          "offerId": "example",
          "name": "Ударная дрель Makita HP1630, 710 Вт",
          "marketCategoryId": 0,
          "category": "example",
          "pictures": [
            null
          ],
          "videos": [
            null
          ],
          "manuals": [
            null
          ],
          "vendor": "LEVENHUK",
          "barcodes": [
            null
          ],
          "description": "example",
          "manufacturerCountries": [
            null
          ],
          "weightDimensions": {},
          "vendorCode": "VNDR-0005A",
          "tags": [
            null
          ],
          "shelfLife": {},
          "lifeTime": null,
          "guaranteePeriod": null,
          "customsCommodityCode": "8517610008",
          "commodityCodes": [
            null
          ],
          "certificates": [
            null
          ],
          "boxCount": 1,
          "condition": {},
          "type": "DEFAULT",
          "downloadable": true,
          "adult": true,
          "age": {},
          "params": [
            null
          ],
          "parameterValues": [
            null
          ],
          "basicPrice": {},
          "purchasePrice": {},
          "additionalExpenses": null,
          "firstVideoAsCover": true,
          "deleteParameters": [
            null
          ]
        },
        "mapping": {
          "marketSku": 1
        }
      }
    ],
    "onlyPartnerMediaContent": true
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerMappings_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateOfferMappingDTO](#entity-UpdateOfferMappingDTO)[]
  
  Список товаров, которые нужно добавить или обновить.
  
  {% note warning "Скоро мы уменьшим максимальное количество товаров в запросе" %}
  
  Уже сейчас не передавайте больше 100.
  
  {% endnote %}
  
   
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `500`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "offer": {
        "offerId": "example",
        "name": "Ударная дрель Makita HP1630, 710 Вт",
        "marketCategoryId": 0,
        "category": "example",
        "pictures": [
          "example"
        ],
        "videos": [
          null
        ],
        "manuals": [
          {}
        ],
        "vendor": "LEVENHUK",
        "barcodes": [
          "46012300000000"
        ],
        "description": "example",
        "manufacturerCountries": [
          "Россия"
        ],
        "weightDimensions": {
          "length": 65.55,
          "width": 50.7,
          "height": 20,
          "weight": 1.001
        },
        "vendorCode": "VNDR-0005A",
        "tags": [
          "до 500 рублей"
        ],
        "shelfLife": {
          "timePeriod": 0,
          "timeUnit": "HOUR",
          "comment": "example"
        },
        "lifeTime": null,
        "guaranteePeriod": null,
        "customsCommodityCode": "8517610008",
        "commodityCodes": [
          {}
        ],
        "certificates": [
          "example"
        ],
        "boxCount": 1,
        "condition": {
          "type": "PREOWNED",
          "quality": "PERFECT",
          "reason": "example"
        },
        "type": "DEFAULT",
        "downloadable": true,
        "adult": true,
        "age": {
          "value": 0,
          "ageUnit": "YEAR"
        },
        "params": [
          {}
        ],
        "parameterValues": [
          {}
        ],
        "basicPrice": {},
        "purchasePrice": null,
        "additionalExpenses": null,
        "firstVideoAsCover": true,
        "deleteParameters": [
          "ADDITIONAL_EXPENSES"
        ]
      },
      "mapping": {
        "marketSku": 1
      }
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _onlyPartnerMediaContent_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Будут ли использоваться только переданные вами данные о товарах.
  
  Значение по умолчанию: `false`. Чтобы удалить данные, которые добавил Маркет, передайте значение `true`.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ShopSku {#entity-ShopSku}
  
  Ваш SKU — идентификатор товара в вашей системе.
  
  Правила использования SKU:
  
  * У каждого товара SKU должен быть свой.
  
  * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.
  
  SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).
  
  {% note warning %}
  
  Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.
  
  {% endnote %}
  
  [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### InternalOfferId {#entity-InternalOfferId}
  
  Внутренний идентификатор товара в системах Маркета. Нужен для создания товаров Лавки с отличными offerId и article.
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferName {#entity-OfferName}
  
  Составляйте название по схеме: тип + бренд или производитель + модель + особенности, если есть (например, цвет, размер или вес) и количество в упаковке.
  
  Не включайте в название условия продажи (например, «скидка», «бесплатная доставка» и т. д.), эмоциональные характеристики («хит», «супер» и т. д.). Не пишите слова большими буквами — кроме устоявшихся названий брендов и моделей.
  
  Оптимальная длина — 50–60 символов.
  
  [Рекомендации и правила](https://yandex.ru/support/marketplace/assortment/fields/title.html)
  
  
  **Type**: string
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `256`
  
  _Example:_{.json-schema-reset .json-schema-example} `Ударная дрель Makita HP1630, 710 Вт`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PartnerMarketCategoryId {#entity-PartnerMarketCategoryId}
  
  Идентификатор категории на Маркете, к которой вы относите свой товар.
  
  {% note warning "Всегда указывайте, когда передаете `parameterValues`" %}
  
  Если при изменении характеристик передать `parameterValues` и не указать `marketCategoryId`, характеристики обновятся, но в ответе придет предупреждение (параметр `warnings`).
  
  Если не передать их оба, будет использована информация из устаревших параметров `params` и `category`, а `marketCategoryId` будет определен автоматически.
  
  {% endnote %}
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferCategory {#entity-OfferCategory}
  
  _Deprecated_{.json-schema-reset .json-schema-deprecated-title}{title="This entity is deprecated and may be removed in future versions."}
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `marketCategoryId`.
  
  {% endnote %}
  
  Категория товара в вашем магазине.
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### Url {#entity-Url}
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferManualDTO {#entity-OfferManualDTO}
  
  Инструкция по использованию товара.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _url_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [Url](#entity-Url)
  
  Ссылка на инструкцию.
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _title_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название инструкции, которое будет отображаться на карточке товара.
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `500`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "url": "example",
    "title": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferVendor {#entity-OfferVendor}
  
  Название бренда или производителя. Должно быть записано так, как его пишет сам бренд.
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `LEVENHUK`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferBarcodes {#entity-OfferBarcodes}
  
  Штрихкод.
  
  Указывайте в виде последовательности цифр. Подойдут коды EAN-13, EAN-8, UPC-A, UPC-E или Code 128. Для книг — ISBN.
  
  Для товаров [определенных категорий и торговых марок](https://yastatic.net/s3/doc-binary/src/support/market/ru/yandex-market-list-for-gtin.xlsx) штрихкод должен быть действительным кодом GTIN. Обратите внимание: внутренние штрихкоды, начинающиеся на 2 или 02, и коды формата Code 128 не являются GTIN.
  
  [Что такое GTIN](*gtin)
  
  
  **Type**: string[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "46012300000000"
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferDescription {#entity-OfferDescription}
  
  Подробное описание товара: например, его преимущества и особенности.
  
  Не давайте в описании инструкций по установке и сборке. Не используйте слова «скидка», «распродажа», «дешевый», «подарок» (кроме подарочных категорий), «бесплатно», «акция», «специальная цена», «новинка», «new», «аналог», «заказ», «хит». Не указывайте никакой контактной информации и не давайте ссылок.
  
  Для форматирования текста можно использовать теги HTML:
  
  * \<h>, \<h1>, \<h2> и так далее — для заголовков;
  * \<br> и \<p> — для переноса строки;
  * \<ol> — для нумерованного списка;
  * \<ul> — для маркированного списка;
  * \<li> — для создания элементов списка (должен находиться внутри \<ol> или \<ul>);
  * \<div> — поддерживается, но не влияет на отображение текста.
  
  Оптимальная длина — 400–600 символов.
  
  [Рекомендации и правила](https://yandex.ru/support/marketplace/assortment/fields/description.html)
  
  
  **Type**: string
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `6000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferManufacturerCountries {#entity-BaseOfferManufacturerCountries}
  
  Страна, где был произведен товар.
  
  Записывайте названия стран так, как они записаны в [списке](https://yastatic.net/s3/doc-binary/src/support/market/ru/countries.xlsx).
  
  
  **Type**: string[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "Россия"
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferWeightDimensionsDTO {#entity-OfferWeightDimensionsDTO}
  
  Габариты упаковки и вес товара.
  
  Если товар занимает несколько коробок, перед измерением размеров сложите их компактно.
  
  ![Схема измерения многоместных грузов](../../_images/reference/boxes-measure.png)
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _height_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Высота упаковки в см.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _length_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Длина упаковки в см.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _weight_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Вес товара в кг с учетом упаковки (брутто).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  ||
  
  _width_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Ширина упаковки в см.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "length": 65.55,
    "width": 50.7,
    "height": 20,
    "weight": 1.001
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferVendorCode {#entity-OfferVendorCode}
  
  Артикул товара от производителя.
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `VNDR-0005A`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferTags {#entity-BaseOfferTags}
  
  Метки товара, которые использует магазин. Покупателям теги не видны. По тегам можно группировать и фильтровать разные товары в каталоге — например, товары одной серии, коллекции или линейки.
  
  Максимальная длина тега — 20 символов. У одного товара может быть максимум 10 тегов.
  
  
  **Type**: string[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "до 500 рублей"
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### TimeUnitType {#entity-TimeUnitType}
  
  Единица измерения времени:
  
  * `HOUR` — час.
  * `DAY` — сутки.
  * `WEEK` — неделя.
  * `MONTH` — месяц.
  * `YEAR` — год.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `HOUR`, `DAY`, `WEEK`, `MONTH`, `YEAR`
  
  </div>
  
  <div class="openapi-entity">
  
  ### TimePeriodDTO {#entity-TimePeriodDTO}
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _timePeriod_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Продолжительность в указанных единицах.
  {.table-cell}
  ||
  ||
  
  _timeUnit_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TimeUnitType](#entity-TimeUnitType)
  
  Единица измерения.
  
  Единица измерения времени:
  
  * `HOUR` — час.
  * `DAY` — сутки.
  * `WEEK` — неделя.
  * `MONTH` — месяц.
  * `YEAR` — год.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `HOUR`, `DAY`, `WEEK`, `MONTH`, `YEAR`
  {.table-cell}
  ||
  ||
  
  _comment_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Комментарий.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `500`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferCustomsCommodityCode {#entity-BaseOfferCustomsCommodityCode}
  
  _Deprecated_{.json-schema-reset .json-schema-deprecated-title}{title="This entity is deprecated and may be removed in future versions."}
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `commodityCodes` с типом `CUSTOMS_COMMODITY_CODE`.
  
  {% endnote %}
  
  Код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  
  Обязательно укажите, если он есть.
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `8517610008`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CommodityCodeType {#entity-CommodityCodeType}
  
  Тип товарного кода:
  
  * `CUSTOMS_COMMODITY_CODE` — код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  * `IKPU_CODE` — идентификационный код продукции и услуг (ИКПУ) в Узбекистане – 17 цифр без пробелов.
  * `OKPD2_CODE` — код по Общероссийскому классификатору продукции по видам экономической деятельности (ОКПД2) — 2, 3, 4, 5, 6 или 9 цифр, разделенных точками: XX, XX.X, XX.XX, XX.XX.X, XX.XX.XX или XX.XX.XX.XXX.
  
  Не передавайте несколько кодов одного типа.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `CUSTOMS_COMMODITY_CODE`, `IKPU_CODE`, `OKPD2_CODE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CommodityCodeDTO {#entity-CommodityCodeDTO}
  
  Товарный код.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Товарный код.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CommodityCodeType](#entity-CommodityCodeType)
  
  Тип товарного кода.
  
  Тип товарного кода:
  
  * `CUSTOMS_COMMODITY_CODE` — код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  * `IKPU_CODE` — идентификационный код продукции и услуг (ИКПУ) в Узбекистане – 17 цифр без пробелов.
  * `OKPD2_CODE` — код по Общероссийскому классификатору продукции по видам экономической деятельности (ОКПД2) — 2, 3, 4, 5, 6 или 9 цифр, разделенных точками: XX, XX.X, XX.XX, XX.XX.X, XX.XX.XX или XX.XX.XX.XXX.
  
  Не передавайте несколько кодов одного типа.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `CUSTOMS_COMMODITY_CODE`, `IKPU_CODE`, `OKPD2_CODE`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "code": "example",
    "type": "CUSTOMS_COMMODITY_CODE"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferCommodityCodes {#entity-BaseOfferCommodityCodes}
  
  Товарные коды.
  
  
  **Type**: [CommodityCodeDTO](#entity-CommodityCodeDTO)[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "code": "example",
      "type": "CUSTOMS_COMMODITY_CODE"
    }
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferBoxCount {#entity-BaseOfferBoxCount}
  
  Количество грузовых мест.
  
  Параметр используется, если товар представляет собой несколько коробок, упаковок и так далее. Например, кондиционер занимает два места — внешний и внутренний блоки в двух коробках.
  
  Для товаров, занимающих одно место, не передавайте этот параметр.
  
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferConditionType {#entity-OfferConditionType}
  
  Тип уценки:
  
  * `PREOWNED` —  бывший в употреблении товар, раньше принадлежал другому человеку.
  * `SHOWCASESAMPLE` — витринный образец.
  * `REFURBISHED` — повторная продажа товара.
  * `REDUCTION` — товар с дефектами.
  * `RENOVATED` — восстановленный товар.
  * `NOT_SPECIFIED` — не выбран.
  
  `REFURBISHED` — специальное значение для одежды, обуви и аксессуаров. Используется только для уцененных товаров из этой категории. Другие значения для одежды, обуви и аксессуаров не используются.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREOWNED`, `SHOWCASESAMPLE`, `REFURBISHED`, `REDUCTION`, `RENOVATED`, `NOT_SPECIFIED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferConditionQualityType {#entity-OfferConditionQualityType}
  
  Внешний вид товара:
  
  * `PERFECT` — идеальный.
  * `EXCELLENT` — отличный.
  * `GOOD` — хороший.
  * `NOT_SPECIFIED` — не выбран.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERFECT`, `EXCELLENT`, `GOOD`, `NOT_SPECIFIED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferConditionDTO {#entity-OfferConditionDTO}
  
  Состояние уцененного товара.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _quality_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferConditionQualityType](#entity-OfferConditionQualityType)
  
  Внешний вид товара.
  
  
  Внешний вид товара:
  
  * `PERFECT` — идеальный.
  * `EXCELLENT` — отличный.
  * `GOOD` — хороший.
  * `NOT_SPECIFIED` — не выбран.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PERFECT`, `EXCELLENT`, `GOOD`, `NOT_SPECIFIED`
  {.table-cell}
  ||
  ||
  
  _reason_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание товара. Подробно опишите дефекты, насколько они заметны и где их искать.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferConditionType](#entity-OfferConditionType)
  
  Тип уценки.
  
  
  Тип уценки:
  
  * `PREOWNED` —  бывший в употреблении товар, раньше принадлежал другому человеку.
  * `SHOWCASESAMPLE` — витринный образец.
  * `REFURBISHED` — повторная продажа товара.
  * `REDUCTION` — товар с дефектами.
  * `RENOVATED` — восстановленный товар.
  * `NOT_SPECIFIED` — не выбран.
  
  `REFURBISHED` — специальное значение для одежды, обуви и аксессуаров. Используется только для уцененных товаров из этой категории. Другие значения для одежды, обуви и аксессуаров не используются.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `PREOWNED`, `SHOWCASESAMPLE`, `REFURBISHED`, `REDUCTION`, `RENOVATED`, `NOT_SPECIFIED`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "PREOWNED",
    "quality": "PERFECT",
    "reason": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferType {#entity-OfferType}
  
  Особый тип товара:
  
  * `DEFAULT` — товары, для которых вы передавали особый тип ранее и хотите убрать его.
  * `MEDICINE` — лекарства.
  * `BOOK` — бумажные и электронные книги.
  * `AUDIOBOOK` — аудиокниги.
  * `ARTIST_TITLE` — музыкальная и видеопродукция.
  * `ON_DEMAND` — товары на заказ.
  * `ALCOHOL` — алкоголь.
  
  {% note info "Если ваш товар — книга" %}
  
  Укажите год издания в характеристиках товара. [Подробнее о параметре](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md#offerparamdto)
  
  {% endnote %}
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEFAULT`, `MEDICINE`, `BOOK`, `AUDIOBOOK`, `ARTIST_TITLE`, `ON_DEMAND`, `ALCOHOL`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferDownloadable {#entity-BaseOfferDownloadable}
  
  Признак цифрового товара. Укажите `true`, если товар доставляется по электронной почте.
  
  [Как работать с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)
  
  
  **Type**: boolean
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferAdult {#entity-BaseOfferAdult}
  
  Параметр включает для товара пометку 18+. Устанавливайте ее только для товаров, которые относятся к удовлетворению сексуальных потребностей.
  
  
  **Type**: boolean
  
  </div>
  
  <div class="openapi-entity">
  
  ### AgeUnitType {#entity-AgeUnitType}
  
  Единицы измерения возраста:
  
  * `YEAR` — год.
  * `MONTH` — месяц.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `YEAR`, `MONTH`
  
  </div>
  
  <div class="openapi-entity">
  
  ### AgeDTO {#entity-AgeDTO}
  
  Возраст в заданных единицах измерения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _ageUnit_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [AgeUnitType](#entity-AgeUnitType)
  
  Единица измерения.
  
  
  Единицы измерения возраста:
  
  * `YEAR` — год.
  * `MONTH` — месяц.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `YEAR`, `MONTH`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Значение.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "ageUnit": "YEAR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferParamDTO {#entity-OfferParamDTO}
  
  Параметры товара.
  
  Если у товара несколько значений одного параметра, передайте их с одним и тем же `name`, но разными `value`.
  
  {% cut "Пример" %}
  
  ```json translate=no
  "params": [
    {
      "name": "Цвет для фильтра",
      "value": "Зеленый"
    },
    {
      "name": "Цвет для фильтра",
      "value": "Желтый"
    }
  ]
  ```
  
  {% endcut %}
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название характеристики.
  
  Должно совпадать с названием характеристики на Маркете. Узнать его можно из Excel-шаблона категории или через запрос [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `200`
  
  _Example:_{.json-schema-reset .json-schema-example} `Wi-Fi`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Значение.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `есть`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "name": "Wi-Fi",
    "value": "есть"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferParams {#entity-BaseOfferParams}
  
  _Deprecated_{.json-schema-reset .json-schema-deprecated-title}{title="This entity is deprecated and may be removed in future versions."}
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  При передаче характеристик используйте `parameterValues`.
  
  {% endnote %}
  
  Характеристики, которые есть только у товаров конкретной категории — например, диаметр колес велосипеда или материал подошвы обуви.
  
  
  **Type**: [OfferParamDTO](#entity-OfferParamDTO)[] | null
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "name": "Wi-Fi",
      "value": "есть"
    }
  ]
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### BaseOfferDTO {#entity-BaseOfferDTO}
  
  Основные параметры товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  Ваш SKU — идентификатор товара в вашей системе.
  
  Правила использования SKU:
  
  * У каждого товара SKU должен быть свой.
  
  * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.
  
  SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).
  
  {% note warning %}
  
  Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.
  
  {% endnote %}
  
  [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _adult_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferAdult](#entity-BaseOfferAdult)
  
  Параметр включает для товара пометку 18+. Устанавливайте ее только для товаров, которые относятся к удовлетворению сексуальных потребностей.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `true`
  {.table-cell}
  ||
  ||
  
  _age_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [AgeDTO](#entity-AgeDTO)
  
  Если товар не предназначен для детей младше определенного возраста, укажите это.
  
  Возрастное ограничение можно задавать в годах (с нуля, с 6, 12, 16 или 18) или в месяцах (любое число от 0 до 12).
  
  
  Возраст в заданных единицах измерения.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "ageUnit": "YEAR"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _barcodes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferBarcodes](#entity-OfferBarcodes)
  
  Штрихкод.
  
  Указывайте в виде последовательности цифр. Подойдут коды EAN-13, EAN-8, UPC-A, UPC-E или Code 128. Для книг — ISBN.
  
  Для товаров [определенных категорий и торговых марок](https://yastatic.net/s3/doc-binary/src/support/market/ru/yandex-market-list-for-gtin.xlsx) штрихкод должен быть действительным кодом GTIN. Обратите внимание: внутренние штрихкоды, начинающиеся на 2 или 02, и коды формата Code 128 не являются GTIN.
  
  [Что такое GTIN](*gtin)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "46012300000000"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _boxCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferBoxCount](#entity-BaseOfferBoxCount)
  
  Количество грузовых мест.
  
  Параметр используется, если товар представляет собой несколько коробок, упаковок и так далее. Например, кондиционер занимает два места — внешний и внутренний блоки в двух коробках.
  
  Для товаров, занимающих одно место, не передавайте этот параметр.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  ||
  
  _category_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [OfferCategory](#entity-OfferCategory)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `marketCategoryId`.
  
  {% endnote %}
  
  Категория товара в вашем магазине.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _certificates_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string[] &#124; null
  
  Номера документов на товар: сертификата, декларации соответствия и т. п.
  
  Документы можно создать с помощью [POST v1/businesses/{businessId}/offers/documents/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/documents/createDocuments.md).
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `6`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "example"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _commodityCodes_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferCommodityCodes](#entity-BaseOfferCommodityCodes)
  
  Товарные коды.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "code": "example",
      "type": "CUSTOMS_COMMODITY_CODE"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _condition_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferConditionDTO](#entity-OfferConditionDTO)
  
  Состояние уцененного товара.
  
  Используется только для товаров, продаваемых с уценкой.
  
  [Правила продажи уцененных товаров](https://yandex.ru/support/marketplace/assortment/restrictions/used-goods.html)
  
  
  Состояние уцененного товара.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "PREOWNED",
    "quality": "PERFECT",
    "reason": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _customsCommodityCode_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [BaseOfferCustomsCommodityCode](#entity-BaseOfferCustomsCommodityCode)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Вместо него используйте `commodityCodes` с типом `CUSTOMS_COMMODITY_CODE`.
  
  {% endnote %}
  
  Код товара в единой Товарной номенклатуре внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  
  Обязательно укажите, если он есть.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `8517610008`
  {.table-cell}
  ||
  ||
  
  _description_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferDescription](#entity-OfferDescription)
  
  Подробное описание товара: например, его преимущества и особенности.
  
  Не давайте в описании инструкций по установке и сборке. Не используйте слова «скидка», «распродажа», «дешевый», «подарок» (кроме подарочных категорий), «бесплатно», «акция», «специальная цена», «новинка», «new», «аналог», «заказ», «хит». Не указывайте никакой контактной информации и не давайте ссылок.
  
  Для форматирования текста можно использовать теги HTML:
  
  * \<h>, \<h1>, \<h2> и так далее — для заголовков;
  * \<br> и \<p> — для переноса строки;
  * \<ol> — для нумерованного списка;
  * \<ul> — для маркированного списка;
  * \<li> — для создания элементов списка (должен находиться внутри \<ol> или \<ul>);
  * \<div> — поддерживается, но не влияет на отображение текста.
  
  Оптимальная длина — 400–600 символов.
  
  [Рекомендации и правила](https://yandex.ru/support/marketplace/assortment/fields/description.html)
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `6000`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _downloadable_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferDownloadable](#entity-BaseOfferDownloadable)
  
  Признак цифрового товара. Укажите `true`, если товар доставляется по электронной почте.
  
  [Как работать с цифровыми товарами](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md)
  
  
  _Example:_{.json-schema-reset .json-schema-example} `true`
  {.table-cell}
  ||
  ||
  
  _guaranteePeriod_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimePeriodDTO](#entity-TimePeriodDTO)
  
  Гарантийный срок — период, в течение которого можно заменить или починить товар без дополнительной платы.
  
  Обязательно указывайте срок, если он есть.
  
  В комментарии опишите особенности гарантийного обслуживания. Например, `Гарантия на аккумулятор — 6 месяцев`.
  
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _lifeTime_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimePeriodDTO](#entity-TimePeriodDTO)
  
  Срок службы — период, в течение которого товар должен исправно выполнять свою функцию.
  
  Обязательно указывайте срок, если он есть.
  
  В комментарии укажите условия хранения. Например, `Использовать при температуре не ниже −10 градусов`.
  
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _manuals_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferManualDTO](#entity-OfferManualDTO)[] &#124; null
  
  Список инструкций по использованию товара.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `6`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "url": "example",
      "title": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _manufacturerCountries_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferManufacturerCountries](#entity-BaseOfferManufacturerCountries)
  
  Страна, где был произведен товар.
  
  Записывайте названия стран так, как они записаны в [списке](https://yastatic.net/s3/doc-binary/src/support/market/ru/countries.xlsx).
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "Россия"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _marketCategoryId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PartnerMarketCategoryId](#entity-PartnerMarketCategoryId)
  
  Идентификатор категории на Маркете, к которой вы относите свой товар.
  
  {% note warning "Всегда указывайте, когда передаете `parameterValues`" %}
  
  Если при изменении характеристик передать `parameterValues` и не указать `marketCategoryId`, характеристики обновятся, но в ответе придет предупреждение (параметр `warnings`).
  
  Если не передать их оба, будет использована информация из устаревших параметров `params` и `category`, а `marketCategoryId` будет определен автоматически.
  
  {% endnote %}
  
  При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.
  
  Список категорий Маркета можно получить с помощью запроса  [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} `0`
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferName](#entity-OfferName)
  
  Составляйте название по схеме: тип + бренд или производитель + модель + особенности, если есть (например, цвет, размер или вес) и количество в упаковке.
  
  Не включайте в название условия продажи (например, «скидка», «бесплатная доставка» и т. д.), эмоциональные характеристики («хит», «супер» и т. д.). Не пишите слова большими буквами — кроме устоявшихся названий брендов и моделей.
  
  Оптимальная длина — 50–60 символов.
  
  [Рекомендации и правила](https://yandex.ru/support/marketplace/assortment/fields/title.html)
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `256`
  
  _Example:_{.json-schema-reset .json-schema-example} `Ударная дрель Makita HP1630, 710 Вт`
  {.table-cell}
  ||
  ||
  
  _params_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: [BaseOfferParams](#entity-BaseOfferParams)
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  При передаче характеристик используйте `parameterValues`.
  
  {% endnote %}
  
  Характеристики, которые есть только у товаров конкретной категории — например, диаметр колес велосипеда или материал подошвы обуви.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "name": "Wi-Fi",
      "value": "есть"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _pictures_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)[] &#124; null
  
  Ссылки на изображения товара. Изображение по первой ссылке считается основным, остальные дополнительными.
  
  **Требования к ссылкам**
  
  * Указывайте ссылку целиком, включая протокол http или https.
  * Русские буквы в URL можно.
  * Можно использовать прямые ссылки на изображения и на Яндекс Диск. Ссылки на Яндекс Диске нужно копировать с помощью функции **Поделиться**. Относительные ссылки и ссылки на другие облачные хранилища — не работают.
  
  ✅ `https://example-shop.ru/images/sku12345.jpg`
  
  ✅ `https://yadi.sk/i/NaBoRsimVOLov`
  
  ❌ `/images/sku12345.jpg`
  
  ❌ `https://www.dropbox.com/s/818f/tovar.jpg`
  
  Ссылки на изображение должны быть постоянными. Нельзя использовать динамические ссылки, меняющиеся от выгрузки к выгрузке.
  
  Если нужно заменить изображение, выложите новое изображение по новой ссылке, а ссылку на старое удалите. Если просто заменить изображение по старой ссылке, оно не обновится.
  
  [Требования к изображениям](https://yandex.ru/support/marketplace/assortment/fields/images.html)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `30`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "example"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _shelfLife_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [TimePeriodDTO](#entity-TimePeriodDTO)
  
  Срок годности — период, по прошествии которого товар становится непригоден.
  
  Указывайте срок, указанный на банке или упаковке. Текущая дата, дата поставки или дата отгрузки значения не имеет.
  
  Обязательно указывайте срок, если он есть.
  
  В комментарии укажите условия хранения. Например, `Хранить в сухом помещении`.
  
  
  Временной отрезок с комментарием. Требования к содержанию комментария зависят от контекста использования параметра и указаны в описании поля, которое его содержит.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "timePeriod": 0,
    "timeUnit": "HOUR",
    "comment": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _tags_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BaseOfferTags](#entity-BaseOfferTags)
  
  Метки товара, которые использует магазин. Покупателям теги не видны. По тегам можно группировать и фильтровать разные товары в каталоге — например, товары одной серии, коллекции или линейки.
  
  Максимальная длина тега — 20 символов. У одного товара может быть максимум 10 тегов.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `50`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "до 500 рублей"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferType](#entity-OfferType)
  
  Особый тип товара. Указывается, если товар:
  
  * имеет особый тип, который хотите убрать;
  * лекарство;
  * бумажная или электронная книга;
  * аудиокнига;
  * музыка или видео;
  * изготовляется на заказ;
  * алкоголь.
  
  
  Особый тип товара:
  
  * `DEFAULT` — товары, для которых вы передавали особый тип ранее и хотите убрать его.
  * `MEDICINE` — лекарства.
  * `BOOK` — бумажные и электронные книги.
  * `AUDIOBOOK` — аудиокниги.
  * `ARTIST_TITLE` — музыкальная и видеопродукция.
  * `ON_DEMAND` — товары на заказ.
  * `ALCOHOL` — алкоголь.
  
  {% note info "Если ваш товар — книга" %}
  
  Укажите год издания в характеристиках товара. [Подробнее о параметре](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md#offerparamdto)
  
  {% endnote %}
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEFAULT`, `MEDICINE`, `BOOK`, `AUDIOBOOK`, `ARTIST_TITLE`, `ON_DEMAND`, `ALCOHOL`
  {.table-cell}
  ||
  ||
  
  _vendor_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferVendor](#entity-OfferVendor)
  
  Название бренда или производителя. Должно быть записано так, как его пишет сам бренд.
  
  _Example:_{.json-schema-reset .json-schema-example} `LEVENHUK`
  {.table-cell}
  ||
  ||
  
  _vendorCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferVendorCode](#entity-OfferVendorCode)
  
  Артикул товара от производителя.
  
  _Example:_{.json-schema-reset .json-schema-example} `VNDR-0005A`
  {.table-cell}
  ||
  ||
  
  _videos_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Url](#entity-Url)[] &#124; null
  
  Ссылки (URL) на видео товара.
  
  **Требования к ссылке**
  
  * Указывайте ссылку целиком, включая протокол http или https.
  * Русские буквы в URL можно.
  * Можно использовать прямые ссылки на видео и на Яндекс Диск. Ссылки на Яндекс Диске нужно копировать с помощью функции **Поделиться**. Относительные ссылки и ссылки на другие облачные хранилища — не работают.
  
  ✅ `https://example-shop.ru/video/sku12345.avi`
  
  ✅ `https://yadi.sk/i/NaBoRsimVOLov`
  
  ❌ `/video/sku12345.avi`
  
  ❌ `https://www.dropbox.com/s/818f/super-tovar.avi`
  
  Ссылки на видео должны быть постоянными. Нельзя использовать динамические ссылки, меняющиеся от выгрузки к выгрузке.
  
  Если нужно заменить видео, выложите новое видео по новой ссылке, а ссылку на старое удалите. Если просто заменить видео по старой ссылке, оно не обновится.
  
  [Требования к видео](https://yandex.ru/support/marketplace/assortment/fields/video.html)
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `6`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "example"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _weightDimensions_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferWeightDimensionsDTO](#entity-OfferWeightDimensionsDTO)
  
  Габариты упаковки и вес товара.
  
  Должны быть больше 0.
  
  
  Габариты упаковки и вес товара.
  
  Если товар занимает несколько коробок, перед измерением размеров сложите их компактно.
  
  ![Схема измерения многоместных грузов](../../_images/reference/boxes-measure.png)
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "length": 65.55,
    "width": 50.7,
    "height": 20,
    "weight": 1.001
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "name": "Ударная дрель Makita HP1630, 710 Вт",
    "marketCategoryId": 0,
    "category": "example",
    "pictures": [
      "example"
    ],
    "videos": [
      null
    ],
    "manuals": [
      {
        "url": null,
        "title": "example"
      }
    ],
    "vendor": "LEVENHUK",
    "barcodes": [
      "46012300000000"
    ],
    "description": "example",
    "manufacturerCountries": [
      "Россия"
    ],
    "weightDimensions": {
      "length": 65.55,
      "width": 50.7,
      "height": 20,
      "weight": 1.001
    },
    "vendorCode": "VNDR-0005A",
    "tags": [
      "до 500 рублей"
    ],
    "shelfLife": {
      "timePeriod": 0,
      "timeUnit": "HOUR",
      "comment": "example"
    },
    "lifeTime": null,
    "guaranteePeriod": null,
    "customsCommodityCode": "8517610008",
    "commodityCodes": [
      {
        "code": "example",
        "type": "CUSTOMS_COMMODITY_CODE"
      }
    ],
    "certificates": [
      "example"
    ],
    "boxCount": 1,
    "condition": {
      "type": "PREOWNED",
      "quality": "PERFECT",
      "reason": "example"
    },
    "type": "DEFAULT",
    "downloadable": true,
    "adult": true,
    "age": {
      "value": 0,
      "ageUnit": "YEAR"
    },
    "params": [
      {
        "name": "Wi-Fi",
        "value": "есть"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ParameterValueDTO {#entity-ParameterValueDTO}
  
  Значение характеристики.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _parameterId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор характеристики.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _unitId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор единицы измерения. Если вы не передали параметр `unitId`, используется единица измерения по умолчанию.
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Значение.
  
  Для характеристик типа `ENUM` передавайте:
  - вместе с `valueId`, если значение берете из справочника;
  - без `valueId`, если значение собственное.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _valueId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор значения.
  
  - Обязательно указывайте идентификатор, если передаете значение из перечня допустимых значений, полученного от Маркета.
  - Не указывайте для собственных значений.
  - Только для характеристик типа `ENUM`.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "parameterId": 1,
    "unitId": 0,
    "valueId": 0,
    "value": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CurrencyType {#entity-CurrencyType}
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BasePriceDTO {#entity-BasePriceDTO}
  
  Цена товара.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _currencyId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [CurrencyType](#entity-CurrencyType)
  
  Валюта.
  
  Коды валют:
  
  * `RUR` — российский рубль.
  * `UAH` — украинская гривна.
  * `BYR` — белорусский рубль.
  * `KZT` — казахстанский тенге.
  * `UZS` — узбекский сум.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `RUR`, `USD`, `EUR`, `UAH`, `AUD`, `GBP`, `BYR`, `BYN`, `DKK`, `ISK`, `KZT`, `CAD`, `CNY`, `NOK`, `XDR`, `SGD`, `TRY`, `SEK`, `CHF`, `JPY`, `AZN`, `ALL`, `DZD`, `AOA`, `ARS`, `AMD`, `AFN`, `BHD`, `BGN`, `BOB`, `BWP`, `BND`, `BRL`, `BIF`, `HUF`, `VEF`, `KPW`, `VND`, `GMD`, `GHS`, `GNF`, `HKD`, `GEL`, `AED`, `EGP`, `ZMK`, `ILS`, `INR`, `IDR`, `JOD`, `IQD`, `IRR`, `YER`, `QAR`, `KES`, `KGS`, `COP`, `CDF`, `CRC`, `KWD`, `CUP`, `LAK`, `LVL`, `SLL`, `LBP`, `LYD`, `SZL`, `LTL`, `MUR`, `MRO`, `MKD`, `MWK`, `MGA`, `MYR`, `MAD`, `MXN`, `MZN`, `MDL`, `MNT`, `NPR`, `NGN`, `NIO`, `NZD`, `OMR`, `PKR`, `PYG`, `PEN`, `PLN`, `KHR`, `SAR`, `RON`, `SCR`, `SYP`, `SKK`, `SOS`, `SDG`, `SRD`, `TJS`, `THB`, `TWD`, `BDT`, `TZS`, `TND`, `TMM`, `UGX`, `UZS`, `UYU`, `PHP`, `DJF`, `XAF`, `XOF`, `HRK`, `CZK`, `CLP`, `LKR`, `EEK`, `ETB`, `RSD`, `ZAR`, `KRW`, `NAD`, `TL`, `UE`
  {.table-cell}
  ||
  ||
  
  _value_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: number
  
  Цена товара.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DiscountBase {#entity-DiscountBase}
  
  Зачеркнутая цена.
  
  Число должно быть целым. Вы можете указать цену со скидкой от 5 до 99%.
  
  Передавайте этот параметр при каждом обновлении цены, если предоставляете скидку на товар.
  
  
  **Type**: number
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
  </div>
  
  <div class="openapi-entity">
  
  ### PriceWithDiscountDTO {#entity-PriceWithDiscountDTO}
  
  Цена с указанием скидки.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BasePriceDTO](#entity-BasePriceDTO)
  
    Цена товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _discountBase_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [DiscountBase](#entity-DiscountBase)
  
    Зачеркнутая цена.
  
    Число должно быть целым. Вы можете указать цену со скидкой от 5 до 99%.
  
    Передавайте этот параметр при каждом обновлении цены, если предоставляете скидку на товар.
  
  
    _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
    _Exclusive min:_{.json-schema-reset .json-schema-assertion} `true`
  
    _Example:_{.json-schema-reset .json-schema-example} `0`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "discountBase": 0
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "value": 0,
    "currencyId": "RUR",
    "discountBase": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DeleteOfferParameterType {#entity-DeleteOfferParameterType}
  
  Значения параметров, которые хотите удалить, и соответствующие параметры в `UpdateOfferDTO`, в которых вы передали эти значения ранее:
  
  * `ADDITIONAL_EXPENSES` — дополнительные расходы на товар (параметр `additionalExpenses`).
  * `ADULT` — пометка 18+ (параметр `adult`)
  * `AGE` — возрастное ограничение для детей (параметр `age`).
  * `BARCODES` — штрихкод (параметр `barcodes`).
  * `BOX_COUNT` — количество грузовых мест (параметр `boxCount`).
  * `CERTIFICATES` — номера документов на товар (параметр `certificates`).
  * `COMMODITY_CODES` — товарные коды (параметр `commodityCodes`).
  * `CONDITION` — состояние уцененного товара (параметр `condition`).
  * `CUSTOMS_COMMODITY_CODE` — код товара в ТН ВЭД (параметр `customsCommodityCode`).
  * `DESCRIPTION` — описание товара (параметр `description`).
  * `DOWNLOADABLE` — признак цифрового товара (параметр `downloadable`).
  * `GUARANTEE_PERIOD` — гарантийный срок (параметр `guaranteePeriod`).
  * `LIFE_TIME` — срок службы (параметр `lifeTime`).
  * `MANUALS` — список инструкций по использованию товара (параметр `manuals`).
  * `MANUFACTURER_COUNTRIES` — страна производства (параметр `manufacturerCountries`).
  * `PARAMETERS` — характеристики товара (параметры `params`, `parameterValues`).
  * `PICTURES` — ссылки на изображения товара (параметр `pictures`).
  * `PURCHASE_PRICE` — себестоимость (параметр `purchasePrice`).
  * `SHELF_LIFE` — срок годности (параметр `shelfLife`).
  * `TAGS` — метки товара, которые использует магазин (параметр `tags`).
  * `TYPE` — особый тип товара (параметр `type`).
  * `VENDOR_CODE` — название бренда или производителя (параметр `vendorCode`).
  * `VIDEOS` — ссылки на видео товара (параметр `videos`).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ADDITIONAL_EXPENSES`, `ADULT`, `AGE`, `BARCODES`, `BOX_COUNT`, `CERTIFICATES`, `COMMODITY_CODES`, `CONDITION`, `CUSTOMS_COMMODITY_CODE`, `DESCRIPTION`, `DOWNLOADABLE`, `GUARANTEE_PERIOD`, `LIFE_TIME`, `MANUALS`, `MANUFACTURER_COUNTRIES`, `PARAMETERS`, `PICTURES`, `PURCHASE_PRICE`, `SHELF_LIFE`, `TAGS`, `TYPE`, `VENDOR_CODE`, `VIDEOS`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOfferDTO {#entity-UpdateOfferDTO}
  
  Параметры товара.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [BaseOfferDTO](#entity-BaseOfferDTO)
  
    Основные параметры товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "offerId": "example",
      "name": "Ударная дрель Makita HP1630, 710 Вт",
      "marketCategoryId": 0,
      "category": "example",
      "pictures": [
        "example"
      ],
      "videos": [
        null
      ],
      "manuals": [
        {
          "url": null,
          "title": "example"
        }
      ],
      "vendor": "LEVENHUK",
      "barcodes": [
        "46012300000000"
      ],
      "description": "example",
      "manufacturerCountries": [
        "Россия"
      ],
      "weightDimensions": {
        "length": 65.55,
        "width": 50.7,
        "height": 20,
        "weight": 1.001
      },
      "vendorCode": "VNDR-0005A",
      "tags": [
        "до 500 рублей"
      ],
      "shelfLife": {
        "timePeriod": 0,
        "timeUnit": "HOUR",
        "comment": "example"
      },
      "lifeTime": null,
      "guaranteePeriod": null,
      "customsCommodityCode": "8517610008",
      "commodityCodes": [
        {
          "code": "example",
          "type": "CUSTOMS_COMMODITY_CODE"
        }
      ],
      "certificates": [
        "example"
      ],
      "boxCount": 1,
      "condition": {
        "type": "PREOWNED",
        "quality": "PERFECT",
        "reason": "example"
      },
      "type": "DEFAULT",
      "downloadable": true,
      "adult": true,
      "age": {
        "value": 0,
        "ageUnit": "YEAR"
      },
      "params": [
        {
          "name": "Wi-Fi",
          "value": "есть"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _additionalExpenses_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [BasePriceDTO](#entity-BasePriceDTO)
  
    Дополнительные расходы на товар. Например, на доставку или упаковку.
  
    Цена товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR"
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _basicPrice_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [PriceWithDiscountDTO](#entity-PriceWithDiscountDTO)
  
    Цена.
  
  
    Цена с указанием скидки.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _deleteParameters_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [DeleteOfferParameterType](#entity-DeleteOfferParameterType)[] &#124; null
  
    Параметры, которые вы ранее передали в `UpdateOfferDTO`, а теперь хотите удалить.
  
    Если передать `adult`, `downloadable` и `firstVideoAsCover`, они не удалятся — их значение изменится на `false`.
  
    Можно передать сразу несколько значений.
  
    Не используйте вместе с соответствующим параметром в `UpdateOfferDTO`. Это приведет к ошибке `400`.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      "ADDITIONAL_EXPENSES"
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _firstVideoAsCover_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
    {.table-cell}|
    **Type**: boolean
  
    {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
     
  
    {% endnote %}
  
    Использовать первое видео в карточке как видеообложку.
  
    Передайте `true`, чтобы первое видео использовалось как видеообложка, или `false`, чтобы видеообложка не отображалась в карточке товара.
  
    {.table-cell}
    ||
    ||
  
    _parameterValues_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [ParameterValueDTO](#entity-ParameterValueDTO)[] &#124; null
  
    Список характеристик с их значениями.
  
    {% note warning "Всегда передавайте вместе с `marketCategoryId`" %}
  
    Если не передать `marketCategoryId` при изменении характеристик, они обновятся, но в ответе придет предупреждение (параметр `warnings`).
  
    Если не передать их оба, будет использована информация из устаревших параметров `params` и `category`, а `marketCategoryId` будет определен автоматически.
  
    {% endnote %}
  
    При **изменении** характеристик передавайте только те, значение которых нужно обновить. Если в `marketCategoryId` вы меняете категорию, значения общих характеристик для старой и новой категории сохранятся, передавать их не нужно.
  
    Подробнее читайте в [«Передача значений характеристики»](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/parameter-values.md).
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    _Max items:_{.json-schema-reset .json-schema-assertion} `300`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "parameterId": 1,
        "unitId": 0,
        "valueId": 0,
        "value": "example"
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _purchasePrice_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [BasePriceDTO](#entity-BasePriceDTO)
  
    Себестоимость — затраты на самостоятельное производство товара или закупку у производителя или поставщиков.
  
    Цена товара.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "value": 0,
      "currencyId": "RUR"
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "parameterValues": [
        {
          "parameterId": 1,
          "unitId": 0,
          "valueId": 0,
          "value": "example"
        }
      ],
      "basicPrice": {
        "value": 0,
        "currencyId": "RUR",
        "discountBase": 0
      },
      "purchasePrice": null,
      "additionalExpenses": null,
      "firstVideoAsCover": true,
      "deleteParameters": [
        "ADDITIONAL_EXPENSES"
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "name": "Ударная дрель Makita HP1630, 710 Вт",
    "marketCategoryId": 0,
    "category": "example",
    "pictures": [
      "example"
    ],
    "videos": [
      null
    ],
    "manuals": [
      {
        "url": null,
        "title": "example"
      }
    ],
    "vendor": "LEVENHUK",
    "barcodes": [
      "46012300000000"
    ],
    "description": "example",
    "manufacturerCountries": [
      "Россия"
    ],
    "weightDimensions": {
      "length": 65.55,
      "width": 50.7,
      "height": 20,
      "weight": 1.001
    },
    "vendorCode": "VNDR-0005A",
    "tags": [
      "до 500 рублей"
    ],
    "shelfLife": {
      "timePeriod": 0,
      "timeUnit": "HOUR",
      "comment": "example"
    },
    "lifeTime": null,
    "guaranteePeriod": null,
    "customsCommodityCode": "8517610008",
    "commodityCodes": [
      {
        "code": "example",
        "type": "CUSTOMS_COMMODITY_CODE"
      }
    ],
    "certificates": [
      "example"
    ],
    "boxCount": 1,
    "condition": {
      "type": "PREOWNED",
      "quality": "PERFECT",
      "reason": "example"
    },
    "type": "DEFAULT",
    "downloadable": true,
    "adult": true,
    "age": {
      "value": 0,
      "ageUnit": "YEAR"
    },
    "params": [
      {
        "name": "Wi-Fi",
        "value": "есть"
      }
    ],
    "parameterValues": [
      {
        "parameterId": 1,
        "unitId": 0,
        "valueId": 0,
        "value": "example"
      }
    ],
    "basicPrice": {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0
    },
    "purchasePrice": null,
    "additionalExpenses": null,
    "firstVideoAsCover": true,
    "deleteParameters": [
      "ADDITIONAL_EXPENSES"
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### MarketSku {#entity-MarketSku}
  
  Идентификатор карточки товара на Маркете.
  
  **Type**: integer
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateMappingDTO {#entity-UpdateMappingDTO}
  
  Карточка на Маркете, которая, с вашей точки зрения, подходит товару. Чтобы определить идентификатор подходящей карточки, воспользуйтесь поиском в кабинете (**Товары** → **Каталог** → **Загрузить товары**).
  
  По результатам проверки Маркет может привязать товар к более подходящей карточке.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _marketSku_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [MarketSku](#entity-MarketSku)
  
  Идентификатор карточки на Маркете.
  
  
  Идентификатор карточки товара на Маркете.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Example:_{.json-schema-reset .json-schema-example} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "marketSku": 1
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOfferMappingDTO {#entity-UpdateOfferMappingDTO}
  
  Информация о товаре.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offer_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [UpdateOfferDTO](#entity-UpdateOfferDTO)
  
  Параметры товара.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "name": "Ударная дрель Makita HP1630, 710 Вт",
    "marketCategoryId": 0,
    "category": "example",
    "pictures": [
      "example"
    ],
    "videos": [
      null
    ],
    "manuals": [
      {
        "url": null,
        "title": "example"
      }
    ],
    "vendor": "LEVENHUK",
    "barcodes": [
      "46012300000000"
    ],
    "description": "example",
    "manufacturerCountries": [
      "Россия"
    ],
    "weightDimensions": {
      "length": 65.55,
      "width": 50.7,
      "height": 20,
      "weight": 1.001
    },
    "vendorCode": "VNDR-0005A",
    "tags": [
      "до 500 рублей"
    ],
    "shelfLife": {
      "timePeriod": 0,
      "timeUnit": "HOUR",
      "comment": "example"
    },
    "lifeTime": null,
    "guaranteePeriod": null,
    "customsCommodityCode": "8517610008",
    "commodityCodes": [
      {
        "code": "example",
        "type": "CUSTOMS_COMMODITY_CODE"
      }
    ],
    "certificates": [
      "example"
    ],
    "boxCount": 1,
    "condition": {
      "type": "PREOWNED",
      "quality": "PERFECT",
      "reason": "example"
    },
    "type": "DEFAULT",
    "downloadable": true,
    "adult": true,
    "age": {
      "value": 0,
      "ageUnit": "YEAR"
    },
    "params": [
      {
        "name": "Wi-Fi",
        "value": "есть"
      }
    ],
    "parameterValues": [
      {
        "parameterId": 1,
        "unitId": 0,
        "valueId": 0,
        "value": "example"
      }
    ],
    "basicPrice": {
      "value": 0,
      "currencyId": "RUR",
      "discountBase": 0
    },
    "purchasePrice": null,
    "additionalExpenses": null,
    "firstVideoAsCover": true,
    "deleteParameters": [
      "ADDITIONAL_EXPENSES"
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _mapping_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [UpdateMappingDTO](#entity-UpdateMappingDTO)
  
  Информация о карточке товара на Маркете.
  
  Карточка на Маркете, которая, с вашей точки зрения, подходит товару. Чтобы определить идентификатор подходящей карточки, воспользуйтесь поиском в кабинете (**Товары** → **Каталог** → **Загрузить товары**).
  
  По результатам проверки Маркет может привязать товар к более подходящей карточке.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "marketSku": 1
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offer": {
      "offerId": "example",
      "name": "Ударная дрель Makita HP1630, 710 Вт",
      "marketCategoryId": 0,
      "category": "example",
      "pictures": [
        "example"
      ],
      "videos": [
        null
      ],
      "manuals": [
        {
          "url": null,
          "title": "example"
        }
      ],
      "vendor": "LEVENHUK",
      "barcodes": [
        "46012300000000"
      ],
      "description": "example",
      "manufacturerCountries": [
        "Россия"
      ],
      "weightDimensions": {
        "length": 65.55,
        "width": 50.7,
        "height": 20,
        "weight": 1.001
      },
      "vendorCode": "VNDR-0005A",
      "tags": [
        "до 500 рублей"
      ],
      "shelfLife": {
        "timePeriod": 0,
        "timeUnit": "HOUR",
        "comment": "example"
      },
      "lifeTime": null,
      "guaranteePeriod": null,
      "customsCommodityCode": "8517610008",
      "commodityCodes": [
        {
          "code": "example",
          "type": "CUSTOMS_COMMODITY_CODE"
        }
      ],
      "certificates": [
        "example"
      ],
      "boxCount": 1,
      "condition": {
        "type": "PREOWNED",
        "quality": "PERFECT",
        "reason": "example"
      },
      "type": "DEFAULT",
      "downloadable": true,
      "adult": true,
      "age": {
        "value": 0,
        "ageUnit": "YEAR"
      },
      "params": [
        {
          "name": "Wi-Fi",
          "value": "есть"
        }
      ],
      "parameterValues": [
        {
          "parameterId": 1,
          "unitId": 0,
          "valueId": 0,
          "value": "example"
        }
      ],
      "basicPrice": {
        "value": 0,
        "currencyId": "RUR",
        "discountBase": 0
      },
      "purchasePrice": null,
      "additionalExpenses": null,
      "firstVideoAsCover": true,
      "deleteParameters": [
        "ADDITIONAL_EXPENSES"
      ]
    },
    "mapping": {
      "marketSku": 1
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Запрос выполнен корректно, данные обработаны.
  
  {% note warning "Ответ `200` сам по себе не значит, что переданные значения корректны" %}
  
  Обязательно посмотрите детали ответа: `status`, а также перечень ошибок (`results.errors`) и замечаний (`results.warnings`), если они есть.
  
  - Если хотя бы по одному товару вернулась ошибка (`results.errors`), поле `status` = `ERROR`. Изменения по всем переданным товарам не будут применены.
  - Если ошибок нет, но хотя бы по одному товару вернулось замечание (`results.warnings`), поле `status` = `OK`, и изменения будут применены.
  
  {% endnote %}
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "results": [
      {
        "offerId": "example",
        "errors": [
          {}
        ],
        "warnings": [
          null
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _results_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [UpdateOfferMappingResultDTO](#entity-UpdateOfferMappingResultDTO)[] &#124; null
  
    Ошибки и предупреждения, которые появились при обработке списка характеристик. Каждый элемент списка соответствует одному товару.
  
    Если ошибок и предупреждений нет, поле не передается.
  
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "offerId": "example",
        "errors": [
          {
            "type": "UNKNOWN_CATEGORY",
            "parameterId": 0,
            "message": "example"
          }
        ],
        "warnings": [
          null
        ]
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "results": [
        {
          "offerId": "example",
          "errors": [
            {
              "type": "UNKNOWN_CATEGORY",
              "parameterId": 0,
              "message": "example"
            }
          ],
          "warnings": [
            null
          ]
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiResponseStatusType {#entity-ApiResponseStatusType}
  
  Тип ответа.
  Возможные значения:
  * `OK` — ошибок нет.
  * `ERROR` — при обработке запроса произошла ошибка.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiResponse {#entity-ApiResponse}
  
  Стандартная обертка для ответов сервера.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _status_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ApiResponseStatusType](#entity-ApiResponseStatusType)
  
  Тип ответа.
  Возможные значения:
  * `OK` — ошибок нет.
  * `ERROR` — при обработке запроса произошла ошибка.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OK`, `ERROR`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "OK"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferMappingErrorType {#entity-OfferMappingErrorType}
  
  Типы ошибок и предупреждений:
  
  * `UNKNOWN_CATEGORY` — указана неизвестная категория.
  * `INVALID_CATEGORY` — указана нелистовая категория. Укажите ту, которая не имеет дочерних категорий.
  * `EMPTY_MARKET_CATEGORY` — не указана категория Маркета при передаче характеристик категории.
  * `UNKNOWN_PARAMETER` — передана характеристика, которой нет среди характеристик категории.
  * `UNEXPECTED_BOOLEAN_VALUE` — вместо boolean-значения передано что-то другое.
  * `NUMBER_FORMAT` — передана строка, не обозначающая число, вместо числа.
  * `INVALID_UNIT_ID` — передана единица измерения, недопустимая для характеристики.
  * `INVALID_GROUP_ID_LENGTH` — в названии превышено допустимое значение символов — 255.
  * `INVALID_GROUP_ID_CHARACTERS` — переданы [недопустимые символы](*ascii-code).
  * `INVALID_PICKER_URL` — передана ссылка на изображение для миниатюры, которой нет в переданных ссылках на изображение товара.
  * `LOCKED_DIMENSIONS` — переданы габариты упаковки, которые нельзя изменить.
  * `INVALID_COMMODITY_CODE` — передан некорректный товарный код.
  
  Проверить, какие категорийные характеристики доступны для заданной категории, и получить их настройки можно с помощью запроса [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNKNOWN_CATEGORY`, `INVALID_CATEGORY`, `EMPTY_MARKET_CATEGORY`, `UNKNOWN_PARAMETER`, `UNEXPECTED_BOOLEAN_VALUE`, `NUMBER_FORMAT`, `INVALID_UNIT_ID`, `INVALID_GROUP_ID_LENGTH`, `INVALID_GROUP_ID_CHARACTERS`, `INVALID_PICKER_URL`, `LOCKED_DIMENSIONS`, `INVALID_COMMODITY_CODE`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OfferMappingErrorDTO {#entity-OfferMappingErrorDTO}
  
  Текст ошибки или предупреждения.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _message_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Текст ошибки или предупреждения.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OfferMappingErrorType](#entity-OfferMappingErrorType)
  
  Типы ошибок и предупреждений:
  
  * `UNKNOWN_CATEGORY` — указана неизвестная категория.
  * `INVALID_CATEGORY` — указана нелистовая категория. Укажите ту, которая не имеет дочерних категорий.
  * `EMPTY_MARKET_CATEGORY` — не указана категория Маркета при передаче характеристик категории.
  * `UNKNOWN_PARAMETER` — передана характеристика, которой нет среди характеристик категории.
  * `UNEXPECTED_BOOLEAN_VALUE` — вместо boolean-значения передано что-то другое.
  * `NUMBER_FORMAT` — передана строка, не обозначающая число, вместо числа.
  * `INVALID_UNIT_ID` — передана единица измерения, недопустимая для характеристики.
  * `INVALID_GROUP_ID_LENGTH` — в названии превышено допустимое значение символов — 255.
  * `INVALID_GROUP_ID_CHARACTERS` — переданы [недопустимые символы](*ascii-code).
  * `INVALID_PICKER_URL` — передана ссылка на изображение для миниатюры, которой нет в переданных ссылках на изображение товара.
  * `LOCKED_DIMENSIONS` — переданы габариты упаковки, которые нельзя изменить.
  * `INVALID_COMMODITY_CODE` — передан некорректный товарный код.
  
  Проверить, какие категорийные характеристики доступны для заданной категории, и получить их настройки можно с помощью запроса [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `UNKNOWN_CATEGORY`, `INVALID_CATEGORY`, `EMPTY_MARKET_CATEGORY`, `UNKNOWN_PARAMETER`, `UNEXPECTED_BOOLEAN_VALUE`, `NUMBER_FORMAT`, `INVALID_UNIT_ID`, `INVALID_GROUP_ID_LENGTH`, `INVALID_GROUP_ID_CHARACTERS`, `INVALID_PICKER_URL`, `LOCKED_DIMENSIONS`, `INVALID_COMMODITY_CODE`
  {.table-cell}
  ||
  ||
  
  _parameterId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор характеристики, с которой связана ошибка или предупреждение.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "type": "UNKNOWN_CATEGORY",
    "parameterId": 0,
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### UpdateOfferMappingResultDTO {#entity-UpdateOfferMappingResultDTO}
  
  Ошибки и предупреждения, которые появились из-за переданных характеристик.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _offerId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ShopSku](#entity-ShopSku)
  
  Ваш SKU — идентификатор товара в вашей системе.
  
  Правила использования SKU:
  
  * У каждого товара SKU должен быть свой.
  
  * Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.
  
  SKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).
  
  {% note warning %}
  
  Пробельные символы в начале и конце значения автоматически удаляются. Например, `"  SKU123  "` и `"SKU123"` будут обработаны как одинаковые значения.
  
  {% endnote %}
  
  [Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `255`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _errors_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferMappingErrorDTO](#entity-OfferMappingErrorDTO)[] &#124; null
  
  Ошибки.
  
  Если хотя бы по одному товару есть ошибка, информация в каталоге не обновится по всем переданным товарам.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "UNKNOWN_CATEGORY",
      "parameterId": 0,
      "message": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _warnings_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OfferMappingErrorDTO](#entity-OfferMappingErrorDTO)[] &#124; null
  
  Предупреждения.
  
  Информация в каталоге обновится.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "type": "UNKNOWN_CATEGORY",
      "parameterId": 0,
      "message": "example"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "offerId": "example",
    "errors": [
      {
        "type": "UNKNOWN_CATEGORY",
        "parameterId": 0,
        "message": "example"
      }
    ],
    "warnings": [
      null
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  ⚠️ Даже если проблема связана всего с одним товаром в запросе, в каталог не отправится ни один.
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с товарами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#offers) и [об ошибках при работе с ценами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#prices)
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiErrorDTO {#entity-ApiErrorDTO}
  
  Общий формат ошибки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Код ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _message_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Описание ошибки.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "code": "example",
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiErrorResponse {#entity-ApiErrorResponse}
  
  Стандартная обертка для ошибок сервера.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiResponse](#entity-ApiResponse)
  
    Стандартная обертка для ответов сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _errors_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [ApiErrorDTO](#entity-ApiErrorDTO)[] &#124; null
  
    Список ошибок.
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "code": "example",
        "message": "example"
      }
    ]
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__401">
  
  ## 401 Unauthorized
  
  В запросе не указаны данные для авторизации. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#401)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__403">
  
  ## 403 Forbidden
  
  Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#403)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__404">
  
  ## 404 Not Found
  
  Запрашиваемый ресурс не найден. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#404)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__420">
  
  ## 420 Method Failure
  
  Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#420)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__423">
  
  ## 423 Locked
  
  К ресурсу нельзя применить указанный метод. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#423)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__500">
  
  ## 500 Internal Server Error
  
  Внутренняя ошибка Маркета. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#500)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "example",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiErrorResponse](#entity-ApiErrorResponse)
  
    Стандартная обертка для ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "example",
          "message": "example"
        }
      ]
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  </div>
  
  </div>
        

- Console

  ```openapi-sandbox translate=no
  pathParams:
    - description: "Идентификатор кабинета.\n\n{% if audience == \"partner\" %}\n\nЧтобы его узнать, воспользуйтесь запросом [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md).\n\nℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html)\n\n{% endif %}\n"
      name: businessId
      in: path
      required: true
      schema:
        type: integer
        format: int64
        minimum: 1
  searchParams:
    - description: >
        Язык, на котором принимаются и возвращаются значения в параметрах `name` и
        `description`.
  
  
        Значение по умолчанию: `RU`.
      name: language
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/CatalogLanguageType
  headers: []
  body: |-
    {
      "offerMappings": [
        {
          "offer": {
            "offerId": "example",
            "name": "Ударная дрель Makita HP1630, 710 Вт",
            "marketCategoryId": 0,
            "category": "example",
            "pictures": [
              null
            ],
            "videos": [
              null
            ],
            "manuals": [
              null
            ],
            "vendor": "LEVENHUK",
            "barcodes": [
              null
            ],
            "description": "example",
            "manufacturerCountries": [
              null
            ],
            "weightDimensions": {},
            "vendorCode": "VNDR-0005A",
            "tags": [
              null
            ],
            "shelfLife": {},
            "lifeTime": null,
            "guaranteePeriod": null,
            "customsCommodityCode": "8517610008",
            "commodityCodes": [
              null
            ],
            "certificates": [
              null
            ],
            "boxCount": 1,
            "condition": {},
            "type": "DEFAULT",
            "downloadable": true,
            "adult": true,
            "age": {},
            "params": [
              null
            ],
            "parameterValues": [
              null
            ],
            "basicPrice": {},
            "purchasePrice": {},
            "additionalExpenses": null,
            "firstVideoAsCover": true,
            "deleteParameters": [
              null
            ]
          },
          "mapping": {
            "marketSku": 1
          }
        }
      ],
      "onlyPartnerMediaContent": true
    }
  schema:
    type: object
    required:
      - offerMappings
    properties:
      offerMappings:
        description: "Список товаров, которые нужно добавить или обновить.\n\n{% note warning \"Скоро мы уменьшим максимальное количество товаров в запросе\" %}\n\nУже сейчас не передавайте больше 100.\n\n{% endnote %}\n\n\_\n"
        type: array
        minItems: 1
        maxItems: 500
        items:
          description: Информация о товаре.
          type: object
          required:
            - offer
          properties:
            offer:
              description: Параметры товара.
              $ref: '#/$defs/UpdateOfferDTO'
            mapping:
              description: Информация о карточке товара на Маркете.
              $ref: '#/$defs/UpdateMappingDTO'
      onlyPartnerMediaContent:
        description: >
          Будут ли использоваться только переданные вами данные о товарах.
  
  
          Значение по умолчанию: `false`. Чтобы удалить данные, которые добавил
          Маркет, передайте значение `true`.
        type: boolean
    $defs:
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/InternalOfferId:
        description: >-
          Внутренний идентификатор товара в системах Маркета. Нужен для создания
          товаров Лавки с отличными offerId и article.
        type: string
        minLength: 1
        maxLength: 255
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/Url:
        type: string
        minLength: 1
        maxLength: 2000
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/OfferWeightDimensionsDTO:
        description: >
          Габариты упаковки и вес товара.
  
  
          Если товар занимает несколько коробок, перед измерением размеров сложите
          их компактно.
  
  
          ![Схема измерения многоместных
          грузов](../../_images/reference/boxes-measure.png)
        type: object
        required:
          - length
          - width
          - height
          - weight
        properties:
          length:
            description: |
              Длина упаковки в см.
            example: 65.55
            type: number
            minimum: 0
          width:
            description: |
              Ширина упаковки в см.
            example: 50.7
            type: number
            minimum: 0
          height:
            description: |
              Высота упаковки в см.
            example: 20
            type: number
            minimum: 0
          weight:
            description: |
              Вес товара в кг с учетом упаковки (брутто).
            example: 1.001
            type: number
            minimum: 0
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/TimeUnitType:
        description: |
          Единица измерения времени:
  
          * `HOUR` — час.
          * `DAY` — сутки.
          * `WEEK` — неделя.
          * `MONTH` — месяц.
          * `YEAR` — год.
        type: string
        enum:
          - HOUR
          - DAY
          - WEEK
          - MONTH
          - YEAR
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/TimePeriodDTO:
        description: >-
          Временной отрезок с комментарием. Требования к содержанию комментария
          зависят от контекста использования параметра и указаны в описании поля,
          которое его содержит.
        type: object
        required:
          - timePeriod
          - timeUnit
        properties:
          timePeriod:
            description: Продолжительность в указанных единицах.
            type: integer
          timeUnit:
            description: Единица измерения.
            $ref: '#/$defs/TimeUnitType'
          comment:
            description: Комментарий.
            type: string
            maxLength: 500
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/CommodityCodeType:
        description: >
          Тип товарного кода:
  
  
          * `CUSTOMS_COMMODITY_CODE` — код товара в единой Товарной номенклатуре
          внешнеэкономической деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  
          * `IKPU_CODE` — идентификационный код продукции и услуг (ИКПУ) в
          Узбекистане – 17 цифр без пробелов.
  
          * `OKPD2_CODE` — код по Общероссийскому классификатору продукции по
          видам экономической деятельности (ОКПД2) — 2, 3, 4, 5, 6 или 9 цифр,
          разделенных точками: XX, XX.X, XX.XX, XX.XX.X, XX.XX.XX или
          XX.XX.XX.XXX.
  
  
          Не передавайте несколько кодов одного типа.
        type: string
        enum:
          - CUSTOMS_COMMODITY_CODE
          - IKPU_CODE
          - OKPD2_CODE
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/OfferConditionType:
        description: >
          Тип уценки:
  
  
          * `PREOWNED` —  бывший в употреблении товар, раньше принадлежал другому
          человеку.
  
          * `SHOWCASESAMPLE` — витринный образец.
  
          * `REFURBISHED` — повторная продажа товара.
  
          * `REDUCTION` — товар с дефектами.
  
          * `RENOVATED` — восстановленный товар.
  
          * `NOT_SPECIFIED` — не выбран.
  
  
          `REFURBISHED` — специальное значение для одежды, обуви и аксессуаров.
          Используется только для уцененных товаров из этой категории. Другие
          значения для одежды, обуви и аксессуаров не используются.
        type: string
        enum:
          - PREOWNED
          - SHOWCASESAMPLE
          - REFURBISHED
          - REDUCTION
          - RENOVATED
          - NOT_SPECIFIED
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/OfferConditionQualityType:
        description: |
          Внешний вид товара:
  
          * `PERFECT` — идеальный.
          * `EXCELLENT` — отличный.
          * `GOOD` — хороший.
          * `NOT_SPECIFIED` — не выбран.
        type: string
        enum:
          - PERFECT
          - EXCELLENT
          - GOOD
          - NOT_SPECIFIED
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/OfferConditionDTO:
        description: |
          Состояние уцененного товара.
        type: object
        properties:
          type:
            description: |
              Тип уценки.
            $ref: '#/$defs/OfferConditionType'
          quality:
            description: |
              Внешний вид товара.
            $ref: '#/$defs/OfferConditionQualityType'
          reason:
            description: >
              Описание товара. Подробно опишите дефекты, насколько они заметны и
              где их искать.
            type: string
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/OfferType:
        description: "Особый тип товара:\n\n* `DEFAULT` — товары, для которых вы передавали особый тип ранее и хотите убрать его.\n* `MEDICINE` — лекарства.\n* `BOOK` — бумажные и электронные книги.\n* `AUDIOBOOK` — аудиокниги.\n* `ARTIST_TITLE` — музыкальная и видеопродукция.\n* `ON_DEMAND` — товары на заказ.\n* `ALCOHOL` — алкоголь.\n\n{% note info \"Если ваш товар —\_книга\" %}\n\nУкажите год издания в характеристиках товара. [Подробнее о параметре](../../reference/business-offer-mappings/updateOfferMappings.md#offerparamdto)\n\n{% endnote %}\n"
        type: string
        enum:
          - DEFAULT
          - MEDICINE
          - BOOK
          - AUDIOBOOK
          - ARTIST_TITLE
          - ON_DEMAND
          - ALCOHOL
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/AgeUnitType:
        description: |
          Единицы измерения возраста:
  
          * `YEAR` — год.
          * `MONTH` — месяц.
        type: string
        enum:
          - YEAR
          - MONTH
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/AgeDTO:
        description: Возраст в заданных единицах измерения.
        type: object
        required:
          - value
          - ageUnit
        properties:
          value:
            description: |
              Значение.
            type: number
            minimum: 0
          ageUnit:
            description: |
              Единица измерения.
            $ref: '#/$defs/AgeUnitType'
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/CurrencyType:
        type: string
        description: |
          Коды валют:
  
          * `RUR` — российский рубль.
          * `UAH` — украинская гривна.
          * `BYR` — белорусский рубль.
          * `KZT` — казахстанский тенге.
          * `UZS` — узбекский сум.
        enum:
          - RUR
          - USD
          - EUR
          - UAH
          - AUD
          - GBP
          - BYR
          - BYN
          - DKK
          - ISK
          - KZT
          - CAD
          - CNY
          - NOK
          - XDR
          - SGD
          - TRY
          - SEK
          - CHF
          - JPY
          - AZN
          - ALL
          - DZD
          - AOA
          - ARS
          - AMD
          - AFN
          - BHD
          - BGN
          - BOB
          - BWP
          - BND
          - BRL
          - BIF
          - HUF
          - VEF
          - KPW
          - VND
          - GMD
          - GHS
          - GNF
          - HKD
          - GEL
          - AED
          - EGP
          - ZMK
          - ILS
          - INR
          - IDR
          - JOD
          - IQD
          - IRR
          - YER
          - QAR
          - KES
          - KGS
          - COP
          - CDF
          - CRC
          - KWD
          - CUP
          - LAK
          - LVL
          - SLL
          - LBP
          - LYD
          - SZL
          - LTL
          - MUR
          - MRO
          - MKD
          - MWK
          - MGA
          - MYR
          - MAD
          - MXN
          - MZN
          - MDL
          - MNT
          - NPR
          - NGN
          - NIO
          - NZD
          - OMR
          - PKR
          - PYG
          - PEN
          - PLN
          - KHR
          - SAR
          - RON
          - SCR
          - SYP
          - SKK
          - SOS
          - SDG
          - SRD
          - TJS
          - THB
          - TWD
          - BDT
          - TZS
          - TND
          - TMM
          - UGX
          - UZS
          - UYU
          - PHP
          - DJF
          - XAF
          - XOF
          - HRK
          - CZK
          - CLP
          - LKR
          - EEK
          - ETB
          - RSD
          - ZAR
          - KRW
          - NAD
          - TL
          - UE
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/catalog-common-schemas.yaml#/PriceWithDiscountDTO:
        description: Цена с указанием скидки.
        type: object
        allOf:
          - description: Цена товара.
            type: object
            required:
              - value
              - currencyId
            properties:
              value:
                description: Цена товара.
                type: number
                minimum: 0
                exclusiveMinimum: true
              currencyId:
                description: Валюта.
                $ref: '#/$defs/CurrencyType'
          - properties:
              discountBase:
                description: >
                  Зачеркнутая цена.
  
  
                  Число должно быть целым. Вы можете указать цену со скидкой от 5
                  до 99%.
  
  
                  Передавайте этот параметр при каждом обновлении цены, если
                  предоставляете скидку на товар.
                type: number
                minimum: 0
                exclusiveMinimum: true
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/catalog-common-schemas.yaml#/BasePriceDTO:
        description: Цена товара.
        type: object
        required:
          - value
          - currencyId
        properties:
          value:
            description: Цена товара.
            type: number
            minimum: 0
            exclusiveMinimum: true
          currencyId:
            description: Валюта.
            $ref: '#/$defs/CurrencyType'
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/api/updateOfferMappings.yaml#/UpdateOfferDTO:
        description: Параметры товара.
        type: object
        allOf:
          - description: Основные параметры товара.
            type: object
            required:
              - offerId
            properties:
              offerId:
                description: "Ваш SKU —\_идентификатор товара в вашей системе.\n\nПравила использования SKU:\n\n* У каждого товара SKU должен быть свой.\n\n* Уже заданный SKU нельзя освободить и использовать заново для другого товара. Каждый товар должен получать новый идентификатор, до того никогда не использовавшийся в вашем каталоге.\n\nSKU товара можно изменить в кабинете продавца на Маркете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/assortment/operations/edit-sku).\n\n{% note warning %}\n\nПробельные символы в начале и конце значения автоматически удаляются. Например, `\"  SKU123  \"` и `\"SKU123\"` будут обработаны как одинаковые значения.\n\n{% endnote %}\n\n[Что такое SKU и как его назначать](https://yandex.ru/support/marketplace/assortment/add/index.html#fields)\n"
                type: string
                pattern: ^(?=.*\S.*)[^\x00-\x08\x0A-\x1f\x7f]{1,255}$
                x-transform: trim
                minLength: 1
                maxLength: 255
              internalOfferId:
                x-hidden: true
                $ref: '#/$defs/InternalOfferId'
              deeplink:
                description: Слаг товара в Лавке. Используется для поиска товара.
                type: string
                minLength: 1
                maxLength: 255
                x-hidden: true
              platformSku:
                description: Идентификатор карточки товара в Еде.
                type: string
                minLength: 1
                maxLength: 255
                x-hidden: true
              name:
                description: >
                  Составляйте название по схеме: тип + бренд или производитель +
                  модель + особенности, если есть (например, цвет, размер или вес)
                  и количество в упаковке.
  
  
                  Не включайте в название условия продажи (например, «скидка»,
                  «бесплатная доставка» и т. д.), эмоциональные характеристики
                  («хит», «супер» и т. д.). Не пишите слова большими буквами —
                  кроме устоявшихся названий брендов и моделей.
  
  
                  Оптимальная длина — 50–60 символов.
  
  
                  [Рекомендации и
                  правила](https://yandex.ru/support/marketplace/assortment/fields/title.html)
                example: Ударная дрель Makita HP1630, 710 Вт
                type: string
                maxLength: 256
              marketCategoryId:
                description: "Идентификатор категории на Маркете, к которой вы относите свой товар.\n\n{% note warning \"Всегда указывайте, когда передаете `parameterValues`\" %}\n\nЕсли при изменении характеристик передать `parameterValues` и не указать `marketCategoryId`, характеристики обновятся, но в ответе придет предупреждение (параметр `warnings`).\n\nЕсли не передать их оба, будет использована информация из устаревших параметров `params` и `category`, а `marketCategoryId` будет определен автоматически.\n\n{% endnote %}\n\nПри изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории.\n\nСписок категорий Маркета можно получить с помощью запроса  [POST\_v2/categories/tree](../../reference/categories/getCategoriesTree.md).\n"
                type: integer
                format: int64
                minimum: 0
                exclusiveMinimum: true
              category:
                description: >
                  {% note warning "Параметр устарел и будет отключен 12.10.2026."
                  %}
  
  
                  Вместо него используйте `marketCategoryId`.
  
  
                  {% endnote %}
  
  
                  Категория товара в вашем магазине.
                type: string
                deprecated: true
                x-deprecation-config:
                  shutdown-date: '2026-10-12'
                  replacement-field: marketCategoryId
              pictures:
                description: >
                  Ссылки на изображения товара. Изображение по первой ссылке
                  считается основным, остальные дополнительными.
  
  
                  **Требования к ссылкам**
  
  
                  * Указывайте ссылку целиком, включая протокол http или https.
  
                  * Русские буквы в URL можно.
  
                  * Можно использовать прямые ссылки на изображения и на Яндекс
                  Диск. Ссылки на Яндекс Диске нужно копировать с помощью функции
                  **Поделиться**. Относительные ссылки и ссылки на другие облачные
                  хранилища — не работают.
  
  
                  ✅ `https://example-shop.ru/images/sku12345.jpg`
  
  
                  ✅ `https://yadi.sk/i/NaBoRsimVOLov`
  
  
                  ❌ `/images/sku12345.jpg`
  
  
                  ❌ `https://www.dropbox.com/s/818f/tovar.jpg`
  
  
                  Ссылки на изображение должны быть постоянными. Нельзя
                  использовать динамические ссылки, меняющиеся от выгрузки к
                  выгрузке.
  
  
                  Если нужно заменить изображение, выложите новое изображение по
                  новой ссылке, а ссылку на старое удалите. Если просто заменить
                  изображение по старой ссылке, оно не обновится.
  
  
                  [Требования к
                  изображениям](https://yandex.ru/support/marketplace/assortment/fields/images.html)
                type: array
                nullable: true
                minItems: 1
                maxItems: 30
                uniqueItems: false
                items:
                  type: string
                  minLength: 1
                  maxLength: 2000
              videos:
                description: >
                  Ссылки (URL) на видео товара.
  
  
                  **Требования к ссылке**
  
  
                  * Указывайте ссылку целиком, включая протокол http или https.
  
                  * Русские буквы в URL можно.
  
                  * Можно использовать прямые ссылки на видео и на Яндекс Диск.
                  Ссылки на Яндекс Диске нужно копировать с помощью функции
                  **Поделиться**. Относительные ссылки и ссылки на другие облачные
                  хранилища — не работают.
  
  
                  ✅ `https://example-shop.ru/video/sku12345.avi`
  
  
                  ✅ `https://yadi.sk/i/NaBoRsimVOLov`
  
  
                  ❌ `/video/sku12345.avi`
  
  
                  ❌ `https://www.dropbox.com/s/818f/super-tovar.avi`
  
  
                  Ссылки на видео должны быть постоянными. Нельзя использовать
                  динамические ссылки, меняющиеся от выгрузки к выгрузке.
  
  
                  Если нужно заменить видео, выложите новое видео по новой ссылке,
                  а ссылку на старое удалите. Если просто заменить видео по старой
                  ссылке, оно не обновится.
  
  
                  [Требования к
                  видео](https://yandex.ru/support/marketplace/assortment/fields/video.html)
                type: array
                nullable: true
                minItems: 1
                maxItems: 6
                uniqueItems: false
                items:
                  type: string
                  minLength: 1
                  maxLength: 2000
              manuals:
                description: |
                  Список инструкций по использованию товара.
                type: array
                nullable: true
                minItems: 1
                maxItems: 6
                items:
                  type: object
                  required:
                    - url
                  description: |
                    Инструкция по использованию товара.
                  properties:
                    url:
                      description: Ссылка на инструкцию.
                      $ref: '#/$defs/Url'
                    title:
                      description: >
                        Название инструкции, которое будет отображаться на
                        карточке товара.
                      type: string
                      maxLength: 500
              vendor:
                description: >-
                  Название бренда или производителя. Должно быть записано так, как
                  его пишет сам бренд.
                example: LEVENHUK
                type: string
              barcodes:
                description: >
                  Штрихкод.
  
  
                  Указывайте в виде последовательности цифр. Подойдут коды
                  EAN-13, EAN-8, UPC-A, UPC-E или
                  Code 128. Для книг — ISBN.
  
  
                  Для товаров [определенных категорий и торговых
                  марок](https://yastatic.net/s3/doc-binary/src/support/market/ru/yandex-market-list-for-gtin.xlsx)
                  штрихкод должен быть действительным кодом GTIN.
                  Обратите внимание: внутренние штрихкоды, начинающиеся на 2 или
                  02, и коды формата Code 128 не являются
                  GTIN.
  
  
                  [Что такое GTIN](*gtin)
                type: array
                nullable: true
                minItems: 1
                uniqueItems: true
                items:
                  type: string
                  example: '46012300000000'
              description:
                description: >
                  Подробное описание товара: например, его преимущества и
                  особенности.
  
  
                  Не давайте в описании инструкций по установке и сборке. Не
                  используйте слова «скидка», «распродажа», «дешевый», «подарок»
                  (кроме подарочных категорий), «бесплатно», «акция», «специальная
                  цена», «новинка», «new», «аналог», «заказ», «хит». Не указывайте
                  никакой контактной информации и не давайте ссылок.
  
  
                  Для форматирования текста можно использовать теги HTML:
  
  
                  * \<h>, \<h1>, \<h2> и так далее — для заголовков;
  
                  * \<br> и \<p> — для переноса строки;
  
                  * \<ol> — для нумерованного списка;
  
                  * \<ul> — для маркированного списка;
  
                  * \<li> — для создания элементов списка (должен находиться
                  внутри \<ol> или \<ul>);
  
                  * \<div> — поддерживается, но не влияет на отображение текста.
  
  
                  Оптимальная длина — 400–600 символов.
  
  
                  [Рекомендации и
                  правила](https://yandex.ru/support/marketplace/assortment/fields/description.html)
                type: string
                maxLength: 6000
              manufacturerCountries:
                description: >
                  Страна, где был произведен товар.
  
  
                  Записывайте названия стран так, как они записаны в
                  [списке](https://yastatic.net/s3/doc-binary/src/support/market/ru/countries.xlsx).
                type: array
                nullable: true
                minItems: 1
                uniqueItems: true
                items:
                  type: string
                  example: Россия
              weightDimensions:
                description: |
                  Габариты упаковки и вес товара.
  
                  Должны быть больше 0.
                $ref: '#/$defs/OfferWeightDimensionsDTO'
              vendorCode:
                description: Артикул товара от производителя.
                example: VNDR-0005A
                type: string
              tags:
                description: >
                  Метки товара, которые использует магазин. Покупателям теги не
                  видны. По тегам можно группировать и фильтровать разные товары в
                  каталоге — например, товары одной серии, коллекции или линейки.
  
  
                  Максимальная длина тега — 20 символов. У одного товара может
                  быть максимум 10 тегов.
                type: array
                nullable: true
                minItems: 1
                maxItems: 50
                uniqueItems: true
                items:
                  type: string
                  example: до 500 рублей
              shelfLife:
                description: >
                  Срок годности — период, по прошествии которого товар становится
                  непригоден.
  
  
                  Указывайте срок, указанный на банке или упаковке. Текущая дата,
                  дата поставки или дата отгрузки значения не имеет.
  
  
                  Обязательно указывайте срок, если он есть.
  
  
                  В комментарии укажите условия хранения. Например, `Хранить в
                  сухом помещении`.
                $ref: '#/$defs/TimePeriodDTO'
              lifeTime:
                description: >
                  Срок службы — период, в течение которого товар должен исправно
                  выполнять свою функцию.
  
  
                  Обязательно указывайте срок, если он есть.
  
  
                  В комментарии укажите условия хранения. Например, `Использовать
                  при температуре не ниже −10 градусов`.
                $ref: '#/$defs/TimePeriodDTO'
              guaranteePeriod:
                description: >
                  Гарантийный срок — период, в течение которого можно заменить или
                  починить товар без дополнительной платы.
  
  
                  Обязательно указывайте срок, если он есть.
  
  
                  В комментарии опишите особенности гарантийного обслуживания.
                  Например, `Гарантия на аккумулятор — 6 месяцев`.
                $ref: '#/$defs/TimePeriodDTO'
              customsCommodityCode:
                description: >
                  {% note warning "Параметр устарел и будет отключен 12.10.2026."
                  %}
  
  
                  Вместо него используйте `commodityCodes` с типом
                  `CUSTOMS_COMMODITY_CODE`.
  
  
                  {% endnote %}
  
  
                  Код товара в единой Товарной номенклатуре внешнеэкономической
                  деятельности (ТН ВЭД) — 10 или 14 цифр без пробелов.
  
  
                  Обязательно укажите, если он есть.
                deprecated: true
                x-deprecation-config:
                  shutdown-date: '2026-10-12'
                  replacement-field: commodityCodes
                example: '8517610008'
                type: string
              commodityCodes:
                description: |
                  Товарные коды.
                type: array
                nullable: true
                minItems: 1
                items:
                  description: Товарный код.
                  type: object
                  required:
                    - code
                    - type
                  properties:
                    code:
                      description: Товарный код.
                      type: string
                    type:
                      description: Тип товарного кода.
                      $ref: '#/$defs/CommodityCodeType'
              certificates:
                description: "Номера документов на товар: сертификата, декларации соответствия и т. п.\n\nДокументы можно создать с помощью [POST\_v1/businesses/{businessId}/offers/documents/create](../../reference/documents/createDocuments.md).\n"
                type: array
                nullable: true
                minItems: 1
                maxItems: 6
                uniqueItems: true
                items:
                  type: string
              boxCount:
                description: >
                  Количество грузовых мест.
  
  
                  Параметр используется, если товар представляет собой несколько
                  коробок, упаковок и так далее. Например, кондиционер занимает
                  два места — внешний и внутренний блоки в двух коробках.
  
  
                  Для товаров, занимающих одно место, не передавайте этот
                  параметр.
                type: integer
                format: int32
                minimum: 1
              condition:
                description: >
                  Состояние уцененного товара.
  
  
                  Используется только для товаров, продаваемых с уценкой.
  
  
                  [Правила продажи уцененных
                  товаров](https://yandex.ru/support/marketplace/assortment/restrictions/used-goods.html)
                $ref: '#/$defs/OfferConditionDTO'
              type:
                description: |
                  Особый тип товара. Указывается, если товар:
  
                  * имеет особый тип, который хотите убрать;
                  * лекарство;
                  * бумажная или электронная книга;
                  * аудиокнига;
                  * музыка или видео;
                  * изготовляется на заказ;
                  * алкоголь.
                $ref: '#/$defs/OfferType'
              downloadable:
                description: >
                  Признак цифрового товара. Укажите `true`, если товар
                  доставляется по электронной почте.
  
  
                  [Как работать с цифровыми
                  товарами](../../step-by-step/digital.md)
                type: boolean
              adult:
                description: >
                  Параметр включает для товара пометку 18+. Устанавливайте ее
                  только для товаров, которые относятся к удовлетворению
                  сексуальных потребностей.
                type: boolean
              age:
                description: >
                  Если товар не предназначен для детей младше определенного
                  возраста, укажите это.
  
  
                  Возрастное ограничение можно задавать в годах (с нуля, с 6, 12,
                  16 или 18) или в месяцах (любое число от 0 до 12).
                $ref: '#/$defs/AgeDTO'
              params:
                description: >
                  {% note warning "Параметр устарел и будет отключен 12.10.2026."
                  %}
  
  
                  При передаче характеристик используйте `parameterValues`.
  
  
                  {% endnote %}
  
  
                  Характеристики, которые есть только у товаров конкретной
                  категории — например, диаметр колес велосипеда или материал
                  подошвы обуви.
                type: array
                nullable: true
                minItems: 1
                deprecated: true
                x-deprecation-config:
                  shutdown-date: '2026-10-12'
                  replacement-field: parameterValues
                items:
                  description: >
                    Параметры товара.
  
  
                    Если у товара несколько значений одного параметра, передайте
                    их с одним и тем же `name`, но разными `value`.
  
  
                    {% cut "Пример" %}
  
  
                    ```json translate=no
  
                    "params": [
                      {
                        "name": "Цвет для фильтра",
                        "value": "Зеленый"
                      },
                      {
                        "name": "Цвет для фильтра",
                        "value": "Желтый"
                      }
                    ]
  
                    ```
  
  
                    {% endcut %}
                  type: object
                  required:
                    - name
                    - value
                  properties:
                    name:
                      description: "Название характеристики.\n\nДолжно совпадать с названием характеристики на Маркете. Узнать его можно из Excel-шаблона категории или через запрос [POST\_v2/category/{categoryId}/parameters](../content/getCategoryContentParameters.md).\n"
                      example: Wi-Fi
                      type: string
                      maxLength: 200
                    value:
                      description: |
                        Значение.
                      example: есть
                      type: string
          - properties:
              parameterValues:
                description: >
                  Список характеристик с их значениями.
  
  
                  {% note warning "Всегда передавайте вместе с `marketCategoryId`"
                  %}
  
  
                  Если не передать `marketCategoryId` при изменении характеристик,
                  они обновятся, но в ответе придет предупреждение (параметр
                  `warnings`).
  
  
                  Если не передать их оба, будет использована информация из
                  устаревших параметров `params` и `category`, а
                  `marketCategoryId` будет определен автоматически.
  
  
                  {% endnote %}
  
  
                  При **изменении** характеристик передавайте только те, значение
                  которых нужно обновить. Если в `marketCategoryId` вы меняете
                  категорию, значения общих характеристик для старой и новой
                  категории сохранятся, передавать их не нужно.
  
  
                  Подробнее читайте в [«Передача значений
                  характеристики»](../../step-by-step/parameter-values.md).
                type: array
                nullable: true
                minItems: 1
                maxItems: 300
                items:
                  description: |
                    Значение характеристики.
                  type: object
                  required:
                    - parameterId
                  properties:
                    parameterId:
                      description: Идентификатор характеристики.
                      type: integer
                      format: int64
                      minimum: 1
                    unitId:
                      description: >-
                        Идентификатор единицы измерения. Если вы не передали
                        параметр `unitId`, используется единица измерения по
                        умолчанию.
                      type: integer
                      format: int64
                    valueId:
                      description: >
                        Идентификатор значения.
  
  
                        - Обязательно указывайте идентификатор, если передаете
                        значение из перечня допустимых значений, полученного от
                        Маркета.
  
                        - Не указывайте для собственных значений.
  
                        - Только для характеристик типа `ENUM`.
                      type: integer
                      format: int64
                    value:
                      description: |
                        Значение.
  
                        Для характеристик типа `ENUM` передавайте:
                        - вместе с `valueId`, если значение берете из справочника;
                        - без `valueId`, если значение собственное.
                      type: string
              basicPrice:
                description: |
                  Цена.
                $ref: '#/$defs/PriceWithDiscountDTO'
              purchasePrice:
                description: >-
                  Себестоимость — затраты на самостоятельное производство товара
                  или закупку у производителя или поставщиков.
                $ref: '#/$defs/BasePriceDTO'
              additionalExpenses:
                description: >-
                  Дополнительные расходы на товар. Например, на доставку или
                  упаковку.
                $ref: '#/$defs/BasePriceDTO'
              firstVideoAsCover:
                deprecated: true
                x-deprecation-config:
                  shutdown-date: '2026-10-12'
                description: "{% note warning \"Параметр устарел и будет отключен 12.10.2026.\" %}\n\n\_\n\n{% endnote %}\n\nИспользовать первое видео в карточке как видеообложку.\n\nПередайте `true`, чтобы первое видео использовалось как видеообложка, или `false`, чтобы видеообложка не отображалась в карточке товара.\n"
                type: boolean
              deleteParameters:
                description: "Параметры, которые вы ранее передали в `UpdateOfferDTO`, а теперь хотите удалить.\n\nЕсли передать `adult`, `downloadable` и `firstVideoAsCover`, они не удалятся —\_их значение изменится на `false`.\n\nМожно передать сразу несколько значений.\n\nНе используйте вместе с соответствующим параметром в `UpdateOfferDTO`. Это приведет к ошибке `400`.\n"
                type: array
                nullable: true
                minItems: 1
                uniqueItems: true
                items:
                  description: >
                    Значения параметров, которые хотите удалить, и соответствующие
                    параметры в `UpdateOfferDTO`, в которых вы передали эти
                    значения ранее:
  
  
                    * `ADDITIONAL_EXPENSES` — дополнительные расходы на товар
                    (параметр `additionalExpenses`).
  
                    * `ADULT` — пометка 18+ (параметр `adult`)
  
                    * `AGE` — возрастное ограничение для детей (параметр `age`).
  
                    * `BARCODES` — штрихкод (параметр `barcodes`).
  
                    * `BOX_COUNT` — количество грузовых мест (параметр
                    `boxCount`).
  
                    * `CERTIFICATES` — номера документов на товар (параметр
                    `certificates`).
  
                    * `COMMODITY_CODES` — товарные коды (параметр
                    `commodityCodes`).
  
                    * `CONDITION` — состояние уцененного товара (параметр
                    `condition`).
  
                    * `CUSTOMS_COMMODITY_CODE` — код товара в ТН ВЭД (параметр
                    `customsCommodityCode`).
  
                    * `DESCRIPTION` — описание товара (параметр `description`).
  
                    * `DOWNLOADABLE` — признак цифрового товара (параметр
                    `downloadable`).
  
                    * `GUARANTEE_PERIOD` — гарантийный срок (параметр
                    `guaranteePeriod`).
  
                    * `LIFE_TIME` — срок службы (параметр `lifeTime`).
  
                    * `MANUALS` — список инструкций по использованию товара
                    (параметр `manuals`).
  
                    * `MANUFACTURER_COUNTRIES` — страна производства (параметр
                    `manufacturerCountries`).
  
                    * `PARAMETERS` — характеристики товара (параметры `params`,
                    `parameterValues`).
  
                    * `PICTURES` — ссылки на изображения товара (параметр
                    `pictures`).
  
                    * `PURCHASE_PRICE` — себестоимость (параметр `purchasePrice`).
  
                    * `SHELF_LIFE` — срок годности (параметр `shelfLife`).
  
                    * `TAGS` — метки товара, которые использует магазин (параметр
                    `tags`).
  
                    * `TYPE` — особый тип товара (параметр `type`).
  
                    * `VENDOR_CODE` — название бренда или производителя (параметр
                    `vendorCode`).
  
                    * `VIDEOS` — ссылки на видео товара (параметр `videos`).
                  type: string
                  enum:
                    - ADDITIONAL_EXPENSES
                    - ADULT
                    - AGE
                    - BARCODES
                    - BOX_COUNT
                    - CERTIFICATES
                    - COMMODITY_CODES
                    - CONDITION
                    - CUSTOMS_COMMODITY_CODE
                    - DESCRIPTION
                    - DOWNLOADABLE
                    - GUARANTEE_PERIOD
                    - LIFE_TIME
                    - MANUALS
                    - MANUFACTURER_COUNTRIES
                    - PARAMETERS
                    - PICTURES
                    - PURCHASE_PRICE
                    - SHELF_LIFE
                    - TAGS
                    - TYPE
                    - VENDOR_CODE
                    - VIDEOS
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/MarketSku:
        description: Идентификатор карточки товара на Маркете.
        type: integer
        format: int64
        minimum: 1
      /home/sandbox/.ya/build/build_root/m8ef/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/business-offer-mappings/schemas.yaml#/UpdateMappingDTO:
        description: >
          Карточка на Маркете, которая, с вашей точки зрения, подходит товару.
          Чтобы определить идентификатор подходящей карточки, воспользуйтесь
          поиском в кабинете (**Товары** → **Каталог** → **Загрузить товары**).
  
  
          По результатам проверки Маркет может привязать товар к более подходящей
          карточке.
        type: object
        properties:
          marketSku:
            description: |
              Идентификатор карточки на Маркете.
            $ref: '#/$defs/MarketSku'
  bodyType: application/json
  method: post
  security:
    - type: apiKey
      name: Api-Key
      in: header
    - type: oauth2
      x-inline: true
      flows:
        implicit:
          authorizationUrl: https://oauth.yandex.ru/authorize
          scopes:
            market:partner-api: API Яндекс.Маркета / Поиска по товарам для партнеров
  path: v2/businesses/{businessId}/offer-mappings/update
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>

[*Deprecated]: No longer supported, please use an alternative and newer version.
<!-- endsource: ru/api/business-offer-mappings/updateOfferMappings.md -->

[*gtin]:
<b>Что такое GTIN</b><br>GTIN — это уникальный номер, присвоенный товару в единой международной базе [GS1](https://ru.wikipedia.org/wiki/GS1). Из этого номера получается штрихкод формата EAN, UPC или ISBN.<br><br><b>Как убедиться, что товар есть в базе</b><br>Проверить код можно на [странице проверки](https://gepir.gs1.org/index.php/search-by-gtin) на сайте ассоциации GS1. Если товар не находится, запросите код GTIN у вашего поставщика.<br><br><b>Как получить GTIN для своих товаров</b><br>Чтобы получить коды GTIN, производителю нужно вступить в ассоциацию GS1 и зарегистрировать товары.

[*ascii-code]:
Запрещены ASCII символы с 0 по 31 (кроме 9) и 127 [из таблицы](https://www.ascii-code.com/compact).

[*list-categories]:
Категории, у которых нет дочерних.
