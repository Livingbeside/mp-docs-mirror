---
title: Подготовка заказа
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md"
fetched_at: "2026-09-15T02:21:51Z"
content_sha: ac6e5106075e051e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/orders/setOrderBoxLayout.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/orders/setOrderBoxLayout.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/orders/setOrderBoxLayout.md -->
<div class="openapi">

# Подготовка заказа

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/setOrderBoxLayout.md -->
  **Метод доступен для моделей: [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/setOrderBoxLayout.md -->
  
  {% note tip "Подходит и для DBS" %}
  
  Запрос предназначен для работы с FBS-заказами, но вы можете использовать его для обработки DBS-заказов, если это удобно.
  
  {% endnote %}
  
  Позволяет выполнить три операции:
  
  * передать Маркету информацию о распределении товаров по коробкам;
  * передать Маркету коды маркировки для товаров;
  * удалить товар из заказа, если его не оказалось на складе.
  
  Если нужно что-то поправить в переданных данных, просто повторите запрос — это можно делать сколько угодно раз до перевода заказа в статус **Готов к отгрузке**. ⚠️ Если вы меняете раскладку уже после печати и расклейки ярлыков, не забудьте перепечатать их и наклеить заново.
  
  {% cut "Как передать информацию о распределении товаров" %}
  
  В этом запросе вам нужно передать Маркету список коробок и указать, какие именно товары лежат в каждой из них. Коробки могут быть двух типов:
  
  * **Содержащие товары целиком.** Такая коробка может содержать сколько угодно единиц любых товаров.
  
  * **Содержащие часть товара.** Такие коробки содержат по одной части одного товара. Например, одна содержит внешний блок кондиционера, а другая — внутренний блок.
  
  ⚠️ Одна коробка не может содержать и товары целиком, и части товаров.
  
  {% endcut %}
  
  {% cut "Как передавать коды маркировки и получать статус их проверки" %}
  
  {% note info "Маркировка товаров в системе [«Честный ЗНАК»](https://честныйзнак.рф/) необязательна для заказов от физических лиц" %}
  
  Для заказов от бизнеса все еще нужно передавать коды маркировки.
  
  {% endnote %}
  
  Если в заказе есть товары, подлежащие маркировке, в запросе нужно передать соответствующие уникальные коды. [Что такое маркировка](https://yandex.ru/support/marketplace/orders/cz.html)
  
  Принимаются коды следующих типов:
  
  * Коды в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  * УИН для ювелирных изделий.
  * РНПТ и ГТД для импортных прослеживаемых товаров.
  
  Для каждой позиции в заказе, требующей маркировки, нужно передать список кодов — по одному для каждой единицы товара. Например, если в заказе две пары тапочек и одна пара туфель, получится список из двух кодов для первой позиции и список из одного кода для второй.
  
  Если товар едет в нескольких коробках, код маркировки нужно передать для каждой из них.
  
  {% note warning "Если вы работаете по модели FBS, EXPRESS" %}
  
  Для заказов, в которых есть ювелирные изделия или товары с маркировкой в системе «Честный ЗНАК», перевод в статус `READY_TO_SHIP` становится доступен, только когда:
  
  1. Вы передадите Маркету УИНы по каждому ювелирному изделию в заказе и коды в системе «Честный ЗНАК» по всем товарам в заказе, для которых обязательна эта маркировка.
  2. Все коды маркировки успешно пройдут проверку. [Как получить статусы проверки](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)
  
  {% endnote %}
  
  {% endcut %}
  
  {% cut "Как удалить товар из заказа" %}
  
  Чтобы удалить товар из заказа:
  
  1. Добавьте в запрос `allowRemove: true`.
  2. Передайте распределение по коробкам без товара, который нужно удалить.
  
  {% note warning "Удаление нельзя отменить" %}
  
  Эта операция необратима: покупатель сразу получит уведомление, а состав заказа изменится.
  
  {% endnote %}
  
  Чтобы удалить позицию целиком, не передавайте соответствующий `OrderBoxLayoutItemDTO`. Чтобы уменьшить количество товара, передайте уменьшенное значение в поле `fullCount`.
  
  Нельзя удалить или уменьшить количество товара, если он:
  
  * добавлен по акции;
  * составляет 99% стоимости заказа;
  * единственный товар в заказе.
  
  Если вы не можете отгрузить такой товар, отмените заказ. Для этого отправьте запрос методом [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) и передайте статус заказа `CANCELLED` с причиной отмены `SHOP_FAILED`.
  
  {% endcut %}
  
  {% note info "Увеличить заказ нельзя" %}
  
  С помощью запроса нельзя увеличить количество одинаковых товаров, добавить новые товары в заказ или заменить один товар другим.
  
  {% endnote %}
  
  ## Примеры
  
  {% cut "Товар умещается в коробку" %}
  
  Вот как будет выглядеть запрос, если в одной коробке едут:
  
    * три единицы одного товара, требующего маркировки;
    * одна единица другого товара, не требущего маркировки.
  
    ```json translate=no
    {
        "boxes": [
            {
                "items": [
                    {
                        "id": 123456,
                        "fullCount": 3,
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            },
                            {
                                "cis": "010304109478gftJ14545762!\u001dhGt264"
                            },
                            {
                                "cis": "010304109478fRs28323ks23!\u001dhet201"
                            }
                        ]
                    },
                    {
                        "id": 654321,
                        "fullCount": 1
                    }
                ]
            }
        ]
    }
    ```
  
  {% endcut %}
  
  {% cut "Товар едет в разных коробках" %}
  
  Вот как будет выглядеть запрос, если товар едет в двух коробках:
  
    ```json translate=no
    {
        "boxes": [
            {
                "items": [
                    {
                        "id": 123456,
                        "partialCount": {
                            "current": 1,
                            "total": 2
                        },
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            }
                        ]
                    }
                ]
            },
            {
                "items": [
                    {
                        "id": 123456,
                        "partialCount": {
                            "current": 2,
                            "total": 2
                        },
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            }
                        ]
                    }
                ]
            }
        ]
    }
    ```
  
  {% endcut %}
  
  {% cut "Одинаковые товары, где каждый едет в нескольких коробках" %}
  
  Вот как будет выглядеть запрос, если каждый из двух одинаковых товаров едет в двух коробках:
  
    ```json translate=no
    {
        "boxes": [
            {
                "items": [
                    {
                        "id": 123456,
                        "partialCount": {
                            "current": 1,
                            "total": 2
                        },
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            }
                        ]
                    }
                ]
            },
            {
                "items": [
                    {
                        "id": 123456,
                        "partialCount": {
                            "current": 2,
                            "total": 2
                        },
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            }
                        ]
                    }
                ]
            },
            {
                "items": [
                    {
                        "id": 123456,
                        "partialCount": {
                            "current": 1,
                            "total": 2
                        },
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            }
                        ]
                    }
                ]
            },
            {
                "items": [
                    {
                        "id": 123456,
                        "partialCount": {
                            "current": 2,
                            "total": 2
                        },
                        "instances": [
                            {
                                "cis": "01030410947874432155Qbag!\u001d93Zjqw"
                            }
                        ]
                    }
                ]
            }
        ]
    }
    ```
  
  {% endcut %}
  
  {% cut "Разные товары в разных коробках" %}
  
  Вот как будет выглядеть запрос, если два разных товара разложены по разным коробкам:
  
    ```json translate=no
    {
        "boxes": [
            {
                "items": [
                    {
                        "id": 123456,
                        "fullCount": 1
                    }
                ]
            },
            {
                "items": [
                    {
                        "id": 654321,
                        "fullCount": 1
                    }
                ]
            }
        ]
    }
    ```
  
  {% endcut %}
  
  <!-- source: ru/_auto/method_limits/setOrderBoxLayout.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/setOrderBoxLayout.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-put);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  PUT {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/boxes
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _campaignId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.
  
  Его можно узнать с помощью запроса [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:
  
  * блок **Идентификатор кампании**;
  * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.
  
  ⚠️ Не путайте его с:
  - идентификатором магазина, который отображается в личном кабинете продавца;
  - рекламными кампаниями.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _orderId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор заказа.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "boxes": [
      {
        "items": [
          {
            "id": 0,
            "fullCount": 1,
            "partialCount": {},
            "instances": [
              null
            ]
          }
        ]
      }
    ],
    "allowRemove": false
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _boxes_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderBoxLayoutDTO](#entity-OrderBoxLayoutDTO)[]
  
  Список коробок.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "items": [
        {
          "id": 0,
          "fullCount": 1,
          "partialCount": {
            "current": 1,
            "total": 2
          },
          "instances": [
            {}
          ]
        }
      ]
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _allowRemove_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Передайте `true`, если вы собираетесь удалить часть товаров из заказа.
  
  _Default:_{.json-schema-reset .json-schema-value} `false`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBoxLayoutPartialCountDTO {#entity-OrderBoxLayoutPartialCountDTO}
  
  Информация о части товара в коробке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _current_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Номер части, начиная с 1.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _total_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  На сколько всего частей разделен товар.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `2`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "current": 1,
    "total": 2
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### Cis {#entity-Cis}
  
  [Код идентификации](*cis-regular-value) единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  {% note warning "Не экранируйте косую черту в коде символа-разделителя `\u001d`" %}
  
  ✅ `01030410947874432155Qbag!\u001d93Zjqw`
  
  ❌ `01030410947874432155Qbag!\\u001d93Zjqw`
  
  Косые черты и кавычки в других местах экранируйте по правилам JSON: `\\` и `\"`
  
  {% endnote %}
  
  
  **Type**: string
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CountryCode {#entity-CountryCode}
  
  Страна производства в формате ISO 3166-1 alpha-2. [Как получить](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
  
  
  **Type**: string
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^[A-Z]{2}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `RU`
  
  </div>
  
  <div class="openapi-entity">
  
  ### BriefOrderItemInstanceDTO {#entity-BriefOrderItemInstanceDTO}
  
  Идентификатор единицы товара.
  
  Заполните только одно поле в зависимости от того, в какой системе маркирован товар.
  
  Подробно о работе с маркируемыми товарами читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/orders/cz.html).
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _cis_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [Cis](#entity-Cis)
  
  [Код идентификации](*cis-regular-value) единицы товара в системе [«Честный ЗНАК»](https://честныйзнак.рф/) или [«ASL BELGISI»](https://aslbelgisi.uz) (для продавцов Market Yandex Go).
  
  {% note warning "Не экранируйте косую черту в коде символа-разделителя `\u001d`" %}
  
  ✅ `01030410947874432155Qbag!\u001d93Zjqw`
  
  ❌ `01030410947874432155Qbag!\\u001d93Zjqw`
  
  Косые черты и кавычки в других местах экранируйте по правилам JSON: `\\` и `\"`
  
  {% endnote %}
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _countryCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CountryCode](#entity-CountryCode)
  
  Страна производства в формате ISO 3166-1 alpha-2. [Как получить](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/getRegionsCodes.md)
  
  
  _Min length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `2`
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^[A-Z]{2}$`
  
  _Example:_{.json-schema-reset .json-schema-example} `RU`
  {.table-cell}
  ||
  ||
  
  _gtd_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Грузовая таможенная декларация.
  
  Представляет собой строку из трех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ.
  
  Первая часть — код таможни, которая зарегистрировала декларацию на ввезенные товары. Далее — дата и номер декларации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _rnpt_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Регистрационный номер партии товара.
  
  Представляет собой строку из четырех чисел, разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ.
  
  Первая часть — код таможни, которая зарегистрировала декларацию на партию товара. Далее — дата, номер декларации и номер маркированного товара в декларации.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _uin_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Уникальный идентификационный номер ювелирного изделия.
  
  Представляет собой число из 16 цифр.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "cis": "example",
    "uin": "example",
    "rnpt": "example",
    "gtd": "example",
    "countryCode": "RU"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBoxLayoutItemDTO {#entity-OrderBoxLayoutItemDTO}
  
  Информация о товаре в коробке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор товара в заказе.
  
  Он приходит в ответе метода [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) — параметр `id` в `items`.
  
  {.table-cell}
  ||
  ||
  
  _fullCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество единиц товара в коробке.
  
  Используйте это поле, если в коробке поедут целые товары, не разделенные на части. Не используйте это поле одновременно с `partialCount`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _instances_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [BriefOrderItemInstanceDTO](#entity-BriefOrderItemInstanceDTO)[] &#124; null
  
  Переданные коды маркировки.
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "cis": "example",
      "uin": "example",
      "rnpt": "example",
      "gtd": "example",
      "countryCode": "RU"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _partialCount_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OrderBoxLayoutPartialCountDTO](#entity-OrderBoxLayoutPartialCountDTO)
  
  Информация о части товара в коробке.
  
  Используйте это поле, если в коробке поедет часть большого товара. Не используйте это поле одновременно с `fullCount`.
  
  
  Информация о части товара в коробке.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "current": 1,
    "total": 2
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "fullCount": 1,
    "partialCount": {
      "current": 1,
      "total": 2
    },
    "instances": [
      {
        "cis": "example",
        "uin": "example",
        "rnpt": "example",
        "gtd": "example",
        "countryCode": "RU"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBoxLayoutDTO {#entity-OrderBoxLayoutDTO}
  
  Информация о коробке.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _items_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OrderBoxLayoutItemDTO](#entity-OrderBoxLayoutItemDTO)[]
  
  Список товаров в коробке.
  
  Если в коробке едет часть большого товара, в списке может быть только один пункт.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "fullCount": 1,
      "partialCount": {
        "current": 1,
        "total": 2
      },
      "instances": [
        {
          "cis": "example",
          "uin": "example",
          "rnpt": "example",
          "gtd": "example",
          "countryCode": "RU"
        }
      ]
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
    "items": [
      {
        "id": 0,
        "fullCount": 1,
        "partialCount": {
          "current": 1,
          "total": 2
        },
        "instances": [
          {
            "cis": "example",
            "uin": "example",
            "rnpt": "example",
            "gtd": "example",
            "countryCode": "RU"
          }
        ]
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  В ответ придет переданная раскладка с идентификаторами коробок — они понадобятся для запроса ярлыков.
  
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "boxes": [
        {}
      ]
    }
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
  
    _result_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OrderBoxesLayoutDTO](#entity-OrderBoxesLayoutDTO)
  
    Распределение товаров по коробкам.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "boxes": [
        {
          "items": [
            {}
          ],
          "boxId": 0
        }
      ]
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
      "result": {
        "boxes": [
          {
            "items": [
              null
            ],
            "boxId": 0
          }
        ]
      }
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
  
  ### EnrichedOrderBoxLayoutDTO {#entity-EnrichedOrderBoxLayoutDTO}
  
  Информация о коробке.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [OrderBoxLayoutDTO](#entity-OrderBoxLayoutDTO)
  
    Информация о коробке.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "items": [
        {
          "id": 0,
          "fullCount": 1,
          "partialCount": {
            "current": 1,
            "total": 2
          },
          "instances": [
            {
              "cis": "example",
              "uin": "example",
              "rnpt": "example",
              "gtd": "example",
              "countryCode": "RU"
            }
          ]
        }
      ]
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _boxId_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: integer
  
    Идентификатор коробки.
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "boxId": 0
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "items": [
      {
        "id": 0,
        "fullCount": 1,
        "partialCount": {
          "current": 1,
          "total": 2
        },
        "instances": [
          {}
        ]
      }
    ],
    "boxId": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OrderBoxesLayoutDTO {#entity-OrderBoxesLayoutDTO}
  
  Распределение товаров по коробкам.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _boxes_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [EnrichedOrderBoxLayoutDTO](#entity-EnrichedOrderBoxLayoutDTO)[]
  
  Список коробок.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "items": [
        {
          "id": 0,
          "fullCount": 1,
          "partialCount": {},
          "instances": [
            null
          ]
        }
      ],
      "boxId": 0
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
    "boxes": [
      {
        "items": [
          {}
        ],
        "boxId": 0
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с заказами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#orders)
  
  
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
    - description: "Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия.\n\nЕго можно узнать с помощью запроса [GET\_v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**:\n\n* блок **Идентификатор кампании**;\n* вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**.\n\n⚠️ Не путайте его с:\n- идентификатором магазина, который отображается в личном кабинете продавца;\n- рекламными кампаниями.\n"
      name: campaignId
      in: path
      required: true
      schema:
        type: integer
        format: int64
        minimum: 1
    - description: Идентификатор заказа.
      name: orderId
      in: path
      required: true
      schema:
        type: integer
        format: int64
  searchParams: []
  headers: []
  body: |-
    {
      "boxes": [
        {
          "items": [
            {
              "id": 0,
              "fullCount": 1,
              "partialCount": {},
              "instances": [
                null
              ]
            }
          ]
        }
      ],
      "allowRemove": false
    }
  schema:
    type: object
    required:
      - boxes
    properties:
      boxes:
        description: Список коробок.
        type: array
        minItems: 1
        items:
          description: Информация о коробке.
          type: object
          required:
            - items
          properties:
            items:
              description: >
                Список товаров в коробке.
  
  
                Если в коробке едет часть большого товара, в списке может быть
                только один пункт.
              type: array
              minItems: 1
              items:
                description: Информация о товаре в коробке.
                type: object
                required:
                  - id
                properties:
                  id:
                    description: "Идентификатор товара в заказе.\n\nОн приходит в ответе метода [POST\_v1/businesses/{businessId}/orders](../../reference/orders/getBusinessOrders.md) — параметр `id` в `items`.\n"
                    type: integer
                    format: int64
                  fullCount:
                    description: >
                      Количество единиц товара в коробке.
  
  
                      Используйте это поле, если в коробке поедут целые товары, не
                      разделенные на части. Не используйте это поле одновременно с
                      `partialCount`.
                    type: integer
                    format: int32
                    minimum: 1
                  partialCount:
                    description: >
                      Информация о части товара в коробке.
  
  
                      Используйте это поле, если в коробке поедет часть большого
                      товара. Не используйте это поле одновременно с `fullCount`.
                    $ref: '#/$defs/OrderBoxLayoutPartialCountDTO'
                  instances:
                    description: Переданные коды маркировки.
                    type: array
                    nullable: true
                    minItems: 1
                    items:
                      description: >
                        Идентификатор единицы товара.
  
  
                        Заполните только одно поле в зависимости от того, в какой
                        системе маркирован товар.
  
  
                        Подробно о работе с маркируемыми товарами читайте [в
                        Справке Маркета для
                        продавцов](https://yandex.ru/support/marketplace/orders/cz.html).
                      type: object
                      properties:
                        cis:
                          description: >
                            [Код идентификации](*cis-regular-value) единицы товара
                            в системе [«Честный ЗНАК»](https://честныйзнак.рф/)
                            или [«ASL BELGISI»](https://aslbelgisi.uz) (для
                            продавцов Market Yandex Go).
  
  
                            {% note warning "Не экранируйте косую черту в коде
                            символа-разделителя `\u001d`" %}
  
  
                            ✅ `01030410947874432155Qbag!\u001d93Zjqw`
  
  
                            ❌ `01030410947874432155Qbag!\\u001d93Zjqw`
  
  
                            Косые черты и кавычки в других местах экранируйте по
                            правилам JSON: `\\` и `\"`
  
  
                            {% endnote %}
                          type: string
                        uin:
                          description: |
                            Уникальный идентификационный номер ювелирного изделия.
  
                            Представляет собой число из 16 цифр.
                          type: string
                        rnpt:
                          description: >
                            Регистрационный номер партии товара.
  
  
                            Представляет собой строку из четырех чисел,
                            разделенных косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ/ХХХ.
  
  
                            Первая часть — код таможни, которая зарегистрировала
                            декларацию на партию товара. Далее — дата, номер
                            декларации и номер маркированного товара в декларации.
                          type: string
                        gtd:
                          description: >
                            Грузовая таможенная декларация.
  
  
                            Представляет собой строку из трех чисел, разделенных
                            косой чертой: ХХХХХХХХ/ХХХХХХ/ХХХХХХХ.
  
  
                            Первая часть — код таможни, которая зарегистрировала
                            декларацию на ввезенные товары. Далее — дата и номер
                            декларации.
                          type: string
                        countryCode:
                          description: >
                            Страна производства в формате ISO 3166-1 alpha-2. [Как
                            получить](../../reference/regions/getRegionsCodes.md)
                          type: string
                          minLength: 2
                          maxLength: 2
                          pattern: ^[A-Z]{2}$
                          example: RU
      allowRemove:
        description: Передайте `true`, если вы собираетесь удалить часть товаров из заказа.
        type: boolean
        default: false
    $defs:
      /home/sandbox/.ya/build/build_root/4tup/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/orders/api/setOrderBoxLayout.yaml#/OrderBoxLayoutPartialCountDTO:
        description: Информация о части товара в коробке.
        type: object
        required:
          - current
          - total
        properties:
          current:
            description: Номер части, начиная с 1.
            type: integer
            format: int32
            minimum: 1
          total:
            description: На сколько всего частей разделен товар.
            type: integer
            format: int32
            minimum: 2
  bodyType: application/json
  method: put
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
  path: v2/campaigns/{campaignId}/orders/{orderId}/boxes
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/orders/setOrderBoxLayout.md -->

[*cis-regular-value]:
Значение `cis` должно соответствовать регулярному выражению `^(?=.{1,256}$)\u001D?(\(?01\)?\d{14}\(?21\)?([!-~]{6,8}|[!-~]{13}|[!-~]{20})(\u001D\(?240\)?.{1,30})?\u001D\(?9[1,3]\)?.+)$`.<br><br>Без криптохвоста — `^(?=[!-~]{1,256}$)(\(?01\)?\d{14}\(?21\)?(.{6,8}|.{13}|.{20}))$`.

[*Deprecated]: No longer supported, please use an alternative and newer version.
