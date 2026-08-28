---
title: Создать акцию с механикой «Скидка от суммы заказа»
api: ozon-seller
method: POST
path: /v1/seller-actions/create/discount-with-condition
operation_id: SellerActionsCreateDiscountWithCondition
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e8e56f0305b6b255
---

# Создать акцию с механикой «Скидка от суммы заказа»

`POST /v1/seller-actions/create/discount-with-condition`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_end` — string<date-time> **обязательный**. Дата и время окончания акции.
- `date_start` — string<date-time> **обязательный**. Дата и время начала акции.
- `discount_type` — string (PERCENT, CURRENCY) **обязательный**. Тип скидки: - `PERCENT` — скидка в процентах; - `CURRENCY` — скидка в валюте.
- `discount_value` — number<float> **обязательный**. Размер скидки.
- `min_order_amount` — number<double> **обязательный**. Сумма заказа, с которой действует скидка.
- `title` — string. Название акции.

## Ответы

**200** — Акция создана

- `action_id` — integer<uint64>. Идентификатор акции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
