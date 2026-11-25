---
title: Удалить товары из сбора отзывов
api: ozon-seller
method: POST
path: /v1/review/first-reviews-collection/product/delete
operation_id: ReviewFirstReviewsCollectionProductDelete
tags:
  - ReviewAPIBeta
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f5149aa1e97e4dea
---

# Удалить товары из сбора отзывов

`POST /v1/review/first-reviews-collection/product/delete`

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

**200** — Товары удалены

- `sku_validation_error` — object. Информация о товарах, которые не прошли проверку.
  - `skus` — array[string<int64>]. Идентификаторы товаров в системе Ozon — SKU.
- `status` — string (SUCCESS, FAILED). Статус удаления товаров: - `SUCCESS` — товары удалены; - `FAILED` — ошибка.

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
