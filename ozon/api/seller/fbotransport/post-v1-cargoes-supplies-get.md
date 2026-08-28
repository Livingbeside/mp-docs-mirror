---
title: Получить информацию о грузоместах в поставках
api: ozon-seller
method: POST
path: /v1/cargoes/supplies/get
operation_id: CargoesSuppliesGet
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: c0778cd53161eb35
---

# Получить информацию о грузоместах в поставках

`POST /v1/cargoes/supplies/get`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev. [Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_ids` — array[string<int64>] **обязательный**. Список идентификаторов поставок.

## Ответы

**200** — Информация о грузоместах в поставках

- `not_found_supply_ids` — array[string<int64>]. Поставки, которые не удалось найти.
- `supplies_cargoes` — array[object]. Информация о грузоместах в поставках.
  - `bundle_id` — string. Идентификатор состава поставки.
  - `cargoes_without_transport_cargoes` — array[object]. Грузоместа, которые не связаны с транспортными грузоместами.
    - `barcode` — string. Штрихкод грузоместа.
    - `bundle_id` — string. Идентификатор состава грузоместа.
    - `cargo_id` — integer<int64>. Идентификатор грузоместа.
  - `supply_id` — integer<int64>. Идентификатор поставки.
  - `transport_cargoes` — array[object]. Список транспортных грузомест в поставке.
    - `bundle_id` — string. Идентификатор состава грузоместа.
    - `cargoes` — array[object]. Грузоместа в транспортном грузоместе.
      - `barcode` — string. Штрихкод грузоместа.
      - `bundle_id` — string. Идентификатор состава грузоместа.
      - `cargo_id` — integer<int64>. Идентификатор грузоместа.
    - `transport_cargo_id` — integer<int64>. Идентификатор транспортного грузоместа.
    - `type` — string (PALLET). Тип транспортного грузоместа: `PALLET` — палета.

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
