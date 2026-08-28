---
title: Получить информацию о грузоместах
api: ozon-seller
method: POST
path: /v2/cargoes/get
operation_id: CargoesGetV2
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 50ac0f2fe5e2509f
---

# Получить информацию о грузоместах

`POST /v2/cargoes/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supplies` — array[object] **обязательный**. Информация о поставках.
  - `cargo_ids` — array[string<int64>] **обязательный**. Идентификаторы грузомест.
  - `supply_id` — integer<int64> **обязательный**. Идентификатор поставки.

## Ответы

**200** — Информация о грузоместах

- `supplies` — array[object]. Информация о грузоместах и транспортных грузоместах.
  - `bundle_id` — string. Идентификатор товарного состава.
  - `cargoes` — array[object]. Грузоместа.
    - `bundle_id` — string. Идентификатор товарного состава.
    - `cargo_id` — integer<int64>. Идентификатор грузоместа.
    - `content_type` — string (UNSPECIFIED, MONO, MIX, NONE). Тип ассортимента грузоместа: - `UNSPECIFIED` — не определён; - `MONO` — палета-моно или коробка-моно; - `MIX` — палета-микс или коробка-микс; - `NONE` — отсутствует. По умолчанию: `UNSPECIFIED`.
    - `placement_zone_type` — string (UNSPECIFIED, UNDEFINED, TYPE_SINGLE, MULTI). Тип зоны размещения: - `UNSPECIFIED` — не требуется распределение по зонам размещения; - `UNDEFINED` — не определён; - `SINGLE` — одинаковая зона размещения в составе грузоместа; - `MULTI` — разные зоны размещения в составе грузоместа. По умолчанию: `UNSPECIFIED`.
    - `tracking_info` — object. Отслеживание грузоместа.
      - `arrival_at` — object. Информация о приёме грузоместа.
        - `date` — string<date-time>. Дата приёма грузоместа.
        - `timezone_info` — object. Часовой пояс.
          - `iana_name` — string. Название часового пояса.
          - `offset` — integer<int64>. Смещение часового пояса от UTC-0 в секундах.
      - `status` — string (UNSPECIFIED, READY_TO_SUPPLY, REFUSED, ON_WAREHOUSE, NOT_DELIVERED, ACCEPTING, PROCESSED, ON_POINT_SHIPMENT, ON_TRANSIT_WAREHOUSE, LOST, CREATED, DELETED…). Статус грузоместа: - `UNSPECIFIED` — не определён; - `READY_TO_SUPPLY` — готово к отгрузке; - `REFUSED` — отказано; - `ON_WAREHOUSE` — на складе размещения; - `NOT_DELIVERED` — не сдано; - `ACCEPTING` — приёмка; - `PROCESSED` — обработано; - `ON_POINT_SHIPMENT` — на точке отгрузки; - `ON_TRANSIT_WAREHOUSE` — в пути; - `LOST` — потеряно; - `CREATED` — создано; - `DELETED` — удалено; - `DECLARED_IN_TRANSPORT_CARGO` — заявлено в транспортном грузоместе. По умолчанию: `UNSPECIFIED`.
      - `type` — string (UNSPECIFIED, EXPECTED_ARRIVAL, ACTUAL_ARRIVAL). Тип отслеживания грузоместа: - `UNSPECIFIED` — не определён; - `EXPECTED_ARRIVAL` — плановая дата отгрузки; - `ACTUAL_ARRIVAL` — фактическая дата отгрузки. По умолчанию: `UNSPECIFIED`.
    - `transport_cargo_id` — integer<int64>. Идентификатор транспортного грузоместа.
    - `type` — string (UNSPECIFIED, BOX, PALLET). Тип грузоместа: - `UNSPECIFIED` — не определён; - `BOX` — коробка; - `PALLET` — палета. По умолчанию: `UNSPECIFIED`.
  - `cargoes_bundle_id` — string. Товарный состав грузомест.
  - `limits` — object. Количество грузомест и товаров в поставке.
    - `max_box_count` — integer<int32>. Максимальное количество коробок.
    - `max_box_sku_count` — integer<int32>. Максимальное количество товаров в коробке.
    - `max_pallet_count` — integer<int32>. Максимальное количество палет.
    - `max_transport_pallet_count` — integer<int32>. Максимальное количество транспортных грузомест.
  - `supply_id` — integer<int64>. Идентификатор поставки.
  - `transport_cargoes` — array[object]. Информация о транспортных грузоместах.
    - `box_count` — integer<int32>. Количество грузомест в транспортном грузоместе.
    - `summary_bundle_id` — string. Идентификатор товарного состава транспортного грузоместа.
    - `tracking_info` — object. Отслеживание транспортного грузоместа.
      - `arrival_at` — object. Информация о приёме транспортного грузоместа.
        - `date` — string<date-time>. Дата приёма транспортного грузоместа.
        - `timezone` — object. Часовой пояс.
          - `iana_name` — string. Название часового пояса.
          - `offset` — integer<int64>. Смещение часового пояса от UTC-0 в секундах.
      - `status` — string (UNSPECIFIED, READY_TO_SUPPLY, REFUSED, ON_WAREHOUSE, NOT_DELIVERED, ON_POINT_SHIPMENT, ON_TRANSIT_WAREHOUSE, LOST, CREATED, CARGO_DISASSEMBLED). Статус транспортного грузоместа: - `UNSPECIFIED` — не определён; - `READY_TO_SUPPLY` — готово к отгрузке; - `REFUSED` — отказано; - `ON_WAREHOUSE` — на складе размещения; - `NOT_DELIVERED` — не сдано; - `ON_POINT_SHIPMENT` — на точке отгрузки; - `ON_TRANSIT_WAREHOUSE` — в пути; - `LOST` — потеряно; - `CREATED` — создано; - `CARGO_DISASSEMBLED` — удалено. По умолчанию: `UNSPECIFIED`.
      - `type` — string (UNSPECIFIED, EXPECTED_ARRIVAL, ACTUAL_ARRIVAL). Тип отслеживания транспортного грузоместа: - `UNSPECIFIED` — не определён; - `EXPECTED_ARRIVAL` — плановая дата отгрузки; - `ACTUAL_ARRIVAL` — фактическая дата отгрузки. По умолчанию: `UNSPECIFIED`.
    - `transport_cargo_id` — integer<int64>. Идентификатор транспортного грузоместа.
    - `type` — string (UNSPECIFIED, PALLET). Тип грузоместа: - `UNSPECIFIED` — не определён; - `PALLET` — палета. По умолчанию: `UNSPECIFIED`.

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
