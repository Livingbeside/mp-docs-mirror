---
title: Получить позаказный отчёт о реализации товаров
api: ozon-seller
method: POST
path: /v1/report/realization/posting/create
operation_id: CreateCompanyFinanceRealizationPostingReport
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: 2ceadc7c7417204a
---

# Получить позаказный отчёт о реализации товаров

`POST /v1/report/realization/posting/create`

> ⚠️ Метод помечен как **deprecated**.

17 января 2027 года отключим метод. Переключитесь на [/v1/report/finance/realization/list](#operation/ReportFinanceRealizationList) и [/v1/report/finance/realization/number/posting/create](#operation/CreateFinanceRealizationNumberPostingReport).

Отчёт о реализации доставленных и возвращённых товаров с детализацией по каждому заказу. Не включает отмены и невыкупы. Отчёт доступен с настоящего времени по август 2023 года включительно.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `month` — integer<int32> **обязательный**. Месяц.
- `year` — integer<int32> **обязательный**. Год.

## Ответы

**200** — Позаказный отчёт о реализации

- `code` — string. Уникальный идентификатор отчёта. Получите отчёт методом [/v1/report/info](#operation/ReportAPI_ReportInfo).

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
