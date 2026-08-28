---
title: Обновить акцию с механикой «Скидка от суммы заказа»
api: ozon-seller
method: POST
path: /v1/seller-actions/update/discount-with-condition
operation_id: SellerActionsUpdateDiscountWithCondition
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 0f7ccfaf95e2d055
---

# Обновить акцию с механикой «Скидка от суммы заказа»

`POST /v1/seller-actions/update/discount-with-condition`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64>. Идентификатор акции. Получите значение параметра методом [/v1/seller-actions/list](#operation/SellerActionsList).
- `action_parameters` — object. Параметры акции.
  - `date_end` — string<date-time> **обязательный**. Дата и время окончания акции.
  - `date_start` — string<date-time> **обязательный**. Дата и время начала акции.
  - `discount_value` — number<double> **обязательный**. Размер скидки.
  - `min_order_amount` — number<double> **обязательный**. Минимальная сумма заказа для получения скидки.
  - `title` — string **обязательный**. Название акции.

## Ответы

**200** — Акция обновлена

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
