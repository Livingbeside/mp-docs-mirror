---
title: Получить детализацию запросов по товару
api: ozon-seller
method: POST
path: /v1/analytics/product-queries/details
operation_id: AnalyticsAPI_AnalyticsProductQueriesDetails
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2e201b6fad16262f
---

# Получить детализацию запросов по товару

`POST /v1/analytics/product-queries/details`

Используйте метод, чтобы получить данные по запросам на конкретный товар. Полная аналитика доступна с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program), [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro). Без подписки вы можете посмотреть часть показателей. Метод аналогичен просмотру данных по товару на вкладке **Товары в поиске → Запросы моего товара** в личном кабинете. Аналитику по запросам можно проверить за определённые даты. Для этого укажите интервал в полях `date_from` и `date_to`. Данные за последний месяц доступны в любом интервале, кроме текущей даты — расчёт происходит в течение 1–2 дней. Аналитика за даты раньше месяца назад доступна только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program), [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro) и только по неделям — в запросе укажите параметр `date_from`. [Подробнее о работе с запросами товара в Базе знаний продавца](https://seller-edu.ozon.ru/analytics-and-metrics/graphs/analitika-po-zaprosu)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string<date-time> **обязательный**. Дата начала формирования аналитики.
- `date_to` — string<date-time>. Дата окончания формирования аналитики.
- `limit_by_sku` — integer<int32> **обязательный**. Лимит числа запросов по одному SKU. Максимум — 15 запросов.
- `page` — integer<int32>. Номер страницы, возвращаемой в запросе. Минимум — 0.
- `page_size` — integer<int32> **обязательный**. Количество элементов на странице. Максимум — 100.
- `skus` — array[string<int64>] **обязательный**. Список SKU, идентификаторов товара в системе Ozon. По ним вернётся аналитика по запросам. Максимум — 1000 SKU.
- `sort_by` — string (BY_SEARCHES, BY_VIEWS, BY_POSITION, BY_CONVERSION, BY_GMV). Параметр, по которому товары будут отсортированы. Возможные значения: - `BY_SEARCHES` — по количеству запросов; - `BY_VIEWS` — по количеству просмотров; - `BY_POSITION` — по средней позиции товара; - `BY_CONVERSION` — по значению конверсии; - `BY_GMV` — по объёму продаж по запросам. Сортировка по параметрам `BY_VIEWS`, `BY_POSITION` и `BY_CONVERSION` доступна только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus). По умолчанию: `BY_SEARCHES`.
- `sort_dir` — string (DESCENDING, ASCENDING). Направление сортировки: - `DESCENDING` — по убыванию; - `ASCENDING` — по возрастанию. По умолчанию: `DESCENDING`.

## Ответы

**200** — Информация о запросах по конкретному товару

- `analytics_period` — object. Период, за который формируется аналитика.
  - `date_from` — string. Дата начала формирования аналитики.
  - `date_to` — string. Дата окончания формирования аналитики.
- `page_count` — integer<int64>. Количество страниц.
- `queries` — array[object]. Список запросов.
  - `currency` — string. Валюта.
  - `gmv` — number<float>. Продажи по запросам.
  - `order_count` — integer<int64>. Количество заказов по запросу.
  - `position` — number<float>. Средняя позиция товара. Доступно только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus), иначе поле вернётся пустым.
  - `query` — string. Текст запроса.
  - `query_index` — integer<int64>. Порядковый номер запроса.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `unique_search_users` — integer<int64>. Количество покупателей, которые искали ваш товар на Ozon.
  - `unique_view_users` — integer<int64>. Количество покупателей, которые увидели ваш товар на Ozon. Доступно только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus), иначе поле вернётся пустым.
  - `view_conversion` — number<float>. Конверсия из просмотра товара. Доступно только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus), иначе поле вернётся пустым.
- `total` — integer<int64>. Общее количество запросов.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
