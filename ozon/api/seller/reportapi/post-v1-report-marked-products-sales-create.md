---
title: Сгенерировать отчёт по продажам товаров с маркировкой
api: ozon-seller
method: POST
path: /v1/report/marked-products-sales/create
operation_id: CreateCompanyMarkedProductsSalesReport
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b551540ec33bb74a
---

# Сгенерировать отчёт по продажам товаров с маркировкой

`POST /v1/report/marked-products-sales/create`

В одном отчёте вы можете получить не больше 50 000 кодов маркировки. Чтобы получить остальные данные, уменьшите период формирования отчёта.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date` — object. Период формирования отчёта.
  - `from` — string **обязательный**. Дата начала отчётного периода в формате `YYYY-MM-DD`.
  - `to` — string **обязательный**. Дата окончания отчётного периода в формате `YYYY-MM-DD`.

## Ответы

**200** — Результат запроса

- `result` — object. Результаты запроса.
  - `code` — string. Уникальный идентификатор отчёта. По нему вы можете получить отчёт в течение 3 дней после запроса. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
