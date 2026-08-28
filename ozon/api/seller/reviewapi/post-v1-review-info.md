---
title: Получить информацию об отзыве
api: ozon-seller
method: POST
path: /v1/review/info
operation_id: ReviewAPI_ReviewInfo
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: a040a422cc8405b4
---

# Получить информацию об отзыве

`POST /v1/review/info`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает. Переключитесь на /v2/review/info.

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Запрос

**Тело запроса** (`application/json`):

- `review_id` — string **обязательный**. Идентификатор отзыва.

## Ответы

**200** — Информация об отзыве

- `comments_amount` — integer<int32>. Количество комментариев к отзыву.
- `dislikes_amount` — integer<int32>. Количество дизлайков на отзыве.
- `id` — string. Идентификатор отзыва.
- `is_rating_participant` — boolean. `true`, если отзыв участвует в подсчёте рейтинга.
- `likes_amount` — integer<int32>. Количество лайков на отзыве.
- `order_status` — string. Статус заказа, на который покупатель оставил отзыв: - `DELIVERED` — доставлен, - `CANCELLED` — отменён.
- `photos` — array[object]. Информация об изображении.
  - `height` — integer<int32>. Высота.
  - `url` — string. Ссылка на изображение.
  - `width` — integer<int32>. Ширина.
- `photos_amount` — integer<int32>. Количество изображений у отзыва.
- `published_at` — string<date-time>. Дата публикации отзыва.
- `rating` — integer<int32>. Оценка отзыва.
- `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `status` — string. Статус отзыва: - `UNPROCESSED` — не обработан, - `PROCESSED` — обработан.
- `text` — string. Текст отзыва.
- `videos` — array[object]. Информация о видео.
  - `height` — integer<int64>. Высота.
  - `preview_url` — string. Ссылка на превью видео.
  - `short_video_preview_url` — string. Ссылка на короткое видео.
  - `url` — string. Ссылка на видео.
  - `width` — integer<int64>. Ширина.
- `videos_amount` — integer<int32>. Количество видео у отзыва.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
