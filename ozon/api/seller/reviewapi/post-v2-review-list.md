---
title: Получить список отзывов
api: ozon-seller
method: POST
path: /v2/review/list
operation_id: ReviewListV2
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e448d1fc45a94d6b
---

# Получить список отзывов

`POST /v2/review/list`

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filters` — object. Фильтры для поиска отзывов.
  - `order_status` — string (ALL, DELIVERED, CANCELLED). Статус заказа, на который покупатель оставил отзыв: - `ALL` — все; - `DELIVERED` — доставлен; - `CANCELLED` — отменён.
  - `published_from` — string<date-time>. Начало периода. Вернутся отзывы, которые созданы после этой даты.
  - `published_to` — string<date-time>. Конец периода. Вернутся отзывы, которые созданы до этой даты.
  - `skus` — array[string<int64>]. Идентификатор товара в системе Ozon — SKU.
  - `status` — string (ALL, NEW, VIEWED, PROCESSED). Статус отзыва: - `ALL` — все; - `NEW` — новый; - `VIEWED` — просмотренный; - `PROCESSED` — обработанный.
- `last_id` — string. Идентификатор последнего отзыва в ответе.
- `limit` — integer<int32> **обязательный**. Количество отзывов в ответе.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию.

## Ответы

**200** — Список отзывов

- `has_next` — boolean. `true`, если в ответе вернули не все отзывы.
- `last_id` — string. Идентификатор последнего отзыва на странице.
- `reviews` — array[object]. Список отзывов.
  - `comments_amount` — integer<int32>. Количество комментариев у отзыва.
  - `id` — string. Идентификатор отзыва.
  - `is_rating_participant` — boolean. `true`, если отзыв участвует в подсчёте рейтинга.
  - `order_status` — string (DELIVERED, CANCELLED). Статус заказа, на который покупатель оставил отзыв: - `DELIVERED` — доставлен; - `CANCELLED` — отменён.
  - `photos_amount` — integer<int32>. Количество изображений у отзыва.
  - `published_at` — string<date-time>. Дата публикации отзыва.
  - `rating` — integer<int32>. Оценка отзыва.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string (NEW, VIEWED, PROCESSED). Статус отзыва: - `NEW` — новый; - `VIEWED` — просмотренный; - `PROCESSED` — обработанный.
  - `text` — string. Текст отзыва.
  - `videos_amount` — integer<int32>. Количество видео у отзыва.

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
