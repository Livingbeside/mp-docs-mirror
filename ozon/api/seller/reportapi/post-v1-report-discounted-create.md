---
title: Отчёт об уценённых товарах
api: ozon-seller
method: POST
path: /v1/report/discounted/create
operation_id: ReportAPI_CreateDiscountedReport
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: bcaf7a26b1c6d95b
---

# Отчёт об уценённых товарах

`POST /v1/report/discounted/create`

Запускает генерацию отчёта по уценённым товарам на складе Ozon.
Ozon может сам уценить товар, например, при повреждении.

В результате запроса будет не сам отчёт, а его уникальный идентификатор. 
Чтобы получить отчёт, отправьте идентификатор в запросе метода [/v1/report/info](#operation/ReportAPI_ReportInfo).

С одного аккаунта продавца можно отправить 1 запрос в минуту.
Соответствует разделу **Аналитика → Отчёты → Продажи со склада Ozon → Товары, уценённые Ozon** в личном кабинете.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Результат запроса

- `code` — string. Уникальный идентификатор отчёта. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

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
