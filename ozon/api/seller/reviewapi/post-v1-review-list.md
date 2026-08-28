---
title: Получить список отзывов
api: ozon-seller
method: POST
path: /v1/review/list
operation_id: ReviewAPI_ReviewList
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: cbe1db4f5ee86465
---

# Получить список отзывов

`POST /v1/review/list`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает. Переключитесь на [/v2/review/list](#operation/ReviewListV2).

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

Метод не возвращает параметры «Достоинства» и «Недостатки», если они есть в отзывах на товар. Эти параметры устарели, в новых отзывах их нет.

## Запрос

**Тело запроса** (`application/json`):

- `last_id` — string. Идентификатор последнего отзыва на странице.
- `limit` — integer<int32> **обязательный**. Количество отзывов в ответе. Минимум — 20, максимум — 100.
- `sort_dir` — string. Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.
- `status` — string. Статусы отзывов: - `ALL` — все, - `UNPROCESSED` — необработанные, - `PROCESSED` — обработанные.

## Ответы

**200** — Список отзывов

- `has_next` — boolean. `true`, если в ответе вернули не все отзывы.
- `last_id` — string. Идентификатор последнего отзыва на странице.
- `reviews` — array[object]. Информация об отзыве.
  - `comments_amount` — integer<int32>. Количество комментариев у отзыва.
  - `id` — string. Идентификатор отзыва.
  - `is_rating_participant` — boolean. `true`, если отзыв участвует в подсчёте рейтинга.
  - `order_status` — string. Статус заказа, на который покупатель оставил отзыв: - `DELIVERED` — доставлен, - `CANCELLED` — отменён.
  - `photos_amount` — integer<int32>. Количество изображений у отзыва.
  - `published_at` — string<date-time>. Дата публикации отзыва.
  - `rating` — integer<int32>. Оценка отзыва.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string. Статус отзыва: - `UNPROCESSED` — не обработан, - `PROCESSED` — обработан.
  - `text` — string. Текст отзыва.
  - `videos_amount` — integer<int32>. Количество видео у отзыва.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
