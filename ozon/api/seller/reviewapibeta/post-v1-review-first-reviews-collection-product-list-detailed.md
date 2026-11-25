---
title: Получить информацию о товарах в сборе отзывов
api: ozon-seller
method: POST
path: /v1/review/first-reviews-collection/product/list-detailed
operation_id: ReviewFirstReviewsCollectionProductListDetailed
tags:
  - ReviewAPIBeta
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5473722bf8455eee
---

# Получить информацию о товарах в сборе отзывов

`POST /v1/review/first-reviews-collection/product/list-detailed`

Вы можете оставить обратную связь по этому методу в [комментариях](https://dev.ozon.ru/community/2405-Novaia-gruppa-metodov-po-rabote-s-kampaniei-Sbor-pervykh-otzyvov/) к обсуждению в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `last_id` — integer<int64>. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса.
- `limit` — integer<int32>. Количество значений на странице. По умолчанию: `100`.
- `status` — string (ALL, ACTIVE, STOPPED, COLLECTED, PLANNED). Статус сбора отзывов: - `ALL` — все статусы; - `ACTIVE` — активен; - `STOPPED` — остановлен; - `COLLECTED` — завершён; - `PLANNED` — запланирован. По умолчанию: `ALL`.

## Ответы

**200** — Информация о товарах

- `has_next` — boolean. `true`, если в ответе вернули не все товары.
- `items` — array[object]. Информация о товарах.
  - `actions` — array[string (UPDATE_TARGET, DELETE_ITEM, CONTINUE_COLLECTING, REPEAT_COLLECTING, STOP_COLLECTING)]. Доступные действия с товаром: - `UPDATE_TARGET` — изменить цель по отзывам; - `DELETE_ITEM` — удалить товар из сбора отзывов; - `CONTINUE_COLLECTING` — продолжить сбор отзывов; - `REPEAT_COLLECTING` — повторить сбор отзывов; - `STOP_COLLECTING` — остановить сбор отзывов.
  - `activated_count` — integer<int64>. Количество собранных отзывов.
  - `activation_at` — string<date-time>. Дата и время активации товара.
  - `is_available` — boolean. `true`, если товар доступен.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string (ACTIVE, COLLECTED, STOPPED, PLANNED). Статус сбора отзывов: - `ACTIVE` — активен; - `COLLECTED` — завершён; - `STOPPED` — остановлен; - `PLANNED` — запланирован.
  - `target` — integer<int64>. Цель по отзывам для товара.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.

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
