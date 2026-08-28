---
title: Получить информацию о грузоместах
api: ozon-seller
method: POST
path: /v1/cargoes/get
operation_id: CargoesGet
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e8ab62ebf373e384
---

# Получить информацию о грузоместах

`POST /v1/cargoes/get`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_ids` — array[string<int64>] **обязательный**. Список идентификаторов поставок в заявке.

## Ответы

**200** — Информация о грузоместах

- `supply` — array[object]. Информация о грузоместах.
  - `bundle_id` — string. Идентификатор товарного состава.
  - `cargoes` — array[object]. Грузоместа.
    - `bundle_id` — string. Идентификатор товарного состава.
    - `cargo_id` — integer<int64>. Идентификатор грузоместа.
    - `content_type` — string (UNSPECIFIED, MONO, MIX, NONE). Тип ассортимента грузоместа: - `UNSPECIFIED` — не определён; - `MONO` — палета-моно или коробка-моно; - `MIX` — палета-микс или коробка-микс; - `NONE` — отсутствует. По умолчанию: `UNSPECIFIED`.
    - `placement_zone_type` — string (UNSPECIFIED, UNDEFINED, SINGLE, MULTI). Тип зоны размещения: - `UNSPECIFIED` — не требуется распределение по зонам размещения; - `UNDEFINED` — не определён; - `SINGLE` — одинаковая зона размещения в составе грузоместа; - `MULTI` — разная зона размещения в составе грузоместа. По умолчанию: `UNSPECIFIED`.
    - `tracking_info` — object. Отслеживание грузоместа.
      - `date` — string. Дата приезда.
      - `status` — string (UNSPECIFIED, READY_TO_SUPPLY, REFUSED, ON_WAREHOUSE, NOT_DELIVERED, ACCEPTING, PROCESSED, ON_POINT_SHIPMENT, ON_TRANSIT_WAREHOUSE, LOST, CREATED, DELETED). Статус грузоместа: - `UNSPECIFIED` — не определён; - `READY_TO_SUPPLY` — готово к отгрузке; - `REFUSED` — отказано; - `ON_WAREHOUSE` — на складе размещения; - `NOT_DELIVERED` — не сдано; - `ACCEPTING` — приёмка; - `PROCESSED` — обработано; - `ON_POINT_SHIPMENT` — на точке отгрузки; - `ON_TRANSIT_WAREHOUSE` — в пути; - `LOST` — потеряно; - `CREATED` — создано; - `DELETED` — удалено. По умолчанию: `UNSPECIFIED`.
      - `type` — string (UNSPECIFIED, EXPECTED_ARRIVAL, ACTUAL_ARRIVAL). Тип грузоместа: - `UNSPECIFIED` — не определён; - `EXPECTED_ARRIVAL` — плановая дата отгрузки; - `ACTUAL_ARRIVAL` — фактическая дата отгрузки. По умолчанию: `UNSPECIFIED`.
    - `type` — string (UNSPECIFIED, BOX, PALLET). Тип грузоместа: - `UNSPECIFIED` — не определён, - `BOX` — коробка, - `PALLET` — палета. По умолчанию: `UNSPECIFIED`.
  - `supply_id` — integer<int64>. Идентификатор поставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
