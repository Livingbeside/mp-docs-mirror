---
title: Несколько точек продаж
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md"
fetched_at: "2026-09-24T02:14:16Z"
content_sha: 13c1cca33c64c8cb
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/outlets/getOutlets.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/outlets/getOutlets.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlets.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/outlets/getOutlets.md -->
<div class="openapi">

# Информация о нескольких точках продаж

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOutlets.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * settings-management — [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOutlets.md -->
  
  Возвращает список точек продаж магазина.
  
  <!-- source: ru/_auto/method_limits/getOutlets.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 000 точек продаж в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOutlets.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-get);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  GET {.openapi__method}
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
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _limit_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Количество значений на одной странице.
  
  
  _Default:_{.json-schema-reset .json-schema-value} `25`
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max value:_{.json-schema-reset .json-schema-assertion} `50`
  {.table-cell}
  ||
  ||
  
  _pageToken_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор страницы c результатами.
  
  Если параметр не указан, возвращается первая страница.
  
  Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе.
  
  
  _Example:_{.json-schema-reset .json-schema-example} ``
  {.table-cell}
  ||
  ||
  
  _region_id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона.
  Если задать идентификатор родительского региона любого уровня, в выходных данных будут отображены точки продаж всех дочерних регионов.
  Идентификатор региона можно получить c помощью метода [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md).
  
  {.table-cell}
  ||
  ||
  
  _regionId_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
  Вместо него используйте `region_id`.
  
  {% endnote %}
  
  {.table-cell}
  ||
  ||
  
  _shop_outlet_code_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор точки продаж, присвоенный магазином.
  
  _Example:_{.json-schema-reset .json-schema-example} ``
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Информация о точках продаж.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "outlets": [
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
            null
          ]
        },
        "deliveryRules": [
          {}
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
    ],
    "paging": {
      "nextPageToken": "example"
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _outlets_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [FullOutletDTO](#entity-FullOutletDTO)[]
  
  Информация о точках продаж.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
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
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _paging_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PackagingForwardScrollingPagerDTO](#entity-PackagingForwardScrollingPagerDTO)
  
  Идентификатор следующей страницы.
  
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "nextPageToken": "example"
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
  
  <div class="openapi-entity">
  
  ### PackagingForwardScrollingPagerDTO {#entity-PackagingForwardScrollingPagerDTO}
  
  Идентификатор следующей страницы.
  
  
  #|
  || **Name** | **Description** ||
  ||
  
  _nextPageToken_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Идентификатор следующей страницы результатов.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "nextPageToken": "example"
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
  searchParams:
    - name: pageToken
      description: >
        Идентификатор страницы c результатами.
  
  
        Если параметр не указан, возвращается первая страница.
  
  
        Передавайте значение выходного параметра `nextPageToken`, полученное при
        последнем запросе.
      in: query
      required: false
      x-transform: token
      x-aliases:
        - pageToken
        - page_token
      schema:
        type: string
    - name: limit
      description: |
        Количество значений на одной странице.
      in: query
      required: false
      schema:
        type: integer
        format: int32
        minimum: 1
        default: 25
        maximum: 50
    - description: "Идентификатор региона.\nЕсли задать идентификатор родительского региона любого уровня, в выходных данных будут отображены точки продаж всех дочерних регионов.\nИдентификатор региона можно получить c помощью метода [GET\_v2/regions](../../reference/regions/searchRegionsByName.md).\n"
      name: region_id
      in: query
      required: false
      schema:
        type: integer
        format: int64
    - description: Идентификатор точки продаж, присвоенный магазином.
      name: shop_outlet_code
      in: query
      required: false
      schema:
        type: string
    - description: |
        {% note warning "Параметр устарел и будет отключен 19.10.2026." %}
  
        Вместо него используйте `region_id`.
  
        {% endnote %}
      name: regionId
      deprecated: true
      x-deprecation-config:
        shutdown-date: '2026-10-19'
        replacement-field: region_id
      in: query
      required: false
      schema:
        type: integer
        format: int64
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
  path: v2/campaigns/{campaignId}/outlets
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/outlets/getOutlets.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
