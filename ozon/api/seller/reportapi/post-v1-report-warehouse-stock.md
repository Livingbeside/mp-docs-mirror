---
title: Отчёт об остатках на FBS-складе
api: ozon-seller
method: POST
path: /v1/report/warehouse/stock
operation_id: ReportAPI_CreateStockByWarehouseReport
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 40e0fd5d8ac35432
---

# Отчёт об остатках на FBS-складе

`POST /v1/report/warehouse/stock`

Отчёт с информацией о количестве доступных и зарезервированных единиц товара на складе.
Соответствует разделу **FBS → Управление логистикой → Управление остатками → Скачать в XLS** в личном кабинете.

В результате запроса будет не сам отчёт, а его уникальный идентификатор. 
Чтобы получить отчёт, отправьте идентификатор в запросе метода [/v1/report/info](#operation/ReportAPI_ReportInfo).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `language` — string. Язык ответа: - `RU` — русский, - `EN` — английский. По умолчанию: `DEFAULT`.
- `warehouseId` — array[string<int64>] **обязательный**. Идентификаторы складов. Ограничение значений в запросе. Максимум — 50.

## Ответы

**200** — Результат запроса

- `result` — object. Результаты запроса.
  - `code` — string. Уникальный идентификатор отчёта. По нему вы можете получить отчёт в течение 3 дней после запроса. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

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
