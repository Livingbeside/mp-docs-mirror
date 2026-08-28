---
title: Отчёт о взаиморасчётах
api: ozon-seller
method: POST
path: /v1/finance/mutual-settlement
operation_id: ReportAPI_CreateMutualSettlementReport
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: cc0541117a0cf1a6
---

# Отчёт о взаиморасчётах

`POST /v1/finance/mutual-settlement`

Используйте метод, чтобы получить отчёт о взаиморасчетах. Соответствует разделу **Финансы → Документы → Аналитические отчеты → Отчет о взаиморасчетах** в личном кабинете.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date` — string **обязательный**. Отчётный период в формате `YYYY-MM`.
- `language` — string. Язык ответа: - `RU` — русский, - `EN` — английский. По умолчанию: `DEFAULT`.

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
