---
title: Получить список товаров, которые участвуют в сборе отзывов
api: ozon-seller
method: POST
path: /v1/review/first-reviews-collection/product/list
operation_id: ReviewFirstReviewsCollectionProductList
tags:
  - ReviewAPIBeta
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 91039c4b3b9a6ab5
---

# Получить список товаров, которые участвуют в сборе отзывов

`POST /v1/review/first-reviews-collection/product/list`

Вы можете оставить обратную связь по этому методу в [комментариях](https://dev.ozon.ru/community/2405-Novaia-gruppa-metodov-po-rabote-s-kampaniei-Sbor-pervykh-otzyvov/) к обсуждению в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<int32>. Количество товаров в ответе. По умолчанию: `100`.
- `offset` — integer<int32>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.

## Ответы

**200** — Список товаров

- `has_excluded_categories` — boolean. `true`, если у продавца есть товары в исключённых категориях. Такие товары не возвращаются в ответе.
- `has_next` — boolean. `true`, если в ответе вернули не все товары.
- `is_only_excluded_categories` — boolean. `true`, если все товары продавца в исключённых категориях.
- `items` — array[object]. Информация о товарах.
  - `activation_at` — string<date-time>. Дата и время активации товара.
  - `in_promotion` — boolean. `true`, если товар участвует в сборе отзывов.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

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
