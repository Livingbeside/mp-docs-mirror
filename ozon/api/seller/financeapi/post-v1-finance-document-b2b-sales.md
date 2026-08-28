---
title: Реестр продаж юридическим лицам
api: ozon-seller
method: POST
path: /v1/finance/document-b2b-sales
operation_id: ReportAPI_CreateDocumentB2BSalesReport
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 295d005c90a2b0c2
---

# Реестр продаж юридическим лицам

`POST /v1/finance/document-b2b-sales`

Используйте метод, чтобы получить отчёт по продажам юридическим лицам. Соответствует разделу **Финансы → Документы → Реестр продаж юр. лицам** в личном кабинете.

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
