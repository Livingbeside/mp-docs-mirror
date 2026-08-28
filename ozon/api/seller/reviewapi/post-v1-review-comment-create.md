---
title: Оставить комментарий на отзыв
api: ozon-seller
method: POST
path: /v1/review/comment/create
operation_id: ReviewAPI_CommentCreate
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9bcdc578002f8ca9
---

# Оставить комментарий на отзыв

`POST /v1/review/comment/create`

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Запрос

**Тело запроса** (`application/json`):

- `mark_review_as_processed` — boolean. Обновление статуса у отзыва: - `true` — статус изменится на `Processed`. - `false` — статус не изменится.
- `parent_comment_id` — string. Идентификатор родительского комментария, на который вы отвечаете.
- `review_id` — string **обязательный**. Идентификатор отзыва.
- `text` — string **обязательный**. Текст комментария.

## Ответы

**200** — Комментарий создан

- `comment_id` — string. Идентификатор комментария.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
