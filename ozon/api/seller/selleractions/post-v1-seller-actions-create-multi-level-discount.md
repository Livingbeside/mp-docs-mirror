---
title: Создать акцию с механикой «Многоуровневая скидка от суммы»
api: ozon-seller
method: POST
path: /v1/seller-actions/create/multi-level-discount
operation_id: SellerActionsCreateMultiLevelDiscount
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d6815ed289232986
---

# Создать акцию с механикой «Многоуровневая скидка от суммы»

`POST /v1/seller-actions/create/multi-level-discount`

Товары в акцию добавляются автоматически, использовать метод [/v1/seller-actions/products/add](#operation/SellerActionsProductsAdd) не нужно.
 
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
- `discount_levels` — array[object] **обязательный**. Уровни скидки.
  - `discount_value` — number<double> **обязательный**. Размер скидки.
  - `order_amount` — number<double> **обязательный**. Минимальная сумма заказа.
- `discount_type` — string (PERCENT, CURRENCY) **обязательный**. Тип скидки: - `PERCENT` — скидка в процентах; - `CURRENCY` — скидка в валюте.
- `is_legal_entities_segment` — boolean. `true`, если акция только для юридических лиц.
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
