---
title: Реестр продаж юридическим лицам в JSON-формате
api: ozon-seller
method: POST
path: /v1/finance/document-b2b-sales/json
operation_id: ReportAPI_CreateDocumentB2BSalesJSONReport
tags:
  - FinanceAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 839d487f432a50bf
---

# Реестр продаж юридическим лицам в JSON-формате

`POST /v1/finance/document-b2b-sales/json`

Используйте метод, чтобы получить отчёт по продажам юридическим лицам в JSON-формате. Соответствует разделу **Финансы → Документы → Реестр продаж юр. лицам** в личном кабинете.

## Запрос

**Тело запроса** (`application/json`):

- `date` — string **обязательный**. Отчётный период в формате `YYYY-MM`. Отчёт доступен до января 2019 включительно.

## Ответы

**200** — Отчёт в JSON-формате

- `date_from` — string. Дата начала отчётного периода в формате `YYYY-MM-DD`.
- `date_to` — string. Дата окончания отчётного периода в формате `YYYY-MM-DD`.
- `invoices` — array[object]. Список счетов-фактур.
  - `buyer_info` — object. Информация о покупателе.
    - `name` — string. Название компании.
    - `address` — string. Юридический адрес.
    - `inn` — string. ИНН.
    - `kpp` — string. КПП.
  - `currency` — string. Валюта.
  - `currency_code` — integer<int32>. Код валюты.
  - `info` — object. Информация о счёте-фактуре.
    - `date` — string. Дата счёта-фактуры продавца в формате `YYYY-MM-DD`.
    - `number` — string. Номер счёта-фактуры продавца.
    - `status` — string. Статус УКД или УПД.
    - `type` — string (UPD, UKD). Тип документа: - `UPD` - УПД; - `UKD` - УКД.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `operations` — array[object]. Список операций.
    - `amount` — number<double>. Сумма реализации или возврата.
    - `cost_without_vat` — number<double>. Стоимость товара без НДС.
    - `date` — string. Дата операции в формате `YYYY-MM-DD`.
    - `gtd_number` — string. Номер ГТД.
    - `origin_country` — string. Страна происхождения товара.
    - `posting_number` — string. Номер отправления.
    - `price` — number<double>. Цена реализации или возврата в рублях.
    - `quantity` — integer<int32>. Количество товаров.
    - `rnpt_number` — string. РНПТ.
    - `type` — string (DELIVERY, RETURN). Тип операции: - `DELIVERY` — отправление, - `RETURN` — возврат.
    - `vat_amount` — number<double>. Сумма НДС, которая взимается с покупателя.
    - `vat_rate` — number<double>. Ставка НДС.
  - `product_name` — string. Название товара.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `unit_code` — integer<int32>. Код условного обозначения.
  - `unit_name` — string. Условное обозначение.
- `seller_info` — object. Информация о продавце.
  - `company_name` — string. Название компании.
  - `inn` — string. ИНН.
  - `kpp` — string. КПП.

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
