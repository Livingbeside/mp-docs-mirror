---
title: Провалидировать список товаров для pick-up поставки
api: ozon-seller
method: POST
path: /v1/fbp/draft/pick-up/product/validate
operation_id: FbpAPI_FbpDraftPickUpProductValidate
tags:
  - DraftPickupFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 20167d627abda52d
---

# Провалидировать список товаров для pick-up поставки

`POST /v1/fbp/draft/pick-up/product/validate`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[object] **обязательный**. Список идентификаторов товаров — SKU.
  - `count` — integer<int32> **обязательный**. Количество единиц товара в поставке.
  - `sku` — integer<int64> **обязательный**. Идентификатор товара — SKU.
- `warehouse_id` — integer<int64> **обязательный**. Идентификатор склада.

## Ответы

**200** — Список провалидирован

- `approved_items` — array[object]. Подтверждённые товары.
  - `barcode` — string. Штрихкод.
  - `icon_name` — string. Ссылка на изображение товара.
  - `name` — string. Наименование товара.
  - `offer_id` — string. Артикул товара в системе продавца.
  - `quantity` — integer<int32>. Количество товара.
  - `sku` — integer<int64>. Идентификатор товара — SKU.
  - `volume` — number<double>. Объём товара.
- `bundle_generated` — boolean. `true`, если проверенный список товаров создан.
- `bundle_id` — string. Идентификатор провалидированного списка товаров.
- `rejected_items` — array[object]. Отклонённые товары.
  - `barcode` — string. Штрихкод.
  - `icon_name` — string. Ссылка на изображение товара.
  - `name` — string. Наименование товара.
  - `offer_id` — string. Артикул товара в системе продавца.
  - `quantity` — integer<int32>. Количество товара.
  - `rejection_reasons` — array[string (BUNDLE_ITEM_ERROR_UNSPECIFIED, OUT_OF_ASSORTMENT, INVALID, INCOMPATIBLE_WAREHOUSE, INVALID_BARCODE, MULTIPLICITY, NO_PRICE, BANNED, DUPLICATE_ITEMS, ZERO_QUANTITY, QUANTITY_GREATER_THEN_MAX, NO_SALES…)]. Причины отклонения: - `BUNDLE_ITEM_ERROR_UNSPECIFIED` — не определена; - `OUT_OF_ASSORTMENT` — товар не найден; - `INVALID` — товар не создан; - `INCOMPATIBLE_WAREHOUSE` — неверный идентификатор склада; - `INVALID_BARCODE` — не указан штрихкод; - `MULTIPLICITY` — количество товара не кратно требуемой партии; - `NO_PRICE` — не указана цена; - `BANNED` — товар не доступен к продаже или поставке на выбранный склад; - `ZERO_QUANTITY` — количество товаров в поставке равно 0; - `QUANTITY_GREATER_THEN_MAX` — количество товаров одной SKU больше максимального значения; - `NO_SALES` — у товара нет продаж больше 60 дней; - `SURPLUS` — товаров на складе хватит на 90 дней; - `AVAILABILITY_IS_EMPTY` — нет информации о доступности товара. По умолчанию: `BUNDLE_ITEM_ERROR_UNSPECIFIED`.
  - `sku` — integer<int64>. Идентификатор товара — SKU.
  - `volume` — number<double>. Объём товара.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
