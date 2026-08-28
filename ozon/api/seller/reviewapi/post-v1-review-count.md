---
title: Количество отзывов по статусам
api: ozon-seller
method: POST
path: /v1/review/count
operation_id: ReviewAPI_ReviewCount
tags:
  - ReviewAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: a6ab6714f0467f53
---

# Количество отзывов по статусам

`POST /v1/review/count`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает. Переключитесь на /v2/review/count.

Доступно для продавцов с подпиской [Управление отзывами](https://seller-edu.ozon.ru/libra/seller-rating/podpiska-upravlenie-otzyvami) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro).

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Количество обработанных и необработанных отзывов

- `processed` — integer<int32>. Количество обработанных отзывов.
- `total` — integer<int32>. Количество всех отзывов.
- `unprocessed` — integer<int32>. Количество необработанных отзывов.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
