---
title: Чек-лист по установке грузомест FBO
api: ozon-seller
method: POST
path: /v1/cargoes/rules/get
operation_id: CargoesAPI_CargoesRulesGet
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: adde5b1f724ea964
---

# Чек-лист по установке грузомест FBO

`POST /v1/cargoes/rules/get`

Метод для получения чек-листа с правилами по установке грузомест.

## Запрос

**Тело запроса** (`application/json`):

- `supply_ids` — array[string<int64>] **обязательный**. Список идентификаторов поставок в заявке. Максимум 100 идентификаторов.

## Ответы

**200** — Чек-лист по установке грузомест

- `supply_check_lists` — array[object]. Список чек-листов с правилами заполнения грузомест по поставкам.
  - `cargoes_presents_rule` — object. Правило указания грузомест.
    - `cargo_count_per_type` — array[object]. Количество грузомест каждого типа.
      - `count` — integer<int32>. Количество грузомест.
      - `type` — string (BOX, PALLET). Тип грузоместа: - `BOX` — коробка, - `PALLET` — палета.
    - `count` — integer<int32>. Общее количество грузомест.
    - `satisfied` — boolean. `true`, если грузоместа указаны.
  - `edit_deadline_expire_rule` — object. Правило крайнего срока редактирования грузомест.
    - `is_applicable` — boolean. `true`, если правило применимо к текущей поставке.
    - `is_required` — boolean. `true`, если правило обязательно для текущей поставки.
    - `satisfied` — boolean. `true`, если крайний срок для редактирования не наступил.
  - `expire_dates_presented_rule` — object. Правило указания сроков годности для товаров.
    - `count_sku_with_expiration` — integer<int32>. Количество SKU с корректным сроком годности.
    - `count_sku_with_expiration_filled` — integer<int32>. Количество SKU, для которых обязателен срок годности.
    - `is_applicable` — boolean. `true`, если правило применимо к текущей поставке.
    - `is_required` — boolean. `true`, если правило обязательно для текущей поставки.
    - `satisfied` — boolean. `true`, если сроки годности указаны корректно.
  - `is_valid_distribution_rule` — object. Правило совпадения составов грузомест с составом поставки.
    - `count_distributed_sku` — integer<int32>. Количество SKU, которые совпадают с поставкой.
    - `count_sku_total` — integer<int32>. Общее количество SKU.
    - `is_applicable` — boolean. `true`, если правило применимо к текущей поставке.
    - `percents_int` — integer<int32>. Процент совпадения состава грузомест с составом поставки.
    - `satisfied` — boolean. `true`, если состав грузомест совпадает с составом поставки.
  - `package_units_with_distribution_rule` — object. Правило заполнения состава грузомест.
    - `count_all` — integer<int32>. Общее количество грузомест.
    - `count_with_distribution` — integer<int32>. Количество заполненных грузомест.
    - `is_applicable` — boolean. `true`, если правило применимо к текущей поставке.
    - `is_required` — boolean. `true`, если правило обязательно для текущей поставки.
    - `satisfied` — boolean. `true`, если указаны составы для всех грузомест.
  - `placement_zones_rule` — object. Правило распределения товаров в грузоместах по зонам размещения.
    - `count_cargoes_all` — integer<int32>. Количество грузомест.
    - `count_cargoes_with_mono_placement_zone` — integer<int32>. Количество грузомест с распределением по зонам размещения.
    - `is_applicable` — boolean. `true`, если правило применимо к текущей поставке.
    - `satisfied` — boolean. `true`, если товары во всех грузоместах распределены по зонам размещения.
  - `supply_id` — integer<int64>. Идентификатор поставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
