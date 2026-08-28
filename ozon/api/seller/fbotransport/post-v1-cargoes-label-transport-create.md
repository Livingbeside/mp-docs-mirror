---
title: Сгенерировать этикетки транспортных грузомест по идентификатору грузоместа
api: ozon-seller
method: POST
path: /v1/cargoes/label/transport/create
operation_id: CargoesLabelTransportCreate
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: dda31633f3b4bad8
---

# Сгенерировать этикетки транспортных грузомест по идентификатору грузоместа

`POST /v1/cargoes/label/transport/create`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev. [Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `supply_id` — integer<int64> **обязательный**. Идентификатор поставки. Получите значение параметра методом [/v3/supply-order/get](#operation/SupplyOrderGet).
- `transport_cargo_ids` — array[string<int64>]. Идентификаторы транспортных грузомест. Если ничего не передать, в ответе вернутся этикетки для всех транспортных грузомест в поставке.

## Ответы

**200** — Этикетки сгенерированы

- `error_reasons` — array[string (INVALID_STATE, OPERATION_NOT_FOUND, OPERATION_FAILED, SUPPLY_NOT_BELONG_CONTRACTOR, SUPPLY_NOT_BELONG_COMPANY, SUPPLY_IS_EMPTY, CARGOES_NOT_FOUND)]. Ошибки при генерации этикеток транспортных грузомест: - `INVALID_STATE` — недопустимое состояние поставки; - `OPERATION_NOT_FOUND` — операция не найдена; - `OPERATION_FAILED` — операция завершилась с ошибкой; - `SUPPLY_NOT_BELONG_CONTRACTOR` — поставка не принадлежит юридическому лицу; - `SUPPLY_NOT_BELONG_COMPANY` — заявка на поставку не принадлежит продавцу; - `SUPPLY_IS_EMPTY` — в поставке нет грузомест; - `CARGOES_NOT_FOUND` — грузоместа не найдены.
- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/cargoes/label/transport-by-order/status](#operation/CargoesLabelTransportStatus).

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
