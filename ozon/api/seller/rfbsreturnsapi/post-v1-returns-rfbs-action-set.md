---
title: Передать доступные действия для rFBS возвратов
api: ozon-seller
method: POST
path: /v1/returns/rfbs/action/set
operation_id: ReturnsAPI_ReturnsRfbsActionSet
tags:
  - RFBSReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2b8e5ef92ad1a4cb
---

# Передать доступные действия для rFBS возвратов

`POST /v1/returns/rfbs/action/set`

Метод для передачи действий для возврата rFBS.

## Запрос

**Тело запроса** (`application/json`):

- `comment` — string. Комментарий продавца. Обязателен для `id: -1` и `id: -10`.
- `compensation_amount` — number<double>. Сумма компенсации. Обязательна для `id: 1020`.
- `id` — integer<int32>. Идентификатор действия. Получите доступные действия `returns.available_actions` методом [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2).
- `rejection_reason_id` — integer<int32>. Идентификатор причины отмены. Обязателен для `id: -1` и `id: -10`. Получите возможные причины отмены `returns.rejection_reason` методом [/v2/returns/rfbs/get](#operation/RFBSReturnsAPI_ReturnsRfbsGetV2).
- `return_for_back_way` — number<double>. Сумма, возмещаемая покупателю за пересылку товара. Отрицательные значения приравниваются к `0`.
- `return_id` — integer<int64> **обязательный**. Идентификатор заявки на возврат.

## Ответы

**200** — Действие передано

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
