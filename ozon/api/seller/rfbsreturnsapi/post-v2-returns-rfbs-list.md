---
title: Список заявок на возврат
api: ozon-seller
method: POST
path: /v2/returns/rfbs/list
operation_id: RFBSReturnsAPI_ReturnsRfbsListV2
tags:
  - RFBSReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fdc27f7fe2526e22
---

# Список заявок на возврат

`POST /v2/returns/rfbs/list`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтр.
  - `created_at` — object. Период создания заявки.
    - `from` — string<date-time>. Дата начала периода.
    - `to` — string<date-time>. Дата окончания периода.
  - `group_state` — array[string]. Фильтр по статусам заявок: - `All` — все заявки. - `New` — новые. - `Delivering` — в пути. - `Checkout` — на проверке. - `Arbitration` — спорные. - `Approved` — согласованные. - `Rejected` — отклонённые.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `posting_number` — string. Номер отправления.
- `last_id` — integer<int32>. Идентификатор последнего значения на странице — `return_id`. Оставьте это поле пустым при выполнении первого запроса.
- `limit` — integer<int32> **обязательный**. Количество значений в ответе.

## Ответы

**200** — Список заявок на возврат

- `returns` — object. Данные о заявках.
  - `client_name` — string. Имя покупателя.
  - `created_at` — string<date-time>. Дата создания заявки.
  - `order_number` — string. Номер заказа.
  - `posting_number` — string. Номер отправления.
  - `product` — object. Данные о товаре.
    - `currency_code` — string. Валюта ваших цен. Cовпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — integer<int32>. Цена товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `return_id` — integer<int64>. Идентификатор заявки на возврат.
  - `return_number` — string. Номер заявки на возврат.
  - `state` — object. Статусы заявки и возврата денег.
    - `group_state` — string. Статус заявки по применённому фильтру.
    - `money_return_state_name` — string. Статус возврата денег.
    - `state` — string. Статус заявки.
    - `state_name` — string. Название статуса заявки на русском.

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
