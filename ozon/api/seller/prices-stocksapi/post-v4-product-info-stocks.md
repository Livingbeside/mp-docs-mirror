---
title: Информация о количестве товаров
api: ozon-seller
method: POST
path: /v4/product/info/stocks
operation_id: ProductAPI_GetProductInfoStocks
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 8425068e18ea7ecc
---

# Информация о количестве товаров

`POST /v4/product/info/stocks`

Возвращает информацию о ĸоличестве товаров по схемам FBO, FBS, rFBS и FBP:
 - сĸольĸо единиц есть в наличии,
 - сĸольĸо зарезервировано поĸупателями.

Чтобы получить аналитику по остаткам по схеме FBO, используйте метод [/v1/analytics/stocks](#operation/AnalyticsAPI_AnalyticsStocks).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object **обязательный**. Фильтр по товарам.
  - `offer_id` — array[string]. Фильтр по параметру `offer_id`. Можно передавать список значений.
  - `product_id` — array[string<int64>]. Фильтр по параметру `product_id`. Можно передавать список значений.
  - `visibility` — string (ALL, VISIBLE, INVISIBLE, EMPTY_STOCK, NOT_MODERATED, MODERATED, DISABLED, STATE_FAILED, READY_TO_SUPPLY, VALIDATION_STATE_PENDING, VALIDATION_STATE_FAIL, VALIDATION_STATE_SUCCESS…). Фильтр по видимости товара: - `ALL` — все товары, кроме архивных; - `VISIBLE` — товары, которые видны покупателям; - `INVISIBLE` — товары, которые не видны покупателям; - `EMPTY_STOCK` — товары, у которых не указано наличие; - `NOT_MODERATED` — товары, которые не прошли модерацию; - `MODERATED` — товары, которые прошли модерацию; - `DISABLED` — товары, которые видны покупателям, но недоступны к покупке; - `STATE_FAILED` — товары, создание которых завершилось ошибкой; - `READY_TO_SUPPLY` — товары, готовые к поставке; - `VALIDATION_STATE_PENDING` — товары, которые проходят проверку валидатором на премодерации; - `VALIDATION_STATE_FAIL` — товары, которые не прошли проверку валидатором на премодерации; - `VALIDATION_STATE_SUCCESS` — товары, которые прошли проверку валидатором на премодерации; - `TO_SUPPLY` — товары, готовые к продаже; - `IN_SALE` — товары в продаже; - `REMOVED_FROM_SALE` — товары, скрытые от покупателей; - `BANNED` — заблокированные товары; - `OVERPRICED` — товары с завышенной ценой; - `CRITICALLY_OVERPRICED` — товары со слишком завышенной ценой; - `EMPTY_BARCODE` — товары без штрихкода; - `BARCODE_EXISTS` — товары со штрихкодом; - `QUARANTINE` — товары на карантине после изменения цены более чем на 50%; - `ARCHIVED` — товары в архиве; - `OVERPRICED_WITH_STOCK` — товары в продаже со стоимостью выше, чем у конкурентов; - `PARTIAL_APPROVED` — товары в продаже с пустым или неполным описанием; - `AUTO_ARCHIVED` — товары, которые система перенесла в архив автоматически; - `MANUAL_ARCHIVED` — товары, которые продавец перенёс в архив вручную; - `SEASONAL_AUTO_ARCHIVED` — сезонные товары, которые система перенесла в архив автоматически; - `VISIBLE_WITH_FBO_STOCK` — товары с остатками на FBO, которые видят покупатели. По умолчанию: `ALL`.
  - `with_quant` — object. Товары по тарифу «Эконом».
    - `created` — boolean. Активные эконом-товары.
    - `exists` — boolean. Эконом-товары во всех статусах.
- `limit` — integer<int32> **обязательный**. Количество значений на странице. Минимум — 1, максимум — 1000.

## Ответы

**200** — Количество товара

- `cursor` — string. Указатель для выборки следующих данных.
- `items` — array[object]. Информация о товарах.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `stocks` — array[object]. Информация об остатках.
    - `present` — integer<int32>. Сейчас на складе.
    - `reserved` — integer<int32>. Зарезервировано.
    - `shipment_type` — string (SHIPMENT_TYPE_GENERAL, SHIPMENT_TYPE_BOX, SHIPMENT_TYPE_PALLET). Тип упаковки: - `SHIPMENT_TYPE_GENERAL` — обычный товар; - `SHIPMENT_TYPE_BOX` — коробка; - `SHIPMENT_TYPE_PALLET` — палета. По умолчанию: `SHIPMENT_TYPE_GENERAL`.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
    - `type` — string. Тип склада: - `fbs` — склад продавца, доставка силами Ozon; - `rfbs` — склад продавца, доставка силами продавца; - `fbo` — склад Ozon; - `fbp` — склад партнёра.
    - `warehouse_ids` — array[integer<int64>]. Идентификаторы складов, на которых хранился или хранится товар.
- `total` — integer<int32>. Количество уникальных товаров, для которых выводится информация об остатках.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
