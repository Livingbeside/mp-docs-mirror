---
title: Получить список drop-off пунктов в провинции
api: ozon-seller
method: POST
path: /v1/fbp/draft/drop-off/point/list
operation_id: FbpDraftDropOffPointList
tags:
  - DraftDropOffFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a985b60c87d80690
---

# Получить список drop-off пунктов в провинции

`POST /v1/fbp/draft/drop-off/point/list`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `next_page_number` — integer<int32>. Следующий номер страницы.
- `page_size` — integer<int32> **обязательный**. Количество элементов на странице.
- `province_uuid` — string **обязательный**. Уникальный идентификатор провинции.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Список drop-off пунктов

- `drop_off_points` — array[object]. Список drop-off пунктов.
  - `city` — string. Город.
  - `drop_off_point_id` — integer<int64>. Идентификатор drop-off пункта.
  - `nearest_drop_off_date` — string<date-time>. Ближайшая дата отгрузки.
  - `point_address` — string. Адрес drop-off пункта.
  - `province_uuid` — string. Уникальный идентификатор провинции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
