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
deprecated: false
content_sha: 4b79858cede4b2af
---

# Проверить доступность доставки для покупателя

`POST /v1/delivery/check`

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
