---
title: Получить информацию об акте
api: ozon-seller
method: POST
path: /v1/supply-order/act/summary/get
operation_id: SupplyOrderActSummaryGet
tags:
  - SupplyOrderAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e017507297f62800
---

# Получить информацию об акте

`POST /v1/supply-order/act/summary/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2294-Novye-beta-metody-dlia-raboty-s-aktami-FBO/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `order_id` — integer<int64> **обязательный**. Идентификатор заявки на поставку из метода [/v3/supply-order/list](#operation/SupplyOrderList).

## Ответы

**200** — Информация об акте

- `supplies_acts` — array[object]. Список актов.
  - `is_agreement_completed` — boolean. `true`, если все акты согласованы.
  - `supply_acts` — array[object]. Информация об актах.
    - `act_id` — integer<int64>. Идентификатор акта.
    - `act_number` — string. Номер акта.
    - `act_state` — string (UNSPECIFIED, AWAITING_APPROVAL_BY_SELLER, REJECT_BY_SELLER, AGREEMENT_WITH_SELLER, ACCEPTED). Статус акта: - `UNSPECIFIED` — не определён; - `AWAITING_APPROVAL_BY_SELLER` — ожидает согласования продавца; - `REJECT_BY_SELLER` — отклонён продавцом; - `AGREEMENT_WITH_SELLER` — согласован продавцом; - `ACCEPTED` — согласование завершено. По умолчанию: `UNSPECIFIED`.
    - `created_date` — string. Дата создания акта.
    - `deadline_utc` — string<date-time>. Дата и время, до которой можно работать с актом.
    - `summary` — object. Информация о товарах в акте.
      - `approved_amount` — object. Согласованная стоимость товаров.
        - `amount` — object. Сумма с НДС.
          - `amount` — string. Сумма.
          - `currency` — string. Валюта.
        - `amount_vat` — object. Сумма НДС.
          - `amount` — string. Сумма.
          - `currency` — string. Валюта.
        - `amount_without_vat` — object. Сумма без НДС.
          - `amount` — string. Сумма.
          - `currency` — string. Валюта.
      - `approved_quantity` — integer<int32>. Количество согласованных товаров.
      - `declared_quantity` — integer<int32>. Количество заявленных товаров.
      - `fact_amount` — object. Фактическая стоимость товаров.
        - `amount` — object. Сумма с НДС.
          - `amount` — string. Сумма.
          - `currency` — string. Валюта.
        - `amount_vat` — object. Сумма НДС.
          - `amount` — string. Сумма.
          - `currency` — string. Валюта.
        - `amount_without_vat` — object. Сумма без НДС.
          - `amount` — string. Сумма.
          - `currency` — string. Валюта.
      - `fact_quantity` — integer<int32>. Количество принятых товаров.
      - `sku_quantity` — integer<int32>. Общее количество товаров.
      - `unidentified_quantity` — integer<int32>. Количество неопознанных излишков.
    - `type` — string (UNSPECIFIED, ACCEPTANCE, DEFECT, SURPLUS, SHORTCOMING). Тип акта: - `UNSPECIFIED` — не определён; - `ACCEPTANCE` — акт приёмки; - `DEFECT` — акт о браке; - `SURPLUS` — акт об излишках; - `SHORTCOMING` — акт о недостаче. По умолчанию: `UNSPECIFIED`.
  - `supply_id` — integer<int64>. Идентификатор поставки.

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
