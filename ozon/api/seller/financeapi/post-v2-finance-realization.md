---
title: Отчёт о реализации товаров (версия 2)
api: ozon-seller
method: POST
path: /v2/finance/realization
operation_id: FinanceAPI_GetRealizationReportV2
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: f6a89124cd158edb
---

# Отчёт о реализации товаров (версия 2)

`POST /v2/finance/realization`

Метод недоступен для продавцов, которые заключили договор с ТОО «ОЗОН Маркетплейс Казахстан». Метод позволяет получить отчёт за период не раньше августа 2023 года. Отчёты за более ранние периоды доступны в личном кабинете. Отчёт о реализации доставленных и возвращённых товаров за месяц. Отмены и невыкупы не включаются. Соответствует разделу **Финансы → Документы → Отчёты о реализации → Отчёт о реализации товара** в личном кабинете. Отчёт придёт не позднее 5-го числа следующего месяца. [Подробнее об отчёте в Базе знаний продавца](https://seller-edu.ozon.ru/docs/finances-documents/calculations-documents/otchet-o-realizacii-tovarov.html)

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

**200** — Отчёт о реализации

- `result` — object. Результат запроса.
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
