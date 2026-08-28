---
title: Состав поставки или заявки на поставку
api: ozon-seller
method: POST
path: /v1/supply-order/bundle
operation_id: SupplyOrderBundle
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 869acdf8362fb262
---

# Состав поставки или заявки на поставку

`POST /v1/supply-order/bundle`

Используйте метод, чтобы получить товарный состав поставки или черновика заявки на поставку. Одним вызовом метода можно получить состав одной поставки или черновика заявки.

## Запрос

**Тело запроса** (`application/json`):

- `bundle_ids` — array[string] **обязательный**. Идентификаторы товарного состава поставки. Можно получить в методе [/v3/supply-order/get](#operation/SupplyOrderGet).
- `is_asc` — boolean. `true`, чтобы сортировать по возрастанию.
- `item_tags_calculation` — object. Список складов для расчёта товарных тегов.
  - `dropoff_warehouse_id` — string **обязательный**. Идентификатор склада отгрузки поставки.
  - `storage_warehouse_ids` — array[string] **обязательный**. Список идентификаторов складов поставки, не больше 25 значений.
- `last_id` — string. Идентификатор последнего значения SKU на странице.
- `limit` — integer<int32> **обязательный**. Количество товаров на странице.
- `query` — string. Поисковый запрос, например: по названию, артикулу или SKU.
- `sort_field` — string (SKU, NAME, QUANTITY, TOTAL_VOLUME_IN_LITRES). Сортировка по параметрам: - `SKU` — SKU; - `NAME` — названию товара; - `QUANTITY` — количеству; - `TOTAL_VOLUME_IN_LITRES` — объёму в литрах.

## Ответы

**200** — Состав поставки

- `items` — array[object]. Список товаров в заявке на поставку.
  - `icon_path` — string. Ссылка на изображение товара.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `quantity` — integer<int32>. Количество товара.
  - `barcode` — string. Штрихкод товара.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `quant` — integer<int32>. Количество товаров в одной упаковке.
  - `is_quant_editable` — boolean. `true`, если количество товаров в одной упаковке можно изменить.
  - `volume_in_litres` — number<double>. Объём товара в литрах.
  - `total_volume_in_litres` — number<double>. Объём всех товаров в литрах.
  - `contractor_item_code` — string. Идентификатор товара в системе продавца — артикул.
  - `sfbo_attribute` — string (ITEM_SFBO_ATTRIBUTE_NONE, ITEM_SFBO_ATTRIBUTE_SUPER_FBO, ITEM_SFBO_ATTRIBUTE_ANTI_FBO). Метка Super-товара: - `ITEM_SFBO_ATTRIBUTE_NONE` — без метки; - `ITEM_SFBO_ATTRIBUTE_SUPER_FBO` — Super-товар; - `ITEM_SFBO_ATTRIBUTE_ANTI_FBO` — неходовой товар. По умолчанию: `ITEM_SFBO_ATTRIBUTE_UNSPECIFIED`.
  - `shipment_type` — string (BUNDLE_ITEM_SHIPMENT_TYPE_GENERAL, BUNDLE_ITEM_SHIPMENT_TYPE_BOX, BUNDLE_ITEM_SHIPMENT_TYPE_PALLET). Тип упаковки: - `BUNDLE_ITEM_SHIPMENT_TYPE_GENERAL` — обычный товар; - `BUNDLE_ITEM_SHIPMENT_TYPE_BOX` — коробка; - `BUNDLE_ITEM_SHIPMENT_TYPE_PALLET` — палета. По умолчанию: `BUNDLE_ITEM_SHIPMENT_TYPE_UNSPECIFIED`.
  - `tags` — array[string (EVSD_REQUIRED, MARKING_REQUIRED, MARKING_POSSIBLE, JEWELRY, TRACEABLE, ETTN_REQUIRED, UNDEFINED)]. Теги товаров из поставки или заявки на поставку. Возможные значения: - `EVSD_REQUIRED` — товар с сертификацией «Меркурий»; - `MARKING_REQUIRED` — товар с обязательной маркировкой «Честный ЗНАК»; - `MARKING_POSSIBLE` — товар с возможной маркировкой «Честный ЗНАК»; - `JEWELRY` — товар с признаком ювелирного изделия; - `TRACEABLE` — товар с признаком прослеживаемости; - `ETTN_REQUIRED` — товар с признаком прослеживаемости, для которого необходима электронная ТТН; - `UNDEFINED` — неизвестный тег.
  - `placement_zone` — string (UNSPECIFIED, CLOSED_ZONE, DANGEROUS_GOODS, PRODUCTS, SORT, NON_SORT, OVERSIZE, JEWELRY, UNRESOLVED). Зона размещения товара: - `UNSPECIFIED` — не указана; - `CLOSED_ZONE` — закрытая зона; - `DANGEROUS_GOODS` — товар 2–4 класса опасности; - `PRODUCTS` — продукты; - `SORT` — сортируемый товар; - `NON_SORT` — несортируемый товар; - `OVERSIZE` — крупногабаритный товар; - `JEWELRY` — ювелирные изделия; - `UNRESOLVED` — неизвестная зона. По умолчанию: `UNSPECIFIED`.
- `total_count` — integer<int32>. Количество товаров в заявке.
- `has_next` — boolean. Признак, что в ответе вернули не все товары: - `true` — сделайте повторный запрос с другим значением `last_id`, чтобы получить остальные значения; - `false` — ответ содержит все значения характеристики.
- `last_id` — string. Идентификатор последнего значения на странице.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
