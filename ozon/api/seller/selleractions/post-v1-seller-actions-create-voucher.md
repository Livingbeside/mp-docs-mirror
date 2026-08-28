---
title: Создать акцию с механикой «Скидка по промокоду»
api: ozon-seller
method: POST
path: /v1/seller-actions/create/voucher
operation_id: SellerActionsCreateVoucher
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 814a6c994447f825
---

# Создать акцию с механикой «Скидка по промокоду»

`POST /v1/seller-actions/create/voucher`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `budget` — integer<int64> **обязательный**. Бюджет акции. Если бюджет закончится, акция остановится.
- `date_end` — string<date-time> **обязательный**. Дата и время окончания акции.
- `date_start` — string<date-time> **обязательный**. Дата и время начала акции.
- `discount_type` — string (PERCENT, CURRENCY) **обязательный**. Тип скидки: - `PERCENT` — скидка в процентах; - `CURRENCY` — скидка в валюте.
- `discount_value` — number<double> **обязательный**. Размер скидки.
- `title` — string **обязательный**. Название акции.
- `user_ids` — array[string<uint64>]. Идентификаторы пользователей, которым доступен промокод.
- `voucher_parameters` — object **обязательный**. Параметры промокодов.
  - `count_codes` — integer<uint64> **обязательный**. Количество промокодов.
  - `is_private` — boolean **обязательный**. `true`, если промокод в открытом доступе.
  - `type` — string (ONE, MULTIPLE, UNIQUE) **обязательный**. Тип промокода: - `ONE` — промокод для всех покупателей на 1 заказ; - `MULTIPLE` — промокод для всех покупателей на любое количество заказов; - `UNIQUE` — промокод для 1 покупателя на 1 заказ.

## Ответы

**200** — Акция создана

- `action_id` — integer<uint64>. Идентификатор акции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
