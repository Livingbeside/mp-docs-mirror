---
title: Получить информацию о сравнении категорий
api: ozon-seller
method: POST
path: /v1/analytics/category/comparison
operation_id: AnalyticsCategoryComparison
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c4bca2abdb86cf3c
---

# Получить информацию о сравнении категорий

`POST /v1/analytics/category/comparison`

Соответствует разделу [**Аналитика → Категории**](https://seller.ozon.ru/app/analytics/what-to-sell/categories-comparison) в личном кабинете.

Метод доступен продавцам с подпиской [Premium Pro](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-premium-pro).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2347-Novyi-metod-dlia-polucheniia-otcheta-Sravnenie-kategorii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр.
  - `brand_ids` — array[string<int64>]. Список идентификаторов бренда. Вернётся информация только по обороту указанных брендов.
  - `category` — object. Список категорий.
    - `category_id` — integer<int32> **обязательный**. Идентификатор категории.
    - `category_type` — string (CATEGORY_3, CATEGORY_2, CATEGORY_1) **обязательный**. - `CATEGORY_3` — категория 3-го уровня. - `CATEGORY_2` — категория 2-го уровня. В ответе вернётся информация по подкатегориям внутри категории. - `CATEGORY_1` — категория 1-го уровня. По умолчанию: `CATEGORY_3`.
    - `is_own` — boolean. `true`, чтобы получить только категории, по которым были продажи.
  - `clothing_for` — array[string (MALE, FEMALE, BOYS, GIRLS)]. Пол: - `MALE` — мужской; - `FEMALE` — женский; - `BOYS` — мальчики, детская одежда; - `GIRLS` — девочки, детская одежда. Указывайте параметр для категорий «Обувь», «Одежда», «Галантерея и аксессуары» и «Ювелирные изделия».
  - `price_segment` — object. Диапазон цены.
    - `from` — integer<int32>. Начало диапазона.
    - `to` — integer<int32>. Конец диапазона.
  - `seller_ids` — array[string<int64>]. Список идентификаторов продавца. Вернётся информация только по обороту указанных продавцов.
- `group` — string (CATEGORY_3, SOURCE, SELLER, BRAND, CLUSTER, PRICE_BOUNDARY). Группировка данных в ответе: - `CATEGORY_3` — по категории 3-го уровня; - `SOURCE` — по источнику продаж; - `SELLER` — по продавцу; - `BRAND` — по бренду; - `CLUSTER` — по кластеру отгрузки; - `PRICE_BOUNDARY` — по ценовому сегменту. По умолчанию: `CATEGORY_3`.
- `limit` — integer<uint64>. Количество значений в ответе.
- `metric` — string (GMV, GMV_GROWTH, ITEMS, AIV, AIV_GROWTH, SELLERS, BRANDS, CLUSTERS, CATEGORY_SHARE, LEADER_SHARE, BUYOUT). Фильтр по метрикам: - `GMV` — объём продаж в денежном выражении; - `GMV_GROWTH` — объём продаж в процентах по сравнению с предыдущим периодом; - `ITEMS` — количество проданных товаров; - `AIV` — средняя стоимость одного проданного товара; - `AIV_GROWTH` — рост средней стоимости товара в процентах; - `SELLERS` — количество уникальных продавцов в категории или сегменте; - `BRANDS` — количество уникальных брендов в категории или сегменте; - `CLUSTERS` — кластры, регионы или города с похожими характеристиками продаж; - `CATEGORY_SHARE` — доля категории в общем объёме продаж; - `LEADER_SHARE` — доля лидера по продажам; - `BUYOUT` — процент выкупа товаров. По умолчанию: `GMV`.
- `offset` — integer<uint64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.
- `period` — string (WEEK, MONTH, QUARTER, YEAR) **обязательный**. Период: - `WEEK` — неделя, - `MONTH` — месяц, - `QUARTER` — квартал, - `YEAR` — год.
- `sort` — string (ASC, DESC) **обязательный**. Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.

## Ответы

**200** — Информация о сравнении категорий

- `has_next` — boolean. `true`, если в ответе вернулись не все значения.
- `items` — array[object]. Массив данных.
  - `id` — string. Идентификатор продавца, бренда или категории.
  - `label` — string. Название продавца, бренда или категории.
  - `max_rating` — integer<uint64>. Максимальный рейтинг.
  - `metric_aiv` — number<double>. Средняя цена.
  - `metric_aiv_growth` — number<double>. Динамика средней цены.
  - `metric_brands` — integer<uint64>. Количество брендов.
  - `metric_buyout` — number<double>. Доля выкупа.
  - `metric_category_share` — number<double>. Доля в категории.
  - `metric_clusters` — integer<uint64>. Количество кластеров доставки.
  - `metric_gmv` — number<double>. Сумма заказов.
  - `metric_gmv_growth` — number<double>. Динамика суммы заказов.
  - `metric_items` — integer<uint64>. Количество заказанных товаров.
  - `metric_leader_share` — number<double>. Доля топ-5 продавцов.
  - `metric_sellers` — integer<uint64>. Количество продавцов.
  - `rating` — integer<uint64>. Позиция продавца в рейтинге.

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
