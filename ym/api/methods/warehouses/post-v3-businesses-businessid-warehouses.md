---
title: Список складов
api: yandex-market
method: POST
path: /v3/businesses/{businessId}/warehouses
operation_id: getPartnerWarehouses
tags:
  - warehouses
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 63f16f8877ddc8f1
---

# Список складов

`POST /v3/businesses/{businessId}/warehouses`

{% include notitle [access](../../_auto/method_scopes/getPartnerWarehouses.md) %} Возвращает список складов кабинета и информацию о них. Для каждого склада возвращается список моделей работы (FBS, DBS, Экспресс) и доступность API для каждой модели. {% note warning "Метод подходит, только если в кабинете нет групп складов" %} Метод возвращает только отдельные склады и не возвращает группы складов. Если в кабинете есть группы складов, используйте метод [POST v2/businesses/{businessId}/warehouses](../../reference/warehouses/getPagedWarehouses.md). [Что такое группы складов и зачем они нужны](https://yandex.ru/support/marketplace/assortment/operations/stocks.html#unified-stocks). {% endnote %} {% include notitle [limit](../../_auto/method_limits/getPartnerWarehouses.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Запрос

**Тело запроса** (`application/json`):

- `warehouseIds` — array[integer<int64>]. Список идентификаторов складов, которые необходимо вернуть. Если параметр не указан, возвращаются все склады кабинета.
- `components` — array[string (ADDRESS)]. Свойства складов, которые необходимо вернуть. Если какое-то значение параметра не задано, этой информации в ответе не будет. Передавайте параметр, только если нужна информация, которую он возвращает.

## Ответы

**200** — Список складов и их свойства, которые вы запрашивали.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о складах в кабинете.
  - `warehouses` — array[object] **обязательный**. Список складов.
    - `id` — integer<int64> **обязательный**. Идентификатор склада.
    - `name` — string **обязательный**. Название склада.
    - `models` — array[object] **обязательный**. Модели работы, доступные для склада.
      - `placementType` — string (FBS, DBS, EXPRESS) **обязательный**. Модель работы: * `FBS` — FBS. * `DBS` — DBS. * `EXPRESS` — Экспресс.
      - `apiAvailability` — string (AVAILABLE, DISABLED_BY_INACTIVITY, DISABLED_BY_NO_ACTIVE_CONTRACT, MANUALLY_DISABLED, DISABLED_BY_NO_PLACEMENT_TYPE) **обязательный**. Возможность использовать API: * `AVAILABLE` — методы API доступны для выполнения запросов. * `DISABLED_BY_INACTIVITY` — методы API недоступны, так как магазин не размещал товары на витрине больше 90 дней. * `DISABLED_BY_NO_ACTIVE_CONTRACT` — методы API недоступны из-за отсутствия активного договора с Маркетом. * `MANUALLY_DISABLED` — методы API недоступны, так как интеграция выключена вручную. * `DISABLED_BY_NO_PLACEMENT_TYPE` — методы API недоступны, так как магазин не подключен к программе размещения. [Подробная инструкция по восстановлению доступа](../../concepts/api-access.md)
    - `address` — object. Адрес склада. Возвращается, только если в запросе параметр `components` принимает значение `ADDRESS`.
      - `city` — string **обязательный**. Город.
      - `street` — string. Улица.
      - `number` — string. Номер дома.
      - `building` — string. Номер строения.
      - `block` — string. Номер корпуса.
      - `gps` — object **обязательный**. GPS-координаты широты и долготы.
        - `latitude` — number **обязательный**. Широта.
        - `longitude` — number **обязательный**. Долгота.
  - `paging` — object. Идентификатор следующей страницы.
    - `nextPageToken` — string. Идентификатор следующей страницы результатов.

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
