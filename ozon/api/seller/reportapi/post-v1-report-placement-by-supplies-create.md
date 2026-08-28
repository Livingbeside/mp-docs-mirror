---
title: Получить отчёт о стоимости размещения по поставкам
api: ozon-seller
method: POST
path: /v1/report/placement/by-supplies/create
operation_id: CreatePlacementBySuppliesReport
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 772f8d67d6e73814
---

# Получить отчёт о стоимости размещения по поставкам

`POST /v1/report/placement/by-supplies/create`

Соответствует разделу **FBO → Стоимость размещения** в личном кабинете.

Отчёт можно получить не больше 5 раз в день.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string **обязательный**. Дата начала отчётного периода в формате `YYYY-MM-DD`.
- `date_to` — string **обязательный**. Дата окончания отчётного периода в формате `YYYY-MM-DD`. Максимальный период — 31 день.

## Ответы

**200** — Отчёт о стоимости размещения

- `code` — string. Уникальный идентификатор отчёта. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
