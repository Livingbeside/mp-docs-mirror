---
title: Индекс качества магазинов
api: yandex-market
method: POST
path: /v2/businesses/{businessId}/ratings/quality
operation_id: getQualityRatings
tags:
  - ratings
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 1767c20b4ed43bf0
---

# Индекс качества магазинов

`POST /v2/businesses/{businessId}/ratings/quality`

{% include notitle [access](../../_auto/method_scopes/getQualityRatings.md) %} Возвращает значение индекса качества магазинов и его составляющие. Подробнее об индексе качества читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/quality/score/). {% include notitle [limit](../../_auto/method_limits/getQualityRatings.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `dateFrom` — string<date>. Начало периода. Формат даты: `ГГГГ‑ММ‑ДД`. Не может быть раньше 30 дней от текущей даты.
- `dateTo` — string<date>. Конец периода. Формат даты: `ГГГГ‑ММ‑ДД`. Не может быть позже текущей даты.
- `campaignIds` — array[integer<int64>] **обязательный**. Список идентификаторов кампаний магазинов.

## Ответы

**200** — Значение индекса качества магазинов и его составляющие.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация об индексе качества магазинов.
  - `campaignRatings` — array[object] **обязательный**. Список магазинов c информацией об их индексе качества.
    - `campaignId` — integer<int64> **обязательный**. Идентификатор кампании (магазина) — технический идентификатор, который представляет ваш магазин в системе Яндекс Маркета при работе через API. Он однозначно связывается с вашим магазином, но предназначен только для автоматизированного взаимодействия. Его можно узнать с помощью запроса [GET v2/campaigns](../../reference/campaigns/getCampaigns.md) или найти в кабинете продавца на Маркете. Нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**: * блок **Идентификатор кампании**; * вкладка **Лог запросов** → выпадающий список в блоке **Показывать логи**. ⚠️ Не путайте его с: - идентификатором магазина, который отображается в личном кабинете продавца; - рекламными кампаниями.
    - `ratings` — array[object] **обязательный**. Список значений индекса качества.
      - `rating` — integer<int64> **обязательный**. Значение индекса качества.
      - `calculationDate` — string<date> **обязательный**. Дата вычисления. Формат даты: `ГГГГ‑ММ‑ДД`.
      - `components` — array[object] **обязательный**. Составляющие индекса качества.
        - `value` — number<double> **обязательный**. Значение составляющей в процентах.
        - `componentType` — string (DBS_CANCELLATION_RATE, DBS_LATE_DELIVERY_RATE, FBS_CANCELLATION_RATE, FBS_LATE_SHIP_RATE, FBY_LATE_DELIVERY_RATE, FBY_CANCELLATION_RATE, FBY_DELIVERY_DIFF_RATE, FBY_LATE_EDITING_RATE) **обязательный**. Тип составляющей.

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
