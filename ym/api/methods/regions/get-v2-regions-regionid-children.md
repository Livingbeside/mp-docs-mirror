---
title: Информация о дочерних регионах
api: yandex-market
method: GET
path: /v2/regions/{regionId}/children
operation_id: searchRegionChildren
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
content_sha: a37126ddc8e34a5c
---

# Информация о дочерних регионах

`GET /v2/regions/{regionId}/children`

{% include notitle [access](../../_auto/method_scopes/searchRegionChildren.md) %} Возвращает информацию о регионах, являющихся дочерними по отношению к региону, идентификатор которого указан в запросе. {% include notitle [limit](../../_auto/method_limits/searchRegionChildren.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `regionId` | path | integer<int64> | да | Идентификатор региона. Идентификатор региона можно получить c помощью запроса [GET v2/regions](../../reference/regions/searchRegionsByName.md). |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-truncate-param-description }} {% note warning %} У данного лимита нет значения по умолчанию. {% endnote %} |
| `page` | query | integer<int32> | нет | {% note warning "Параметр устарел и будет отключен 05.10.2026." %} Вместо `page` и `pageSize` используйте пагинацию по `pageToken` и `limit`. [Подробнее о типах пагинации и их использовании](../../concepts/pagination.md) {% endnote %} Номер страницы результатов. Используется вместе с параметром `pageSize`. |
| `pageSize` | query | integer<int32> | нет | {% note warning "Параметр устарел и будет отключен 05.10.2026." %} Вместо `page` и `pageSize` используйте пагинацию по `pageToken` и `limit`. [Подробнее о типах пагинации и их использовании](../../concepts/pagination.md) {% endnote %} Размер страницы. Используется вместе с параметром `page`. |

## Ответы

**200** — Регионы, являющиеся дочерними к указанному в запросе.

- `pager` — object. Модель для пагинации.
  - `total` — integer<int32>. Сколько всего найдено элементов.
  - `from` — integer<int32>. Начальный номер найденного элемента на странице.
  - `to` — integer<int32>. Конечный номер найденного элемента на странице.
  - `currentPage` — integer<int32>. Текущая страница.
  - `pagesCount` — integer<int32>. Общее количество страниц.
  - `pageSize` — integer<int32>. Размер страницы.
- `paging` — object. Идентификатор следующей страницы.
  - `nextPageToken` — string. Идентификатор следующей страницы результатов.
- `regions` — object. Информация о родительском и дочерних регионах.
  - `id` — integer<int64> **обязательный**. Идентификатор региона.
  - `name` — string **обязательный**. Название региона.
  - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
  - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
  - `children` — array[object]. Дочерние регионы.
    - `id` — integer<int64> **обязательный**. Идентификатор региона.
    - `name` — string **обязательный**. Название региона.
    - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
    - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)

**400** — Запрос содержит неправильные данные. [Подробнее об ошибке](../../concepts/error-codes.md#400)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

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
