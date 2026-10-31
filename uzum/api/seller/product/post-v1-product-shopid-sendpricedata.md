---
title: Изменение цен SKU
api: uzum-seller
method: POST
path: /v1/product/{shopId}/sendPriceData
operation_id: saveProductPriceData
tags:
  - Product
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 1efcc81813719565
---

# Изменение цен SKU

`POST /v1/product/{shopId}/sendPriceData`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Этот метод позволяет менять цены SKU.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `shopId` | path | integer<int64> | да | ID магазина, для которого необходимо изменить цены SKU. |

## Запрос

**Тело запроса** (`application/json`):

- `productId` — integer<int64>. Идентификатор продукта
- `skuList` — array[object]. Список SKU, связанных с ценой
  - `fullPrice` — integer<int64>. Полная цена SKU
  - `sellPrice` — integer<int64>. Цена продажи SKU
  - `skuId` — integer<int64> **обязательный**. Идентификатор SKU
  - `skuTitle` — string. Название SKU

## Ответы

**200** — OK

**401** — Заголовок Authorization отсутствует или пуст. Передайте Authorization: API_TOKEN без префикса Bearer; заголовок token не используется.

**403** — Ключ не найден, истёк, выключен, не даёт доступа к магазину или изменениям. Если метод требует shopIds, проверьте наличие этого параметра и доступ ко всем указанным магазинам. Значение Authorization передавайте без Bearer.
