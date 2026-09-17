---
title: Получить информацию о локальности продаж по кластерам
api: ozon-seller
method: POST
path: /v1/analytics/local-sale/clusters-items/info
operation_id: AnalyticsLocalSaleClustersItemsInfo
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: a564f5afc7a75c12
---

# Получить информацию о локальности продаж по кластерам

`POST /v1/analytics/local-sale/clusters-items/info`

Метод соответствует разделу [**Аналитика → Планирование поставок → Локальность продаж**](https://seller.ozon.ru/app/analytics/sales-geography/local-packaging).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2335-Novye-beta-metody-dlia-polucheniia-lokalnosti-prodazh/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object **обязательный**. Фильтр.
  - `delivery_schema` — string (ALL, FBO, FBS). Схема продажи: - `ALL` — все схемы; - `FBO`; - `FBS`.
  - `description_categories` — array[object]. Категория товара.
    - `category_id` — integer<int64> **обязательный**. Идентификатор родительской категории. Получите методом [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
    - `children_category_id` — integer<int64>. Идентификатор дочерней категории. Получите методом [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
    - `type_id` — integer<int64>. Идентификатор типа товара. Получите методом [/v1/description-category/tree](#operation/DescriptionCategoryAPI_GetTree).
  - `macrolocal_cluster_from_ids` — array[string<int64>]. Идентификатор кластера отгрузки. Получите методом [/v2/cluster/list](#operation/DraftClusterList).
  - `macrolocal_cluster_to_ids` — array[string<int64>] **обязательный**. Идентификатор кластера доставки. Получите методом [/v2/cluster/list](#operation/DraftClusterList).
  - `overpayment_reasons` — array[string (NO_SUPPLIES_TO_CLUSTER, MISSING_ITEMS_IN_CLUSTER, FREQUENT_OUT_OF_STOCK)]. Причина переплаты: - `NO_SUPPLIES_TO_CLUSTER` — не было поставок в кластер; - `MISSING_ITEMS_IN_CLUSTER` — не все товары поставлялись в кластер; - `FREQUENT_OUT_OF_STOCK` — часто заканчиваются товары.
  - `period` — object **обязательный**. Период.
    - `from` — string< YYYY-MM-DD> **обязательный**. Начало периода.
    - `to` — string< YYYY-MM-DD> **обязательный**. Конец периода.
  - `skus` — array[string]. Идентификатор товара в системе Ozon — SKU.
  - `supply_period` — string (ONE_WEEK, TWO_WEEKS, FOUR_WEEKS, EIGHT_WEEKS). Частота поставки: - `ONE_WEEK` — раз в одну неделю; - `TWO_WEEKS` — раз в две недели; - `FOUR_WEEKS` — раз в четыре недели; - `EIGHT_WEEKS` — раз в восемь недель.
- `limit` — integer<int64> **обязательный**. Количество товаров в ответе.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.
- `sort_by` — string (IMPACT_SHARE, LOCALITY, OVERPAYMENT_TOTAL, OVERPAYMENT_NON_LOCAL, OVERPAYMENT_DELTA). Параметр, по которому будут отсортированы товары: - `IMPACT_SHARE` — доля влияния на переплату; - `LOCALITY` — доля локальных продаж; - `OVERPAYMENT_TOTAL` — общая переплата за логистику; - `OVERPAYMENT_NON_LOCAL` — наценка за нелокальную продажу; - `OVERPAYMENT_DELTA` — разница с тарифом для локальной продажи.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — во возрастанию; - `DESC` — по убыванию.

## Ответы

**200** — Информация о локальности продаж по кластерам

- `items` — array[object]. Список товаров.
  - `cluster_to_id` — integer<int64>. Идентификатор кластера.
  - `item` — object. Информация о товаре.
    - `delivery_schemas` — array[string (FBO, FBS)]. Схема продажи: - `FBO`, - `FBS`.
    - `image` — string. Ссылка на изображение товара.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `metrics` — object. Информация о метриках локальности продаж.
    - `attention_level` — string (LOW, MEDIUM, HIGH). Уровень влияния на переплату: - `LOW` — низкий; - `MEDIUM` — средний; - `HIGH` — высокий.
    - `impact_share` — number<double>. Доля влияния на переплату в процентах.
    - `local_data` — object. Информация о локальных продажах.
      - `index` — number<double>. Индекс локальных продаж в процентах.
      - `local_quantity` — integer<int64>. Количество товаров, которые доставили локально.
      - `total_quantity` — integer<int64>. Общее количество товаров.
    - `overpayment` — object. Информация о переплате по логистике.
      - `delta` — number<double>. Разница с тарифом для локальной продажи.
      - `non_local_delivery` — number<double>. Наценка за нелокальную продажу.
      - `total` — number<double>. Общая переплата.
    - `overpayment_reasons` — array[object]. Причины переплат за логистику.
      - `amount` — number<double>. Сумма переплаты.
      - `quantity` — integer<int64>. Количество товаров.
      - `reason` — string (NO_SUPPLIES_TO_CLUSTER, MISSING_ITEMS_IN_CLUSTER, FREQUENT_OUT_OF_STOCK). Причина переплаты: - `NO_SUPPLIES_TO_CLUSTER` — не было поставок в кластер; - `MISSING_ITEMS_IN_CLUSTER` — не все товары поставлялись в кластер; - `FREQUENT_OUT_OF_STOCK` — часто заканчиваются товары.
    - `price` — number<double>. Стоимость товаров, которые рекомендуются к поставке.
    - `recommended_supply` — integer<int32>. Рекомендуемое количество товаров к поставке.
- `total` — integer<int64>. Общее количество товаров.

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
