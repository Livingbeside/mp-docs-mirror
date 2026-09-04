---
title: Информация о лицензиях
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md"
fetched_at: "2026-09-04T01:58:56Z"
content_sha: 0763a3134b618857
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/outlet-licenses/getOutletLicenses.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/outlet-licenses/getOutletLicenses.md
  - href: ru/reference/outlet-licenses/getOutletLicenses.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/outlet-licenses/getOutletLicenses.md -->
<div class="openapi">

# Информация о лицензиях для точек продаж

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/getOutletLicenses.md -->
  **Метод доступен для модели [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * settings-management — [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md)
  * all-methods — Полное управление кабинетом
  * all-methods:read-only — Просмотр всех данных

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/getOutletLicenses.md -->
  
  Возвращает информацию о лицензиях для точек продаж.
  
  <!-- source: ru/_auto/method_limits/getOutletLicenses.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 100 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/getOutletLicenses.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-get);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  GET {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/outlets/licenses
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
  
  _ids_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[]
  
  Список идентификаторов лицензий, информацию о которых нужно получить.
  
  Идентификаторы указываются через запятую. Идентификатор лицензии присваивается Маркетом. Не путайте его с номером, указанным на лицензии.
  
  В запросе должен быть либо параметр `outletIds`, либо параметр `ids`. Запрос с обоими параметрами или без них приведет к ошибке.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `500`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} ``
  {.table-cell}
  ||
  ||
  
  _outletIds_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer[]
  
  Список идентификаторов точек продаж, для которых нужно получить информацию о лицензиях. Идентификаторы указываются через запятую.
  
  В запросе должен быть либо параметр `outletIds`, либо параметр `ids`. Запрос с обоими параметрами или без них приведет к ошибке.
  
  
  _Min items:_{.json-schema-reset .json-schema-assertion} `1`
  
  _Max items:_{.json-schema-reset .json-schema-assertion} `500`
  
  _Unique items:_{.json-schema-reset .json-schema-assertion} `true`
  
  _Example:_{.json-schema-reset .json-schema-example} ``
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  Найденные лицензии собственных точек продаж.
  
  <div class="openapi-entity">
  
  ### Body
  
  {% cut "application/json" %}
  
  ```json translate=no
  {
    "status": "OK",
    "result": {
      "licenses": [
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
    **Type**: [OutletLicensesResponseDTO](#entity-OutletLicensesResponseDTO)
  
    Ответ на запрос информации о лицензиях для точек продаж.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "licenses": [
        {
          "id": 0,
          "outletId": 1,
          "licenseType": "ALCOHOL",
          "number": "example",
          "dateOfIssue": "2017-11-13T00:00:00+03:00",
          "dateOfExpiry": "2022-11-20T00:00:00+03:00",
          "checkStatus": "NEW",
          "checkComment": "example"
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
        "licenses": [
          {
            "id": 0,
            "outletId": 1,
            "licenseType": "ALCOHOL",
            "number": "example",
            "dateOfIssue": "2017-11-13T00:00:00+03:00",
            "dateOfExpiry": "2022-11-20T00:00:00+03:00",
            "checkStatus": "NEW",
            "checkComment": "example"
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
  
  ### LicenseType {#entity-LicenseType}
  
  Тип лицензии:
  
  * `ALCOHOL` — лицензия на розничную продажу алкогольной продукции.
  * `UNKNOWN` — неизвестный тип лицензии.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `ALCOHOL`, `UNKNOWN`
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletLicenseDTO {#entity-OutletLicenseDTO}
  
  Информация о лицензии.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _dateOfExpiry_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата окончания действия лицензии.
  
  Формат даты: ISO 8601 со смещением относительно UTC. Нужно передать дату, указанную на лицензии, время `00:00:00` и часовой пояс, соответствующий региону точки продаж. Например, если действие лицензии для точки продаж в Москве заканчивается 20 ноября 2022 года, то параметр должен иметь значение `2022-11-20T00:00:00+03:00`.
  
  Не может быть раньше даты выдачи, указанной в параметре `dateOfIssue`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2022-11-20T00:00:00+03:00`
  {.table-cell}
  ||
  ||
  
  _dateOfIssue_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string&lt;date-time&gt;
  
  Дата выдачи лицензии.
  
  Формат даты: ISO 8601 со смещением относительно UTC. Нужно передать дату, указанную на лицензии, время `00:00:00` и часовой пояс, соответствующий региону точки продаж. Например, если лицензия для точки продаж в Москве выдана 13 ноября 2017 года, то параметр должен иметь значение `2017-11-13T00:00:00+03:00`.
  
  Не может быть позже даты окончания срока действия, указанной в параметре `dateOfExpiry`.
  
  
  _Example:_{.json-schema-reset .json-schema-example} `2017-11-13T00:00:00+03:00`
  {.table-cell}
  ||
  ||
  
  _licenseType_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [LicenseType](#entity-LicenseType)
  
  Тип лицензии:
  
  * `ALCOHOL` — лицензия на розничную продажу алкогольной продукции.
  * `UNKNOWN` — неизвестный тип лицензии.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `ALCOHOL`, `UNKNOWN`
  {.table-cell}
  ||
  ||
  
  _number_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: string
  
  Номер лицензии.
  
  _Example:_{.json-schema-reset .json-schema-example} `example`
  {.table-cell}
  ||
  ||
  
  _outletId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор точки продаж, для которой действительна лицензия.
  
  _Min value:_{.json-schema-reset .json-schema-assertion} `1`
  {.table-cell}
  ||
  ||
  
  _id_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор лицензии.
  
  Параметр указывается, только если нужно изменить информацию о существующей лицензии. Ее идентификатор можно узнать с помощью запроса [GET v2/campaigns/{campaignId}/outlets/licenses](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlet-licenses/getOutletLicenses.md). При передаче информации о новой лицензии указывать идентификатор не нужно.
  
  Идентификатор лицензии присваивается Маркетом. Не путайте его с номером, указанным на лицензии: он передается в параметре `number`.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "outletId": 1,
    "licenseType": "ALCOHOL",
    "number": "example",
    "dateOfIssue": "2017-11-13T00:00:00+03:00",
    "dateOfExpiry": "2022-11-20T00:00:00+03:00"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### LicenseCheckStatusType {#entity-LicenseCheckStatusType}
  
  Статус проверки лицензии:
  
  * `NEW` — лицензия проверяется.
  * `SUCCESS` — лицензия прошла проверку.
  * `FAIL` — лицензия не прошла проверку.
  * `REVOKE` — лицензия отозвана службой качества.
  * `DONT_WANT` — не проверяется.
  * `FAIL_MANUAL` — лицензия не прошла проверку службы качества.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `NEW`, `SUCCESS`, `FAIL`, `REVOKE`, `DONT_WANT`, `FAIL_MANUAL`
  
  </div>
  
  <div class="openapi-entity">
  
  ### FullOutletLicenseDTO {#entity-FullOutletLicenseDTO}
  
  Информация о лицензии.
  
  **Type**: object
  
  {% cut "**All of 2 types**" %}{.json-schema-combinators data-marker=and}
  
  - **Type**: [OutletLicenseDTO](#entity-OutletLicenseDTO)
  
    Информация о лицензии.
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "id": 0,
      "outletId": 1,
      "licenseType": "ALCOHOL",
      "number": "example",
      "dateOfIssue": "2017-11-13T00:00:00+03:00",
      "dateOfExpiry": "2022-11-20T00:00:00+03:00"
    }
    ```
  
    {% endcut %}
  
  - {% cut "**Type**: object" %}
  
    #|
    ||
  
    _checkComment_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: string
  
    Причина, по которой лицензия не прошла проверку.
  
    Параметр возвращается, только если параметр `checkStatus` имеет значение `FAIL`.
  
  
    _Example:_{.json-schema-reset .json-schema-example} `example`
    {.table-cell}
    ||
    ||
  
    _checkStatus_{.json-schema-reset .json-schema-property}
    {.table-cell}|
    **Type**: [LicenseCheckStatusType](#entity-LicenseCheckStatusType)
  
    Статус проверки лицензии:
  
    * `NEW` — лицензия проверяется.
    * `SUCCESS` — лицензия прошла проверку.
    * `FAIL` — лицензия не прошла проверку.
    * `REVOKE` — лицензия отозвана службой качества.
    * `DONT_WANT` — не проверяется.
    * `FAIL_MANUAL` — лицензия не прошла проверку службы качества.
  
  
    _Enum:_{.json-schema-reset .json-schema-value} `NEW`, `SUCCESS`, `FAIL`, `REVOKE`, `DONT_WANT`, `FAIL_MANUAL`
    {.table-cell}
    ||
    |#{.json-schema-properties}
  
    {% endcut %}
  
    {% cut "**Example**" %}{.json-schema-example}
  
    ```json translate=no
    {
      "checkStatus": "NEW",
      "checkComment": "example"
    }
    ```
  
    {% endcut %}
  
  {% endcut %}
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  {
    "id": 0,
    "outletId": 1,
    "licenseType": "ALCOHOL",
    "number": "example",
    "dateOfIssue": "2017-11-13T00:00:00+03:00",
    "dateOfExpiry": "2022-11-20T00:00:00+03:00",
    "checkStatus": "NEW",
    "checkComment": "example"
  }
  ```
  
  {% endcut %}
  
  </div>
  
  <div class="openapi-entity">
  
  ### OutletLicensesResponseDTO {#entity-OutletLicensesResponseDTO}
  
  Ответ на запрос информации о лицензиях для точек продаж.
  
  #|
  || **Name** | **Description** ||
  ||
  
  _licenses_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: [FullOutletLicenseDTO](#entity-FullOutletLicenseDTO)[]
  
  Список лицензий.
  
  {% cut "**Example**" %}{.json-schema-example}
  
  ```json translate=no
  [
    {
      "id": 0,
      "outletId": 1,
      "licenseType": "ALCOHOL",
      "number": "example",
      "dateOfIssue": "2017-11-13T00:00:00+03:00",
      "dateOfExpiry": "2022-11-20T00:00:00+03:00",
      "checkStatus": "NEW",
      "checkComment": "example"
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
    "licenses": [
      {
        "id": 0,
        "outletId": 1,
        "licenseType": "ALCOHOL",
        "number": "example",
        "dateOfIssue": "2017-11-13T00:00:00+03:00",
        "dateOfExpiry": "2022-11-20T00:00:00+03:00",
        "checkStatus": "NEW",
        "checkComment": "example"
      }
    ]
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
  searchParams:
    - description: >
        Список идентификаторов точек продаж, для которых нужно получить информацию
        о лицензиях. Идентификаторы указываются через запятую.
  
  
        В запросе должен быть либо параметр `outletIds`, либо параметр `ids`.
        Запрос с обоими параметрами или без них приведет к ошибке.
      name: outletIds
      in: query
      required: false
      schema:
        type: array
        uniqueItems: true
        maxItems: 500
        minItems: 1
        items:
          type: integer
          format: int64
          minimum: 1
    - description: >
        Список идентификаторов лицензий, информацию о которых нужно получить.
  
  
        Идентификаторы указываются через запятую. Идентификатор лицензии
        присваивается Маркетом. Не путайте его с номером, указанным на лицензии.
  
  
        В запросе должен быть либо параметр `outletIds`, либо параметр `ids`.
        Запрос с обоими параметрами или без них приведет к ошибке.
      name: ids
      in: query
      required: false
      schema:
        type: array
        uniqueItems: true
        maxItems: 500
        minItems: 1
        items:
          type: integer
          format: int64
          minimum: 1
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
  path: v2/campaigns/{campaignId}/outlets/licenses
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/outlet-licenses/getOutletLicenses.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
