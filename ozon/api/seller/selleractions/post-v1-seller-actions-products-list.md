---
title: Получить список участвующих в акции товаров
api: ozon-seller
method: POST
path: /v1/seller-actions/products/list
operation_id: SellerActionsProductsList
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c93646bd1ee50aba
---

# Получить список участвующих в акции товаров

`POST /v1/seller-actions/products/list`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64> **обязательный**. Идентификатор акции. Получите значение параметра методом [/v1/seller-actions/list](#operation/SellerActionsList).
- `cursor` — integer<uint64>. Указатель для выборки следующих данных.
- `limit` — integer<int64> **обязательный**. Максимальное количество элементов в ответе. По умолчанию: `100`.

## Ответы

**200** — Список товаров

- `cursor` — integer<uint64>. Указатель для выборки следующих данных.
- `has_next` — boolean. Признак, что в ответе вернулась только часть значений: - `true` — сделайте повторный запрос с новым параметром `cursor` для получения остальных значений; - `false` — ответ содержит все значения.
- `products` — array[object]. Информация о товарах.
  - `action_price` — number<double>. Цена товара с учётом акции.
  - `base_price` — number<double>. Базовая цена, по которой товар продаётся на Ozon, если не участвует в акции.
  - `currency` — string. Валюта.
  - `discount_percent` — number<double>. Процент скидки.
  - `is_active` — boolean. `true`, если товар участвует в акции.
  - `min_seller_price` — number<double>. Минимальная цена для автоматического добавления товара в акцию.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `price` — number<double>. Цена товара для покупателя.
  - `product_id` — integer<uint64>. Идентификатор товара в системе Ozon — `product_id`.
  - `quant_size` — integer<uint64>. Размер кванта.
  - `quant_type` — string (UNSPECIFIED, BOX, PALLET, GENERAL). Тип кванта: - `UNSPECIFIED` — не определён, - `BOX` — коробка, - `PALLET` — палета, - `GENERAL` — товар. По умолчанию: `UNSPECIFIED`.
  - `sku` — array[string<uint64>]. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
