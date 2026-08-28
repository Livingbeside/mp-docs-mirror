---
title: Получить информацию о запросах моих товаров
api: ozon-seller
method: POST
path: /v1/analytics/product-queries
operation_id: AnalyticsAPI_AnalyticsProductQueries
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4facc48a37b8fdcb
---

# Получить информацию о запросах моих товаров

`POST /v1/analytics/product-queries`

Используйте метод, чтобы получить данные о запросах ваших товаров. Полная аналитика доступна с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program), [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro). Без подписки вы можете посмотреть часть показателей. Метод аналогичен вкладке **Товары в поиске → Запросы моего товара** в личном кабинете.

Аналитику по запросам можно проверить за определённые даты. Для этого укажите интервал в полях `date_from` и `date_to`. Данные за последний месяц доступны в любом интервале, кроме текущей даты — расчёт происходит в течение 1–2 дней. Аналитика за даты раньше месяца назад доступна только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program), [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro) и только по неделям — в запросе укажите параметр `date_from`.

[Подробнее о работе с запросами товара в Базе знаний продавца](https://seller-edu.ozon.ru/analytics-and-metrics/graphs/analitika-po-zaprosu)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string<date-time> **обязательный**. Дата начала формирования аналитики.
- `date_to` — string<date-time>. Дата окончания формирования аналитики.
- `page` — integer<int32>. Индекс страницы, которую возвращает запрос.
- `page_size` — integer<int32> **обязательный**. Количество элементов на странице.
- `skus` — array[string<int64>] **обязательный**. Список SKU, идентификаторов товара в системе Ozon. По ним вернётся аналитика по запросам. Максимум — 1000 SKU.
- `sort_by` — string (BY_SEARCHES, BY_VIEWS, BY_POSITION, BY_CONVERSION, BY_GMV). Параметр, по которому товары будут отсортированы. Возможные значения: - `BY_SEARCHES` — по количеству запросов; - `BY_VIEWS` — по количеству просмотров; - `BY_POSITION` — по средней позиции товара; - `BY_CONVERSION` — по значению конверсии; - `BY_GMV` — по объёму продаж по запросам. По умолчанию: `BY_SEARCHES`.
- `sort_dir` — string (DESCENDING, ASCENDING). Направление сортировки: - `DESCENDING` — по убыванию; - `ASCENDING` — по возрастанию. По умолчанию: `DESCENDING`.

## Ответы

**200** — Информация о запросах моих товаров

- `analytics_period` — object. Период, за который формируется аналитика.
  - `date_from` — string. Дата начала формирования аналитики.
  - `date_to` — string. Дата окончания формирования аналитики.
- `items` — array[object]. Список товаров.
  - `category` — string. Название категории.
  - `currency` — string. Валюта.
  - `gmv` — number<float>. Продажи по запросам.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `position` — number<float>. Средняя позиция товара. Доступно только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus), иначе поле вернётся пустым.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `unique_search_users` — integer<int64>. Количество покупателей, которые искали ваш товар на Ozon.
  - `unique_view_users` — integer<int64>. Количество покупателей, которые увидели ваш товар на Ozon. Доступно только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus), иначе поле вернётся пустым.
  - `view_conversion` — number<float>. Конверсия из просмотра товара. Доступно только с подпиской [Premium](https://seller-edu.ozon.ru/seller-rating/about-rating/premium-program) или [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus), иначе поле вернётся пустым.
- `page_count` — integer<int64>. Количество страниц.
- `total` — integer<int64>. Общее количество запросов.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
