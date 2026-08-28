---
title: Позаказный отчёт о реализации товаров
api: ozon-seller
method: POST
path: /v1/finance/realization/posting
operation_id: FinanceAPI_GetRealizationReportV1
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f9e5bfef885d7663
---

# Позаказный отчёт о реализации товаров

`POST /v1/finance/realization/posting`

Метод недоступен для продавцов, которые заключили договор с ТОО «ОЗОН Маркетплейс Казахстан». Отчёт о реализации доставленных и возвращённых товаров с детализацией по каждому заказу. Отмены и невыкупы не включаются. Отчёт доступен с настоящего времени по август 2023 года включительно.

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

- `header` — object. Титульный лист отчёта.
  - `contract_date` — string. Дата заключения договора.
  - `contract_number` — string. Номер договора.
  - `currency_sys_name` — string. Валюта.
  - `doc_date` — string. Дата формирования документа.
  - `number` — string. Номер отчёта о реализации.
  - `payer_inn` — string. ИНН плательщика.
  - `payer_kpp` — string. КПП плательщика.
  - `payer_name` — string. Название плательщика.
  - `receiver_inn` — string. ИНН получателя.
  - `receiver_kpp` — string. КПП получателя.
  - `receiver_name` — string. Название получателя.
  - `start_date` — string. Начало периода.
  - `stop_date` — string. Конец периода.
- `rows` — array[object]. Таблица отчёта.
  - `commission_ratio` — number<double>. Доля комиссии за продажу по категории.
  - `delivery_commission` — object. Комиссия за доставку.
    - `amount` — number<double>. Сумма.
    - `bonus` — number<double>. Баллы за скидки.
    - `commission` — number<double>. Итоговая комиссия с учётом скидок и наценки. Для отчётов до 30 апреля 2024 года.
    - `compensation` — number<double>. Доплата за счёт Ozon. Для отчётов до 30 апреля 2024 года.
    - `price_per_instance` — number<double>. Цена за экземпляр.
    - `quantity` — integer<int32>. Количество товара.
    - `standard_fee` — number<double>. Базовое вознаграждение Ozon.
    - `bank_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: зелёные цены.
    - `stars` — number<double>. Выплаты по механикам лояльности партнёров: звёзды.
    - `pick_up_point_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: АПВЗ.
    - `total` — number<double>. Итого к начислению.
  - `item` — object. Информация о товаре.
    - `barcode` — string. Штрихкод товара.
    - `name` — string. Наименование товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `return_commission` — object. Комиссия за возврат товара.
    - `amount` — number<double>. Сумма.
    - `bonus` — number<double>. Баллы за скидки.
    - `commission` — number<double>. Итоговая комиссия с учётом скидок и наценки. Для отчётов до 30 апреля 2024 года.
    - `compensation` — number<double>. Доплата за счёт Ozon. Для отчётов до 30 апреля 2024 года.
    - `price_per_instance` — number<double>. Цена за экземпляр.
    - `quantity` — integer<int32>. Количество товара.
    - `standard_fee` — number<double>. Базовое вознаграждение Ozon.
    - `bank_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: зелёные цены.
    - `stars` — number<double>. Выплаты по механикам лояльности партнёров: звёзды.
    - `pick_up_point_coinvestment` — number<double>. Выплаты по механикам лояльности партнёров: АПВЗ.
    - `total` — number<double>. Итого к начислению.
  - `row_number` — integer<int32>. Номер строки в отчёте.
  - `seller_price_per_instance` — number<double>. Цена продавца с учётом скидки.
  - `order` — object. Информация о заказе.
    - `posting_number` — string. Номер отправления.
    - `created_date` — string. Дата заказа в формате «ГГГГ-ММ-ДД».
  - `legal_entity_document` — object. Информация о продаже юридическому лицу.
    - `number` — string. Номер счёта-фактуры.
    - `sale_date` — string. Дата в формате «ГГГГ-ММ-ДД».

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки: - `The requested report is too large. Use /v1/report/realization/posting/create.` — отчёт нельзя получить методом [/v1/finance/realization/posting](#operation/FinanceAPI_GetRealizationReportV1). Используйте метод [/v1/report/realization/posting/create](#operation/CreateCompanyFinanceRealizationPostingReport). - `Request validation error: invalid GetRealizationReportPostingRequest.Month: value must be inside range [1, 12]` — некорректное значение месяца. - `Year, Month, and Day parameters describe an un-representable DateTime.` — некорректная дата. - `Request validation error: invalid GetRealizationReportPostingRequest.Year: value must be greater than or equal to 2023` — некорректный год. Отчёт доступен с настоящего времени по август 2023 года включительно.

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
