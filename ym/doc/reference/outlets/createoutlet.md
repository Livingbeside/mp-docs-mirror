---
title: Создание
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md"
fetched_at: "2026-08-28T11:52:37Z"
content_sha: 7af547e69d6a003e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/outlets/createOutlet.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/outlets/createOutlet.md
  - href: ru/reference/outlets/createOutlet.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/outlets/createOutlet.md -->
<div class="openapi">

# Создание точки продаж

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/createOutlet.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * settings-management — [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/createOutlet.md -->
  
  Создает точку продаж магазина на Маркете.
  
  <!-- source: ru/_auto/method_limits/createOutlet.md -->
  |<div style="text-align: left;">**⚙️ Лимит без подписки:** 35 000 запросов в час<br>**⭐️ [Лимит с подпиской Медиум](https://yandex.ru/support/marketplace/ru/marketing/subscription):** 100 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/createOutlet.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-post);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  POST {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/outlets
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
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "name": "example",
    "type": "DEPOT",
    "coords": "example",
    "isMain": true,
    "shopOutletCode": "example",
    "visibility": "HIDDEN",
    "address": {
      "regionId": 0,
      "street": "example",
      "number": "example",
      "building": "example",
      "estate": "example",
      "block": "example",
      "additional": "example",
      "km": 0,
      "city": "example"
    },
    "phones": [
      "example"
    ],
    "workingSchedule": {
      "workInHoliday": true,
      "scheduleItems": [
        {
          "startDay": "MONDAY",
          "endDay": null,
          "startTime": "09:59",
          "endTime": "23:59"
        }
      ]
    },
    "deliveryRules": [
      {
        "minDeliveryDays": 0,
        "maxDeliveryDays": 0,
        "deliveryServiceId": 1,
        "orderBefore": 0,
        "priceFreePickup": 0.5,
        "unspecifiedDeliveryInterval": true
      }
    ],
    "storagePeriod": 0
  }
  ```
  
  {% endcut %}
  
  **Type**: [OutletDTO](#entity-OutletDTO)
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletType {#entity-OutletType}
  
  Тип точки продаж.
  
  Возможные значения:
  
  * `DEPOT` — пункт выдачи заказов.
  * `MIXED` — смешанный тип точки продаж (торговый зал и пункт выдачи заказов).
  * `RETAIL` — розничная точка продаж (торговый зал).
  * `NOT_DEFINED` — неизвестный тип точки продажи. При определении типа произошла ошибка.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEPOT`, `MIXED`, `RETAIL`, `NOT_DEFINED`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletVisibilityType {#entity-OutletVisibilityType}
  
  Состояние точки продаж.
  
  Возможные значения:
  
  * `HIDDEN` — точка продаж выключена.
  * `VISIBLE` — точка продаж включена.
  * `UNKNOWN` — неизвестное состояние точки продажи. При определении состояния произошла ошибка.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `HIDDEN`, `VISIBLE`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletAddressDTO {#entity-OutletAddressDTO}
  
  Адрес точки продаж.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _regionId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона.
  
  Идентификатор можно получить c помощью запроса [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md).
  
  {% note alert "Типы регионов при создании и редактировании точек продаж" %}
  
  Указывайте только регионы типов `TOWN` (город), `CITY` (крупный город) и `REPUBLIC_AREA` (район субъекта федерации). Тип региона указан в выходных параметрах `type` запросов [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md) и [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md).
  
  {% endnote %}
  
  {.table-cell}
  ||
  ||
  
  _additional_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Дополнительная информация.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _block_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер корпуса.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _building_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер строения.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _city_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: string
  
  {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
  В ответах города и населенные пункты возвращаются в параметре `regionId`.
  
  {% endnote %}
  
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `200`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _estate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер владения.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `16`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _km_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Порядковый номер километра дороги, на котором располагается точка продаж, если отсутствует улица.
  {.table-cell}
  ||
  ||
  
  _number_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Номер дома.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `256`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _street_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Улица.
  
  _Max length:_{.json-schema-reset .json-schema-assertion} `512`
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "regionId": 0,
    "street": "example",
    "number": "example",
    "building": "example",
    "estate": "example",
    "block": "example",
    "additional": "example",
    "km": 0,
    "city": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### DayOfWeekType {#entity-DayOfWeekType}
  
  День недели:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `MONDAY`, `TUESDAY`, `WEDNESDAY`, `THURSDAY`, `FRIDAY`, `SATURDAY`, `SUNDAY`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletWorkingScheduleItemDTO {#entity-OutletWorkingScheduleItemDTO}
  
  Расписание работы точки продаж.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _endDay_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DayOfWeekType](#entity-DayOfWeekType)
  
  Точка продаж работает до указанного дня недели.
  
  Возможные значения:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  День недели:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MONDAY`, `TUESDAY`, `WEDNESDAY`, `THURSDAY`, `FRIDAY`, `SATURDAY`, `SUNDAY`
  {.table-cell}
  ||
  ||
  
  _endTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Точка продаж работает до указанного часа.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `23:59`
  {.table-cell}
  ||
  ||
  
  _startDay_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DayOfWeekType](#entity-DayOfWeekType)
  
  Точка продаж работает с указанного дня недели.
  
  Возможные значения:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  День недели:
  
  * `MONDAY` — понедельник.
  * `TUESDAY` — вторник.
  * `WEDNESDAY` — среда.
  * `THURSDAY` — четверг.
  * `FRIDAY` — пятница.
  * `SATURDAY` — суббота.
  * `SUNDAY` — воскресенье.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `MONDAY`, `TUESDAY`, `WEDNESDAY`, `THURSDAY`, `FRIDAY`, `SATURDAY`, `SUNDAY`
  {.table-cell}
  ||
  ||
  
  _startTime_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Точка продаж работает c указанного часа.
  
  Формат: `ЧЧ:ММ`.
  
  
  _Pattern:_{.json-schema-reset .json-schema-assertion} `^([0-1][0-9]&#124;2[0-3]):[0-5][0-9]$`
  
  _Example:_{.json-schema-reset .json-schema-example} `09:59`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "startDay": "MONDAY",
    "endDay": null,
    "startTime": "09:59",
    "endTime": "23:59"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletWorkingScheduleDTO {#entity-OutletWorkingScheduleDTO}
  
  Список режимов работы точки продаж.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _scheduleItems_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OutletWorkingScheduleItemDTO](#entity-OutletWorkingScheduleItemDTO)[]
  
  Список расписаний работы точки продаж.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "startDay": "MONDAY",
      "endDay": null,
      "startTime": "09:59",
      "endTime": "23:59"
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _workInHoliday_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Признак, работает ли точка продаж в дни государственных праздников.
  
  Возможные значения:
  
  * `false` — точка продаж не работает в дни государственных праздников.
  * `true` — точка продаж работает в дни государственных праздников.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "workInHoliday": true,
    "scheduleItems": [
      {
        "startDay": "MONDAY",
        "endDay": null,
        "startTime": "09:59",
        "endTime": "23:59"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletDeliveryRuleDTO {#entity-OutletDeliveryRuleDTO}
  
  Информация об условиях доставки для данной точки продаж.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _deliveryServiceId_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор службы доставки товаров в точку продаж.
  
  Информацию о службе доставки можно получить с помощью запроса [GET delivery/services](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-services/getDeliveryServices.md).
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _maxDeliveryDays_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Максимальный срок доставки товаров в точку продаж. Указан в рабочих днях.
  
  Минимальное значение: `0` — доставка в день заказа.
  
  Максимальное значение: `60`.
  
  Допустимые сроки доставки (разница между `minDeliveryDays` и `maxDeliveryDays`) зависят от региона.
  
  Для доставки по своему региону разница не должна превышать двух дней. Например, если `minDeliveryDays` равно 1, то для `maxDeliveryDays` допускаются значения от 1 до 3.
  
  Для доставки в другие регионы:
  
  * Если `minDeliveryDays` до 18 дней, разница не должна превышать четырех дней. Например, если `minDeliveryDays` равно 10, то для `maxDeliveryDays` допускаются значения от 10 до 14.
  * Если `minDeliveryDays` больше 18 дней, разница должна быть не больше чем в два раза. Например, если `minDeliveryDays` равно 21, то для `maxDeliveryDays` допускаются значения от 21 до 42.
  
  Обязательный параметр, если `type="DEPOT"` или `type="MIXED"`.
  
  Взаимоисключающий с параметром `unspecifiedDeliveryInterval`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `60`
  {.table-cell}
  ||
  ||
  
  _minDeliveryDays_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Минимальный срок доставки товаров в точку продаж. Указан в рабочих днях.
  
  Минимальное значение: `0` — доставка в день заказа.
  
  Максимальное значение: `60`.
  
  Допустимые сроки доставки (разница между `minDeliveryDays` и `maxDeliveryDays`) зависят от региона.
  
  Для доставки по своему региону разница не должна превышать двух дней. Например, если `minDeliveryDays` равно 1, то для `maxDeliveryDays` допускаются значения от 1 до 3.
  
  Для доставки в другие регионы:
  
  * Если `minDeliveryDays` до 18 дней, разница не должна превышать четырех дней. Например, если `minDeliveryDays` равно 10, то для `maxDeliveryDays` допускаются значения от 10 до 14.
  * Если `minDeliveryDays` больше 18 дней, разница должна быть не больше чем в два раза. Например, если `minDeliveryDays` равно 21, то для `maxDeliveryDays` допускаются значения от 21 до 42.
  
  Обязательный параметр, если `type="DEPOT"` или `type="MIXED"`.
  
  Взаимоисключающий с параметром `unspecifiedDeliveryInterval`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `60`
  {.table-cell}
  ||
  ||
  
  _orderBefore_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Час, до которого покупателю нужно сделать заказ, чтобы он был доставлен в точку продаж в сроки от `minDeliveryDays` до `maxDeliveryDays`.
  
  Если покупатель оформит заказ после указанного часа, он будет доставлен в сроки от `minDeliveryDays` + 1 рабочий день до `maxDeliveryDays` + 1 рабочий день.
  
  Значение по умолчанию: `24`.
  
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `0`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `24`
  {.table-cell}
  ||
  ||
  
  _priceFreePickup_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: number
  
  Цена товара, начиная с которой действует бесплатный самовывоз товара из точки продаж.
  {.table-cell}
  ||
  ||
  
  _unspecifiedDeliveryInterval_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Признак доставки товаров в точку продаж на заказ.
  
  Признак выставлен, если:
  
  * точный срок доставки в точку продаж заранее неизвестен (например, если магазин собирает несколько заказов для отправки в точку или населенный пункт);
  * все товары изготавливаются или поставляются на заказ.
  
  Возможные значения:
  * `true` — товары доставляются в точку продаж на заказ.
  
  Параметр указывается только со значением `true`.
  
  Взаимоисключающий с параметрами `minDeliveryDays` и `maxDeliveryDays`.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "minDeliveryDays": 0,
    "maxDeliveryDays": 0,
    "deliveryServiceId": 1,
    "orderBefore": 0,
    "priceFreePickup": 0.5,
    "unspecifiedDeliveryInterval": true
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletDTO {#entity-OutletDTO}
  
  Информация о точке продаж.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _address_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OutletAddressDTO](#entity-OutletAddressDTO)
  
  Адрес точки продаж.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "regionId": 0,
    "street": "example",
    "number": "example",
    "building": "example",
    "estate": "example",
    "block": "example",
    "additional": "example",
    "km": 0,
    "city": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название точки продаж.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _phones_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string[]
  
  Номера телефонов точки продаж.
  Передавайте номер в формате: `+<код страны>(<код города>)<номер>[#<добавочный>]`.
  
  Примеры:
  - `+7 (999) 999-99-99`
  - `+7 (999) 999-99-99#1234`
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
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
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OutletType](#entity-OutletType)
  
  Тип точки продаж.
  
  Возможные значения:
  
  * `DEPOT` — пункт выдачи заказов.
  * `MIXED` — смешанный тип точки продаж (торговый зал и пункт выдачи заказов).
  * `RETAIL` — розничная точка продаж (торговый зал).
  * `NOT_DEFINED` — неизвестный тип точки продажи. При определении типа произошла ошибка.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `DEPOT`, `MIXED`, `RETAIL`, `NOT_DEFINED`
  {.table-cell}
  ||
  ||
  
  _workingSchedule_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [OutletWorkingScheduleDTO](#entity-OutletWorkingScheduleDTO)
  
  Список режимов работы точки продаж.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "workInHoliday": true,
    "scheduleItems": [
      {
        "startDay": "MONDAY",
        "endDay": null,
        "startTime": "09:59",
        "endTime": "23:59"
      }
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _coords_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Координаты точки продаж.
  
  Формат: долгота, широта. Разделители: запятая и / или пробел. Например, `20.4522144, 54.7104264`.
  
  Если параметр не передан, координаты будут определены по значениям параметров, вложенных в `address`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _deliveryRules_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OutletDeliveryRuleDTO](#entity-OutletDeliveryRuleDTO)[] &#124; null
  
  Информация об условиях доставки для данной точки продаж.
  
  Обязательный параметр, если параметр `type=DEPOT` или `type=MIXED`.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "minDeliveryDays": 0,
      "maxDeliveryDays": 0,
      "deliveryServiceId": 1,
      "orderBefore": 0,
      "priceFreePickup": 0.5,
      "unspecifiedDeliveryInterval": true
    }
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _isMain_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Признак основной точки продаж.
  
  Возможные значения:
  
  * `false` — неосновная точка продаж.
  * `true` — основная точка продаж.
  
  {.table-cell}
  ||
  ||
  
  _shopOutletCode_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор точки продаж, присвоенный магазином.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _storagePeriod_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Срок хранения заказа в собственном пункте выдачи заказов. Считается в днях.
  {.table-cell}
  ||
  ||
  
  _visibility_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [OutletVisibilityType](#entity-OutletVisibilityType)
  
  Состояние точки продаж.
  
  Возможные значения:
  
  * `HIDDEN` — точка продаж выключена.
  * `VISIBLE` — точка продаж включена.
  * `UNKNOWN` — неизвестное состояние точки продажи. При определении состояния произошла ошибка.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `HIDDEN`, `VISIBLE`, `UNKNOWN`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "name": "example",
    "type": "DEPOT",
    "coords": "example",
    "isMain": true,
    "shopOutletCode": "example",
    "visibility": "HIDDEN",
    "address": {
      "regionId": 0,
      "street": "example",
      "number": "example",
      "building": "example",
      "estate": "example",
      "block": "example",
      "additional": "example",
      "km": 0,
      "city": "example"
    },
    "phones": [
      "example"
    ],
    "workingSchedule": {
      "workInHoliday": true,
      "scheduleItems": [
        {
          "startDay": "MONDAY",
          "endDay": null,
          "startTime": "09:59",
          "endTime": "23:59"
        }
      ]
    },
    "deliveryRules": [
      {
        "minDeliveryDays": 0,
        "maxDeliveryDays": 0,
        "deliveryServiceId": 1,
        "orderBefore": 0,
        "priceFreePickup": 0.5,
        "unspecifiedDeliveryInterval": true
      }
    ],
    "storagePeriod": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о созданной точке продаж.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "id": 0
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
    **Type**: [OutletResponseDTO](#entity-OutletResponseDTO)
  
    Результат выполнения запроса.
    Выводится, если `status="OK"`.
  
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 0
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
        "id": 0
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
  
  ### OutletResponseDTO {#entity-OutletResponseDTO}
  
  Результат выполнения запроса.
  Выводится, если `status="OK"`.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор точки продаж, присвоенный Маркетом.
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибках при работе с точками продаж](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#outlets)
  
  
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
  searchParams: []
  headers: []
  body: |-
    {
      "name": "example",
      "type": "DEPOT",
      "coords": "example",
      "isMain": true,
      "shopOutletCode": "example",
      "visibility": "HIDDEN",
      "address": {
        "regionId": 0,
        "street": "example",
        "number": "example",
        "building": "example",
        "estate": "example",
        "block": "example",
        "additional": "example",
        "km": 0,
        "city": "example"
      },
      "phones": [
        "example"
      ],
      "workingSchedule": {
        "workInHoliday": true,
        "scheduleItems": [
          {
            "startDay": "MONDAY",
            "endDay": null,
            "startTime": "09:59",
            "endTime": "23:59"
          }
        ]
      },
      "deliveryRules": [
        {
          "minDeliveryDays": 0,
          "maxDeliveryDays": 0,
          "deliveryServiceId": 1,
          "orderBefore": 0,
          "priceFreePickup": 0.5,
          "unspecifiedDeliveryInterval": true
        }
      ],
      "storagePeriod": 0
    }
  schema:
    type: object
    allOf:
      - description: Информация о точке продаж.
        type: object
        required:
          - name
          - type
          - address
          - phones
          - workingSchedule
        properties:
          name:
            description: |
              Название точки продаж.
            type: string
          type:
            description: >
              Тип точки продаж.
  
  
              Возможные значения:
  
  
              * `DEPOT` — пункт выдачи заказов.
  
              * `MIXED` — смешанный тип точки продаж (торговый зал и пункт выдачи
              заказов).
  
              * `RETAIL` — розничная точка продаж (торговый зал).
  
              * `NOT_DEFINED` — неизвестный тип точки продажи. При определении
              типа произошла ошибка.
            type: string
            enum:
              - DEPOT
              - MIXED
              - RETAIL
              - NOT_DEFINED
          coords:
            description: >
              Координаты точки продаж.
  
  
              Формат: долгота, широта. Разделители: запятая и / или пробел.
              Например, `20.4522144, 54.7104264`.
  
  
              Если параметр не передан, координаты будут определены по значениям
              параметров, вложенных в `address`.
            type: string
          isMain:
            description: |
              Признак основной точки продаж.
  
              Возможные значения:
  
              * `false` — неосновная точка продаж.
              * `true` — основная точка продаж.
            type: boolean
          shopOutletCode:
            description: Идентификатор точки продаж, присвоенный магазином.
            type: string
          visibility:
            description: >
              Состояние точки продаж.
  
  
              Возможные значения:
  
  
              * `HIDDEN` — точка продаж выключена.
  
              * `VISIBLE` — точка продаж включена.
  
              * `UNKNOWN` — неизвестное состояние точки продажи. При определении
              состояния произошла ошибка.
            type: string
            enum:
              - HIDDEN
              - VISIBLE
              - UNKNOWN
          address:
            description: |
              Адрес точки продаж.
            type: object
            required:
              - regionId
            properties:
              regionId:
                description: "Идентификатор региона.\n\nИдентификатор можно получить c помощью запроса [GET\_v2/regions](../../reference/regions/searchRegionsByName.md).\n\n{% note alert \"Типы регионов при создании и редактировании точек продаж\" %}\n\nУказывайте только регионы типов `TOWN` (город), `CITY` (крупный город) и `REPUBLIC_AREA` (район субъекта федерации). Тип региона указан в выходных параметрах `type` запросов [GET\_v2/regions](../../reference/regions/searchRegionsByName.md) и [GET\_v2/regions/{regionId}](../../reference/regions/searchRegionsById.md).\n\n{% endnote %}\n"
                type: integer
                format: int64
              street:
                description: Улица.
                type: string
                maxLength: 512
              number:
                description: Номер дома.
                type: string
                maxLength: 256
              building:
                description: Номер строения.
                type: string
                maxLength: 16
              estate:
                description: Номер владения.
                type: string
                maxLength: 16
              block:
                description: Номер корпуса.
                type: string
                maxLength: 16
              additional:
                description: Дополнительная информация.
                type: string
              km:
                description: >-
                  Порядковый номер километра дороги, на котором располагается
                  точка продаж, если отсутствует улица.
                type: integer
                format: int32
              city:
                description: >
                  {% note warning "Параметр устарел и будет отключен 19.10.2026."
                  %}
  
  
                  В ответах города и населенные пункты возвращаются в параметре
                  `regionId`.
  
  
                  {% endnote %}
                maxLength: 200
                type: string
                deprecated: true
                x-deprecation-config:
                  shutdown-date: '2026-10-19'
                  replacement-field: regionId
          phones:
            description: >
              Номера телефонов точки продаж.
  
              Передавайте номер в формате: `+<код страны>(<код
              города>)<номер>[#<добавочный>]`.
  
  
              Примеры:
  
              - `+7 (999) 999-99-99`
  
              - `+7 (999) 999-99-99#1234`
            type: array
            minItems: 1
            uniqueItems: true
            items:
              type: string
              minLength: 1
          workingSchedule:
            description: |
              Список режимов работы точки продаж.
            type: object
            required:
              - scheduleItems
            properties:
              workInHoliday:
                description: >
                  Признак, работает ли точка продаж в дни государственных
                  праздников.
  
  
                  Возможные значения:
  
  
                  * `false` — точка продаж не работает в дни государственных
                  праздников.
  
                  * `true` — точка продаж работает в дни государственных
                  праздников.
                type: boolean
              scheduleItems:
                description: |
                  Список расписаний работы точки продаж.
                type: array
                minItems: 1
                items:
                  description: Расписание работы точки продаж.
                  type: object
                  required:
                    - startDay
                    - endDay
                    - startTime
                    - endTime
                  properties:
                    startDay:
                      description: |
                        Точка продаж работает с указанного дня недели.
  
                        Возможные значения:
  
                        * `MONDAY` — понедельник.
                        * `TUESDAY` — вторник.
                        * `WEDNESDAY` — среда.
                        * `THURSDAY` — четверг.
                        * `FRIDAY` — пятница.
                        * `SATURDAY` — суббота.
                        * `SUNDAY` — воскресенье.
                      $ref: '#/$defs/DayOfWeekType'
                    endDay:
                      description: |
                        Точка продаж работает до указанного дня недели.
  
                        Возможные значения:
  
                        * `MONDAY` — понедельник.
                        * `TUESDAY` — вторник.
                        * `WEDNESDAY` — среда.
                        * `THURSDAY` — четверг.
                        * `FRIDAY` — пятница.
                        * `SATURDAY` — суббота.
                        * `SUNDAY` — воскресенье.
                      $ref: '#/$defs/DayOfWeekType'
                    startTime:
                      description: |
                        Точка продаж работает c указанного часа.
  
                        Формат: `ЧЧ:ММ`.
                      type: string
                      pattern: ^([0-1][0-9]|2[0-3]):[0-5][0-9]$
                      example: '09:59'
                    endTime:
                      description: |
                        Точка продаж работает до указанного часа.
  
                        Формат: `ЧЧ:ММ`.
                      type: string
                      pattern: ^([0-1][0-9]|2[0-3]):[0-5][0-9]$
                      example: '23:59'
          deliveryRules:
            description: |
              Информация об условиях доставки для данной точки продаж.
  
              Обязательный параметр, если параметр `type=DEPOT` или `type=MIXED`.
            type: array
            nullable: true
            minItems: 1
            items:
              description: Информация об условиях доставки для данной точки продаж.
              type: object
              properties:
                minDeliveryDays:
                  description: >
                    Минимальный срок доставки товаров в точку продаж. Указан в
                    рабочих днях.
  
  
                    Минимальное значение: `0` — доставка в день заказа.
  
  
                    Максимальное значение: `60`.
  
  
                    Допустимые сроки доставки (разница между `minDeliveryDays` и
                    `maxDeliveryDays`) зависят от региона.
  
  
                    Для доставки по своему региону разница не должна превышать
                    двух дней. Например, если `minDeliveryDays` равно 1, то для
                    `maxDeliveryDays` допускаются значения от 1 до 3.
  
  
                    Для доставки в другие регионы:
  
  
                    * Если `minDeliveryDays` до 18 дней, разница не должна
                    превышать четырех дней. Например, если `minDeliveryDays` равно
                    10, то для `maxDeliveryDays` допускаются значения от 10 до 14.
  
                    * Если `minDeliveryDays` больше 18 дней, разница должна быть
                    не больше чем в два раза. Например, если `minDeliveryDays`
                    равно 21, то для `maxDeliveryDays` допускаются значения от 21
                    до 42.
  
  
                    Обязательный параметр, если `type="DEPOT"` или `type="MIXED"`.
  
  
                    Взаимоисключающий с параметром `unspecifiedDeliveryInterval`.
                  type: integer
                  format: int32
                  minimum: 0
                  maximum: 60
                maxDeliveryDays:
                  description: >
                    Максимальный срок доставки товаров в точку продаж. Указан в
                    рабочих днях.
  
  
                    Минимальное значение: `0` — доставка в день заказа.
  
  
                    Максимальное значение: `60`.
  
  
                    Допустимые сроки доставки (разница между `minDeliveryDays` и
                    `maxDeliveryDays`) зависят от региона.
  
  
                    Для доставки по своему региону разница не должна превышать
                    двух дней. Например, если `minDeliveryDays` равно 1, то для
                    `maxDeliveryDays` допускаются значения от 1 до 3.
  
  
                    Для доставки в другие регионы:
  
  
                    * Если `minDeliveryDays` до 18 дней, разница не должна
                    превышать четырех дней. Например, если `minDeliveryDays` равно
                    10, то для `maxDeliveryDays` допускаются значения от 10 до 14.
  
                    * Если `minDeliveryDays` больше 18 дней, разница должна быть
                    не больше чем в два раза. Например, если `minDeliveryDays`
                    равно 21, то для `maxDeliveryDays` допускаются значения от 21
                    до 42.
  
  
                    Обязательный параметр, если `type="DEPOT"` или `type="MIXED"`.
  
  
                    Взаимоисключающий с параметром `unspecifiedDeliveryInterval`.
                  type: integer
                  format: int32
                  minimum: 0
                  maximum: 60
                deliveryServiceId:
                  description: "Идентификатор службы доставки товаров в точку продаж.\n\nИнформацию о службе доставки можно получить с помощью запроса [GET\_delivery/services](../../reference/delivery-services/getDeliveryServices.md).\n"
                  type: integer
                  format: int64
                  minimum: 1
                orderBefore:
                  description: >
                    Час, до которого покупателю нужно сделать заказ, чтобы он был
                    доставлен в точку продаж в сроки от `minDeliveryDays` до
                    `maxDeliveryDays`.
  
  
                    Если покупатель оформит заказ после указанного часа, он будет
                    доставлен в сроки от `minDeliveryDays` + 1 рабочий день до
                    `maxDeliveryDays` + 1 рабочий день.
  
  
                    Значение по умолчанию: `24`.
                  type: integer
                  format: int32
                  minimum: 0
                  maximum: 24
                priceFreePickup:
                  description: >-
                    Цена товара, начиная с которой действует бесплатный самовывоз
                    товара из точки продаж.
                  type: number
                unspecifiedDeliveryInterval:
                  description: >
                    Признак доставки товаров в точку продаж на заказ.
  
  
                    Признак выставлен, если:
  
  
                    * точный срок доставки в точку продаж заранее неизвестен
                    (например, если магазин собирает несколько заказов для
                    отправки в точку или населенный пункт);
  
                    * все товары изготавливаются или поставляются на заказ.
  
  
                    Возможные значения:
  
                    * `true` — товары доставляются в точку продаж на заказ.
  
  
                    Параметр указывается только со значением `true`.
  
  
                    Взаимоисключающий с параметрами `minDeliveryDays` и
                    `maxDeliveryDays`.
                  type: boolean
          storagePeriod:
            description: >-
              Срок хранения заказа в собственном пункте выдачи заказов. Считается
              в днях.
            type: integer
            format: int64
    $defs:
      /home/sandbox/.ya/build/build_root/guyl/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/common/schemas.yaml#/DayOfWeekType:
        description: |
          День недели:
  
          * `MONDAY` — понедельник.
          * `TUESDAY` — вторник.
          * `WEDNESDAY` — среда.
          * `THURSDAY` — четверг.
          * `FRIDAY` — пятница.
          * `SATURDAY` — суббота.
          * `SUNDAY` — воскресенье.
        type: string
        enum:
          - MONDAY
          - TUESDAY
          - WEDNESDAY
          - THURSDAY
          - FRIDAY
          - SATURDAY
          - SUNDAY
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
  path: v2/campaigns/{campaignId}/outlets
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/outlets/createOutlet.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
