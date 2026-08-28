---
title: Списки характеристик товаров по категориям
api: yandex-market
method: POST
path: /v2/category/{categoryId}/parameters
operation_id: getCategoryContentParameters
tags:
  - content
  - dbs
  - fby
  - fbs
  - express
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 1185ad5e47f06551
---

# Списки характеристик товаров по категориям

`POST /v2/category/{categoryId}/parameters`

{% include notitle [access](../../_auto/method_scopes/getCategoryContentParameters.md) %} Возвращает список характеристик с допустимыми значениями для заданной [листовой категории](*list-category). Поля в ответе определяют правила передачи характеристики в методах: - [POST v2/businesses/{businessId}/offer-mappings/update](../../reference/business-offer-mappings/updateOfferMappings.md) - [POST v2/businesses/{businessId}/offer-cards/update](../../reference/content/updateOfferContent.md) {% include notitle [limit](../../_auto/method_limits/getCategoryContentParameters.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `categoryId` | path | integer<int64> | да | Идентификатор категории на Маркете. Чтобы узнать идентификатор категории, к которой относится интересующий вас товар, воспользуйтесь запросом [POST v2/categories/tree](../../reference/categories/getCategoriesTree.md). |
| `businessId` | query | integer<int64> | нет | Идентификатор кабинета. Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). Передайте параметр, чтобы получить характеристики, которые являются особенностями варианта товара в данном кабинете. |

## Ответы

**200** — Список характеристик товаров из заданной категории.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о параметрах категории.
  - `categoryId` — integer<int32> **обязательный**. Идентификатор категории на Маркете. При изменении категории убедитесь, что характеристики товара и их значения в параметре `parameterValues` вы передаете для новой категории. Список категорий Маркета можно получить с помощью запроса [POST v2/categories/tree](../../reference/categories/getCategoriesTree.md).
  - `parameters` — array[object]. Список характеристик.
    - `id` — integer<int64> **обязательный**. Идентификатор характеристики.
    - `name` — string. Название характеристики.
    - `type` — string (TEXT, ENUM, BOOLEAN, NUMERIC) **обязательный**. Тип данных.
    - `unit` — object. Единицы измерения характеристики товара.
      - `defaultUnitId` — integer<int64> **обязательный**. Единица измерения по умолчанию.
      - `units` — array[object] **обязательный**. Допустимые единицы измерения.
        - `id` — integer<int64> **обязательный**. Идентификатор единицы измерения.
        - `name` — string **обязательный**. Сокращенное название единицы измерения.
        - `fullName` — string **обязательный**. Полное название единицы измерения.
    - `description` — string. Описание характеристики.
    - `recommendationTypes` — array[string (HAS_VIDEO, RECOGNIZED_VENDOR, MAIN, ADDITIONAL, DISTINCTIVE, FILTERABLE, PICTURE_COUNT, HAS_DESCRIPTION, HAS_BARCODE, FIRST_PICTURE_SIZE, TITLE_LENGTH, DESCRIPTION_LENGTH…)]. Перечень возможных рекомендаций по заполнению карточки, к которым относится данная характеристика.
    - `required` — boolean **обязательный**. Обязательность характеристики.
    - `filtering` — boolean **обязательный**. Используется ли характеристика в фильтре.
    - `distinctive` — boolean **обязательный**. Является ли характеристика особенностью варианта.
    - `multivalue` — boolean **обязательный**. Можно ли передать сразу несколько значений.
    - `allowCustomValues` — boolean **обязательный**. Можно ли передавать собственное значение, которого нет в списке вариантов Маркета. Только для характеристик типа `ENUM`.
    - `values` — array[object]. Список допустимых значений параметра. Только для характеристик типа `ENUM`.
      - `id` — integer<int64> **обязательный**. Идентификатор значения.
      - `value` — string **обязательный**. Значение.
      - `description` — string. Описание значения.
    - `constraints` — object. Ограничения на значения. Только для характеристик типа `TEXT` и `NUMERIC`. - Для `NUMERIC` используются поля `minValue` и `maxValue`. - Для `TEXT` используется поле `maxLength`.
      - `minValue` — number<double>. Минимальное число.
      - `maxValue` — number<double>. Максимальное число.
      - `maxLength` — integer<int32>. Максимальная длина текста.
    - `valueRestrictions` — array[object]. Ограничения на значения, накладываемые другими характеристиками. Только для характеристик типа `ENUM`.
      - `limitingParameterId` — integer<int64> **обязательный**. Идентификатор ограничивающей характеристики.
      - `limitedValues` — array[object] **обязательный**. Значения ограничивающей характеристики и соответствующие допустимые значения текущей характеристики.
        - `limitingOptionValueId` — integer<int64> **обязательный**. Идентификатор значения ограничивающей характеристики.
        - `optionValueIds` — array[integer<int64>] **обязательный**. Идентификаторы допустимых значений ограничиваемой характеристики.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибках при работе с категориями](../../concepts/error-codes#categories)

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
