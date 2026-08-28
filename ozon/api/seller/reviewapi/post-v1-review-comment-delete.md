---
title: Удалить комментарий на отзыв
api: ozon-seller
method: POST
path: /v1/review/comment/delete
operation_id: ReviewAPI_CommentDelete
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: f602c5e023e00992
---

# Удалить комментарий на отзыв

`POST /v1/review/comment/delete`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает. Переключитесь на /v2/review/comment/delete.

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Запрос

**Тело запроса** (`application/json`):

- `comment_id` — string **обязательный**. Идентификатор комментария.

## Ответы

**200** — Комментарий удалён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
