---
title: Получить аналитику по остаткам
api: ozon-seller
method: POST
path: /v1/analytics/stocks
operation_id: AnalyticsAPI_AnalyticsStocks
tags:
  - AnalyticsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 9240f15ab5aa1a4d
---

# Получить аналитику по остаткам

`POST /v1/analytics/stocks`

С 17 августа 2026 года метод возвращает информацию об остатках в реальном времени. Используйте метод, чтобы получить аналитику по остаткам товаров на складах. Метод соответствует разделу [**FBO → Управление остатками**](https://seller.ozon.ru/app/fbo-stocks/stocks-management/) в личном кабинете. Аналитика обновляется два раза в день: примерно в 07:00 и 16:00 по UTC. В запросе используйте только одно из полей: `cluster_ids` или `macrolocal_cluster_ids`, иначе вернётся ошибка.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cluster_ids` — array[string<int64>]. Фильтр по идентификаторам кластеров. Получить идентификаторы можно через метод [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList).
- `item_tags` — array[string (ITEM_ATTRIBUTE_NONE, ECONOM, NOVEL, DISCOUNT, FBS_RETURN, SUPER, MARKABLE)]. Фильтр по тегам товара: - `ITEM_ATTRIBUTE_NONE` — без тега; - `ECONOM` — эконом-товар; - `NOVEL` — новинка; - `DISCOUNT` — уценённый товар; - `FBS_RETURN` — товар из возврата FBS; - `SUPER` — Super-товар; - `MARKABLE` — товар, подлежащий маркировке.
- `macrolocal_cluster_ids` — array[string<int64>]. Фильтр по идентификаторам макролокальных кластеров. Получить идентификаторы можно в параметре `macrolocal_cluster_ids` метода [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) или через метод [/v2/cluster/list](#operation/DraftClusterList).
- `placement_zone` — array[string (PLACEMENT_ZONE_NONE, CLOSED_ZONE, DANGEROUS_GOOD, PRODUCTS_PLUS_17, SORT, NON_SORT_MEZ, OVERSIZE, JEWELRY, UNRESOLVED)]. Зона размещения товара: - `PLACEMENT_ZONE_NONE` — не указана; - `CLOSED_ZONE` — закрытая; - `DANGEROUS_GOOD` — опасные товары; - `PRODUCTS_PLUS_17` — продукты; - `SORT` — сортируемый товар; - `NON_SORT_MEZ` — несортируемый товар; - `OVERSIZE` — крупногабаритный товар; - `JEWELRY` — ювелирные изделия; - `UNRESOLVED` — ещё не определена.
- `skus` — array[string<int64>] **обязательный**. Фильтр по идентификаторам товаров в системе Ozon — SKU.
- `turnover_grades` — array[string (TURNOVER_GRADE_NONE, DEFICIT, POPULAR, ACTUAL, SURPLUS, NO_SALES, WAS_NO_SALES, RESTRICTED_NO_SALES, COLLECTING_DATA, WAITING_FOR_SUPPLY, WAS_DEFICIT, WAS_POPULAR…)]. Фильтр по статусу ликвидности товаров: - `TURNOVER_GRADE_NONE` — нет статуса ликвидности. - `DEFICIT` — дефицитный. Остатков товара хватит до 28 дней. - `POPULAR` — очень популярный. Остатков товара хватит на 28–56 дней. - `ACTUAL` — популярный. Остатков товара хватит на 56–120 дней. - `SURPLUS` — избыточный. Товар продаётся медленно, остатков хватит более чем на 120 дней. - `NO_SALES` — без продаж. У товара нет продаж последние 28 дней. - `WAS_NO_SALES` — был без продаж. У товара не было продаж и остатков последние 28 дней. - `RESTRICTED_NO_SALES` — без продаж, ограничен. У товара не было продаж более 120 дней. Такой товар [нельзя добавить в поставку](https://seller-edu.ozon.ru/fbo/rabota-so-stokom/nehodovye-tovary). - `COLLECTING_DATA` — сбор данных. Для расчёта ликвидности нового товара собираем данные в течение 60 дней после поставки. - `WAITING_FOR_SUPPLY` — ожидаем поставки. На складе нет остатков, доступных к продаже. Сделайте поставку для начала сбора данных. - `WAS_DEFICIT` — был дефицитным. Товар был дефицитным последние 56 дней. Сейчас у него нет остатков. - `WAS_POPULAR` — был очень популярным. Товар был очень популярным последние 56 дней. Сейчас у него нет остатков. - `WAS_ACTUAL` — был популярным. Товар был популярным последние 56 дней. Сейчас у него нет остатков. - `WAS_SURPLUS` — был избыточным. Товар был избыточным последние 56 дней. Сейчас у него нет остатков.
- `unmarked_stocks_only` — boolean. `true`, чтобы получить только товары, которые нужно промаркировать.
- `warehouse_ids` — array[string<int64>]. Фильтр по идентификаторам складов. Получить идентификаторы можно через метод [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList).

## Ответы

**200** — Аналитика по остаткам на складах

- `items` — array[object]. Информация о товарах.
  - `ads` — number<double>. Среднесуточное количество проданных единиц товара за последние 28 дней по всем кластерам.
  - `ads_cluster` — number<double>. Среднесуточное количество проданных единиц товара за последние 28 дней в кластере.
  - `available_stock_count` — integer<int32>. Количество товаров, которые доступны к продаже. Соответствует столбцу «Доступно к продаже».
  - `cluster_id` — integer<int64>. Идентификатор кластера. Получить подробную информацию о кластере можно через метод [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList).
  - `cluster_name` — string. Название кластера.
  - `days_without_sales` — integer<int32>. Количество дней без продаж по всем кластерам.
  - `days_without_sales_cluster` — integer<int32>. Количество дней без продаж в кластере.
  - `excess_stock_count` — integer<int32>. Количество излишков с поставки, которые доступны к вывозу.
  - `expiring_stock_count` — integer<int32>. Количество единиц товара с истекающим сроком годности.
  - `idc` — number<double>. Количество дней, на которое хватит остатка товара с учётом среднесуточных продаж за 28 дней по всем кластерам.
  - `idc_cluster` — number<double>. Количество дней, на которое хватит остатка товара с учётом среднесуточных продаж за 28 дней в кластере.
  - `item_tags` — array[string (UNSPECIFIED, ITEM_ATTRIBUTE_NONE, ECONOM, NOVEL, DISCOUNT, FBS_RETURN, SUPER, MARKABLE)]. Теги товара: - `UNSPECIFIED` — не определено; - `ITEM_ATTRIBUTE_NONE` — без тега; - `ECONOM` — эконом-товар; - `NOVEL` — новинка; - `DISCOUNT` — уценённый товар; - `FBS_RETURN` — товар из возврата FBS; - `SUPER` — Super-товар; - `MARKABLE` — товар, подлежащий маркировке.
  - `macrolocal_cluster_id` — integer<int64>. Идентификатор макролокального кластера. Получите информацию о кластере методом [/v1/cluster/list](#operation/SupplyDraftAPI_DraftClusterList) или [/v2/cluster/list](#operation/DraftClusterList).
  - `name` — string. Название товара.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `other_stock_count` — integer<int32>. Количество единиц товара, проходящих проверку.
  - `placement_zone` — array[string (UNSPECIFIED, CLOSED_ZONE, DANGEROUS_GOOD, PRODUCTS, SORT, NON_SORT, OVERSIZE, JEWELRY, UNRESOLVED)]. Зона размещения товара: - `UNSPECIFIED` — не указана; - `CLOSED_ZONE` — закрытая; - `DANGEROUS_GOOD` — опасные товары; - `PRODUCTS` — продукты; - `SORT` — сортируемый товар; - `NON_SORT` — несортируемый товар; - `OVERSIZE` — крупногабаритный товар; - `JEWELRY` — ювелирные изделия; - `UNRESOLVED` — ещё не определена.
  - `requested_stock_count` — integer<int32>. Количество единиц товара в заявках на поставку.
  - `return_from_customer_stock_count` — integer<int32>. Количество единиц товара в процессе возврата от покупателей.
  - `return_to_seller_stock_count` — integer<int32>. Количество единиц товара, готовящихся к вывозу по вашей заявке.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `stock_defect_stock_count` — integer<int32>. Количество брака, доступное к вывозу со стока.
  - `transit_defect_stock_count` — integer<int32>. Количество брака, доступное к вывозу с поставки.
  - `transit_stock_count` — integer<int32>. Количество единиц товара в поставках в пути.
  - `turnover_grade` — string (UNSPECIFIED, TURNOVER_GRADE_NONE, DEFICIT, POPULAR, ACTUAL, SURPLUS, NO_SALES, WAS_NO_SALES, RESTRICTED_NO_SALES, COLLECTING_DATA, WAITING_FOR_SUPPLY, WAS_DEFICIT…). Статус ликвидности товара по всем кластерам: - `UNSPECIFIED` — значение не определено. - `TURNOVER_GRADE_NONE` — нет статуса ликвидности. - `DEFICIT` — дефицитный. Остатков товара хватит до 28 дней. - `POPULAR` — очень популярный. Остатков товара хватит на 28–56 дней. - `ACTUAL` — популярный. Остатков товара хватит на 56–120 дней. - `SURPLUS` — избыточный. Товар продаётся медленно, остатков хватит более чем на 120 дней. - `NO_SALES` — без продаж. У товара нет продаж последние 28 дней. - `WAS_NO_SALES` — был без продаж. У товара не было продаж и остатков последние 28 дней. - `RESTRICTED_NO_SALES` — без продаж, ограничен. У товара не было продаж более 120 дней. Такой товар [нельзя добавить в поставку](https://seller-edu.ozon.ru/fbo/rabota-so-stokom/nehodovye-tovary). - `COLLECTING_DATA` — сбор данных. Для расчёта ликвидности нового товара собираем данные в течение 60 дней после поставки. - `WAITING_FOR_SUPPLY` — ожидаем поставки. На складе нет остатков, доступных к продаже. Сделайте поставку для начала сбора данных. - `WAS_DEFICIT` — был дефицитным. Товар был дефицитным последние 56 дней. Сейчас у него нет остатков. - `WAS_POPULAR` — был очень популярным. Товар был очень популярным последние 56 дней. Сейчас у него нет остатков. - `WAS_ACTUAL` — был популярным. Товар был популярным последние 56 дней. Сейчас у него нет остатков. - `WAS_SURPLUS` — был избыточным. Товар был избыточным последние 56 дней. Сейчас у него нет остатков.
  - `turnover_grade_cluster` — string (UNSPECIFIED, TURNOVER_GRADE_NONE, DEFICIT, POPULAR, ACTUAL, SURPLUS, NO_SALES, WAS_NO_SALES, RESTRICTED_NO_SALES, COLLECTING_DATA, WAITING_FOR_SUPPLY, WAS_DEFICIT…). Статус ликвидности товара в кластере: - `UNSPECIFIED` — значение не определено. - `TURNOVER_GRADE_NONE` — нет статуса ликвидности. - `DEFICIT` — дефицитный. Остатков товара хватит до 28 дней. - `POPULAR` — очень популярный. Остатков товара хватит на 28–56 дней. - `ACTUAL` — популярный. Остатков товара хватит на 56–120 дней. - `SURPLUS` — избыточный. Товар продаётся медленно, остатков хватит более чем на 120 дней. - `NO_SALES` — без продаж. У товара нет продаж последние 28 дней. - `WAS_NO_SALES` — был без продаж. У товара не было продаж и остатков последние 28 дней. - `RESTRICTED_NO_SALES` — без продаж, ограничен. У товара не было продаж более 120 дней. Такой товар [нельзя добавить в поставку](https://seller-edu.ozon.ru/fbo/rabota-so-stokom/nehodovye-tovary). - `COLLECTING_DATA` — сбор данных. Для расчёта ликвидности нового товара собираем данные в течение 60 дней после поставки. - `WAITING_FOR_SUPPLY` — ожидаем поставки. На складе нет остатков, доступных к продаже. Сделайте поставку для начала сбора данных. - `WAS_DEFICIT` — был дефицитным. Товар был дефицитным последние 56 дней. Сейчас у него нет остатков. - `WAS_POPULAR` — был очень популярным. Товар был очень популярным последние 56 дней. Сейчас у него нет остатков. - `WAS_ACTUAL` — был популярным. Товар был популярным последние 56 дней. Сейчас у него нет остатков. - `WAS_SURPLUS` — был избыточным. Товар был избыточным последние 56 дней. Сейчас у него нет остатков.
  - `valid_stock_count` — integer<int32>. Количество товаров, которые готовятся к продаже. Соответствует столбцу «Готовим к продаже».
  - `waiting_docs_stock_count` — integer<int32>. Количество маркируемых товаров, которые ожидают ваших действий.
  - `waiting_docs_to_export_stock_count` — integer<int32>. Количество маркируемых товаров, которые ожидают вывоз.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_name` — string. Название склада.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
