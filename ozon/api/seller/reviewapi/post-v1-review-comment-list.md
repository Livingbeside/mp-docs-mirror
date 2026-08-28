---
title: Получить список комментариев на отзыв
api: ozon-seller
method: POST
path: /v1/review/comment/list
operation_id: ReviewAPI_CommentList
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: eb97f9029d5feb76
---

# Получить список комментариев на отзыв

`POST /v1/review/comment/list`

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro). Метод возвращает информацию по комментариям на отзывы, которые прошли модерацию.

## Запрос

**Тело запроса** (`application/json`):

- `filter` — ?

## Ответы

**200** — Информация о комментариях на отзыв

- `comments` — array[object]. Информация о комментарии.
  - `deviation_reason` — string. Причина отклонения на модерации.
  - `dislikes_amount` — integer<int32>. Количество дизлайков.
  - `id` — string. Идентификатор комментария.
  - `is_official` — boolean. `true`, если комментарий оставило официальное лицо, `false` — покупатель.
  - `is_owner` — boolean. `true`, если комментарий оставил продавец, `false` — покупатель.
  - `is_published` — boolean. `true`, если комментарий опубликован.
  - `is_rejected` — boolean. `true`, если комментарий отклонён.
  - `likes_amount` — integer<int32>. Количество лайков.
  - `parent_comment_id` — string. Идентификатор родительского комментария, на который нужно ответить.
  - `published_at` — string<date-time>. Дата публикации комментария.
  - `text` — string. Текст комментария.
- `offset` — integer<int32>. Количество элементов в выдаче.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
