---
title: Информация о регионе
api: yandex-market
method: GET
path: /v2/regions/{regionId}
operation_id: searchRegionsById
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
content_sha: ae402f6fbf5e063d
---

# Информация о регионе

`GET /v2/regions/{regionId}`

{% include notitle [access](../../_auto/method_scopes/searchRegionsById.md) %} Возвращает информацию о регионе. {% include notitle [limit](../../_auto/method_limits/searchRegionsById.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `regionId` | path | integer<int64> | да | Идентификатор региона. Идентификатор региона можно получить c помощью запроса [GET v2/regions](../../reference/regions/searchRegionsByName.md). |

## Ответы

**200** — Найденный регион.

- `regions` — array[object]. Регион доставки. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} В массиве всегда возвращается один регион, используйте поле `region` вместо него. {% endnote %}
  - `id` — integer<int64> **обязательный**. Идентификатор региона.
  - `name` — string **обязательный**. Название региона.
  - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
  - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
- `region` — object **обязательный**. Регион доставки.
  - `id` — integer<int64> **обязательный**. Идентификатор региона.
  - `name` — string **обязательный**. Название региона.
  - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
  - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)

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

**404** — Запрашиваемый ресурс не найден. [Подробнее об ошибке](../../concepts/error-codes.md#404)

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
