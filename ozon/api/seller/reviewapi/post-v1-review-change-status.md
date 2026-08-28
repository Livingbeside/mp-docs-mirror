---
title: Изменить статус отзывов
api: ozon-seller
method: POST
path: /v1/review/change-status
operation_id: ReviewAPI_ReviewChangeStatus
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: f0413a0dfc1493d2
---

# Изменить статус отзывов

`POST /v1/review/change-status`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает. Переключитесь на [/v2/review/change-status](#operation/ReviewChangeStatusV2).

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Запрос

**Тело запроса** (`application/json`):

- `review_ids` — array[string] **обязательный**. Массив с идентификаторами отзывов от 1 до 100.
- `status` — string **обязательный**. Статус отзыва: - `PROCESSED` — обработанный, - `UNPROCESSED` — необработанный.

## Ответы

**200** — Статус изменён

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
