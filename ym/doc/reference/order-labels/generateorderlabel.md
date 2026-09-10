---
title: Готовый ярлык для коробки
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md"
fetched_at: "2026-09-10T01:56:37Z"
content_sha: 9a80a892c19f0ecb
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/reference/order-labels/generateOrderLabel.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/reference/order-labels/generateOrderLabel.md
  - href: ru/reference/order-labels/generateOrderLabel.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

<!-- source: ru/api/order-labels/generateOrderLabel.md -->
<div class="openapi">

# Готовый ярлык‑наклейка для коробки в заказе

<!-- markdownlint-disable-file -->

{% list tabs %}

- Info

  <!-- source: ru/_auto/method_scopes/generateOrderLabel.md -->
  **Метод доступен для моделей: [FBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/fbs.md), [Экспресс](https://yandex.ru/dev/market/partner-api/doc/ru/overview/express.md) и [DBS](https://yandex.ru/dev/market/partner-api/doc/ru/overview/dbs.md).**

  {% cut "**Если вы используете API-Key-токен, для вызова метода необходим один из доступов в списке**" %}

  * inventory-and-order-processing — [Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
  * all-methods — Полное управление кабинетом

  {% endcut %}
  <!-- endsource: ru/_auto/method_scopes/generateOrderLabel.md -->
  
  Формирует ярлык‑наклейку для коробки в заказе и возвращает ярлык в PDF‑файле.
  
  Чтобы на ярлыке отображался внешний идентификатор заказа, передайте его в методе [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md).
  
  <!-- source: ru/_auto/method_limits/generateOrderLabel.md -->
  |<div style="text-align: left;">**⚙️ Лимит:** 10 000 запросов в час</div>|
  |-|
  <!-- endsource: ru/_auto/method_limits/generateOrderLabel.md -->
  
  
  ## Request
  
  <div class="openapi__requests">
  
  <div class="openapi__request__wrapper" style="--method: var(--dc-openapi-methods-get);margin-bottom: 12px">
  
  <div class="openapi__request">
  
  GET {.openapi__method}
  ```text translate=no
  https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label
  ```
  
  </div>
  
  </div>
  
  </div>
  
  ### Path parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _boxId_{.json-schema-reset .json-schema-property .json-schema-required}
  {.table-cell}|
  **Type**: integer
  
  Идентификатор коробки.
  {.table-cell}
  ||
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
  ||
  
  _shipmentId_{.json-schema-reset .json-schema-property .json-schema-required .json-schema-deprecated}_[ ](*Deprecated)_{.openapi-deprecated .openapi-deprecated-compact}
  {.table-cell}|
  **Type**: integer
  
  {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
  Передайте любое число, чтобы получился корректный URL.
  
  {% endnote %}
  
  Идентификатор грузового места.
  
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  ### Query parameters
  
  #|
  || **Name** | **Description** ||
  ||
  
  _format_{.json-schema-reset .json-schema-property}
  {.table-cell}|
  **Type**: [PageFormatType](#entity-PageFormatType)
  
  Настройка размещения ярлыков на странице. Если параметра нет, возвращается PDF с ярлыками формата A7.
  
  Размещение ярлыков на странице PDF-файла:
  
  * `A9_HORIZONTALLY` — ярлык размером 58 × 40 мм без полей, близок к формату A9.
  
    {% cut "Пример ярлыка для продавцов Маркета" %}
  
    ![Изображение горизонтального ярлыка формата A9 для продавцов Маркета](../../_images/labels/label-A9-horizontally.png)
  
    {% endcut %}
  
    {% cut "Пример ярлыка для продавцов Market Yandex Go" %}
  
    ![Изображение горизонтального ярлыка формата A9 для продавцов Market Yandex Go](../../_images/labels/label-A9-horizontally-uz.png)
  
    {% endcut %}
  
  * `A9` — ярлык размером 40 × 58 мм без полей, близок к формату A9.
  
    {% cut "Пример ярлыка для продавцов Маркета" %}
  
    ![Изображение вертикального ярлыка формата A9 для продавцов Маркета](../../_images/labels/label-A9.png)
  
    {% endcut %}
  
    {% cut "Пример ярлыка для продавцов Market Yandex Go" %}
  
    ![Изображение вертикального ярлыка формата A9 для продавцов Market Yandex Go](../../_images/labels/label-A9-uz.png)
  
    {% endcut %}
  
  * `A7` — ярлык размером 75 × 120 мм (80,4 × 125,6 мм с учетом полей), близок к формату A7.
  
    {% cut "Пример ярлыка для продавцов Маркета" %}
  
    ![Изображение ярлыка формата A7 для продавцов Маркета](../../_images/labels/label-A7.jpg)
  
    {% endcut %}
  
    {% cut "Пример ярлыка для продавцов Market Yandex Go" %}
  
    ![Изображение ярлыка формата A7 для продавцов Market Yandex Go](../../_images/labels/label-A7-uz.png)
  
    {% endcut %}
  
  * `A4` — на листе A4 располагается ярлык того формата, который выбран в кабинете продавца на Маркете — перейдите на страницу **Заказы** → **Заказы и отгрузки** → на вкладке нужной модели работы нажмите кнопку **Формат ярлыков**.
  
  
  _Enum:_{.json-schema-reset .json-schema-value} `A9_HORIZONTALLY`, `A9`, `A7`, `A4`
  {.table-cell}
  ||
  |#{.json-schema-properties}
  
  <div class="openapi-entity">
  
  ### PageFormatType {#entity-PageFormatType}
  
  Размещение ярлыков на странице PDF-файла:
  
  * `A9_HORIZONTALLY` — ярлык размером 58 × 40 мм без полей, близок к формату A9.
  
    {% cut "Пример ярлыка для продавцов Маркета" %}
  
    ![Изображение горизонтального ярлыка формата A9 для продавцов Маркета](../../_images/labels/label-A9-horizontally.png)
  
    {% endcut %}
  
    {% cut "Пример ярлыка для продавцов Market Yandex Go" %}
  
    ![Изображение горизонтального ярлыка формата A9 для продавцов Market Yandex Go](../../_images/labels/label-A9-horizontally-uz.png)
  
    {% endcut %}
  
  * `A9` — ярлык размером 40 × 58 мм без полей, близок к формату A9.
  
    {% cut "Пример ярлыка для продавцов Маркета" %}
  
    ![Изображение вертикального ярлыка формата A9 для продавцов Маркета](../../_images/labels/label-A9.png)
  
    {% endcut %}
  
    {% cut "Пример ярлыка для продавцов Market Yandex Go" %}
  
    ![Изображение вертикального ярлыка формата A9 для продавцов Market Yandex Go](../../_images/labels/label-A9-uz.png)
  
    {% endcut %}
  
  * `A7` — ярлык размером 75 × 120 мм (80,4 × 125,6 мм с учетом полей), близок к формату A7.
  
    {% cut "Пример ярлыка для продавцов Маркета" %}
  
    ![Изображение ярлыка формата A7 для продавцов Маркета](../../_images/labels/label-A7.jpg)
  
    {% endcut %}
  
    {% cut "Пример ярлыка для продавцов Market Yandex Go" %}
  
    ![Изображение ярлыка формата A7 для продавцов Market Yandex Go](../../_images/labels/label-A7-uz.png)
  
    {% endcut %}
  
  * `A4` — на листе A4 располагается ярлык того формата, который выбран в кабинете продавца на Маркете — перейдите на страницу **Заказы** → **Заказы и отгрузки** → на вкладке нужной модели работы нажмите кнопку **Формат ярлыков**.
  
  
  **Type**: string
  
  _Enum:_{.json-schema-reset .json-schema-value} `A9_HORIZONTALLY`, `A9`, `A7`, `A4`
  
  </div>
  
  ## Responses
  
  <div class="openapi__response__code__200">
  
  ## 200 OK
  
  PDF‑файл с ярлыками для коробки. Файл содержит одну страницу с ярлыком.
  
  ### Body
  
  application/pdf
  
  **Type:** string
  
  **Format:** binary
  
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
    - description: Идентификатор заказа.
      name: orderId
      in: path
      required: true
      schema:
        type: integer
        format: int64
    - deprecated: true
      x-deprecation-config:
        shutdown-date: '2026-10-12'
      description: |
        {% note warning "Параметр устарел и будет отключен 12.10.2026." %}
  
        Передайте любое число, чтобы получился корректный URL.
  
        {% endnote %}
  
        Идентификатор грузового места.
      name: shipmentId
      in: path
      required: true
      schema:
        type: integer
        format: int64
    - description: Идентификатор коробки.
      name: boxId
      in: path
      required: true
      schema:
        type: integer
        format: int64
  searchParams:
    - description: >-
        Настройка размещения ярлыков на странице. Если параметра нет, возвращается
        PDF с ярлыками формата A7.
      name: format
      in: query
      required: false
      schema:
        $ref: >-
          /home/sandbox/.ya/build/build_root/oxq2/00000b/market/mbi/docs/partner-api/docfiles/__docsbuild/.tmp_input/ru/openapi/partner-api-spec/order-labels/schemas.yaml#/PageFormatType
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
  path: >-
    v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label
  host: https://api.partner.market.yandex.ru
  
  ```
        

{% endlist %}


</div>
<!-- endsource: ru/api/order-labels/generateOrderLabel.md -->

[*Deprecated]: No longer supported, please use an alternative and newer version.
