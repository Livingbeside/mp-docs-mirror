---
title: Получение точек ПВЗ Маркета
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/logistics-points
operation_id: getLogisticPoints
tags:
  - logistic-points
  - laas
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 62b0e2ff73d3fe6c
---

# Получение точек ПВЗ Маркета

`POST /v1/businesses/{businessId}/logistics-points`

{% include notitle [access](../../_auto/method_scopes/getLogisticPoints.md) %} Возвращает список пунктов выдачи заказов Маркета. Регулярно запрашивайте эту информацию, чтобы в системе магазина хранить актуальные данные. Например, раз в день. {% include notitle [limit](../../_auto/method_limits/getLogisticPoints.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |
| `pageToken` | query | string | нет | Идентификатор страницы c результатами. Если параметр не указан, возвращается первая страница. Передавайте значение выходного параметра `nextPageToken`, полученное при последнем запросе. |
| `limit` | query | integer<int32> | нет | {{ limit-param-description }} |

## Ответы

**200** — Информация о пунктах выдачи заказов Маркета.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о пунктах выдачи заказов.
  - `logisticPoints` — array[object] **обязательный**. Пункты выдачи заказов.
    - `logisticPointId` — integer<int64> **обязательный**. Идентификатор пункта выдачи. Его можно узнать с помощью метода [POST v1/businesses/{businessId}/logistics-points](../../reference/logistic-points/getLogisticPoints.md).
    - `brand` — string (MARKET) **обязательный**. Тип пункта выдачи: * `MARKET` — пункт выдачи Маркета.
    - `address` — object **обязательный**. Адрес пункта выдачи.
      - `fullAddress` — string **обязательный**. Полный адрес.
      - `gps` — object **обязательный**. GPS-координаты широты и долготы.
        - `latitude` — number **обязательный**. Широта.
        - `longitude` — number **обязательный**. Долгота.
      - `regionId` — integer<int64> **обязательный**. Идентификатор региона. Информацию о регионе можно получить c помощью метода [GET v2/regions](../../reference/regions/searchRegionsById.md).
      - `city` — string. Город.
      - `street` — string. Улица.
      - `house` — string. Номер дома.
      - `building` — string. Номер строения.
      - `block` — string. Номер корпуса.
      - `km` — integer<int32>. Порядковый номер километра, на котором располагается пункт выдачи. Указывается, если в адресе нет улицы.
      - `additional` — string. Дополнительная информация.
    - `workingSchedule` — object **обязательный**. Расписание работы пункта выдачи.
      - `schedule` — array[object] **обязательный**. График работы.
        - `day` — string (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY) **обязательный**. День недели.
        - `startTime` — string **обязательный**. Время начала рабочего дня. Формат: `ЧЧ:ММ`.
        - `endTime` — string **обязательный**. Время конца рабочего дня. Формат: `ЧЧ:ММ`.
      - `holidays` — array[string<date>]. Расписание праздничных дней.
    - `deliveryRestrictions` — object **обязательный**. Ограничения на доставку в пункт выдачи.
      - `dimensionsRestrictions` — object **обязательный**. Ограничения по размеру одного товара.
        - `weight` — integer<int32> **обязательный**. Максимальный вес в граммах.
        - `height` — integer<int32> **обязательный**. Максимальная высота в сантиметрах.
        - `width` — integer<int32> **обязательный**. Максимальная ширина в сантиметрах.
        - `length` — integer<int32> **обязательный**. Максимальная длина в сантиметрах.
        - `dimensionsSum` — integer<int32> **обязательный**. Максимальная сумма измерений в сантиметрах.
    - `features` — array[string (RETURN_ALLOWED)]. Свойства пункта выдачи.
    - `storagePeriod` — integer<int64> **обязательный**. Срок хранения заказа в пункте выдачи. Указывается в днях.
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
