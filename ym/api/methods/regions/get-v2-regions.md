---
title: Поиск регионов по их имени
api: yandex-market
method: GET
path: /v2/regions
operation_id: searchRegionsByName
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
content_sha: f4741a828f003e83
---

# Поиск регионов по их имени

`GET /v2/regions`

{% include notitle [access](../../_auto/method_scopes/searchRegionsByName.md) %} Возвращает информацию о регионе, удовлетворяющем заданным в запросе условиям поиска. Если найдено несколько регионов, удовлетворяющих условиям поиска, возвращается информация по каждому найденному региону (но не более десяти регионов) для возможности определения нужного региона по родительским регионам. {% include notitle [limit](../../_auto/method_limits/searchRegionsByName.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `name` | query | string | да | Название региона. Важно учитывать регистр: первая буква должна быть заглавной, остальные — строчными. Например, `Москва`. |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Ответы

**200** — Список найденных регионов.

- `regions` — array[object] **обязательный**. Регион доставки.
  - `id` — integer<int64> **обязательный**. Идентификатор региона.
  - `name` — string **обязательный**. Название региона.
  - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
  - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
- `paging` — object. Идентификатор следующей страницы.
  - `nextPageToken` — string. Идентификатор следующей страницы результатов.

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
