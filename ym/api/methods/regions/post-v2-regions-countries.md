---
title: Список допустимых кодов стран
api: yandex-market
method: POST
path: /v2/regions/countries
operation_id: getRegionsCodes
tags:
  - regions
  - fby
  - fbs
  - dbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 8e9dfe46fb84566d
---

# Список допустимых кодов стран

`POST /v2/regions/countries`

{% include notitle [access](../../_auto/method_scopes/getRegionsCodes.md) %}

Возвращает список стран с их кодами в формате :no-translate[ISO 3166-1 alpha-2].

Страна производства `countryCode` понадобится при продаже товаров из-за рубежа для бизнеса. [Инструкция](../../step-by-step/business-info.md)

{% include notitle [limit](../../_auto/method_limits/getRegionsCodes.md) %}

## Ответы

**200** — Список стран с их кодами в формате :no-translate[ISO 3166-1 alpha-2].

- `countries` — array[object] **обязательный**. Список стран с их кодами в формате :no-translate[ISO 3166-1 alpha-2].
  - `region` — object **обязательный**. Регион доставки.
    - `id` — integer<int64> **обязательный**. Идентификатор региона.
    - `name` — string **обязательный**. Название региона.
    - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
    - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
  - `countryCode` — string **обязательный**. Страна производства в формате ISO 3166-1 alpha-2. [Как получить](../../reference/regions/getRegionsCodes.md)

**401** — В запросе не указаны данные для авторизации. [Подробнее об ошибке](../../concepts/error-codes.md#401)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**403** — Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](../../concepts/error-codes.md#403)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
