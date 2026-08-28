---
title: Получить зоны размещения товаров по SKU перед поставкой
api: ozon-seller
method: POST
path: /v1/product/placement-zone/info
operation_id: ProductAPI_GetProductPlacementZoneInfo
tags:
  - CategoryAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 897709a659dec84d
---

# Получить зоны размещения товаров по SKU перед поставкой

`POST /v1/product/placement-zone/info`

Вы можете отправить не больше 10 запросов в секунду. [Подробнее о зонах размещения в Базе знаний продавца](https://seller-edu.ozon.ru/libra/fbo/gruzomesta-i-podgotovka-k-otgruzke/k-kakoi-zone-otnositsya-tovar)

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>] **обязательный**. Список идентификаторов товаров в системе Ozon — SKU.

## Ответы

**200** — Информация о зонах размещения

- `products_placement` — array[object]. Список товаров с их зонами размещения.
  - `placement_zone` — string (UNSPECIFIED, CLOSED_ZONE, DANGEROUS_GOODS, PRODUCTS, SORT, NON_SORT, OVERSIZE, JEWELRY, UNRESOLVED). Зона размещения товара: - `UNSPECIFIED` — не указана; - `CLOSED_ZONE` — закрытая зона; - `DANGEROUS_GOODS` — товар 2–4 класса опасности; - `PRODUCTS` — продукты; - `SORT` — сортируемый товар; - `NON_SORT` — несортируемый товар; - `OVERSIZE` — крупногабаритный товар; - `JEWELRY` — ювелирные изделия; - `UNRESOLVED` — неизвестная зона. По умолчанию: `UNSPECIFIED`.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
