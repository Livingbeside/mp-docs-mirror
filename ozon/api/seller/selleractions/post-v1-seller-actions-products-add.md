---
title: Добавить товары в акцию
api: ozon-seller
method: POST
path: /v1/seller-actions/products/add
operation_id: SellerActionsProductsAdd
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: b71cdb65fe89b2ac
---

# Добавить товары в акцию

`POST /v1/seller-actions/products/add`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции. Получите значение параметра методом [/v1/seller-actions/list](#operation/SellerActionsList).
- `products` — array[object] **обязательный**. Информация о товарах.
  - `currency` — string (RUB, BYN, KZT, EUR, USD, CNY). Валюта: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань. По умолчанию: `RUB`.
  - `discount_percent` — number<float>. Размер скидки в процентах. Передайте параметр, если механика акции «Скидка».
  - `sku` — integer<uint64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Товары добавлены

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
