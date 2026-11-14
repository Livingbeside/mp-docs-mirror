---
title: Проверить доступность доставки для покупателя
api: ozon-seller
method: POST
path: /v1/delivery/check
operation_id: DeliveryCheck
tags:
  - DeliveryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: b827170edcab70dd
---

# Проверить доступность доставки для покупателя

`POST /v1/delivery/check`

> ⚠️ Метод помечен как **deprecated**.

Метод устаревает и будет отключён.

Проверяет доступность доставки Ozon для покупателя. Не учитывает ограничения по сумме покупки, категории товаров и географии.

## Запрос

**Тело запроса** (`application/json`):

- `client_phone` — string **обязательный**. Номер телефона покупателя.

## Ответы

**200** — Успешно

- `is_possible` — boolean. `true`, если доставка доступна.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
