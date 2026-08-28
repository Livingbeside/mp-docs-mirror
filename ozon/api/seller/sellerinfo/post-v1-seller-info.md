---
title: Информация о кабинете продавца
api: ozon-seller
method: POST
path: /v1/seller/info
operation_id: SellerAPI_SellerInfo
tags:
  - SellerInfo
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0ab82f73b7089693
---

# Информация о кабинете продавца

`POST /v1/seller/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Информация о кабинете продавца

- `company` — object. Компания.
  - `country` — string. Страна.
  - `currency` — string. Валюта: - `RUB` — российский рубль; - `EUR` — евро; - `USD` — доллар США; - `CNY` — юань; - `BYN` — белорусский рубль; - `KZT` — тенге; - `KGS` — киргизский сом.
  - `inn` — string. ИНН.
  - `legal_name` — string. Название юридического лица.
  - `name` — string. Название компании на Ozon.
  - `ogrn` — string. ОГРН.
  - `ownership_form` — string. Форма собственности.
  - `tax_system` — string (UNKNOWN, UNSPECIFIED, OSNO, USN, NPD, AUSN, PSN). Система налогообложения: - `UNKNOWN` — неизвестная, - `UNSPECIFIED` — не определена, - `OSNO` — ОСНО, - `USN` — УСН, - `NPD` — НПД, - `AUSN` — АУСН, - `PSN` — ПСН. По умолчанию: `UNKNOWN`.
- `ratings` — array[object]. Список рейтингов.
  - `current_value` — object. Значение рейтинга.
    - `date_from` — string<date-time>. Дата начала подсчёта рейтинга.
    - `date_to` — string<date-time>. Дата конца подсчёта рейтинга.
    - `formatted` — string. Отформатированное значение рейтинга.
    - `status` — object. Статус рейтинга.
      - `danger` — boolean. Признак, превышено ли пороговое значение рейтинга для блокировки.
      - `premium` — boolean. Признак, достигнуто ли пороговое значение для участия в Premium-программе.
      - `warning` — boolean. Признак наличия предупреждения о возможном превышении порогового значения для блокировки.
    - `value` — number<double>. Значение рейтинга в системе.
  - `name` — string. Название рейтинга.
  - `past_value` — object. Предыдущее значение рейтинга.
    - `date_from` — string<date-time>. Дата начала подсчёта рейтинга.
    - `date_to` — string<date-time>. Дата конца подсчёта рейтинга.
    - `formatted` — string. Отформатированное значение рейтинга.
    - `status` — object. Статус рейтинга.
      - `danger` — boolean. Признак, превышено ли пороговое значение рейтинга для блокировки.
      - `premium` — boolean. Признак, достигнуто ли пороговое значение для участия в Premium-программе.
      - `warning` — boolean. Признак наличия предупреждения о возможном превышении порогового значения для блокировки.
    - `value` — number<double>. Значение рейтинга в системе.
  - `rating` — string. Название рейтинга в системе.
  - `status` — string (UNKNOWN, OK, WARNING, CRITICAL). Статус рейтинга: - `UNKNOWN` — не определён; - `OK` — хороший; - `WARNING` — показатели требуют внимания; - `CRITICAL` — критичный. По умолчанию: `UNKNOWN`.
  - `value_type` — string (UNKNOWN, INDEX, PERCENT, TIME, RATIO, REVIEW_SCORE, COUNT). Тип значения: - `UNKNOWN` — не определён, - `INDEX` — индекс, - `PERCENT` — процент, - `TIME` — время, - `RATIO` — коэффициент, - `REVIEW_SCORE` — оценка, - `COUNT` — счёт. По умолчанию: `UNKNOWN`.
- `subscription` — object. Подписка.
  - `is_premium` — boolean. `true`, если есть подписка.
  - `type` — string (UNKNOWN, UNSPECIFIED, PREMIUM, PREMIUM_LITE, PREMIUM_PLUS, PREMIUM_PRO). Тип подписки: - `UNKNOWN` — неизвестный, - `UNSPECIFIED` — нет подписки, - `PREMIUM` — Premium, - `PREMIUM_LITE` — Premium Lite, - `PREMIUM_PLUS` — Premium Plus, - `PREMIUM_PRO` — Premium Pro. По умолчанию: `UNKNOWN`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
