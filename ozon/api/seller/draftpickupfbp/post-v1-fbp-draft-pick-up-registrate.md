---
title: Перевести черновик в действующую поставку
api: ozon-seller
method: POST
path: /v1/fbp/draft/pick-up/registrate
operation_id: FbpDraftPickUpRegistrate
tags:
  - DraftPickupFBP
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 70e8150ddc5ed0d9
---

# Перевести черновик в действующую поставку

`POST /v1/fbp/draft/pick-up/registrate`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1700-FBP-metody/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `row_version` — integer<int64> **обязательный**. Идентификатор актуальной версии черновика.
- `supply_id` — string **обязательный**. Идентификатор заявки на поставку.

## Ответы

**200** — Успешно

- `error` — object. Ошибка.
  - `bundle_errors` — array[object]. Ошибки провалидированного списка товаров.
    - `errors` — array[string (BUNDLE_ITEM_ERROR_UNSPECIFIED, OUT_OF_ASSORTMENT, INVALID, INCOMPATIBLE_WAREHOUSE, INVALID_BARCODE, MULTIPLICITY, NO_PRICE, BANNED, DUPLICATE_ITEMS, ZERO_QUANTITY, QUANTITY_GREATER_THEN_MAX, NO_SALES…)]. Ошибки: - `BUNDLE_ITEM_ERROR_UNSPECIFIED` — не определена; - `OUT_OF_ASSORTMENT` — товара нет в ассортименте поставки; - `INVALID` — неверный статус; - `INCOMPATIBLE_WAREHOUSE` — неверный идентификатор склада; - `INVALID_BARCODE` — штрихкод не указан; - `MULTIPLICITY` — количество товара не кратно упаковке; - `NO_PRICE` — цена не указана; - `BANNED` — товар заблокирован; - `ZERO_QUANTITY` — количество товара не может быть 0; - `QUANTITY_GREATER_THEN_MAX` — превышено максимальное количество товара для одного SKU; - `NO_SALES` — у товара нет продаж больше 60 дней; - `SURPLUS` — товаров на складе хватит на 90 дней; - `AVAILABILITY_IS_EMPTY` — нет информации о доступности товара. По умолчанию: `BUNDLE_ITEM_ERROR_UNSPECIFIED`.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `order_error` — string (ORDER_ERROR_TYPE_UNSPECIFIED, INVALID_NUMBER_OF_PACKAGE_UNITS, MAXIMUM_NUMBER_OF_UNIQUE_SKU_REACHED, MAXIMUM_BUNDLE_VOLUME_REACHED, BUNDLE_ID_EMPTY, INVALID_SUPPLY_TYPE, INVALID_TIMESLOT, INVALID_WHC_NUMBER, DRAFT_LOCKED, DROP_OFF_POINTS_IS_EMPTY, WAREHOUSE_IS_EMPTY, BUSINESS_FLOW_TYPE_IS_EMPTY…). Ошибка регистрации поставки: - `ORDER_ERROR_TYPE_UNSPECIFIED` — не определена; - `INVALID_NUMBER_OF_PACKAGE_UNITS` — указано неверное количество грузомест в заявке; - `MAXIMUM_NUMBER_OF_UNIQUE_SKU_REACHED` — превышено максимальное количество уникальных SKU в заявке; - `MAXIMUM_BUNDLE_VOLUME_REACHED` — достигнут максимальный объём поставки; - `BUNDLE_ID_EMPTY` — состав поставки пуст; - `INVALID_SUPPLY_TYPE` — тип поставки не указан или указан неверный; - `INVALID_TIMESLOT` — таймслот не указан или указан неверный; - `INVALID_WHC_NUMBER` — неверный идентификатор поставки WHC; - `DRAFT_LOCKED` — заявка ожидает переноса в ордер; - `DROP_OFF_POINTS_IS_EMPTY` — для поставки drop-off не указано место отгрузки; - `WAREHOUSE_IS_EMPTY` — не указаны данные склада; - `BUSINESS_FLOW_TYPE_IS_EMPTY` — не определён тип бизнес-процесса; - `WAS_CANCELLED` — поставка уже отменена; - `PICK_UP_DETAILS_IS_EMPTY` — для поставки pick-up не указаны данные по отгрузке курьеру со склада продавца; - `INVALID_PICK_UP_DETAILS` — для поставки pick-up указаны неверные данные по отгрузке курьеру со склада продавца; - `INVALID_PICK_UP_DATE` — для поставки pick-up указана неверная дата отгрузки курьеру со склада продавца; - `INTERNAL_ERROR` — ошибка при проверке параметров. По умолчанию: `ORDER_ERROR_TYPE_UNSPECIFIED`.
- `is_error` — boolean. `true`, если есть ошибка.
- `row_version` — integer<int64>. Идентификатор актуальной версии черновика.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
