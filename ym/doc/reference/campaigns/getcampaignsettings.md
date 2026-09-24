---
title: Настройки магазина
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md"
fetched_at: "2026-09-24T02:13:34Z"
content_sha: bfea1e3873ccd500
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/campaigns/getCampaignSettings.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/campaigns/getCampaignSettings.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/campaigns/getCampaignSettings.md -->
<div class="openapi">

# Настройки магазина

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getCampaignSettings.md -->
  **Метод доступен для [всех моделей](https://yandex.ru/dev/market/partner-api/doc/ru/overview/comparison.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * inventory-and-order-processing:read-only — [Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
  * pricing — [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md)
  * pricing:read-only — [Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md)
  * offers-and-cards-management — [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md)
  * offers-and-cards-management:read-only — [Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
  * promotion — [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md)
  * promotion:read-only — [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md)
  * finance-and-accounting — [Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
  * communication — [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md)
  * settings-management — [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
  * supplies-management:read-only — [Получение информации по FBY-заявкам](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getCampaignSettings.md -->
  
  Возвращает информацию о настройках магазина, идентификатор которого указан в запросе.
  
  <!-- source: ru/_auto/method_limits/getCampaignSettings.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 1 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getCampaignSettings.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-get);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  GET {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/settings
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
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Настройки магазина.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "settings": {
      "countryRegion": 0,
      "shopName": "example",
      "showInContext": true,
      "showInPremium": true,
      "useOpenStat": true,
      "localRegion": {
        "id": 0,
        "name": "example",
        "type": "OTHER",
        "deliveryOptionsSource": "WEB",
        "delivery": {
          "schedule": {
            "availableOnHolidays": true,
            "customHolidays": [
              null
            ],
            "customWorkingDays": [
              null
            ],
            "period": {},
            "totalHolidays": [
              null
            ],
            "weeklyHolidays": [
              null
            ]
          }
        }
      },
      "taxation": {
        "vat": "VAT_22"
      }
    }
  }
  ```
  
  {% endcut %}
  
  #|
  || **Name** | **Description** ||
  ||
  
  _settings_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignSettingsDTO](#entity-CampaignSettingsDTO)
  
  Настройки магазина.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "countryRegion": 0,
    "shopName": "example",
    "showInContext": true,
    "showInPremium": true,
    "useOpenStat": true,
    "localRegion": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "deliveryOptionsSource": "WEB",
      "delivery": {
        "schedule": {
          "availableOnHolidays": true,
          "customHolidays": [
            "23-09-2022"
          ],
          "customWorkingDays": [
            null
          ],
          "period": {
            "fromDate": null,
            "toDate": null
          },
          "totalHolidays": [
            null
          ],
          "weeklyHolidays": [
            1
          ]
        }
      }
    },
    "taxation": {
      "vat": "VAT_22"
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
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
  
  ### CampaignSettingsScheduleSourceType {#entity-CampaignSettingsScheduleSourceType}
  
  Источник информации о расписании работы службы доставки.
  Возможные значения:
  * `WEB` — информация получена из настроек кабинета продавца на Маркете.
  * `YML` — информация получена из прайс-листа магазина.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `WEB`, `YML`
  
  </div>
  
  <div class="openapi-entity">
  
  ### DateDdMmYyyy {#entity-DateDdMmYyyy}
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  **Type**: string&lt;date-dd-MM-yyyy&gt;
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignSettingsTimePeriodDTO {#entity-CampaignSettingsTimePeriodDTO}
  
  Период, за который рассчитывается итоговый список нерабочих дней службы доставки.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _fromDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Дата (включительно) начала периода, по которому рассчитан итоговый список нерабочих дней службы доставки.
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  {.table-cell}
  ||
  ||
  
  _toDate_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)
  
  Дата (включительно) окончания периода, по которому рассчитан итоговый список нерабочих дней службы доставки.
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  Формат даты: `ДД-ММ-ГГГГ`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `23-09-2022`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "23-09-2022",
    "toDate": null
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignSettingsScheduleDTO {#entity-CampaignSettingsScheduleDTO}
  
  Расписание работы службы доставки в своем регионе.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _customHolidays_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)[]
  
  Список дней, в которые служба доставки не работает. Дни магазин указал в кабинете продавца на Маркете.
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "23-09-2022"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _customWorkingDays_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)[]
  
  Список выходных и праздничных дней, в которые служба доставки работает. Дни магазин указал в кабинете продавца на Маркете.
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "23-09-2022"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _totalHolidays_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [DateDdMmYyyy](#entity-DateDdMmYyyy)[]
  
  Итоговый список нерабочих дней службы доставки. Список рассчитывается с учетом выходных, нерабочих дней и государственных праздников. Информацию по ним магазин указывает в кабинете продавца на Маркете.
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    "23-09-2022"
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _weeklyHolidays_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer[]
  
  Список выходных дней недели и государственных праздников.
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    1
  ]
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _availableOnHolidays_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: boolean
  
  Признак работы службы доставки в государственные праздники.
  Возможные значения.
  * `false` — служба доставки не работает в праздничные дни.
  * `true` — служба доставки работает в праздничные дни.
  
  {.table-cell}
  ||
  ||
  
  _period_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignSettingsTimePeriodDTO](#entity-CampaignSettingsTimePeriodDTO)
  
  Период, за который рассчитывается итоговый список нерабочих дней службы доставки.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "fromDate": "23-09-2022",
    "toDate": null
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "availableOnHolidays": true,
    "customHolidays": [
      "23-09-2022"
    ],
    "customWorkingDays": [
      null
    ],
    "period": {
      "fromDate": null,
      "toDate": null
    },
    "totalHolidays": [
      null
    ],
    "weeklyHolidays": [
      1
    ]
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignSettingsDeliveryDTO {#entity-CampaignSettingsDeliveryDTO}
  
  Информация о доставке в своем регионе магазина.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _schedule_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignSettingsScheduleDTO](#entity-CampaignSettingsScheduleDTO)
  
  Расписание работы службы доставки в своем регионе.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "availableOnHolidays": true,
    "customHolidays": [
      "23-09-2022"
    ],
    "customWorkingDays": [
      null
    ],
    "period": {
      "fromDate": null,
      "toDate": null
    },
    "totalHolidays": [
      null
    ],
    "weeklyHolidays": [
      1
    ]
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "schedule": {
      "availableOnHolidays": true,
      "customHolidays": [
        "23-09-2022"
      ],
      "customWorkingDays": [
        null
      ],
      "period": {
        "fromDate": null,
        "toDate": null
      },
      "totalHolidays": [
        null
      ],
      "weeklyHolidays": [
        1
      ]
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignSettingsLocalRegionDTO {#entity-CampaignSettingsLocalRegionDTO}
  
  Информация о своем регионе магазина.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _delivery_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignSettingsDeliveryDTO](#entity-CampaignSettingsDeliveryDTO)
  
  Информация о доставке в своем регионе магазина.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "schedule": {
      "availableOnHolidays": true,
      "customHolidays": [
        "23-09-2022"
      ],
      "customWorkingDays": [
        null
      ],
      "period": {
        "fromDate": null,
        "toDate": null
      },
      "totalHolidays": [
        null
      ],
      "weeklyHolidays": [
        1
      ]
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _deliveryOptionsSource_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignSettingsScheduleSourceType](#entity-CampaignSettingsScheduleSourceType)
  
  Источник информации о расписании работы службы доставки.
  Возможные значения:
  * `WEB` — информация получена из настроек кабинета продавца на Маркете.
  * `YML` — информация получена из прайс-листа магазина.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `WEB`, `YML`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона.
  {.table-cell}
  ||
  ||
  
  _name_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Название региона.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _type_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [RegionType](#entity-RegionType)
  
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
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "deliveryOptionsSource": "WEB",
    "delivery": {
      "schedule": {
        "availableOnHolidays": true,
        "customHolidays": [
          "23-09-2022"
        ],
        "customWorkingDays": [
          null
        ],
        "period": {
          "fromDate": null,
          "toDate": null
        },
        "totalHolidays": [
          null
        ],
        "weeklyHolidays": [
          1
        ]
      }
    }
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### VatRateType {#entity-VatRateType}
  
  Ставка НДС.
  Возможные значения:
  
  * `VAT_22` — НДС 22%.
  * `NO_VAT` — НДС не облагается.
  * `VAT_12` — НДС 12%.
  * `VAT_10` — НДС 10%.
  * `VAT_05` — НДС 5%.
  * `VAT_07` — НДС 7%.
  
  Если у партнёра в кабинете установлена ставка, не входящая в список, — значение не возвращается.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `VAT_22`, `NO_VAT`, `VAT_12`, `VAT_10`, `VAT_05`, `VAT_07`
  
  </div>
  
  <div class="openapi-entity">
  
  ### TaxationInfoDTO {#entity-TaxationInfoDTO}
  
  Информация о налогообложении.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _vat_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [VatRateType](#entity-VatRateType) &#124; null
  
  Ставка НДС.
  Возможные значения:
  
  * `VAT_22` — НДС 22%.
  * `NO_VAT` — НДС не облагается.
  * `VAT_12` — НДС 12%.
  * `VAT_10` — НДС 10%.
  * `VAT_05` — НДС 5%.
  * `VAT_07` — НДС 7%.
  
  Если у партнёра в кабинете установлена ставка, не входящая в список, — значение не возвращается.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `VAT_22`, `NO_VAT`, `VAT_12`, `VAT_10`, `VAT_05`, `VAT_07`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "vat": "VAT_22"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### CampaignSettingsDTO {#entity-CampaignSettingsDTO}
  
  Настройки магазина.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _taxation_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [TaxationInfoDTO](#entity-TaxationInfoDTO)
  
  Информация о налогообложении.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "vat": "VAT_22"
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _countryRegion_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор региона, в котором находится магазин.
  {.table-cell}
  ||
  ||
  
  _localRegion_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [CampaignSettingsLocalRegionDTO](#entity-CampaignSettingsLocalRegionDTO)
  
  Информация о своем регионе магазина.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "name": "example",
    "type": "OTHER",
    "deliveryOptionsSource": "WEB",
    "delivery": {
      "schedule": {
        "availableOnHolidays": true,
        "customHolidays": [
          "23-09-2022"
        ],
        "customWorkingDays": [
          null
        ],
        "period": {
          "fromDate": null,
          "toDate": null
        },
        "totalHolidays": [
          null
        ],
        "weeklyHolidays": [
          1
        ]
      }
    }
  }
  ```
  
  {% endcut %}
  {.table-cell}
  ||
  ||
  
  _shopName_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: string
  
  Наименование магазина на Яндекс Маркете.
  Если наименование отсутствует, значение параметра выводится — `null`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _showInContext_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: boolean
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
   
  
  {% endnote %}
  
  Признак размещения магазина на сайтах партнеров Яндекс Дистрибуции.
  Возможные значения:
  * `false` — магазин не размещен на сайтах партнеров Яндекс Дистрибуции.
  * `true` — магазин размещен на сайтах партнеров Яндекс Дистрибуции.
  
  {.table-cell}
  ||
  ||
  
  _showInPremium_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: boolean
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
   
  
  {% endnote %}
  
  Признак показа предложений магазина в блоке над результатами поиска (cпецразмещение).
  Возможные значения:
  * `false` — предложения не показываются в блоке cпецразмещения.
  * `true` — предложения показываются в блоке cпецразмещения.
  
  {.table-cell}
  ||
  ||
  
  _useOpenStat_{.json-schema-reset .json-schema-property .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: boolean
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
   
  
  {% endnote %}
  
  Признак использования внешней интернет-статистики.
  Возможные значения:
  * `false` — внешняя интернет-статистика не используется.
  * `true` — внешняя интернет-статистика используется.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "countryRegion": 0,
    "shopName": "example",
    "showInContext": true,
    "showInPremium": true,
    "useOpenStat": true,
    "localRegion": {
      "id": 0,
      "name": "example",
      "type": "OTHER",
      "deliveryOptionsSource": "WEB",
      "delivery": {
        "schedule": {
          "availableOnHolidays": true,
          "customHolidays": [
            "23-09-2022"
          ],
          "customWorkingDays": [
            null
          ],
          "period": {
            "fromDate": null,
            "toDate": null
          },
          "totalHolidays": [
            null
          ],
          "weeklyHolidays": [
            1
          ]
        }
      }
    },
    "taxation": {
      "vat": "VAT_22"
    }
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
  path: v2/campaigns/{campaignId}/settings
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/campaigns/getCampaignSettings.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
