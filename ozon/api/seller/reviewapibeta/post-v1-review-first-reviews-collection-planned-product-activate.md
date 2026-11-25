---
title: Запустить запланированный сбор отзывов
api: ozon-seller
method: POST
path: /v1/review/first-reviews-collection/planned-product/activate
operation_id: ReviewFirstReviewsCollectionPlannedProductActivate
tags:
  - ReviewAPIBeta
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 03cf206e632dfb69
---

# Запустить запланированный сбор отзывов

`POST /v1/review/first-reviews-collection/planned-product/activate`

Вы можете оставить обратную связь по этому методу в [комментариях](https://dev.ozon.ru/community/2405-Novaia-gruppa-metodov-po-rabote-s-kampaniei-Sbor-pervykh-otzyvov/) к обсуждению в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>] **обязательный**. Идентификаторы товаров в системе Ozon — SKU.

## Ответы

**200** — Сбор отзывов запущен

- `sku_validation_error` — object. Информация о товарах, которые не прошли проверку.
  - `skus` — array[string<int64>]. Идентификаторы товаров в системе Ozon — SKU.
- `status` — string (SUCCESS, FAILED). Статус запуска сбора отзывов: - `SUCCESS` — сбор отзывов запущен; - `FAILED` — ошибка.

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
