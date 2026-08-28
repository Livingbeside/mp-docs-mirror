---
title: Причины отмены заказа
api: ozon-seller
method: POST
path: /v1/cancel-reason/list-by-order
operation_id: CancelReasonListByOrder
tags:
  - CancelReasonAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e4192101f8477160
---

# Причины отмены заказа

`POST /v1/cancel-reason/list-by-order`

Возвращает возможные причины отмены для заказа.

## Запрос

**Тело запроса** (`application/json`):

- `order_number` — string **обязательный**. Номер заказа.

## Ответы

**200** — Причины отмены заказа

- `reasons` — array[object]. Информация о причинах отмены.
  - `id` — integer<int64>. Идентификатор причины отмены: - `501` — «Ozon перенёс срок доставки»; - `502` — «Отменили часть товаров из заказа»; - `503` — «Не применилась скидка или промокод»; - `504` — «Хочу изменить заказ и оформить заново»; - `505` — «Слишком долго ждать»; - `506` — «Нашёл дешевле»; - `508` — «Не нашёл нужную причину»; - `710` — «Указал неверный адрес».
  - `name` — string. Причина отмены.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
