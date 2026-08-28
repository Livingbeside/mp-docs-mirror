---
title: Получить статус создания транспортного грузоместа
api: ozon-seller
method: POST
path: /v1/cargoes/transport/create/status
operation_id: CargoesTransportCreateStatus
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1b8c15647a84a22a
---

# Получить статус создания транспортного грузоместа

`POST /v1/cargoes/transport/create/status`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev. [Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `operation_id` — string. Идентификатор операции из метода [/v1/cargoes/transport/create](#operation/CargoesTransportCreate).

## Ответы

**200** — Статус

- `error_reasons` — array[string (SUPPLY_NOT_FOUND, WAREHOUSE_LIMITS_EXCEED, SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR, SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY, PALLET_SUPPLY_CONTAINS_BOXES, SUPPLY_CARGOES_IS_FINALIZED, SUPPLY_CARGOES_LOCKED, OPERATION_NOT_FOUND, ETTN_IS_UPLOADED, BOX_SUPPLY_CONTAINS_PALLETS, UNDEFINED)]. Ошибки при создании транспортных грузомест: - `SUPPLY_NOT_FOUND` — поставка не найдена; - `WAREHOUSE_LIMITS_EXCEED` — превышены лимиты склада; - `SUPPLY_DOES_NOT_BELONG_TO_THE_CONTRACTOR` — заявка на поставку не принадлежит юридическому лицу; - `SUPPLY_DOES_NOT_BELONG_TO_THE_COMPANY` — заявка на поставку не принадлежит продавцу; - `PALLET_SUPPLY_CONTAINS_BOXES` — палетная поставка не может содержать коробки; - `SUPPLY_CARGOES_IS_FINALIZED` — нельзя редактировать заявку на поставку; - `SUPPLY_CARGOES_LOCKED` — другой процесс блокирует редактирование грузомест поставки; - `OPERATION_NOT_FOUND` — операция не найдена; - `ETTN_IS_UPLOADED` — нельзя редактировать поставку с загруженной эТТН; - `BOX_SUPPLY_CONTAINS_PALLETS` — поставка может содержать только коробки; - `UNDEFINED` — неизвестная ошибка.
- `result` — object. Созданные транспортные грузоместа.
  - `transport_cargoes` — array[object]. Информация о созданных транспортных грузоместах.
    - `id` — integer<int64>. Идентификатор транспортного грузоместа.
    - `type` — string (PALLET). Тип транспортного грузоместа: `PALLET` — палета.
- `status` — string (SUCCESS, IN_PROGRESS, FAILED). Статус создания транспортных грузомест: - `SUCCESS` — успешно; - `IN_PROGRESS` — в процессе; - `FAILED` — ошибка.

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
