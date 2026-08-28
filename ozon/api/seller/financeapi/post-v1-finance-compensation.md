---
title: Отчёт о компенсациях
api: ozon-seller
method: POST
path: /v1/finance/compensation
operation_id: ReportAPI_GetCompensationReport
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 19d934c88f9114e7
---

# Отчёт о компенсациях

`POST /v1/finance/compensation`

Метод для получения отчёта о компенсациях. Соответствует отчёту из раздела **Финансы → Документы → Компенсации и прочие начисления** в личном кабинете.

## Запрос

**Тело запроса** (`application/json`):

- `date` — string **обязательный**. Отчётный период в формате `YYYY-MM`.
- `language` — string. Язык отчёта: - `RU` — русский, - `EN` — английский. По умолчанию: `RU`.

## Ответы

**200** — Отчёт о компенсациях

- `result` — object. Результат запроса.
  - `code` — string. Уникальный идентификатор отчёта. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
