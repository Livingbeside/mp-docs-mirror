---
title: Получить индекс ошибок FBS и rFBS
api: ozon-seller
method: POST
path: /v1/rating/index/fbs/info
operation_id: RatingAPI_GetFBSRatingIndexInfoV1
tags:
  - SellerRating
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f083850e537fa395
---

# Получить индекс ошибок FBS и rFBS

`POST /v1/rating/index/fbs/info`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Индекс ошибок

- `currency_code` — string. Код валюты стоимости обработки ошибок.
- `defects` — array[object]. Индекс ошибок по дням.
  - `date` — string. Дата в формате `YYYY-MM-DD`.
  - `index_by_date` — number<double>. Значение индекса ошибок.
  - `processing_costs_sum_by_date` — number<double>. Расходы на обработку ошибок.
- `index` — number<double>. Значение индекса ошибок за период.
- `period_from` — string. Дата начала расчётного периода в формате `YYYY-MM-DD`.
- `period_to` — string. Дата окончания расчётного периода в формате `YYYY-MM-DD`.
- `processing_costs_sum` — number<double>. Расходы на обработку ошибок за период.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
