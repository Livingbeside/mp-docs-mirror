---
title: Получить начисления за день
api: ozon-seller
method: POST
path: /v1/finance/accrual/by-day
operation_id: GetFinanceAccrualByDay
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 085b52a7b1ee82e7
---

# Получить начисления за день

`POST /v1/finance/accrual/by-day`

Если укажете `last_id` в запросе, передайте значение `date` из предыдущего запроса, иначе вернётся ошибка `400 Bad Request`. Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2008-Novye-beta-metody-dlia-polucheniia-nachislenii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date` — string **обязательный**. Дата начислений. Самая ранняя — 1 января 2022 года. Если укажете `last_id`, передайте значение `date` из предыдущего запроса.
- `last_id` — string **обязательный**. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса. Срок жизни идентификатора — 15 минут.

## Ответы

**200** — Начисления за день

- `accruals` — array[object]. Список начислений по отправлению.
  - `accrued_category` — string (UNSPECIFIED, POSTING, ITEM, NON_ITEM, CONTAINER_FEES). Тип начисления: - `UNSPECIFIED` — не определён; - `POSTING` — начисление по отправлению; - `ITEM` — начисление по товару; - `NON_ITEM` — начисление по продавцу без привязки к товару; - `CONTAINER_FEES` — начисление по контейнеру. По умолчанию: `UNSPECIFIED`.
  - `container_fees` — object. Начисления по контейнеру.
    - `fees` — array[object]. Начисления.
      - `accrued` — object. Начислено за услугу.
        - `amount` — string. Сумма. Значение может быть отрицательным.
        - `currency` — string. Валюта.
      - `type_id` — integer<int32>. Идентификатор типа начисления. Получите значение параметра методом [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes).
  - `date` — string. Дата начислений.
  - `item_fees` — object. Начисления по товарам.
    - `fees` — array[object]. Начисления по товару.
      - `fees` — array[object]. Начисления.
        - `accrued` — object. Начислено за услугу.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `type_id` — integer<int32>. Идентификатор типа начисления. Получите значение параметра методом [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes).
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `non_item_fee` — object. Начисление по продавцу без привязки к товару.
    - `accrued` — object. Начислено за услугу.
      - `amount` — string. Сумма. Значение может быть отрицательным.
      - `currency` — string. Валюта.
    - `type_id` — integer<int32>. Идентификатор типа начисления. Можно получить методом [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes).
  - `posting` — object. Начисления по отправлению.
    - `delivery_schema` — string. Схема продаж.
    - `delivery_speed` — integer<int32>. Скорость доставки.
    - `products` — array[object]. Данные по товарам из отправления.
      - `commission` — object. Итоговая комиссия с учётом скидок и наценки.
        - `bonus` — object. Начислено баллов за скидки.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `coinvestment` — object. Начислено по программе партнёров.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `commission` — object. Итоговая комиссия с учётом скидок и наценки.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `commission_ratio` — string. Доля комиссии за продажу по категории.
        - `sale_amount` — object. Реализовано на сумму.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `sale_commission` — object. Комиссия по прайс-листу.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `sale_price` — object. Цена покупателя.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
        - `seller_price` — object. Цена за единицу.
          - `amount` — string. Сумма. Значение может быть отрицательным, если начисляется комиссия за продажу.
          - `currency` — string. Валюта.
      - `delivery` — object. Начисления по доставке.
        - `services` — array[object]. Начисления по услугам доставки.
          - `accrued` — object. Начислено за услугу.
            - `amount` — string. Сумма. Значение может быть отрицательным.
            - `currency` — string. Валюта.
          - `type_id` — integer<int32>. Идентификатор типа начисления. Получите значение параметра методом [/v1/finance/accrual/types](#operation/GetFinanceAccrualTypes).
        - `total_accrued` — object. Общая сумма начислений за услугу.
          - `amount` — string. Сумма. Значение может быть отрицательным.
          - `currency` — string. Валюта.
      - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `total_amount` — object. Общая сумма начислений.
    - `amount` — string. Сумма.
    - `currency` — string. Валюта.
  - `accrual_id` — integer<int64>. Идентификатор начисления.
  - `unit_number` — string. Идентификатор заказа или услуги. Например, номер отправления или номер рекламного договора.
- `last_id` — string. Идентификатор последнего значения на странице. Срок жизни идентификатора — 15 минут.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
