---
title: Сгенерировать этикетки для транспортных грузомест по идентификатору поставки
api: ozon-seller
method: POST
path: /v1/cargoes/label/transport-by-order/create
operation_id: CargoesLabelTransportByOrderCreate
tags:
  - FBOTransport
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1655cb35b76adfd4
---

# Сгенерировать этикетки для транспортных грузомест по идентификатору поставки

`POST /v1/cargoes/label/transport-by-order/create`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2179-Novye-beta-metody-dlia-raboty-s-transportnymi-gruzr/) в сообществе разработчиков Ozon for dev. [Подробнее о работе с транспортными грузоместами](https://dev.ozon.ru/start/525-Rabota-s-transportnymi-gruzomestami-TGM-v-postavkakh-FBO/)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `order_id` — integer<int64> **обязательный**. Идентификатор поставки. Получите значение параметра методом [/v3/supply-order/get](#operation/SupplyOrderGet).

## Ответы

**200** — Этикетки сгенерированы

- `error_reasons` — array[string (ORDER_NOT_FOUND, OPERATION_NOT_FOUND, OPERATION_FAILED, ALL_SUPPLIES_SKIPPED, LABELS_COUNT_EXCEED, UNDEFINED)]. Ошибки при генерации этикеток транспортных грузомест: - `ORDER_NOT_FOUND` — заявка не найдена; - `OPERATION_NOT_FOUND` — операция не найдена; - `OPERATION_FAILED` — операция завершилась с ошибкой; - `ALL_SUPPLIES_SKIPPED` — нет этикеток для поставок; - `LABELS_COUNT_EXCEED` — превышено количество генерируемых этикеток; - `UNDEFINED` — неизвестная ошибка.
- `operation_id` — string. Идентификатор операции. Получите статус операции методом [/v1/cargoes/label/transport-by-order/status](#operation/CargoesLabelTransportByOrderStatus).

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
