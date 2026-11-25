---
title: Получить список номеров отчётов о реализации товаров
api: ozon-seller
method: POST
path: /v1/report/finance/realization/list
operation_id: ReportFinanceRealizationList
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 8ffc319cd1f13e7b
---

# Получить список номеров отчётов о реализации товаров

`POST /v1/report/finance/realization/list`

Отчёты доступны с настоящего времени по сентябрь 2023 года включительно.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2481-Novye-metody-dlia-polucheniia-otcheta-o-realizatsii-i-pozakaznnogo-otchet-o-realizatsii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `from` — string **обязательный**. Дата начала отчётного периода.
- `to` — string **обязательный**. Дата окончания отчётного периода. Максимальный период — 31 день.

## Ответы

**200** — Список номеров отчётов

- `reports` — array[object]. Список отчётов.
  - `from` — string. Начало отчётного периода.
  - `number` — string. Номер отчёта. Получите идентификатор: - отчёта о реализации товаров — методом [/v1/report/finance/realization/number/create](#operation/CreateFinanceRealizationNumberReport); - позаказного отчёта о реализации товаров — методом [/v1/report/finance/realization/number/posting/create](#operation/CreateFinanceRealizationNumberPostingReport).
  - `to` — string. Конец отчётного периода.

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
