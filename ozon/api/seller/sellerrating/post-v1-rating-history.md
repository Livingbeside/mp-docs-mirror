---
title: Получить информацию о рейтингах продавца за период
api: ozon-seller
method: POST
path: /v1/rating/history
operation_id: RatingAPI_RatingHistoryV1
tags:
  - SellerRating
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 671ee8b9e8f92de0
---

# Получить информацию о рейтингах продавца за период

`POST /v1/rating/history`

Информация о рейтингах за заданный период и с фильтром по нужному рейтингу.
Соответствует разделу **Рейтинги → Рейтинги продавца** в личном кабинете.

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string<date-time> **обязательный**. Начало периода.
- `date_to` — string<date-time> **обязательный**. Конец периода.
- `ratings` — ? **обязательный**. Фильтр по рейтингу. Рейтинги, по которым нужно получить значение за период: - `rating_on_time` — процент заказов, выполненных вовремя за последние 30 дней. - `rating_review_avg_score_total` — средняя оценка всех товаров. - `rating_ssl` — оценка работы по FBO. Учитывает `rating_on_time_supply_delivery`, `rating_on_time_supply_cancellation` и `rating_order_accuracy`. - `rating_on_time_supply_delivery` — процент поставок, которые вы привезли на склад в выбранный временной интервал за последние 60 дней. - `rating_order_accuracy` — процент поставок без излишков, недостач, пересорта и брака за последние 60 дней. - `rating_on_time_supply_cancellation` — процент заявок на поставку, которые завершились или были отменены без опоздания за последние 60 дней. - `rating_reaction_time` — время в секундах, в течение которого покупатели в среднем ждали ответа на своё первое сообщение в чате за последние 30 дней. - `rating_average_response_time` — время в секундах, в течение которого покупатели в среднем ждали вашего ответа за последние 30 дней. - `rating_replied_dialogs_ratio` — доля диалогов хотя бы с одним вашим ответом в течение 24 часов за последние 30 дней. - `rating_general_indicator_fbs_rfbs` — индекс ошибок FBS и rFBS. - `rating_price_green` — выгодный индекс цен. - `rating_price_yellow` — умеренный индекс цен. - `rating_price_red` — невыгодный индекс цен. - `rating_price_super` — супер-выгодный индекс цен. Если вы хотите получить информацию по начисленным штрафным баллам для рейтингов `rating_on_time` и `rating_review_avg_score_total`, передайте значения нужных рейтингов в этом параметре и `with_premium_scores=true`.
- `with_premium_scores` — boolean. Признак, что в ответе нужно вернуть информацию о штрафных баллах в Premium-программе.

## Ответы

**200** — Информация о рейтингах

- `premium_scores` — ?. Информация о штрафных баллах в Premium-программе.
  - `rating` — string. Название рейтинга.
  - `scores` — ?. Информация о штрафных баллах.
    - `date` — string<date-time>. Дата, когда были начислены штрафные баллы.
    - `rating_value` — number<double>. Значение рейтинга, за которое были начислены штрафные баллы.
    - `value` — integer<int32>. Количество начисленных штрафных баллов.
- `ratings` — ?. Информация о рейтингах продавца.
  - `danger_threshold` — number<double>. Пороговое значение рейтинга, после которого продажи будут заблокированы.
  - `premium_threshold` — number<double>. Пороговое значение рейтинга для участия в Premium-программе.
  - `rating` — string. Системное название рейтинга.
  - `values` — ?. Список значений рейтинга.
    - `date_from` — string<date-time>. Дата начала подсчёта рейтинга.
    - `date_to` — string<date-time>. Дата конца подсчёта рейтинга.
    - `status` — object. Статус рейтинга.
      - `danger` — boolean. Признак, превышено ли пороговое значение рейтинга для блокировки.
      - `premium` — boolean. Признак, достигнуто ли пороговое значение для участия в Premium-программе.
      - `warning` — boolean. Признак наличия предупреждения о возможном превышении порогового значения для блокировки.
    - `value` — number<double>. Значение рейтинга.
  - `warning_threshold` — number<double>. Пороговое значение рейтинга, после которого появится предупреждение о возможной блокировке.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
