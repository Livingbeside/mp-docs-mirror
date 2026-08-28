---
title: Получить историю изменений автоутилизации
api: ozon-seller
method: POST
path: /v1/returns/settings/utilization/history
operation_id: UtilizationHistory
tags:
  - ReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b68fb1488d28e3e8
---

# Получить историю изменений автоутилизации

`POST /v1/returns/settings/utilization/history`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — История изменений

- `history` — array[object]. История изменений.
  - `descriptions` — array[string]. Описание события.
  - `updated_at` — string<date-time>. Дата обновления.
  - `user_name` — string. Имя пользователя.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
