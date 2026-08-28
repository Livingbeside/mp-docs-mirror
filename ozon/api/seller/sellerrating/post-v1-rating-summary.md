---
title: Получить информацию о текущих рейтингах продавца
api: ozon-seller
method: POST
path: /v1/rating/summary
operation_id: RatingAPI_RatingSummaryV1
tags:
  - SellerRating
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 034c930365c20ec0
---

# Получить информацию о текущих рейтингах продавца

`POST /v1/rating/summary`

Рейтинг продавца по следующим показателям: индекс цен, доставки вовремя, процент отмен, жалобы и другие. Соответствует разделу **Рейтинги → Рейтинги продавца** в личном кабинете.

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Информация о рейтингах

- `groups` — ?. Список с группами рейтингов.
  - `group_name` — string. Название группы рейтингов.
  - `items` — ?. Список рейтингов.
    - `change` — object. Изменение рейтинга: отношение предыдущего значения к текущему.
      - `direction` — string. Как изменилось значение рейтинга: - `DIRECTION_UNKNOWN` — не определено. - `DIRECTION_NONE` — не изменилось. - `DIRECTION_RISE` — выросло. - `DIRECTION_FALL` — упало.
      - `meaning` — string. Что означает изменение: - `MEANING_UNKNOWN` — неизвестно. - `MEANING_NONE` — нейтрально. - `MEANING_GOOD` — показатель улучшается, всё хорошо. - `MEANING_BAD` — показатель падает, нужно что-то сделать.
    - `current_value` — number<double>. Текущее значение рейтинга.
    - `name` — string. Название рейтинга.
    - `past_value` — number<double>. Предыдущее значение рейтинга.
    - `rating` — string. Название рейтинга в системе.
    - `rating_direction` — string. Каким должно быть значение рейтинга, чтобы оно считалось хорошим: - `UNKNOWN_DIRECTION` — не определено. - `NEUTRAL` — неважно. - `HIGHER_IS_BETTER` — чем выше, тем лучше. - `LOWER_IS_BETTER` — чем ниже, тем лучше.
    - `status` — string. Статус рейтинга: - `UNKNOWN_STATUS` — не определён. - `OK` — все хорошо. - `WARNING` — показатели требуют внимания. - `CRITICAL` — критичный рейтинг.
    - `value_type` — string. Тип значения: - `UNKNOWN_VALUE` — не определён. - `INDEX` — индекс. - `PERCENT` — процент. - `TIME` — время. - `RATIO` — коэффициент. - `REVIEW_SCORE` — оценка. - `COUNT` — счёт.
- `localization_index` — ?. Данные по индексу локализации. Если за последние 14 дней у вас не было продаж, поля параметра будут пустыми.
  - `calculation_date` — string<date-time>. Дата расчёта индекса локализации.
  - `localization_percentage` — integer<int32>. Значение индекса локализации.
- `penalty_score_exceeded` — boolean. Признак, что баланс штрафных баллов превышен.
- `premium` — boolean. Признак наличия подписки [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program).
- `premium_plus` — boolean. Признак наличия подписки [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
