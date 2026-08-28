---
title: Отчёт о реализации товаров за день
api: ozon-seller
method: POST
path: /v1/finance/realization/by-day
operation_id: FinanceAPI_GetRealizationByDayReportV1
tags:
  - Premium
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: eca5f77c0c6d447b
---

# Отчёт о реализации товаров за день

`POST /v1/finance/realization/by-day`

Доступно для продавцов с подпиской [Premium Plus](https://seller-edu.ozon.ru/seller-rating/about-rating/subscription-premium-plus) или [Premium Pro](https://seller-edu.ozon.ru/seller-rating/about-rating/podpiska-premium-pro). 

Возвращает данные о суммах реализации из [отчёта о реализации товаров](#operation/FinanceAPI_GetRealizationReportV2) за день. Отмены и невыкупы не включаются. Данные доступны не более чем за 32 календарных дня от текущей даты.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `day` — integer<int32> **обязательный**. День.
- `month` — integer<int32> **обязательный**. Месяц.
- `year` — integer<int32> **обязательный**. Год.

## Ответы

**200** — Отчёт о реализации за день

- `rows` — array[object]. Таблица отчёта.
  - `commission_ratio` — number<double>. Доля комиссии за продажу по категории.
  - `delivery_commission` — object. Комиссия за доставку.
    - `amount` — number<double>. Сумма.
    - `bank_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: зелёные цены.
    - `bonus` — number<double>. Баллы за скидки.
    - `commission` — number<double>. Итоговая комиссия с учётом скидок и наценки. Для отчётов до 30 апреля 2024 года.
    - `compensation` — number<double>. Доплата за счёт Ozon. Для отчётов до 30 апреля 2024 года.
    - `pick_up_point_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: АПВЗ.
    - `price_per_instance` — number<double>. Цена за экземпляр.
    - `quantity` — integer<int32>. Количество товара.
    - `standard_fee` — number<double>. Базовое вознаграждение Ozon.
    - `stars` — number<double>. Выплаты по механикам лояльности партнёров: звёзды.
    - `total` — number<double>. Итого к начислению.
  - `item` — object. Информация о товаре.
    - `barcode` — string. Штрихкод товара.
    - `name` — string. Наименование товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `return_commission` — object. Комиссия за возврат товара.
    - `amount` — number<double>. Сумма.
    - `bank_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: зелёные цены.
    - `bonus` — number<double>. Баллы за скидки.
    - `commission` — number<double>. Итоговая комиссия с учётом скидок и наценки. Для отчётов до 30 апреля 2024 года.
    - `compensation` — number<double>. Доплата за счёт Ozon. Для отчётов до 30 апреля 2024 года.
    - `pick_up_point_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: АПВЗ.
    - `price_per_instance` — number<double>. Цена за экземпляр.
    - `quantity` — integer<int32>. Количество товара.
    - `standard_fee` — number<double>. Базовое вознаграждение Ozon.
    - `stars` — number<double>. Выплаты по механикам лояльности партнёров: звёзды.
    - `total` — number<double>. Итого к начислению.
  - `rowNumber` — integer<int32>. Номер строки в отчёте.
  - `seller_price_per_instance` — number<double>. Цена продавца с учётом скидки.

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
