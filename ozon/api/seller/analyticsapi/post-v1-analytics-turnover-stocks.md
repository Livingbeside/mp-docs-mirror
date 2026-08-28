---
title: Оборачиваемость товара
api: ozon-seller
method: POST
path: /v1/analytics/turnover/stocks
operation_id: AnalyticsAPI_StocksTurnover
tags:
  - AnalyticsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5525927d853876aa
---

# Оборачиваемость товара

`POST /v1/analytics/turnover/stocks`

Используйте метод, чтобы узнать оборачиваемость товара и количество дней, на которое хватит текущего остатка. 
Метод соответствует разделу [**FBO -> Управление остатками**](https://seller.ozon.ru/app/supply/stocks-management) в личном кабинете.
Вы можете делать не больше 1 запроса в минуту по одному кабинету `Client-Id`.
 
Если вы запрашиваете список товаров по `sku`, параметры `limit` и `offset` необязательны.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer<int32>. Количество значений в ответе.
- `offset` — integer<int32>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, ответ начнётся с 11-го найденного элемента.
- `sku` — array[string<int64>]. Идентификаторы товаров в системе Ozon — SKU.

## Ответы

**200** — Информация об оборачиваемости

- `items` — array[object]. Товары.
  - `ads` — number<double>. Среднесуточное количество проданных единиц товара за последние 60 дней.
  - `current_stock` — integer<int64>. Остаток товара, шт.
  - `idc` — number<double>. На сколько дней хватит остатка товара с учётом среднесуточных продаж.
  - `idc_grade` — string (GRADES_NONE, GRADES_NOSALES, GRADES_GREEN, GRADES_YELLOW, GRADES_RED, GRADES_CRITICAL). Уровень остатка товара: - `GRADES_NONE` — ожидаются поставки; - `GRADES_NOSALES` — нет продаж; - `GRADES_GREEN` — зелёный, «хороший»; - `GRADES_YELLOW` — жёлтый, «средний»; - `GRADES_RED` — красный, «плохой»; - `GRADES_CRITICAL` — критический. По умолчанию: `GRADES_NONE`.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `turnover` — number<double>. Фактическая оборачиваемость в днях.
  - `turnover_grade` — string (GRADES_NONE, GRADES_NOSALES, GRADES_GREEN, GRADES_YELLOW, GRADES_RED, GRADES_CRITICAL). Уровень оборачиваемости: - `GRADES_NONE` — ожидаются поставки; - `GRADES_NOSALES` — нет продаж; - `GRADES_GREEN` — зелёный, «хороший»; - `GRADES_YELLOW` — жёлтый, «средний»; - `GRADES_RED` — красный, «плохой»; - `GRADES_CRITICAL` — критический. По умолчанию: `GRADES_NONE`.

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
