---
title: Данные аналитики
api: ozon-seller
method: POST
path: /v1/analytics/data
operation_id: AnalyticsAPI_AnalyticsGetData
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e9873f81dbd3bfc9
---

# Данные аналитики

`POST /v1/analytics/data`

Уĸажите период и метриĸи, ĸоторые нужно посчитать. В ответе будет аналитиĸа, сгруппированная по параметру `dimensions`. Для продавцов без подписки [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus): - доступны данные за последние 3 месяца, - есть ограничения по способам группировки данных и метрикам. Для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro) ограничений нет. Метод можно использовать не больше 1 раза в минуту. Соответствует разделу **Аналитика → Графики** в личном кабинете.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string **обязательный**. Дата, с которой будут данные в отчёте. Если у вас нет Premium-подписки, укажите дату в пределах последних трёх месяцев.
- `date_to` — string **обязательный**. Дата, по которую будут данные в отчёте.
- `dimension` — array[string (unknownDimension, sku, spu, day, week, month, year, category1, category2, brand, modelID, descriptionType)] **обязательный**. Группировка данных в отчёте. Способы группировки, доступные всем продавцам: - `unknownDimension` — неизвестное измерение; - `sku` — идентификатор товара; - `spu` — идентификатор товара — объединённая карточка; - `day` — день; - `week` — неделя; - `month` — месяц. Способы группировки, доступные только продавцам с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus): - `year` — год; - `category1` — категория первого уровня; - `category2` — категория второго уровня; - `brand` — бренд; - `modelID` — модель; - `descriptionType` — тип товара.
- `filters` — array[object]. Фильтры.
  - `key` — string. Параметр сортировки. Можно передать любой атрибут из параметров `dimension` и `metric`, кроме атрибута `brand`.
  - `op` — string. Операция сравнения: - `EQ` — равно, - `GT` — больше, - `GTE` — больше или равно, - `LT` — меньше, - `LTE` — меньше или равно. По умолчанию: `EQ`.
  - `value` — string. Значение для сравнения.
- `limit` — integer<int64> **обязательный**. Количество значений в ответе: - максимум — 1000, - минимум — 1.
- `metrics` — array[string] **обязательный**. Укажите до 14 метрик. Если их будет больше, вы получите ошибку с кодом `InvalidArgument`. Список метриĸ, по ĸоторым будет сформирован отчёт. Метрики, доступные всем продавцам: - `revenue` — заказано на сумму, - `ordered_units` — заказано товаров. Метрики, доступные только продавцам с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus): - `unknown_metric` — неизвестная метрика. - `hits_view_search` — показы в поиске и в категории. - `hits_view_pdp` — показы на карточке товара. - `hits_view` — всего показов. - `hits_tocart_search` — в корзину из поиска или категории. - `hits_tocart_pdp` — в корзину из карточки товара. - `hits_tocart` — всего добавлено в корзину. - `session_view_search` — сессии с показом в поиске или в каталоге. Считаются уникальные посетители с просмотром в поиске или каталоге. - `session_view_pdp` — сессии с показом на карточке товара. Считаются уникальные посетители, которые просмотрели карточку товара. - `session_view` — всего сессий. Считаются уникальные посетители. - `conv_tocart_search` — конверсия в корзину из поиска или категории. - `conv_tocart_pdp` — конверсия в корзину из карточки товара. - `conv_tocart` — общая конверсия в корзину. - `returns` — возвращено товаров. - `cancellations` — отменено товаров. - `delivered_units` — доставлено товаров. - `position_category` — позиция в поиске и категории.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.
- `sort` — array[object]. Настройки сортировки отчёта.
  - `key` — string. Метрика, по которой будет отсортирован результат запроса.
  - `order` — string. Вид сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию. По умолчанию: `ASC`.

## Ответы

**200** — Данные аналитики

- `result` — object. Результаты запроса.
  - `data` — array[object]. Массив данных.
    - `dimensions` — array[object]. Группировка данных в отчёте.
      - `id` — string. Идентификатор товара в системе Ozon — SKU.
      - `name` — string. Наименование.
    - `metrics` — array[number<double>]. Список значений метрики.
  - `totals` — array[number<double>]. Итоговые и средние значения метрик.
- `timestamp` — string. Время создания отчёта.

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
