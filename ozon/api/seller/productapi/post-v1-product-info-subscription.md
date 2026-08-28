---
title: Количество подписавшихся на товар пользователей
api: ozon-seller
method: POST
path: /v1/product/info/subscription
operation_id: ProductAPI_GetProductInfoSubscription
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: abd82aa2ba16b92f
---

# Количество подписавшихся на товар пользователей

`POST /v1/product/info/subscription`

Метод для получения количества пользователей, которые нажали **Узнать о поступлении** на странице товара. Вы можете передать несколько товаров в запросе.

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>] **обязательный**. Список SKU, идентификаторов товара в системе Ozon.

## Ответы

**200** — Количество подписавшихся пользователей

- `result` — array[object]. Результат работы метода.
  - `count` — integer<int64>. Количество подписавшихся пользователей.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon, SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
