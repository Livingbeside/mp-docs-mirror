---
title: Получить список популярных поисковых запросов
api: ozon-seller
method: POST
path: /v1/search-queries/top
operation_id: SearchQueriesAPI_SearchQueriesTop
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 730910d55fce2f1a
---

# Получить список популярных поисковых запросов

`POST /v1/search-queries/top`

Доступно для продавцов с подпиской [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — string<int64> **обязательный**. Количество значений на странице.
- `offset` — string<int64> **обязательный**. Количество элементов, которое будет пропущено в ответе.

## Ответы

**200** — Список популярных поисковых запросов

- `offset` — string<int64>. Количество поисковых запросов на странице.
- `search_queries` — array[object]. Информация о поисковых запросах.
  - `add_to_cart` — number<float>. Количество покупателей, которые добавили хотя бы 1 товар в корзину.
  - `avg_price` — number<float>. Средняя цена товаров в рублях.
  - `client_count` — number<float>. Количество покупателей, которые искали товар по этому запросу.
  - `conversion_to_cart` — number<float>. Процент покупателей, которые добавили хотя бы 1 товар в корзину.
  - `items_views` — number<float>. Количество просмотров по товарам.
  - `query` — string. Поисковый запрос.
  - `sellers_count` — number<float>. Среднее количество продавцов, чьи товары посмотрели покупатели по этому запросу.
- `total` — string<int64>. Общее количество поисковых запросов.

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
