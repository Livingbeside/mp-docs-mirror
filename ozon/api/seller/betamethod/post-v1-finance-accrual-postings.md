---
title: Получить начисления по отправлениям
api: ozon-seller
method: POST
path: /v1/finance/accrual/postings
operation_id: GetFinanceAccrualPostings
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2aeeec66e57a6a59
---

# Получить начисления по отправлениям

`POST /v1/finance/accrual/postings`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2008-Novye-beta-metody-dlia-polucheniia-nachislenii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_numbers` — array[string] **обязательный**. Номера отправлений.

## Ответы

**200** — Начисления по отправлениям

- `posting_accruals` — array[object]. Список начислений по отправлениям.
  - `accruals` — array[object]. Список начислений.
    - `accrual_date` — string. Дата начисления.
    - `accrued` — object. Начислено за услугу.
      - `amount` — string. Сумма. Значение может быть отрицательным.
      - `currency` — string. Валюта.
    - `quantity` — integer<int32>. Количество товара.
    - `seller_price` — object. Цена за единицу.
      - `amount` — string. Сумма. Значение может быть отрицательным, если начисляется комиссия за продажу.
      - `currency` — string. Валюта.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `type_id` — integer<int32>. Идентификатор типа начисления. Можно получить методом [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes).
  - `posting_number` — string. Номер отправления.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
