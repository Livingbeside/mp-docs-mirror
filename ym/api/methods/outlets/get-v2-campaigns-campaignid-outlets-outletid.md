---
title: Информация об одной точке продаж
api: yandex-market
method: GET
path: /v2/campaigns/{campaignId}/outlets/{outletId}
operation_id: getOutlet
tags:
  - outlets
  - dbs
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 95a22d5e88d40866
---

# Информация об одной точке продаж

`GET /v2/campaigns/{campaignId}/outlets/{outletId}`

{% include notitle [access](../../_auto/method_scopes/getOutlet.md) %}

Возвращает информацию о точках продаж магазина.

{% include notitle [limit](../../_auto/method_limits/getOutlet.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `campaignId` | path | integer<int64> | да | Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями. |
| `outletId` | path | integer<int64> | да | Идентификатор точки продаж. |

## Ответы

**200** — Информация о точке продаж.

- `outlet` — object. Информация о точке продаж.
  - `name` — string **обязательный**. Название точки продаж.
  - `type` — string (DEPOT, MIXED, RETAIL, NOT_DEFINED) **обязательный**. Тип точки продаж. Возможные значения: * `DEPOT` — пункт выдачи заказов. * `MIXED` — смешанный тип точки продаж (торговый зал и пункт выдачи заказов). * `RETAIL` — розничная точка продаж (торговый зал). * `NOT_DEFINED` — неизвестный тип точки продажи. При определении типа произошла ошибка.
  - `coords` — string. Координаты точки продаж. Формат: долгота, широта. Разделители: запятая и / или пробел. Например, `20.4522144, 54.7104264`. Если параметр не передан, координаты будут определены по значениям параметров, вложенных в `address`.
  - `isMain` — boolean. Признак основной точки продаж. Возможные значения: * `false` — неосновная точка продаж. * `true` — основная точка продаж.
  - `shopOutletCode` — string. Идентификатор точки продаж, присвоенный магазином.
  - `visibility` — string (HIDDEN, VISIBLE, UNKNOWN). Состояние точки продаж. Возможные значения: * `HIDDEN` — точка продаж выключена. * `VISIBLE` — точка продаж включена. * `UNKNOWN` — неизвестное состояние точки продажи. При определении состояния произошла ошибка.
  - `address` — object **обязательный**. Адрес точки продаж.
    - `regionId` — integer<int64> **обязательный**. Идентификатор региона. Идентификатор можно получить c помощью запроса [GET v2/regions](../../reference/regions/searchRegionsByName.md). {% note alert "Типы регионов при создании и редактировании точек продаж" %} Указывайте только регионы типов `TOWN` (город), `CITY` (крупный город) и `REPUBLIC_AREA` (район субъекта федерации). Тип региона указан в выходных параметрах `type` запросов [GET v2/regions](../../reference/regions/searchRegionsByName.md) и [GET v2/regions/{regionId}](../../reference/regions/searchRegionsById.md). {% endnote %}
    - `street` — string. Улица.
    - `number` — string. Номер дома.
    - `building` — string. Номер строения.
    - `estate` — string. Номер владения.
    - `block` — string. Номер корпуса.
    - `additional` — string. Дополнительная информация.
    - `km` — integer<int32>. Порядковый номер километра дороги, на котором располагается точка продаж, если отсутствует улица.
    - `city` — string. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} В ответах города и населенные пункты возвращаются в параметре `regionId`. {% endnote %}
  - `phones` — array[string] **обязательный**. Номера телефонов точки продаж. Передавайте номер в формате: `+ ( ) [# ]`. Примеры: - `+7 (999) 999-99-99` - `+7 (999) 999-99-99#1234`
  - `workingSchedule` — object **обязательный**. Список режимов работы точки продаж.
    - `workInHoliday` — boolean. Признак, работает ли точка продаж в дни государственных праздников. Возможные значения: * `false` — точка продаж не работает в дни государственных праздников. * `true` — точка продаж работает в дни государственных праздников.
    - `scheduleItems` — array[object] **обязательный**. Список расписаний работы точки продаж.
      - `startDay` — string (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY) **обязательный**. Точка продаж работает с указанного дня недели. Возможные значения: * `MONDAY` — понедельник. * `TUESDAY` — вторник. * `WEDNESDAY` — среда. * `THURSDAY` — четверг. * `FRIDAY` — пятница. * `SATURDAY` — суббота. * `SUNDAY` — воскресенье.
      - `endDay` — string (MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY) **обязательный**. Точка продаж работает до указанного дня недели. Возможные значения: * `MONDAY` — понедельник. * `TUESDAY` — вторник. * `WEDNESDAY` — среда. * `THURSDAY` — четверг. * `FRIDAY` — пятница. * `SATURDAY` — суббота. * `SUNDAY` — воскресенье.
      - `startTime` — string **обязательный**. Точка продаж работает c указанного часа. Формат: `ЧЧ:ММ`.
      - `endTime` — string **обязательный**. Точка продаж работает до указанного часа. Формат: `ЧЧ:ММ`.
  - `deliveryRules` — array[object]. Информация об условиях доставки для данной точки продаж. Обязательный параметр, если параметр `type=DEPOT` или `type=MIXED`.
    - `minDeliveryDays` — integer<int32>. Минимальный срок доставки товаров в точку продаж. Указан в рабочих днях. Минимальное значение: `0` — доставка в день заказа. Максимальное значение: `60`. Допустимые сроки доставки (разница между `minDeliveryDays` и `maxDeliveryDays`) зависят от региона. Для доставки по своему региону разница не должна превышать двух дней. Например, если `minDeliveryDays` равно 1, то для `maxDeliveryDays` допускаются значения от 1 до 3. Для доставки в другие регионы: * Если `minDeliveryDays` до 18 дней, разница не должна превышать четырех дней. Например, если `minDeliveryDays` равно 10, то для `maxDeliveryDays` допускаются значения от 10 до 14. * Если `minDeliveryDays` больше 18 дней, разница должна быть не больше чем в два раза. Например, если `minDeliveryDays` равно 21, то для `maxDeliveryDays` допускаются значения от 21 до 42. Обязательный параметр, если `type="DEPOT"` или `type="MIXED"`. Взаимоисключающий с параметром `unspecifiedDeliveryInterval`.
    - `maxDeliveryDays` — integer<int32>. Максимальный срок доставки товаров в точку продаж. Указан в рабочих днях. Минимальное значение: `0` — доставка в день заказа. Максимальное значение: `60`. Допустимые сроки доставки (разница между `minDeliveryDays` и `maxDeliveryDays`) зависят от региона. Для доставки по своему региону разница не должна превышать двух дней. Например, если `minDeliveryDays` равно 1, то для `maxDeliveryDays` допускаются значения от 1 до 3. Для доставки в другие регионы: * Если `minDeliveryDays` до 18 дней, разница не должна превышать четырех дней. Например, если `minDeliveryDays` равно 10, то для `maxDeliveryDays` допускаются значения от 10 до 14. * Если `minDeliveryDays` больше 18 дней, разница должна быть не больше чем в два раза. Например, если `minDeliveryDays` равно 21, то для `maxDeliveryDays` допускаются значения от 21 до 42. Обязательный параметр, если `type="DEPOT"` или `type="MIXED"`. Взаимоисключающий с параметром `unspecifiedDeliveryInterval`.
    - `deliveryServiceId` — integer<int64>. Идентификатор службы доставки товаров в точку продаж. Информацию о службе доставки можно получить с помощью запроса [GET delivery/services](../../reference/delivery-services/getDeliveryServices.md).
    - `orderBefore` — integer<int32>. Час, до которого покупателю нужно сделать заказ, чтобы он был доставлен в точку продаж в сроки от `minDeliveryDays` до `maxDeliveryDays`. Если покупатель оформит заказ после указанного часа, он будет доставлен в сроки от `minDeliveryDays` + 1 рабочий день до `maxDeliveryDays` + 1 рабочий день. Значение по умолчанию: `24`.
    - `priceFreePickup` — number. Цена товара, начиная с которой действует бесплатный самовывоз товара из точки продаж.
    - `unspecifiedDeliveryInterval` — boolean. Признак доставки товаров в точку продаж на заказ. Признак выставлен, если: * точный срок доставки в точку продаж заранее неизвестен (например, если магазин собирает несколько заказов для отправки в точку или населенный пункт); * все товары изготавливаются или поставляются на заказ. Возможные значения: * `true` — товары доставляются в точку продаж на заказ. Параметр указывается только со значением `true`. Взаимоисключающий с параметрами `minDeliveryDays` и `maxDeliveryDays`.
  - `storagePeriod` — integer<int64>. Срок хранения заказа в собственном пункте выдачи заказов. Считается в днях.
  - `id` — integer<int64>. Идентификатор точки продаж, присвоенный Маркетом.
  - `status` — string (AT_MODERATION, FAILED, MODERATED, NONMODERATED, UNKNOWN). Статус точки продаж. Возможные значения: * `AT_MODERATION` — проверяется. * `FAILED` — не прошла проверку и отклонена модератором. * `MODERATED` — проверена и одобрена. * `NONMODERATED` — новая точка, нуждается в проверке. * `UNKNOWN` — статус не указан. При определении статуса произошла ошибка.
  - `region` — object. Регион доставки.
    - `id` — integer<int64> **обязательный**. Идентификатор региона.
    - `name` — string **обязательный**. Название региона.
    - `type` — string (OTHER, CONTINENT, REGION, COUNTRY, COUNTRY_DISTRICT, REPUBLIC, CITY, VILLAGE, CITY_DISTRICT, SUBWAY_STATION, REPUBLIC_AREA) **обязательный**. Тип региона.
    - `parent` — object. (циклическая ссылка ./RegionDTO.yaml)
  - `shopOutletId` — string. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} Вместо него используйте `shopOutletCode`. {% endnote %} Идентификатор точки продаж, заданный магазином.
  - `workingTime` — string. {% note warning "Параметр устарел и будет отключен 19.10.2026." %} Вместо него используйте `workingSchedule`. {% endnote %} Рабочее время.
  - `moderationReason` — string. Статус модерации.

**400** — Запрос содержит неправильные данные. [Подробнее об ошибке](../../concepts/error-codes.md#400)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string (INVALID_FEED_ID, INVALID_WAREHOUSE_ID, GROUPED_WAREHOUSE, DUPLICATE_OFFER, INVALID_TTL, INVALID_COMMENT, LIMIT_EXCEEDED, NON_POSITIVE_LIMIT, REQUEST_LIMIT_EXCEEDED, INVALID_OFFER_ID, MISSING_OFFER_ID, MISSING_OFFER…) **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**401** — В запросе не указаны данные для авторизации. [Подробнее об ошибке](../../concepts/error-codes.md#401)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string (INVALID_FEED_ID, INVALID_WAREHOUSE_ID, GROUPED_WAREHOUSE, DUPLICATE_OFFER, INVALID_TTL, INVALID_COMMENT, LIMIT_EXCEEDED, NON_POSITIVE_LIMIT, REQUEST_LIMIT_EXCEEDED, INVALID_OFFER_ID, MISSING_OFFER_ID, MISSING_OFFER…) **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**403** — Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](../../concepts/error-codes.md#403)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string (INVALID_FEED_ID, INVALID_WAREHOUSE_ID, GROUPED_WAREHOUSE, DUPLICATE_OFFER, INVALID_TTL, INVALID_COMMENT, LIMIT_EXCEEDED, NON_POSITIVE_LIMIT, REQUEST_LIMIT_EXCEEDED, INVALID_OFFER_ID, MISSING_OFFER_ID, MISSING_OFFER…) **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**404** — Запрашиваемый ресурс не найден. [Подробнее об ошибке](../../concepts/error-codes.md#404)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string (INVALID_FEED_ID, INVALID_WAREHOUSE_ID, GROUPED_WAREHOUSE, DUPLICATE_OFFER, INVALID_TTL, INVALID_COMMENT, LIMIT_EXCEEDED, NON_POSITIVE_LIMIT, REQUEST_LIMIT_EXCEEDED, INVALID_OFFER_ID, MISSING_OFFER_ID, MISSING_OFFER…) **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string (INVALID_FEED_ID, INVALID_WAREHOUSE_ID, GROUPED_WAREHOUSE, DUPLICATE_OFFER, INVALID_TTL, INVALID_COMMENT, LIMIT_EXCEEDED, NON_POSITIVE_LIMIT, REQUEST_LIMIT_EXCEEDED, INVALID_OFFER_ID, MISSING_OFFER_ID, MISSING_OFFER…) **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string (INVALID_FEED_ID, INVALID_WAREHOUSE_ID, GROUPED_WAREHOUSE, DUPLICATE_OFFER, INVALID_TTL, INVALID_COMMENT, LIMIT_EXCEEDED, NON_POSITIVE_LIMIT, REQUEST_LIMIT_EXCEEDED, INVALID_OFFER_ID, MISSING_OFFER_ID, MISSING_OFFER…) **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
