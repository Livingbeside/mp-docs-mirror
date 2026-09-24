---
title: Одна точка продаж
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md"
fetched_at: "2026-09-24T02:14:15Z"
content_sha: 09ac5caa4af29012
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/outlets/getOutlet.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/outlets/getOutlet.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/outlets/getOutlet.md -->
<div class="openapi">

# Информация об одной точке продаж

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOutlet.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * settings-management — [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOutlet.md -->
  
  Возвращает информацию о точках продаж магазина.
  
  <!-- source: ru/_auto/method_limits/getOutlet.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOutlet.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-get);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  GET {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/outlets/{outletId}
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
  
  _outletId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор точки продаж.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о точке продаж.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "outlet": {
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
          {}
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
      "storagePeriod": 0,
      "id": 0,
      "status": "AT_MODERATION",
      "region": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "parent": null
      },
      "shopOutletId": "example",
      "workingTime": "example",
      "moderationReason": "example"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _outlet_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [FullOutletDTO](#entity-FullOutletDTO)
  
  Информация о точке продаж.
  
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
    "storagePeriod": 0,
    "id": 0,
    "status": "AT_MODERATION",
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    },
    "shopOutletId": "example",
    "workingTime": "example",
    "moderationReason": "example"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  <div class="openapi-entity">
  
  ### OutletStatusType {#entity-OutletStatusType}
  
  Статус точки продаж.
  
  Возможные значения:
  
  * `AT_MODERATION` — проверяется.
  * `FAILED` — не прошла проверку и отклонена модератором.
  * `MODERATED` — проверена и одобрена.
  * `NONMODERATED` — новая точка, нуждается в проверке.
  * `UNKNOWN` — статус не указан. При определении статуса произошла ошибка.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `AT_MODERATION`, `FAILED`, `MODERATED`, `NONMODERATED`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### RegionType {#entity-RegionType}
  
  Тип региона.
  
  Возможные значения:
  
  * `CITY_DISTRICT` — район города.
  
  * `CITY` — крупный город.
  
  * `CONTINENT` — континент.
  
  * `COUNTRY_DISTRICT` — область.
  
  * `COUNTRY` — страна.
  
  * `REGION` — регион.
  
  * `REPUBLIC_AREA` — район субъекта федерации.
  
  * `REPUBLIC` — субъект федерации.
  
  * `SUBWAY_STATION` — станция метро.
  
  * `VILLAGE` — город.
  
  * `OTHER` — неизвестный регион.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `OTHER`, `CONTINENT`, `REGION`, `COUNTRY`, `COUNTRY_DISTRICT`, `REPUBLIC`, `CITY`, `VILLAGE`, `CITY_DISTRICT`, `SUBWAY_STATION`, `REPUBLIC_AREA`
  
  </div>
  
  <div class="openapi-entity">
  
  ### RegionDTO {#entity-RegionDTO}
  
  Регион доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _id_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Название региона.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [RegionType](#entity-RegionType)
  
  Тип региона.
  
  Тип региона.
  
  Возможные значения:
  
  * `CITY_DISTRICT` — район города.
  
  * `CITY` — крупный город.
  
  * `CONTINENT` — континент.
  
  * `COUNTRY_DISTRICT` — область.
  
  * `COUNTRY` — страна.
  
  * `REGION` — регион.
  
  * `REPUBLIC_AREA` — район субъекта федерации.
  
  * `REPUBLIC` — субъект федерации.
  
  * `SUBWAY_STATION` — станция метро.
  
  * `VILLAGE` — город.
  
  * `OTHER` — неизвестный регион.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `OTHER`, `CONTINENT`, `REGION`, `COUNTRY`, `COUNTRY_DISTRICT`, `REPUBLIC`, `CITY`, `VILLAGE`, `CITY_DISTRICT`, `SUBWAY_STATION`, `REPUBLIC_AREA`
  {.table-cell}
  ||
  ||
  
  _parent_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RegionDTO](#entity-RegionDTO)
  
  Информация о родительском регионе.
  
  Указываются родительские регионы до уровня страны.
  
  
  Регион доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "parent": null
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
    "name": "example",
    "type": "OTHER",
    "parent": {
      "id": 0,
      "name": "example",
      "type": null,
      "parent": null
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### FullOutletDTO {#entity-FullOutletDTO}
  
  Информация о точке продаж.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [OutletDTO](#entity-OutletDTO)
  
    Информация о точке продаж.
  
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
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _id_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: integer
  
    Идентификатор точки продаж, присвоенный Маркетом.
    {.table-cell}
    ||
    ||
  
    _moderationReason_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Статус модерации.
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _region_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [RegionDTO](#entity-RegionDTO)
  
    Регион доставки.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    }
    ```
  
    {% endcut %}
    {.table-cell}
    ||
    ||
  
    _shopOutletId_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
    {.table-cell}|
    **Type**: string
  
    {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
    Вместо него используйте `shopOutletCode`.
  
    {% endnote %}
  
    Идентификатор точки продаж, заданный магазином.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _status_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [OutletStatusType](#entity-OutletStatusType)
  
    Статус точки продаж.
  
    Возможные значения:
  
    * `AT_MODERATION` — проверяется.
    * `FAILED` — не прошла проверку и отклонена модератором.
    * `MODERATED` — проверена и одобрена.
    * `NONMODERATED` — новая точка, нуждается в проверке.
    * `UNKNOWN` — статус не указан. При определении статуса произошла ошибка.
  
  
    _Enum:_{.json-schema-reset .json-schema-value} `AT_MODERATION`, `FAILED`, `MODERATED`, `NONMODERATED`, `UNKNOWN`
    {.table-cell}
    ||
    ||
  
    _workingTime_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
    {.table-cell}|
    **Type**: string
  
    {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
    Вместо него используйте `workingSchedule`.
  
    {% endnote %}
  
    Рабочее время.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 0,
      "status": "AT_MODERATION",
      "region": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "parent": null
      },
      "shopOutletId": "example",
      "workingTime": "example",
      "moderationReason": "example"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
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
    "storagePeriod": 0,
    "id": 0,
    "status": "AT_MODERATION",
    "region": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "parent": null
    },
    "shopOutletId": "example",
    "workingTime": "example",
    "moderationReason": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  </div>
  
  <div class="openapi__response__code__400">
  
  ## 400 Bad Request
  
  Запрос содержит неправильные данные. [Подробнее об ошибке](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#400)
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "errors": [
      {
        "code": "INVALID_FEED_ID",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiTypedErrorResponse](#entity-ApiTypedErrorResponse)
  
    Стандартная обертка для типизированных ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "INVALID_FEED_ID",
          "message": "example"
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
  
  ### ApiErrorCodeType {#entity-ApiErrorCodeType}
  
  Типизированный код ошибки. Описания возможных значений приведены в разделе [Коды ошибок](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md).
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `INVALID_FEED_ID`, `INVALID_WAREHOUSE_ID`, `GROUPED_WAREHOUSE`, `DUPLICATE_OFFER`, `INVALID_TTL`, `INVALID_COMMENT`, `LIMIT_EXCEEDED`, `NON_POSITIVE_LIMIT`, `REQUEST_LIMIT_EXCEEDED`, `INVALID_OFFER_ID`, `MISSING_OFFER_ID`, `MISSING_OFFER`, `INVALID_SHOP_SKU`, `AMBIGUOUS_OFFER`, `OFFER_NOT_FOUND`, `MODEL_NOT_FOUND`, `CATEGORY_NOT_FOUND`, `NO_REQUIRED_FIELDS`, `FORBIDDEN_FIELD_DEFINITION`, `PROBLEMS_IN_OTHER_OFFERS`, `AMBIGUOUS_FIELD_DEFINITION`, `INVALID_OUTLET_INFO`, `DUPLICATE_OUTLET_CODE`, `UNKNOWN_REGION`, `WRONG_REGION`, `NOT_SPECIFIED`, `INVALID_PHONE_FORMAT`, `INVALID_TIME_FORMAT`, `COULD_NOT_FIND_COORDS`, `WRONG_OUTLET_GPS_COORDINATES`, `ITEM_NOT_FOUND`, `INVALID_ITEM`, `ITEM_DUPLICATE`, `ITEM_SHIPPED`, `ITEMS_ADDITION_NOT_SUPPORTED`, `CANNOT_REMOVE_LAST_ITEM`, `OTHER_REMOVE_ITEM_ERROR`, `TRACK_CODE_ALREADY_USED`, `TOO_MANY_CISES_FOR_ITEM`, `TOO_FEW_CISES_FOR_ITEM`, `INVALID_CIS`, `DUPLICATE_CIS`, `TOO_MANY_UINS_FOR_ITEM`, `TOO_FEW_UINS_FOR_ITEM`, `INVALID_UIN`, `UIN_VALIDATION_IN_PROGRESS_ERROR`, `CIS_VALIDATION_IN_PROGRESS_ERROR`, `INVALID_RNPT`, `INVALID_GTD`, `INVALID_COUNTRY_CODE`, `COUNTRY_CODE_AND_GTD_ARE_REQUIRED_VALIDATION_ERROR`, `DUPLICATE_UIN`, `DELETED_ITEMS_EXCEEDS_THRESHOLD`, `PROMO_PROHIBITS_DELETE`, `PAYMENT_PROHIBITS_DELETE`, `CANCELLATION_REQUESTED`, `ORDER_IN_TERMINAL_STATE`, `EDIT_COUNT_EXCEEDED`, `DAYS_COUNT_EXCEEDED`, `SAME_DELIVERY_DATES`, `INCORRECT_INN`, `BAD_REQUEST`, `UNSUPPORTED_MEDIA_TYPE`, `FORBIDDEN`, `NOT_FOUND`, `LOCKED`, `CONSTRAINT_VIOLATION`, `DUPLICATE_MARKET_SKU`, `INVALID_MARKET_SKU`, `INVALID_MAPPING`, `MISSING_MAPPING`, `UNKNOWN_PARAMETER`, `INTERNAL_ERROR`, `MISSING_PARAM`, `DUPLICATE_SHOP_SKU`, `INVALID_CURRENCY`, `INVALID_PAYMENT_SETTINGS`, `OTHER`, `INVALID_CATEGORY`, `INVALID_QUERY_PARAMETER`, `CAMPAIGN_NOT_FOUND`, `PARTNER_NOT_FOUND`, `BUSINESS_NOT_FOUND`, `CAMPAIGN_TYPE_NOT_SUPPORTED`, `BAD_OFFERS`, `ALREADY_CONFIRMED`, `CUTOFF_NOT_REACHED`, `NO_ORDERS`, `BAD_ORDERS`, `NO_BOXES`, `INVALID_ORDER_BEFORE`, `STATUS_NOT_ALLOWED`, `SUBSTATUS_NOT_ALLOWED`, `USER_UNREACHABLE_NOT_ALLOWED`, `ACTION_FORBIDDEN`, `CANT_DELIVER_ORDER_TO_ADDRESS`, `PICKUP_EXPIRED_CANCELLATION_FORBIDDEN`, `INVALID_ORDER_STATUS`, `CODE_NEED_BE_REFRESHED`, `CODE_ALREADY_ACCEPTED`, `NO_EMAIL`, `PROMO_ENDED`, `PROMO_ENTRY_DEADLINE_EXCEEDED`, `PROMO_MECHANICS_NOT_SUPPORTED`, `PROMO_SINGLE_OFFER_TASK_LIMIT_EXCEEDED`, `SUPPLY_REQUEST_NOT_FOUND`, `DOCUMENT_NOT_FOUND`, `EXTERNAL_ORDER_ID_UPDATE_ERROR`, `DECLINE_REASON_ARE_REQUIRED_ERROR`, `CONTRACT_NOT_FOUND`, `CONTRACT_WITH_AGENCY`, `NOT_ENOUGH_STOCK`, `INVALID_DELIVERY_OPTION`, `ORDER_ALREADY_EXISTS`, `ORDER_MODIFICATION_NOT_ALLOWED`, `DELIVERY_TAX_INFO_NO_DBS_PARTNER`, `DELIVERY_TAX_INFO_INCORRECT_ORDER_STATUS`, `DELIVERY_TAX_INFO_TAX_SYSTEM_IS_NOT_SUPPORTED`, `DELIVERY_TAX_INFO_INCORRECT_DELIVERY_SERVICE`, `DELIVERY_TAX_INFO_INCORRECT_REQUEST`, `RETURN_ALREADY_EXISTS`, `INVALID_RETURN_OFFERS`, `PHOTO_UPLOAD_FAILED`, `INVALID_DELIVERY_TYPE`, `INVALID_RETURN_REASON`, `INVALID_ITEM_DIMENSIONS`, `API_DISABLED`, `RESTRICTED_BY_MARKETPLACE_REGION`, `NO_ACCESS_BY_DEPRECATION_POLICY`, `ORDER_EDIT_ERROR`, `ADVERTISER_STATUS_MISMATCH`, `RESTRICTED_FOR_ADVERTISER`, `SUBSCRIPTION_REQUIRED`, `CIS_HANDLE_MODE_RESTRICTION`
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiTypedErrorDTO {#entity-ApiTypedErrorDTO}
  
  Общий формат типизированной ошибки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _code_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [ApiErrorCodeType](#entity-ApiErrorCodeType)
  
  Код ошибки.
  
  Типизированный код ошибки. Описания возможных значений приведены в разделе [Коды ошибок](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md).
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `INVALID_FEED_ID`, `INVALID_WAREHOUSE_ID`, `GROUPED_WAREHOUSE`, `DUPLICATE_OFFER`, `INVALID_TTL`, `INVALID_COMMENT`, `LIMIT_EXCEEDED`, `NON_POSITIVE_LIMIT`, `REQUEST_LIMIT_EXCEEDED`, `INVALID_OFFER_ID`, `MISSING_OFFER_ID`, `MISSING_OFFER`, `INVALID_SHOP_SKU`, `AMBIGUOUS_OFFER`, `OFFER_NOT_FOUND`, `MODEL_NOT_FOUND`, `CATEGORY_NOT_FOUND`, `NO_REQUIRED_FIELDS`, `FORBIDDEN_FIELD_DEFINITION`, `PROBLEMS_IN_OTHER_OFFERS`, `AMBIGUOUS_FIELD_DEFINITION`, `INVALID_OUTLET_INFO`, `DUPLICATE_OUTLET_CODE`, `UNKNOWN_REGION`, `WRONG_REGION`, `NOT_SPECIFIED`, `INVALID_PHONE_FORMAT`, `INVALID_TIME_FORMAT`, `COULD_NOT_FIND_COORDS`, `WRONG_OUTLET_GPS_COORDINATES`, `ITEM_NOT_FOUND`, `INVALID_ITEM`, `ITEM_DUPLICATE`, `ITEM_SHIPPED`, `ITEMS_ADDITION_NOT_SUPPORTED`, `CANNOT_REMOVE_LAST_ITEM`, `OTHER_REMOVE_ITEM_ERROR`, `TRACK_CODE_ALREADY_USED`, `TOO_MANY_CISES_FOR_ITEM`, `TOO_FEW_CISES_FOR_ITEM`, `INVALID_CIS`, `DUPLICATE_CIS`, `TOO_MANY_UINS_FOR_ITEM`, `TOO_FEW_UINS_FOR_ITEM`, `INVALID_UIN`, `UIN_VALIDATION_IN_PROGRESS_ERROR`, `CIS_VALIDATION_IN_PROGRESS_ERROR`, `INVALID_RNPT`, `INVALID_GTD`, `INVALID_COUNTRY_CODE`, `COUNTRY_CODE_AND_GTD_ARE_REQUIRED_VALIDATION_ERROR`, `DUPLICATE_UIN`, `DELETED_ITEMS_EXCEEDS_THRESHOLD`, `PROMO_PROHIBITS_DELETE`, `PAYMENT_PROHIBITS_DELETE`, `CANCELLATION_REQUESTED`, `ORDER_IN_TERMINAL_STATE`, `EDIT_COUNT_EXCEEDED`, `DAYS_COUNT_EXCEEDED`, `SAME_DELIVERY_DATES`, `INCORRECT_INN`, `BAD_REQUEST`, `UNSUPPORTED_MEDIA_TYPE`, `FORBIDDEN`, `NOT_FOUND`, `LOCKED`, `CONSTRAINT_VIOLATION`, `DUPLICATE_MARKET_SKU`, `INVALID_MARKET_SKU`, `INVALID_MAPPING`, `MISSING_MAPPING`, `UNKNOWN_PARAMETER`, `INTERNAL_ERROR`, `MISSING_PARAM`, `DUPLICATE_SHOP_SKU`, `INVALID_CURRENCY`, `INVALID_PAYMENT_SETTINGS`, `OTHER`, `INVALID_CATEGORY`, `INVALID_QUERY_PARAMETER`, `CAMPAIGN_NOT_FOUND`, `PARTNER_NOT_FOUND`, `BUSINESS_NOT_FOUND`, `CAMPAIGN_TYPE_NOT_SUPPORTED`, `BAD_OFFERS`, `ALREADY_CONFIRMED`, `CUTOFF_NOT_REACHED`, `NO_ORDERS`, `BAD_ORDERS`, `NO_BOXES`, `INVALID_ORDER_BEFORE`, `STATUS_NOT_ALLOWED`, `SUBSTATUS_NOT_ALLOWED`, `USER_UNREACHABLE_NOT_ALLOWED`, `ACTION_FORBIDDEN`, `CANT_DELIVER_ORDER_TO_ADDRESS`, `PICKUP_EXPIRED_CANCELLATION_FORBIDDEN`, `INVALID_ORDER_STATUS`, `CODE_NEED_BE_REFRESHED`, `CODE_ALREADY_ACCEPTED`, `NO_EMAIL`, `PROMO_ENDED`, `PROMO_ENTRY_DEADLINE_EXCEEDED`, `PROMO_MECHANICS_NOT_SUPPORTED`, `PROMO_SINGLE_OFFER_TASK_LIMIT_EXCEEDED`, `SUPPLY_REQUEST_NOT_FOUND`, `DOCUMENT_NOT_FOUND`, `EXTERNAL_ORDER_ID_UPDATE_ERROR`, `DECLINE_REASON_ARE_REQUIRED_ERROR`, `CONTRACT_NOT_FOUND`, `CONTRACT_WITH_AGENCY`, `NOT_ENOUGH_STOCK`, `INVALID_DELIVERY_OPTION`, `ORDER_ALREADY_EXISTS`, `ORDER_MODIFICATION_NOT_ALLOWED`, `DELIVERY_TAX_INFO_NO_DBS_PARTNER`, `DELIVERY_TAX_INFO_INCORRECT_ORDER_STATUS`, `DELIVERY_TAX_INFO_TAX_SYSTEM_IS_NOT_SUPPORTED`, `DELIVERY_TAX_INFO_INCORRECT_DELIVERY_SERVICE`, `DELIVERY_TAX_INFO_INCORRECT_REQUEST`, `RETURN_ALREADY_EXISTS`, `INVALID_RETURN_OFFERS`, `PHOTO_UPLOAD_FAILED`, `INVALID_DELIVERY_TYPE`, `INVALID_RETURN_REASON`, `INVALID_ITEM_DIMENSIONS`, `API_DISABLED`, `RESTRICTED_BY_MARKETPLACE_REGION`, `NO_ACCESS_BY_DEPRECATION_POLICY`, `ORDER_EDIT_ERROR`, `ADVERTISER_STATUS_MISMATCH`, `RESTRICTED_FOR_ADVERTISER`, `SUBSCRIPTION_REQUIRED`, `CIS_HANDLE_MODE_RESTRICTION`
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
    "code": "INVALID_FEED_ID",
    "message": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### ApiTypedErrorResponse {#entity-ApiTypedErrorResponse}
  
  Стандартная обертка для типизированных ошибок сервера.
  
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
    **Type**: [ApiTypedErrorDTO](#entity-ApiTypedErrorDTO)[] &#124; null
  
    Список ошибок.
  
    _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    [
      {
        "code": "INVALID_FEED_ID",
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
          "code": "INVALID_FEED_ID",
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
        "code": "INVALID_FEED_ID",
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
        "code": "INVALID_FEED_ID",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiTypedErrorResponse](#entity-ApiTypedErrorResponse)
  
    Стандартная обертка для типизированных ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "INVALID_FEED_ID",
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
        "code": "INVALID_FEED_ID",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiTypedErrorResponse](#entity-ApiTypedErrorResponse)
  
    Стандартная обертка для типизированных ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "INVALID_FEED_ID",
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
        "code": "INVALID_FEED_ID",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiTypedErrorResponse](#entity-ApiTypedErrorResponse)
  
    Стандартная обертка для типизированных ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "INVALID_FEED_ID",
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
        "code": "INVALID_FEED_ID",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiTypedErrorResponse](#entity-ApiTypedErrorResponse)
  
    Стандартная обертка для типизированных ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "INVALID_FEED_ID",
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
        "code": "INVALID_FEED_ID",
        "message": "example"
      }
    ]
  }
  ```
  
  {% endcut %}
  
  **Type**: object
  
  {% cut "**All of 1 type**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [ApiTypedErrorResponse](#entity-ApiTypedErrorResponse)
  
    Стандартная обертка для типизированных ошибок сервера.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "status": "OK",
      "errors": [
        {
          "code": "INVALID_FEED_ID",
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
    - description: Идентификатор точки продаж.
      name: outletId
      in: path
      required: true
      schema:
        type: integer
        format: int64
        minimum: 1
  searchParams: []
  headers: []
  body: null
  schema: {}
  method: get
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
  path: v2/campaigns/{campaignId}/outlets/{outletId}
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/outlets/getOutlet.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
