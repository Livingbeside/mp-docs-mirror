---
title: Получить информацию о возвратных коробках по штрихкоду с этикетки
api: ozon-seller
method: POST
path: /v1/return/box/get-by-barcode
operation_id: ReturnAPI_BoxGetByBarcode
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 3e0f61f09eb0cfd2
---

# Получить информацию о возвратных коробках по штрихкоду с этикетки

`POST /v1/return/box/get-by-barcode`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2177-Novyi-metod-dlia-polucheniia-ostatkov-FBO/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `barcode` — integer<int64> **обязательный**. Штрихкод с возвратной этикетки — `lozon_id`.

## Ответы

**200** — Информация о возвратных коробках

- `box_barcode` — string. Штрихкод коробки.
- `box_id` — integer<int64>. Идентификатор коробки.
- `cargo_box_id` — string. Идентификатор груза.
- `destination_warehouse` — object. Склад назначения.
  - `id` — integer<int64>. Идентификатор склада.
  - `name` — string. Название склада.
  - `type` — string (UNSPECIFIED, SELLER_WAREHOUSE, OZON_WAREHOUSE). Тип склада: - `UNSPECIFIED` — не указан; - `SELLER_WAREHOUSE` — склад продавца; - `OZON_WAREHOUSE` — склад Ozon. По умолчанию: `UNSPECIFIED`.
- `dimensions` — object. Габариты коробки в сантиметрах.
  - `height` — integer<int32>. Высота.
  - `length` — integer<int32>. Длина.
  - `width` — integer<int32>. Ширина.
- `label_barcode` — integer<int64>. Штрихкод этикетки возврата. Если `0`, получить штрихкод не удалось.
- `return_type` — string (UNSPECIFIED, SUPPLY_RETURN, STOCK_RETURN). Тип возврата: - `UNSPECIFIED` — не указан; - `SUPPLY_RETURN` — возврат с поставки; - `STOCK_RETURN` — возврат со стока. По умолчанию: `UNSPECIFIED`.
- `state` — string (UNSPECIFIED, IN_STORAGE, CONFIRMED, APPROVAL, BLOCKED, PROCESSING, REMOVED, SHIPPED, COMPENSATED, UTILIZED, LOADED, NOT_SHIPPED…). Статус коробки: - `UNSPECIFIED` — не указан; - `IN_STORAGE` — доступна к вывозу; - `CONFIRMED` — добавлена в заявку на вывоз или доступна к вывозу; - `APPROVAL`, `BLOCKED`, `PROCESSING`, `NOT_SHIPPED` — готова к вывозу; - `REMOVED`, `LOST_IN_TRANSIT`, `LOST` — потеряна; - `SHIPPED` — в пути; - `COMPENSATED` — отправили компенсацию продавцу; - `UTILIZED` — утилизирована; - `LOADED` — собрана; - `READY_FOR_DELIVERY` — на сортировке в сортировочном центре; - `GIVEN_OUT` — у курьера; - `DELIVERY_ATTEMPT_FAILED` — неудачная попытка доставки; - `DELIVERED` — получена; - `DELIVERY_CANCELLED` — доставка отменена; - `UTILIZING` — в процессе утилизации; - `STORED_AT_DELIVERY_POINT` — в пункте вывоза; - `UNPACKED` — расформирована. По умолчанию: `UNSPECIFIED`.
- `supply_id` — integer<int64>. Идентификатор поставки.
- `type` — string (UNSPECIFIED, SUPPLY_SURPLUS, SUPPLY_DEFECT, STOCK). Тип коробки: - `UNSPECIFIED` — не указан; - `SUPPLY_SURPLUS` — излишки; - `SUPPLY_DEFECT` — брак; - `STOCK` — остатки. По умолчанию: `UNSPECIFIED`.
- `updated_at` — string<date-time>. Дата последнего обновления.
- `utilization_reason` — string (UNSPECIFIED, SELLER_DEMAND, EXPIRATION, DEFECT_1P, COMPENSATED_BOX_WAS_FOUND, STORAGE_FAULT, STORAGE_RULES_VIOLATION). Причина утилизации: - `UNSPECIFIED` — не указана; - `SELLER_DEMAND` — вы заказали утилизацию; - `EXPIRATION` — истёк срок годности у товара; - `DEFECT_1P` — брак; - `COMPENSATED_BOX_WAS_FOUND` — обнаружена компенсированная коробка; - `STORAGE_FAULT` — складская ошибка; - `STORAGE_RULES_VIOLATION` — нарушены правила хранения. По умолчанию: `UNSPECIFIED`.
- `volume_in_litres` — number<double>. Объём коробки в литрах.
- `warehouse` — object. Информация о складе.
  - `id` — integer<int64>. Идентификатор склада.
  - `name` — string. Название склада.
- `weight` — integer<int32>. Вес коробки в граммах.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
